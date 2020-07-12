FROM ubuntu:latest

# update
RUN apt-get -y update && \
    apt-get install -y \
        sudo \
        vim \
        wget

#install anaconda3
WORKDIR /opt
# download anaconda package and install anaconda
# archive -> https://repo.continuum.io/archive/
RUN wget https://repo.continuum.io/archive/Anaconda3-2020.02-Linux-x86_64.sh && \
    sh Anaconda3-2020.02-Linux-x86_64.sh -b -p /opt/anaconda3 && \
    rm -f Anaconda3-2020.02-Linux-x86_64.sh
# set path
ENV PATH /opt/anaconda3/bin:$PATH

COPY requirements.txt /opt/requirements.txt

# update pip and conda
RUN pip install --upgrade pip && \
    pip install -r /opt/requirements.txt

WORKDIR /

# execute jupyterlab as a default command
# jupyter lab --ip=0.0.0.0 --allow-root --LabApp.token=''
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--allow-root", "--LabApp.token=''"]