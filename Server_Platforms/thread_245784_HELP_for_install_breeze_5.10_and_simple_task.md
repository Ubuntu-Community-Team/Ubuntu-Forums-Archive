---
title: "HELP for install breeze 5.10 and simple task"
date: 2006-08-28
forum: Server Platforms
---

### Post by dirkdekker on 2006-08-28
I'm working on a simple software task on Ububu's Breezy version 5.10. It is running for one hour now and I want to add software.
Any Q. are:

- I have to download pound-2.1.tgz from [www.apsis.ch](www.apsis.ch). How?
- or, How do I copy software to this OS. ( floppy?)
- then Unpack it. How?

Then this:  Warning: as Pound is a multi-threaded program it requires a version of OpenSSL with thread support. 
- is 5.10 multi-threading and if yes: How will I start the OpenSSL?

Maybe someone likes to help me with this questions.
Dirk

---

### Post by az on 2006-08-28
sudo apt-get install pound.

It is in the repositories - you have to enable the universe repo.

And why are you running Breezy?  I would recommend you dist-upgrade to Dapper.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

or

[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by dirkdekker on 2006-08-28
Hi Azz, thanks for the reply. In mine opinion to install pound (  a reverse proxy, load balancer and HTTPS front-end for Web servers) what I need asap. So I installed a simple Linux OS because I had the CD of Ubuntu ready by hand. I'm absolutly not an expert in Linux either. So please maybe you tell me how I transport from a Windows OS to floppy-disk the sofware named pound-2.1.tgz into the Ubuntu program. On this moment the floppy drive in the Ubuntu is not working and I dont know why that is.

Thanks for your help, Dirk

---

### Post by az on 2006-08-28
If that machine is on the net, you can install pound from the repositories on line.  That's the preferred method.  You have more control over your system if you use the package manager and the repositories and avoid installing things directly from upstream.

As well, you can dist-upgrade your machine from the net in the same way - you will then be running a current and secure Dapper.

---

### Post by dirkdekker on 2006-08-29
that machine is on the net , but I can't find any example how to reach the net from the prompt. I tried it with FTP to get the tar-file from a MSDOS machine, but that will not work. If you have an example to use the net for this purpose and get the pound-2.1.tar file from there and an example how to run then package manager your oar og great help for me!

---

### Post by az on 2006-08-29
[https://help.ubuntu.com/community/CommandLinePackageManagement](https://help.ubuntu.com/community/CommandLinePackageManagement)

---

### Post by dirkdekker on 2006-08-29
Hi Azz, thanks for the update. I refreshed my info now by reading all repositeries/Commandline you mentioned. Did update the repositories by changing the sources.list :
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe 
Ran the sudo apt-get update and after reboot all should be happy now..

But can't make up how to make any connection from the commandline to get the ( or any) files from internet!
(btw: it's a server installation so no GUI)
Any help i do appreciate!!
Dirk

---

### Post by az on 2006-08-29
What kind of internet connection do you have?

ADSL, Cable, dial-up?  Are you using an ethernet port or wireless?

What do you get with 

ifconfig

---

### Post by dirkdekker on 2006-08-29
hi nice to have you back agian.! i have two nic's and from the commandprompt can ping to either ip-address in the world. Have a Cable connection 2Mbit/1Mbit and the server is behind a firewall like the others here in the room.
The firewall will redirect anyway because the upload from the sources.list file was successful ! That means : connected to the net.
ifconfig shows eth0 and eth1, both working with the local address range 192.168.8.nnn and class C mask plus gateway.

But now I don't know how to reach the world on the net with a commandline like : ( http??)
dirk

---

### Post by az on 2006-08-29
> **dirkdekker said:**
> 
But now I don't know how to reach the world on the net with a commandline like : ( http??)
dirk

apt-get downloads and installes the packages from the net and you just said you updated fine.  

You can't run

sudo apt-get dist-upgrade?  

What do you mean?

---

### Post by dirkdekker on 2006-08-29
hi,yes I can and run sudo apt-get dist-upgrade. It has worked allready and after the reboot I hope everything needed is installed now.
I have only a commandline. What I do now to connect to the internet and download the nessecary files I have to use for installing the aplication: pound ( pound-2.1.tgz from the URL: [http://www.apsis.ch/pound/index_html](http://www.apsis.ch/pound/index_html) )

Dirk

---

### Post by az on 2006-08-29
sudo apt-get install pound


Make sure that you have the universe repository enabled.

---

### Post by dirkdekker on 2006-08-29
Hi Azz, you are genious! I did never now that pound was one of the repositories and a package file ! The commandline instructions  loaded pound 1.9-1  in the /etc/defauld directory . Is that the same file as mentioned in the  URL: [http://www.apsis.ch/pound/index_html??](http://www.apsis.ch/pound/index_html??) 

Now i can use it to follow the instructions :

   Unpack. 
   Do the usual thing:

            ./configure

How do I unpack? and than a configure that must result in a make-file??


And, do you eventualy use also pound as reverse proxy, load balancer and HTTPS front-end for Web servers ??

 pound-2.1.tgz is the latest version and that will also be loaded as a package file anywhere?

I hope you dont mind so many questions... :)
Dirk

---

### Post by az on 2006-08-29
They are binary packages - you don't nede to compile them.  They are ready to go.

You now have the 1.9 version.  If you really really need to most current version, then you will want to remove that package and compile the upstream source yourself.

It is easier to keep up-to-date with security patches by using the version in the repositories, though.  If there is a new version available in the repos, tt is updated by the package manager every time you run

sudo apt-get upgrade

---

### Post by dirkdekker on 2006-08-29
Hi Azz, thanks! Do you make use of pound yourself?
In the directory /etc/default I found pound and also: man pound, the helpfile.

Now I have to run it.
I read this:  'Make sure Pound gets started on boot. Read the man page for available options and examples.'

How its possible to see if pound is running?

Dirk

---

### Post by az on 2006-08-29
I don't run it.

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=pound&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=pound&version=dapper&arch=i386)

I am sure that it is started upon boot, since it provides /etc/init.d scripts.

---

### Post by dirkdekker on 2006-08-29
Hi Azz, is there a command to see what is running and/or installed ?
When I hit this: top than i dont see pound...
Dirk

---

