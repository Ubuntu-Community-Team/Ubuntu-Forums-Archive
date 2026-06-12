---
title: "Docker won't build a container on Ubuntu 14.04 via AWS"
date: 2015-05-10
forum: Virtualisation
---

### Post by RandallHere on 2015-05-10
I'm using Ubuntu 14.04 via AWS.


My Docker build is failing:
```
sudo docker build -t nginx_img_1 .

```

I see these errors (among others):

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages 404 Not Found [IP: 91.189.91.15 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages 404 Not Found [IP: 91.189.91.15 80]

```

I cannot download the packages themselves to try to get Docker to work. Those URLs are indeed broken: just try to go them manually in a web browser. Someone else out there is using Docker on Ubuntu. What are those people doing? Is there a configuration file that I can use to circumvent this error?

---

### Post by Habitual on 2015-05-11
Show us your Dockerfile. (Sanitize it if necessary, shouldn't be)

[http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/](http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/)

On your terminal, issue this command and report the output:
```
docker version | grep "Server version"
lsb_release -dc && uname -r
```

There's a few (more than 12) nginx images on docker.com, would one of those suffice?
Have you ever built anything before using "docker build" ?

---

### Post by RandallHere on 2015-05-11
Here is my Dockerfile (taken from [https://www.digitalocean.com/community/tutorials/docker-explained-how-to-containerize-and-use-nginx-as-a-proxy):](https://www.digitalocean.com/community/tutorials/docker-explained-how-to-containerize-and-use-nginx-as-a-proxy):)

```
############################################################
# Dockerfile to build Nginx Installed Containers
# Based on Ubuntu
############################################################

# Set the base image to Ubuntu
FROM ubuntu

# File Author / Maintainer
MAINTAINER Maintaner Name

# Install Nginx

# Add application repository URL to the default sources
RUN echo "deb http://archive.ubuntu.com/ubuntu/ raring main universe" >> /etc/apt/sources.list

# Update the repository
RUN apt-get update

# Install necessary tools
RUN apt-get install -y nano wget dialog net-tools

# Download and Install Nginx
RUN apt-get install -y nginx

# Remove the default Nginx configuration file
RUN rm -v /etc/nginx/nginx.conf

# Copy a configuration file from the current directory
ADD nginx.conf /etc/nginx/

# Append "daemon off;" to the beginning of the configuration
RUN echo "daemon off;" >> /etc/nginx/nginx.conf

# Expose ports
EXPOSE 80

# Set the default command to execute
# when creating a new container
CMD service nginx start
```

<eof>

docker version | grep "Server version"
Server version: 1.6.1


Description: Ubuntu 14.04.2 LTS
Codename:    trusty
3.13.0-52-generic

"There's a few (more than 12) nginx images on docker.com, would one of those suffice?"

Maybe.  I've tried.  Can you recommend one?

"Have you ever built anything before using "docker build" ? "

I'm not sure.  I guess my answer is "no."

---

### Post by Habitual on 2015-05-12
Excellent reference and starting point, that [article]("https://www.digitalocean.com/community/tutorials/docker-explained-how-to-containerize-and-use-nginx-as-a-proxy").
I intend to follow those instructions here locally and on another non-AWS host using 1.6.1 also

[jwilder/nginx-proxy]("https://registry.hub.docker.com/u/jwilder/nginx-proxy/") got some high praise on the #docker@freenode.irc channel.
Looks pretty straight forward and I intend to have a run through this myself, *I'm just not sure it will be today*.

Can you build this on any other non-AWS host successfully?
Maybe you can make some progress with the jwilder proxy in the meantime.

subscribed with interest...

---

### Post by Habitual on 2015-05-12
After stepping through the steps listed under "[Building a Docker Container With Nginx Installed]("https://www.digitalocean.com/community/tutorials/docker-explained-how-to-containerize-and-use-nginx-as-a-proxy")"
I have these notes:
```
### 05/12/2015 09:54:56 AM
### nginx build
### https://www.digitalocean.com/community/tutorials/docker-explained-how-to-containerize-and-use-nginx-as-a-proxy
docker pull ubuntu
docker run -i -t -p 80:80 ubuntu /bin/bash
echo "deb http://archive.ubuntu.com/ubuntu/ raring main universe" >> /etc/apt/sources.list
apt-get udpate # barfs, so REM'd out the last line in /etc/apt/sources.list and re-ran
apt-get update w\out issue.
```

so, it is my advice that your Dockerfile NOT have the
```
# Add application repository URL to the default sources 
RUN echo "deb http://archive.ubuntu.com/ubuntu/ raring main universe" >> /etc/apt/sources.list
```
Just REM (#) that out 
```
 #RUN echo "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring main universe" >> /etc/apt/sources.list
```from your Dockerfile and re-run 
```
sudo docker build -t nginx_img_1 .
```

And for 
```
# Install necessary tools
RUN apt-get install -y nano wget dialog net-tools
```

I used
```
apt-get install -y linux-image-extra-`uname -r` nano wget dialog net-tools nginx
```
so, your line in the Dockerfile could be
```

# Install necessary tools
RUN apt-get install -y linux-image-extra-`uname -r` nano wget dialog net-tools nginx
```

Let us know.

---

### Post by Habitual on 2015-05-14
There is something in that Dockerfile that throws some errors.
Massive errors on build: "You chose not to install GRUB to any devices." for which I don't care.
I suggest another nginx image with an emphasis on jwilder/nginx-proxy

See also [https://blog.docker.com/2015/04/tips-for-deploying-nginx-official-image-with-docker/](https://blog.docker.com/2015/04/tips-for-deploying-nginx-official-image-with-docker/)

---

