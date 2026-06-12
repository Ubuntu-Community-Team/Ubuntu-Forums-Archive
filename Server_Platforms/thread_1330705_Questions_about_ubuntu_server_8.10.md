---
title: "Questions about ubuntu server 8.10"
date: 2009-11-18
forum: Server Platforms
---

### Post by GSI on 2009-11-18
Hello! I have some questions about ubuntu server edition 8.10

1.How much free space do I need?

2. Will 200MB of RAM and 400Mhz CPU be enough to run a test Home server

and the last one

3. Which program should I use to log into the server remotly?

Thanks in advance :)

---

### Post by Cheesemill on 2009-11-18
Your specs are fine for testing Ubuntu Server.
 
Just to let you know Ubuntu Server is command line only, there isn't a GUI installed by default. To connect from another machine just install openssh-server on your server then to connect use ssh from a linux box or use putty from windows.
 
Is there any reason you have decided to install 8.10 instead of 9.10 (the latest) or 8.04 (the long term support version)?

---

### Post by garfonzo on 2009-11-18
I ran a Server with Ubunutu on specs lower than that so you should be good to go. As far as remotely logging in, I believe SSH is installed by default on the server edition of Ubuntu (someone correct me if I'm wrong). 

To log into my server from another machine in the house (all other machines are Windows) is I run putty. That gets me to a console and, like GSI said, the server edition is, rightfully, command line only.

As far as required space, I installed it on a 4GB drive (full OS) but I believe you need a minimum of 500MB hard drive for the OS. Keep in mind that as you add 'features' (different services) you will need more space. However, the space requirements are really low.

---

### Post by GSI on 2009-11-19
Another question...

Do I need to do some special setings when i install the server or i just polug it in an it will work fine?

---

### Post by Cheesemill on 2009-11-19
It depends.

The server will boot OK after install but you have to install and configure any services that you require (apache, mysql, etc). You may also have to set up your networking settings manually during the install depending on your setup.

What are you planning to use the server for?

---

### Post by GSI on 2009-11-19
Well its not very powerful PC so it will be home file server...

I'll be testing it with the small 4gb HDD and if I like it ill buy bigger :)

---

### Post by Cheesemill on 2009-11-19
If you are wanting to share files with Windows machines you have to set up Samba.

Take a look at this link or just google for 'ubuntu samba server', there are loads of good how-to's out there.

[http://www.ghacks.net/2009/09/04/set-up-your-new-ubuntu-server-as-a-samba-server/](http://www.ghacks.net/2009/09/04/set-up-your-new-ubuntu-server-as-a-samba-server/)
(The above link is for 9.04 but should work fine on 9.10 as well)

---

### Post by GSI on 2009-11-19
I could install samba on desktop edition too? 

[http://www.jonathanmoeller.com/screed/?p=532](http://www.jonathanmoeller.com/screed/?p=532)

---

### Post by trundlenut on 2009-11-19
installing Ubuntu desktop on the machine you described above would probably be soooo slooooooow, I think you would be better off with the server version.  If you have another machine with desktop version already on it you could easily install the samba server, you should already have the client installed on it at least.

---

### Post by GSI on 2009-11-20
Yes I do have onther PC with the desktop edition already on and the other PC is my experimental PC...So im testing out different distributions of linux and I will try ubuntu server if I can't get  the PC's ISA sound card running at both channels

---

### Post by Iowan on 2009-11-20
You can (must?) install Samba server on any (Ubuntu) machine you wish to share files (from).

---

