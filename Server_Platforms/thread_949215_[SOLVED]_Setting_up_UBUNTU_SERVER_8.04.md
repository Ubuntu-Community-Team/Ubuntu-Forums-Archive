---
title: "[SOLVED] Setting up UBUNTU SERVER 8.04"
date: 2008-10-15
forum: Server Platforms
---

### Post by pogztimz on 2008-10-15
hi. i need help and advice on how to install and configure an ubuntu server in our computer laboratory. our laboratory needs are File server, print server, web server and we need user accounts for each student that will authenticate with the server. i have been using ubuntu/edubuntu for over a year now but i am still a complete noob in these matter.or  can u guys pls tell me where can i find HOWTO's to accomplish this. ty in advance. :guitar:

---

### Post by lykwydchykyn on 2008-10-16
howtoforge.com is a good place to start.  Are your clients running Windows or Ubuntu, or are you looking to set up (diskless) thin clients?

---

### Post by pogztimz on 2008-10-16
> **lykwydchykyn said:**
> howtoforge.com is a good place to start.  Are your clients running Windows or Ubuntu, or are you looking to set up (diskless) thin clients?

the clients are running on edubuntu 8.04 on newer machines and edubuntu 6.06 on older machines.

---

### Post by sil3nt on 2008-10-16
> **pogztimz said:**
> hi. i need help and advice on how to install and configure an ubuntu server in our computer laboratory. our laboratory needs are File server, print server, web server and we need user accounts for each student that will authenticate with the server. i have been using ubuntu/edubuntu for over a year now but i am still a complete noob in these matter.or  can u guys pls tell me where can i find HOWTO's to accomplish this. ty in advance. :guitar:

