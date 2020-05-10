# ros-dev-docker
ROS development environment with docker.

## Prerequirements
* Ubuntu 20.04
* docker
* docker-compose
* nvidia-docker2 (Not nvidia-container-toolkit)


## Quickstart
This manual assumes Ubuntu 20.04.
You might use this in another enviromnent with following requirements:
* docker (>=19.03.08)
* docker-compose (>= 1.25.0)
* nvidia-docker2 (>= 2.2.2)
* appropriate nvidia proprietary driver

### Install nvidia proprietary driver
Install appropriate nvidia proprietary driver for your video card.  
Please find detailed instruction on your own because required instruction differs for each enviroment.

### Install docker and dokcer-compose
```
sudo apt install docker.io docker-compose
```

### Install nvidia-docker2

See https://github.com/NVIDIA/nvidia-docker to check more precise infomation.

```
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt install nvidia-docker2
sudo systemctl restart docker
```

### Clone the repository and execute docker-compose

```
git clone https://github.com/ykmarble/ros-dev-docker
cd ros-dev-docker
echo "UID=$(id -u)\nGID=$(id -g)" > .env
docker-compose build
dokcer-compose up
```

You have to set your UID and GID to .env file so that clients (e.g. rviz) can connect mounted X11 socket.

