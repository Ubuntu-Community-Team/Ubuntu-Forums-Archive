---
title: "I wish to get some basics of ubuntu server"
date: 2010-11-19
forum: Server Platforms
---

### Post by Rakeshvijayan on 2010-11-19
Hi friend 

I am new user in ubuntu server . I wish to migrate windows server  to ubuntu server

first I install ubuntu in vmware and install ubuntu server  on vmware .But I didn't get grafical interface for that what should  I do . 
if you can please share, after installation what is the fisrt step that  I have to do......
I wish to configure file server,Dns, samba,firwall etc but i don't know how can I gain.I have only  confidence that i got from this forum

---

### Post by endotherm on 2010-11-19
welcome

ubuntu server edition does not use an graphical interface, so nothing is wrong with your install. if you want to install the gnome desktop package on your server, all you need to do is run this command:

```

sudo apt-get install ubuntu-desktop

```

after that, if you want to administer the server remotely, I recommend FreeNX
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) . 

if you don;t want to install a GUI, there are several web-based administration frameworks for linux servers, like Webmin. 

as for each of your services, they are entire threads unto themselves, and there are how-to's posted here for all of them, so search around the forums for each service you wish to install. this may be a great starting place: [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
have fun

---

### Post by CharlesA on 2010-11-19
endotherm pretty much covered it.

IMO if you want a GUI, install the desktop edition, or read this: [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

I don't run a GUI on my Ubuntu server, but I do use some web interfaces and forwarding X over SSH helps too.

---

### Post by Rakeshvijayan on 2010-11-22
**lancard** 
Hi 

I installed two lancard in my pc . And I install ubuntu server 10.10..
At install time os ask me for which is the default connection and it show me that 
dhcp not working configure your network manually I give ip 192.168.1.100
and subnet 255.255.255.0 gateway and dns 192.168.1.1...
after I installed server i tried to update and install Desktop i got a message that

"Reading package list done 
Building dependency tree
Reading state information ....Done 
E: Unable to locate package updates"

how can i check the network connections 

and I want share the cdrom with out Desktop

Thanks

---

### Post by drdos2006 on 2010-11-22
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by HermanAB on 2010-11-22
Howdy,

If you want a GUI, just use ordinary Ubuntu.  

If you want a Windows Server-like system with wizards for everything so you can go click happy, use OpenSuse or Mandriva Linux, not Ubuntu.

---

### Post by Spice Weasel on 2010-11-22
Ubuntu Server isn't a very good platform for those who are new to GNU/Linux servering (unless you want to learn the CLI, trust me, it's worth it). If you want graphical configuration tools you should probably try CentOS (DVD) or the Webmin web-based interface.

---

### Post by Rakeshvijayan on 2010-11-25
In windows after dcpromo that os will serve server services , There we can configure services with graphically  I dont want GUI In Ubuntu Because U all are my GUI I can see solution from u

am writing this from my ubuntu 10.10 64bit desktop edition 

am configure server in vmware . I want to learn ubuntu it for only my knowledge...... 

Let me  know which is the service that i want to configure in the ubuntu 

for  server Clint model .I wish to know is it possible that Clint logging to server as windows system (ubuntu server , ubuntu Clint and windows clint )

---

### Post by Rakeshvijayan on 2010-11-25
any one give your smb.conf file configuration as an example

---

### Post by HugoSerrano on 2010-11-25
Hi!

You can get some read here:
[http://doc.ubuntu.com/ubuntu/serverguide/](http://doc.ubuntu.com/ubuntu/serverguide/)

For what I read, you are trying to learn Linux. My advice is that you start with Ubuntu Desktop, and learn from there. 
You can install services in there too, like dhcp, dns, smb... and all the others that you can remember! You got Desktop environment and command line!
It's not good to do it in a production environment because you will get a lot of stuff that you don't need in a server and that means less resources free. I don't have any server with Desktop environment... its against the nature of the thing... (not for a windows user :-P)

Regards!

---

### Post by lennartz on 2010-11-25
Recommended read is The Official Ubuntu Server Book by Kyle Rankin en Banjamin Mako Hil.   It´s the perfect starting point and helped me a lot.

Since I came from being a Windows Admin at first I missed the GUI, especially for file operations.  (moving stuff from the command line is just very boring and slower than with a GUI)

However, I now use Midnight Commander (A `*NIX version of the good old Norton Commander) for these things.   If you don´t know it, it´s a (ASCII) GUI file manager and works perfect.  I even prefer it over dragging and dropping within a desktop environment.
(it´s fast!)

So, I really don´t need the GUI. :)

---

### Post by Rakeshvijayan on 2010-11-26
Thanks . you meen desktop edition also act as server roles ? If it is rigth it will be great for me .....

---

### Post by HugoSerrano on 2010-11-26
> **Rakeshvijayan said:**
> Thanks . you meen desktop edition also act as server roles ? If it is rigth it will be great for me .....

yep... but you will have a lot of stuff that you don't need...

But I think that when you install Ubuntu server you can choose to have graphical environment installed on the installations menu. It's better to have that in a server then have a Desktop acting as a server. 
But try to do everything in command line... one day you will remove the gui! :-)

---

### Post by elico on 2010-11-26
the main question is "why?"
why you want to migrate from windows server?
do you want to gain something?
what you system needs to supply?
i think it's a must to read some and start testing the cli before going to gui.
im using webmin to manage most of my server stuff as a gui interface.
many things are done better for me in cli but still if i want to see it in place webmin does it for me many times.

---

### Post by HugoSerrano on 2010-11-26
Well... don't think that's the right thing to say in here.

Don't need to say a "why" to migrate from MS to Linux. hehe

But from the posts, it seems that it's for learning proposes!

---

### Post by CharlesA on 2010-11-26
I'm running my dev LAMP on an Ubuntu Desktop box, since I can code on it and then test it locally. I had to flub with the hosts file to get apache to stop complaining, but everything is working fine now.

Once the site is done, it's going to my production web server.

---

### Post by ronkmonster on 2010-11-26
You should learn the command line to do as much as possible. You could install webmin and have a web interface to manage some parts of it. I do 80% command line and 20% webmin. Things like samba configuring for file shares I find easier in webmin.

But even if everything can be done in webmin, you should still try everything in command line first to learn things.

---

### Post by Rakeshvijayan on 2011-06-22
Thanks for the great help from you all .........Now I am little bit improve in linux

I am now facing a problem . that on my system have to partitions instead of ext4 and swap ,that is ntfs partitions ,and have two account one is sysadmin and my name csmct....
sysadmin have admin power and  csmct is a user account .....if i login ed as user csmct
,I cant able access those ntfs files .....ubuntu asking me for the sysadmin password authentication ...how can i access those ntfs partitions with rakesh password .... for frequent access I changed both passwords to same (csmct123@)

---