As suggested howtoforge is an excellent place to start you could use the like of this article [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") but you may need to do some further reading into defining your requirements.

I would suggest you use the likes of Webmin (a web based GUI tool) to help manage your server if you are not comfortable yet with CLI.

Good luck

---

### Post by pogztimz on 2008-10-16
> **sil3nt said:**
> As suggested howtoforge is an excellent place to start you could use the like of this article [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") but you may need to do some further reading into defining your requirements.

I would suggest you use the likes of Webmin (a web based GUI tool) to help manage your server if you are not comfortable yet with CLI.

Good luck

hmm. i will take it into great consideration.. can u give me a link pls.

---

### Post by lykwydchykyn on 2008-10-16
If you have a decent piece of hardware for a server (multi-core processor and several GB of RAM), you might try doing an LTSP server and turning the clients into diskless terminals.  That right away nullifies the file, print, and authentication issues.  The cons are that you need a whopping great server to power more than a handful of clients, and you have created a single point of failure for the whole lab.  

Otherwise, these would be my suggestions:
 - File sharing: NFS since you have all linux clients
 - Print: CUPS -- if you enable sharing on the server, and listening on the clients, it sets up automatically.
 - Web: Apache, of course.  Look for any of the millions of LAMP how-to's
 - Authentication: OpenLDAP is what you need, but it's a bit tricky to deal with.  I believe ebox has some kind of easy interface for this, but I am not experienced with it.  The old solution was to use NIS, but it's not considered secure.

In fact, I briefly checked out ebox (web interface) and it seems to have all these services nicely integrated.  Someone more experienced with ebox may want to comment on this.

---

### Post by pogztimz on 2008-10-17
i have successfully installed Ubuntu Server 8.04. i selected LAMP, SAMBA and CUPS. 

for now i want to do certain tasks. e.g. 

1. how do i make the clients authenticate to it, so that unauthorized use can be avoided. by the way we have 20 clients.

2. i want to create a folder wherein all documents will be stored, and also i want to create user accounts for each student.

3. i also want this server to be our print server.


can u guys please help me.. ty.. :)

---

### Post by subbzz on 2008-10-17
Hi,

Today I installed Ubunto 8.04, but unable to install CVS, the error is always "E: Couldn't find package cvs".

Can you please help me??

Thanks,
Subbzz

---

### Post by pogztimz on 2008-10-19
> **subbzz said:**
> Hi,

Today I installed Ubunto 8.04, but unable to install CVS, the error is always "E: Couldn't find package cvs".

Can you please help me??

Thanks,
Subbzz

try running this on your terminal.. 
1. sudo apt-get update
2. sudo apt-get upgrade
3. sudo apt-get install cvs

---

### Post by gpsmikey on 2008-10-19
You don't say what the clients are for the "file server" and "print server" applications -- if they are windows machines, you need to check out Samba.  See the samba site for documentation (normally Samba is installed as part of the server install ... I think - can't remember for sure if I had to add it now ... more coffee is required):
[http://us3.samba.org/samba/](http://us3.samba.org/samba/) 

Another good book is (free pdf version):
[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)

mikey

---

### Post by lykwydchykyn on 2008-10-19
> **gpsmikey said:**
> You don't say what the clients are for the "file server" and "print server" applications -- if they are windows machines, you need to check out Samba.  See the samba site for documentation (normally Samba is installed as part of the server install ... I think - can't remember for sure if I had to add it now ... more coffee is required):
[http://us3.samba.org/samba/](http://us3.samba.org/samba/) 

Another good book is (free pdf version):
[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)

mikey

He did say, the clients are running edubuntu.  No windows involved.

So I would personally not recommend messing with Samba, though it's not entirely out of the question.

---

### Post by thiyagu912 on 2008-10-19
Hi I am using Ubuntu 8.04 server and win clients. I am using the server for file sharing using samba. I want to know how to set a passwords for those folders. 

Please help me. I am new to Linux.

Thanks
Thiyagu

---

### Post by pogztimz on 2008-10-20
> **thiyagu912 said:**
> Hi I am using Ubuntu 8.04 server and win clients. I am using the server for file sharing using samba. I want to know how to set a passwords for those folders. 

Please help me. I am new to Linux.

Thanks
Thiyagu

hey.. check this out.. i hope it can help u..

[http://us3.samba.org/samba/docs/using_samba/toc.html]("http://us3.samba.org/samba/docs/using_samba/toc.html")

---

### Post by pogztimz on 2008-10-22
> **lykwydchykyn said:**
> He did say, the clients are running edubuntu.  No windows involved.

So I would personally not recommend messing with Samba, though it's not entirely out of the question.

is there a way to view webpages in a CLI?

---

### Post by lykwydchykyn on 2008-10-22
> **pogztimz said:**
> is there a way to view webpages in a CLI?

Check out:
 - lynx
 - links
 - w3m

All available in the repositories.

---

### Post by Iowan on 2008-10-22
**elinks** is the new version.

---

### Post by pogztimz on 2008-10-29
> **lykwydchykyn said:**
> Check out:
 - lynx
 - links
 - w3m

All available in the repositories.

  	
Policy: 	
i would like to thank u very much for ur help. the links that u gave prove to be helpful in my case.. however, there is so much tasks that must be done. i have successfully installed ubuntu server 8.04 detailed here [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts").

i also installed ebox platform, and now i am able to access the server remotely.. i followed the steps discussed here. [http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server]("http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server")..


as what i have stated earlier in this post, there are still tasks to be done, namely;

given with the present configuration of my ubuntu server,

1. how do i configure the clients to make it authenticate with the server. btw, we have 15 clients at the moment. the number of computers may increase soon.

2. how do i create separate user accounts for the students.

help me guys... :) cheers!!!

---

### Post by whyiamhere on 2008-11-07
apt-get is notworking

I have tried all methods 

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

I have got stuck this big problem. can someone help me regarding this problem.

I am using ubuntu server 8.04

---

### Post by alcfez on 2008-11-10
Hello,
I am having save issues, can anyone help please?
Thank you
a

---

### Post by Iowan on 2008-11-10
@alcfez & whyiamhere: 
I'd recommend you start your own thread(s). It'll let us concentrate on your problem(s), and the thread(s) can be marked [SOLVED] when/if it is (they are).

---

