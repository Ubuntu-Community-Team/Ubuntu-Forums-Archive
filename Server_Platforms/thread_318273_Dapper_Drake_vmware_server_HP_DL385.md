---
title: "Dapper Drake /vmware server /HP DL385"
date: 2006-12-13
forum: Server Platforms
---

### Post by atilla_the_hun on 2006-12-13
Hello from Florida USA, 

Has anyone out there recently run vmware server on an ubuntu version, and if so , which one(s)?  

Background/life story:  I am trying to get an understanding of how to match the vmware server (the free one that is on their site) to play well with Ubuntu.   A step by step guide would be best since I have run into problems with the perl installer script.  ONE of the messages is

"Your kernel was build with gcc version 4.0.3 while you are trying to use /usr/bin/gcc-3.4 version 3.4.6.   This configuration is not supported and vmware server cannot work in such a configuration.   Please either recompile your kernel with  /usr/bin/gcc-3.4 version 3.4.6 or restart /usr/bin/vmware-config-pl with CC environment pointing to the gcc version 4.0.3.  


Ok, and steps I have ALREADY TAKEN include:
   
 - pointing CC to both version of the gcc to no avail.
- trying unsuccessfully compile vmlinuz (says I don't have a makefile, which is true, I have zero files of that order including no GNUmake either).  
- I have currently actually removed the 3.4 version libraries in a feeble attempt to get it to like 4.0.3.  


My current resources include: 
- a live internet connection
- basic understanding of apt-get and apt-cache
-a lot of experience in UNIX as well as other linux distros

I have never compiled a kernel but I also don't have make, and cannot get it when I run apt for some reason (don't ask me why since the thing is very updated).  

Also my cruddy handwritten instructions from a coworker tell me to run the following command which I can't even apt-cache for anything similarly named:  

# apt-get install build-essential linux-headers - 'uname -r'

then run CC=gcc3.4 which works ok but doesn't fix the overall problem.  

My problem, I THINK is that I cannot seem to match the AGES of the vmware software (and therefore the libraries it wants), with the AGES of what came with my recent Dapper 6.0.1 download.   

One reason which leads me to believe this, is because I know that this has been run before on 'Breezy' ---which I now cannot find to download - would've been relatively painless but I guess the good thing is I will now learn how to fix this!  

Thanks in advance. 

Atilla

---

### Post by Tibor60 on 2006-12-23
I did on Dapper without problems with some easy commands:

sudo aptitude install build-essential linux-headers-386 netkit-inetd

(be sure to replace linux-headers-386 with the appropriate package for your architecture such as linux-headers-686 or linux-headers-k7)

 download the tar.gz package from vmware site, and untar it:

tar zxvf Vmware-server-e.x.p.-22088.tar.gz

sudo ./vmware-install.pl

answer the questions of the installer and that was all on my system...

---

### Post by xianthax on 2006-12-23
[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

-xian

---

