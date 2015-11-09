# NOTICE
This repository only distributes a source code of Image Annotation Viewer for a developer. If you are an end user that need the detail information about IAV tools, please visit our home page.
[RegMed Home](http://regmed.hgc.jp)

http://regmed.hgc.jp

# Image Annotation Viewer
Image Annotation Viewer (IAV) is a Web-based image annotation tool. It can store a high-resolution figure, and view scale-free slide smooth. This tool includes a rich user interface for graphical annotation such as shape of a line, circle, rectangle and color pallet. This viewer has an easy administration tools for user management. Additionally you can describe a annotated information for an image as metadata.
![Image Annotation Viewer](https://regmed.hgc.jp/figure/coverview1.png "Image Annotation Viewer")

---

### Preparation of Docker for Mac OSX 

* M-1. Install "Command Line Tools for Xcode".

```
$ xcode-select --install
```

* M-2. Install a package management system of "Homebrew".
 * [http://brew.sh/index.html](http://brew.sh/index.html)

```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

* M-3. Update the package of Homebrew. 

```
$ brew update
$ brew upgrade
```

* M-4. Install application of "VirtualBox".
 * [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

* M-5. Install Boot2Docker and Docker.

```
$ brew install boot2docker docker
```

* M-6. Upgrade Boot2Docker.

```
$ boot2docker upgrade
```

* M-7. Check the IP address assigned using the command of Boot2Docker.

```
$ boot2docker ip
```

---

# Preparation of Docker for Windows
* W-1. Install application of "Windows Docker Client".
 * [https://docs.docker.com/installation/windows/](https://docs.docker.com/installation/windows/)
 * [https://github.com/boot2docker/windows-installer/releases](https://github.com/boot2docker/windows-installer/releases)
 * (Boot2Docker, Boot2Docker Management Tool, Docker, VirtualBox, msysGit are installed)
* W-2. Start Boot2Docker from start menu.
* W-3. Make a note of the IP address and port of DOCKER_HOST displayed at the time of starting. 

---

# Preparation of Docker for Linux
* LC-0. Install Docker from EPEL of Fedora in CentOS 6. (you do not need this process at after version 6.5) 

```
$ sudo rpm -ivh http://ftp.riken.jp/Linux/fedora/epel/6/x86_64/epel-release-6-8.noarch.rpm
```

* LC-0. Install Docker from EPEL of Fedora in CentOS 6. (don't need after version 6.5) 

```
$ sudo rpm -ivh http://ftp.riken.jp/Linux/fedora/epel/6/x86_64/epel-release-6-8.noarch.rpm
```

* LC-1. Update package of yum.

```
$ sudo yum update
```

* LC-2. Install Docker.

```
$ sudo yum install docker-io (in case CentOS 6)
$ sudo yum install docker (in case CentOS 7)
```

* LC-3. Set up to start Docker at the time of boot of CentOS. 

```
$ sudo chkconfig docker on
```

* LC-4. Start Docker service.

```
$ sudo /etc/rc.d/init.d/docker start
```

* LC-5. Inspect a host name, in order to access from a browser to a Web server.

---

# Common process of remote installation for Image Annotation Viewer from Docker Hub
* C-0. Register your account into Docker Hub.
https://registry.hub.docker.com/

* C-1. If you encounter the message of "Cannot connect to the Docker daemon. Is 'docker -d' running on this host?" then you execute next command.

```
$ export $(boot2docker shellinit)
```

* C-2. login to Docker Hub.

```
$ docker login
```

* C-3. Pull container image of annotation image viewer from Docker Hub.

```
$ docker pull komiyama/binder
```

* C-4. Cheak an information of container image.

```
$ docker images
```

* C-5. Start a container as a daemon and assign HTTP port to the contaier.

```
* $ docker run -t -i -d -p 80:80 --name binder komiyama/binder
```

* C-6. Check a sturted container.

```
$ docker ps -a
```

* C-7. Accese http://HOSTNAME:PORT/binder/login/ via a browser.

Example: http://192.168.59.103:10080/binder/login/

* C-8. Default user accounts were registered as each user roles. 

```
Administrator: (ID:admin, Password:adminadmin)
User: (ID:user1, Password:useruser)
Supervisor: (ID:demo1, Password:demodemo)
```

* C-9. Set up the CONTAINER ID into a stop option of Docker at the termination of a container.

```
$ docker stop CONTAINER_ID
```

---

# Common process of local installation for Image Annotation Viewer from Docker Images of TAR file

* C'-1. If you encounter the message of "Cannot connect to the Docker daemon. Is 'docker -d' running on this host?" then you execute next command.

```
$ export $(boot2docker shellinit)
```

* C'-2. Download the TAR file of container image of annotation image viewer from our Web site.
https://regmed.hgc.jp/docker/ImageAnnotationViewer_latest.tar

* C'-3. Load the TAR file in to your docker.

```
$ docker load -i /YOUR/FILE/PATH/AnnotationImageViewer_latest.tar
```

* C'-4. Check an information of container image.

```
$ docker images
```

* C'-5. Set a human redable tag to the loaded IAV image.

```
$ docker tag IMAGE_ID komiyama/binder:latest
```

* C'-6. Start a container as a daemon and assign HTTP port to the container.

```
$ docker run -t -i -d -p 80:80 --name binder komiyama/binder
```

* C'-7. Check a sturted container.

```
$ docker ps -a
```

* C'-8. Accese http://DOCKER_HOST:PORT/binder/login/ via a browser. 
 * Example: http://192.168.59.103:10080/binder/login/

* C'-9. Default user accounts were registered as each user roles. 
 * Administrator: (ID:admin, Password:adminadmin)
 * User: (ID:user1, Password:useruser)
 * Supervisor: (ID:demo1, Password:demodemo)

* C'-10. Set up the CONTAINER ID into an option parameter of docker stop command at the termination of a container.

```
$ docker stop CONTAINER_ID
```
