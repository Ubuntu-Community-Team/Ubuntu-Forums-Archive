---
title: "I can't access local repository from other machines"
date: 2014-10-22
forum: Server Platforms
---

### Post by Pituso on 2014-10-22
Hi, 
First , sorry for my English.
Second
Few days ago, I install a local reposritory in last ubuntu server. 
I installed the repository in /home/user/apt-mirror

I installed apt-mirror
I changed mirror.list , the line set base_path /home/user/apt-mirror.
I run apt-mirror
after some hours y downladed 120Gb. 
below de directory apt-mirror, it was created /mirror/ubunt......../ubuntu ( I don't remember now the exactly route)
ok, 
Ì've created a symlink in /var/www/ubuntu
under /var/www I wrote
ln -s /home/user/apt-mirror/mirror/........../ubuntu  ubuntu

well, 
if in the other machines put the server ip, I can see the default page of apache2, but ip/ubuntu I can't access,  why? :mad:


n the other hand
 if I change and put in sources.list

 deb http: // ip / ubuntu trusty main. ..

 apt-get update fail, it does not Acced to local repository. why again?:mad:

---

### Post by lukeiamyourfather on 2014-10-22
I think by default Apache won't follow symbolic links. Either move the repository mirror there or configure Apache to follow symbolic links.

[http://httpd.apache.org/docs/2.2/urlmapping.html#outside](http://httpd.apache.org/docs/2.2/urlmapping.html#outside)
[http://httpd.apache.org/docs/2.2/mod/core.html#options](http://httpd.apache.org/docs/2.2/mod/core.html#options)

---

