---
title: "pserver"
date: 2009-03-17
forum: Server Platforms
---

### Post by raghurani on 2009-03-17
Hi,

I am unable to set up pserver for CVS in ubuntu
I was able to do it in redhat 7.2. but the same is not working in ubuntu.

The default path it is recognizing which is /var/lib/cvsd/

How do I change this to read a new one.

---

### Post by albandy on 2009-03-17
edit /etc/cvsd/cvsd.conf

---

### Post by raghurani on 2009-03-18
What do I change here? I have the OS in one harddisk and data in another. How do I set the path now? HDD3 is where my data is and HDD1 is where I have OS installed!!!!!!!!!!!Hope Iam clear

---

### Post by albandy on 2009-03-18
you need to define the path of the repository at the end of the file, also you should use cvs commands to generate it.

sudo cvsd-buildroot /path_to_destination
then change the owner of the folder to cvsd
finally initialize the repository: sudo cvs -d /path_to_destination init
also you can add users to your repository:
sudo cvsd-passwd /path_to_destination username


I think you should read cvs documentation

---

### Post by raghurani on 2009-03-19
Can you suggest any cvs documentation please. Thanks for the reply.

---

### Post by albandy on 2009-03-19
[http://sanatio.blogspot.com/2005/12/cvs-server-on-ubuntu.html](http://sanatio.blogspot.com/2005/12/cvs-server-on-ubuntu.html)
[http://www.bernie.net.my/blog/2007/10/08/setting-up-a-cvs-server-in-ubuntu/](http://www.bernie.net.my/blog/2007/10/08/setting-up-a-cvs-server-in-ubuntu/)
[http://manpages.ubuntu.com/manpages/hardy/man5/cvsd.conf.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/cvsd.conf.5.html)
man cvsd.conf

---

### Post by raghurani on 2009-03-19
Can we change the root using "cvsd-buildroot" to point to any new path? we remember using this to set to the default "/var/lib/cvsd". Let me try and let you know.

---

### Post by albandy on 2009-03-19
First edit cvsd.conf, at the end of the file you will find the repo folder
add or modify the repository and finally build it.

---

### Post by raghurani on 2009-03-19
Here are the changes I did "cvsd-buildroot /projects" on command prompt. I could see few files created in /projects. After that I modified cvspserver file accordingly to point to the path of the repository. I added the path of the repository at the end of cvsd.conf file also. Now I am getting new error
Logging in to :pserver:devarani@ubuntucvsserver:2401:/projects/testcvs
cvs [login aborted]: authorization failed: server ubuntuCVSserver rejected access to /projects/testcvs for user devarani

---

### Post by albandy on 2009-03-19
As I said before.

sudo cvsd-passwd /path_to_destination username

---

### Post by raghurani on 2009-03-20
Hi,

I am still getting same error

---

### Post by albandy on 2009-03-20
please attach your cvsd.conf file

---

