---
title: "Nooby- Need info setting up and connect to Win 10 network"
date: 2022-11-12
forum: Ubuntu/Debian BASED
---

### Post by ozstar on 2022-11-12
Hi,

I am on/off nooby with Linux. Years ago tried the old RedHat and Centas and recently Zorin, Mint, and now Linux Lite however I seem always to get stuck connecting to my Win 10 box on our LAN.

I have Linux set up in a VM on a Qnap NAS and it runs fine but it's the Linux permission and etc that fry my brain.

I chase Google and Youtube constantly to find answers but get halfway through a tutorial to find that it now talks about something my version doesn't show.

May be wrong but it seems all these other versions based on Ubuntu have some different methods of doing things, like Samba, and most of the tutorials shopw the ubuntu version so I am going to install that in a VM too to see if things play out easier for me. Then again I am a nooby !

I am hopeful that I will et some help here as we go along.

Thanks in advance

---

### Post by TheFu on 2022-11-12
Well, perhaps if you said clearly, which ubuntu version you were using, someone could help?  Seems like a basic thing.  If you aren't using an official Ubuntu, the steps that we find in the official ubuntu documentation won't likely work.

Also, what does "setting up and connect to Win 10 network" mean?  That's pretty vague to me.  The more things you need, the harder it will be.  I usually start with centralized DNS and network management.  Then move on to centralized user management, shared storage, shared printers, and logins to internal webapps.

But that's me. 

It also matters what other infrastructure exists and is configured on the network already.  Care to enlighten us about that too?  Please?

Again, the more you ask to accomplish, the deeper your skill level will need to be and saying "noob" doesn't remove that requirement.  Linux requires learning in stages.  The next stage requires the knowledge from the prior stages.  There's no jumping to the end and typing 1 command. Sorry.  

So, let's start with some brief information about the Linux system. run this command and post the results along with the answers to the questions above, as best you can:
```
inxi -bz |head -7
```

Oh, and do you want the Linux system to connect to Windows or do you want the Windows system to connect to Linux? It matters.

---

### Post by ozstar on 2022-11-13
Thank you for the reply and offer to help.
I'll start at the top.
The ubuntu on Linux Lite was 12.4 and it is set up and working fine inside my Qnap NAS VM.
My main problem us getting samba to work and getting the webserver to work.  I am nearly finished the webserver, just need the .conf files set up..  I think :-)
The ubuntu I have just downloaded now is 20.04 LTS so I will set this up in its own VM now.
I mainly need to connect from Win 10 Pro to the folders in the Linux box especially the /VAR/WWW/ and on... because I want to set up a webserver.
I have a Win 10 LAN with 8 other boxes and we all enjoy our company., and want to add Linux to the Workplace.
I do appreciate it being a 'pain in the b' trying to help someone who needs cuddling a bit as I too am on that end in my other life.
Anyway I am thankful for anyone to help if and when they can as I do really want to get it working if I can.

I will run the command and post.

---

### Post by ozstar on 2022-11-13
david &#57520; ~ &#57520; inxi -bz |head -7
System:
  Kernel: 5.15.0-52-generic x86_64 bits: 64 Desktop: Xfce 4.16.0 
  Distro: Linux Lite 6.2 LTS 
Machine:
  Type: Kvm Mobo: QEMU model: Standard PC (i440FX + PIIX, 1996) 
  v: pc-i440fx-4.1 serial: <filter> BIOS: N/A v: N/A date: N/A 
CPU:
 david &#57520; ~ &#57520; SIGPIPE &#57520; 0 &#57520;

---

### Post by Irihapeti on 2022-11-13
*Thread moved to **Ubuntu/Debian BASED** for a better fit.*

---

### Post by TheFu on 2022-11-13
> **ozstar said:**
> 
The ubuntu on Linux Lite was 12.4 and it is set up and working fine inside my Qnap NAS VM.


I know zero about Linux Lite. Never heard of it before. Someone else will need to help.

> **ozstar said:**
> 
My main problem us getting samba to work and getting the webserver to work.  I am nearly finished the webserver, just need the .conf files set up..  I think :-)
The ubuntu I have just downloaded now is 20.04 LTS so I will set this up in its own VM now.


Once you get 20.04 Server installed, seek out the official Samba documentation from Ubuntu. Should be easy enough to follow.  
[https://ubuntu.com/server/docs/samba-introduction](https://ubuntu.com/server/docs/samba-introduction) - this is part of the official server guide
[https://www.linuxbabe.com/ubuntu/install-samba-server-file-share](https://www.linuxbabe.com/ubuntu/install-samba-server-file-share) is reputable. Use that if the official docs don't work.

As for a webserver, there are many of those.  Serving static files is pretty easy. Check the official documentation at the link above. For a webapp, you'll need to follow the guide for the specific webapp you hope to use.  There are as many different installation instructions as there are webapps, so nobody can really help if you don't have a specific one to be run. These days, it might be more sensible to use a docker container version of a webapp.  I've never used docker stuff. I don't like the security risks, but lots of people do.

> **ozstar said:**
> 
I mainly need to connect from Win 10 Pro to the folders in the Linux box especially the /VAR/WWW/ and on... because I want to set up a webserver.

There shouldn't be any /VAR/WWW/ .... Linux is always case sensitive. Those directories are almost always /var/www/   and you probably don't want to allow Samba access to them to avoid terrible security issues.  Samba doesn't allow sufficient control over file and directory permissions which is mandatory to run a webapp in a secure way.  Best to give up on that idea, provide samba access to a staging area only, then copy/move the files to the final location, handling any permissions, owner, group and web-optimization (images) during that last stage.  Or you can use a DVCS for staging and have the production server "pull" updates that way.  I don't like doing it that way - security - but lots of websites do.

> **ozstar said:**
> 
I have a Win 10 LAN with 8 other boxes and we all enjoy our company., and want to add Linux to the Workplace.

I have no idea what a "workplace" is.  That term doesn't get used in Linux/Unix.  I'm guessing it could be a subnet or domain or LDAP group in Unix speak, but IDK.

> **ozstar said:**
> 
I do appreciate it being a 'pain in the b' trying to help someone who needs cuddling a bit as I too am on that end in my other life.

I fear from the questions asked and some of the post that starting from the beginning is needed. Here's a book that provides fundamental ideas, which are absolutely key in understanding any Unix OS that tend to be ignored in the Windows world.  Those things cannot be ignored in Unix. 

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  You should be able to get through the first 250 pgs fairly quickly.  Be certain to learn file permissions, users/groups, and process management.  They are all basic, but absolutely critical for securing any Unix system.  Linux is multi-user from the ground up.  Every process runs as a user. Services tend to run as specific users just for that service.  The current user of a process determines what file access the process has - read, write, and/or execute. Same for directories.  If it was just about data on files, this wouldn't be much different than on MS-Windows, but files are used to interact with hardware too, so in the Unix world, there are 2 things.  Files and processes.  In short, anything that isn't a process is a file.  Everything.  So all files have access rights and permissions which follow the Unix permissions model.  To have access to hardware, the process wanting that access needs appropriate permissions to the file(s) which allow the HW access/controls.

Which is why samba having direct access to webfiles probably isn't a good idea.  Samba controlling file permissions is like wearing thick gloves, and heavy mittens, but trying to replace a watch battery.  Can't be done. Not enough fine control.  Plus there's the entire case-sensitive directories and file problem.  Java programmers know this well, if they try to move their code from Windows to any other OS.

---

### Post by ozstar on 2022-11-13
Thank you very much for the explanations. I will ingest them and see what I can put into action. 
It is hard to recreate habits and mine is Windows. 
Been heavily into it and stuff well before so it's not that easy for an old brain to reconfigure itself.
Sorry yes, /var/www/.  'Workplace' is the name of the Windows default LAN network.
Once again many thanks

---

### Post by TheFu on 2022-11-14
> **ozstar said:**
>   'Workplace' is the name of the Windows default LAN network.
Once again many thanks

My initial thought on "workplace" was  the same as "workspace", which is an virtual desktop thing.  I'm using a 1x3 workspace today, but in my prime, I used a 3x3 for better organization by task.

In the 1990s, Unix systems used NIS domains to manage @netgroups - which is a fancy way to group hosts, groups, users, into an "NIS Domain."  The term "Domain" started becoming abused in the late 1990s. DNS Domains. NIS Domains. NIS+ Domains. AD Domains.  LDAP Domains. Domain names.  People get lazy and just say "domain" and we are supposed to figure out by context what is meant.

But none of those aren't connected to a subnet. Networking is separate.  There could be a loose connection between a LAN subnet and a LAN DNS domain, but not necessarily.  DNS doesn't care about subnets ... er ... mostly. There are some edge situations.

---

