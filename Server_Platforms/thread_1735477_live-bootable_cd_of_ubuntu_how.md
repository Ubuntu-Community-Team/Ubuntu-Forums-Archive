---
title: "live-bootable cd of ubuntu how?"
date: 2011-04-21
forum: Server Platforms
---

### Post by lazerz on 2011-04-21
I tried to ask this question before but no-one really answered this...i guess it must be so HARD as everyone is ignoring my post.

I want to make a live bootable cd of my ubuntu-server (10.0.4) which is currently running in vmware-enviromoment. ? How could i make this? I want to make it such that it would be able to boot in my dell production server dell 2850?

Thanks once agian.

---

### Post by collisionystm on 2011-04-21
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

---

### Post by collisionystm on 2011-04-21
Instead of a live cd,
 
What you should do to transfer the image to your dell server is:
 
Boot the server with a Desktop live cd and rsync the root partition of your vmware server to the partition on the dell.
 
Then run a grub install.
 
Voila. Your vmware is now on a real server.

---

### Post by lazerz on 2011-04-21
> **collisionystm said:**
> Instead of a live cd,
 
What you should do to transfer the image to your dell server is:
 
Boot the server with a Desktop live cd and rsync the root partition of your vmware server to the partition on the dell.
 
Then run a grub install.
 
Voila. Your vmware is now on a real server.


Thank you for your help so far. I appreciate that greatly.  Well i know there is a pxe option that i can use. But right now my dell is all skeleton right now ..it has no internet connectivity...and yes no network connection...too

so what are the pre-requisite of such deployment...? do i need rsync on the server end? do i need to open a firewall port? and more....

Is there a step by step guide that i can follow for your procedure. It looks freaking cool and easy ..can you help me in some way? which is like more hands-one thanks 

take care

---

### Post by collisionystm on 2011-04-21
First off, you need a network connection. Is the server internal to your site? Is it on the same subnet / internal network as your vmware?

You only need to worry about firewall ports if the server is offsite from you. In that case, you would need the server near you regardless so you can handle the live cd etc.....

---

### Post by collisionystm on 2011-04-21
First things first.

Load the live cd on your server

Give the live cd a static ip addres

Open terminal


```

 
sudo apt-get install ssh
 

```This installs the SSH Server and Client.

Do the same on your Vmware if you dont arleady have SSH server installed.

Now that SSH is installed, test your connection. Go to your vmware box and run the following command : 

NOTE - the root account on the live cd should not have a password

```

 ssh root@<ipaddressofserverlivecd>

```If prompted, press yes to connect

Hopefully that was a success. The boxes can now see eachother.

On the live cd server you need to format the drive and find the path to the hard drive array you have in there. 

You can use the disk utility under System, Administration.
Format the Hard drive with EXT4 ( THIS WILL ERASE EVERYTHING ON THE DELL DRIVES)

When  its done.....

click on your hard drive on the left, and on teh right it will say the Device: /dev/***

mine is /dev/sda

On your live cd server is where you will be doing your rsync commands

type rsync --help to look at the rsync options


```

 
rsync - <options> -e /usr/bin/ssh <username>@<ipaddressofdestkop>:/* /dev/***/
 
I.E.
 
rsync -rqaHpEAXogt -e /usr/bin/ssh root@172.16.64.2:/*  /dev/sda/
 
 

```Make sure you include the colon : at end of <ipaddressofdesktop>

and make sure to include the asterisk * at the end of <pathtofolder>/

the * is a wildcard to grab everything in there

Once it is complete, you will need to install grub.

Follow this tutorial 

[http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/](http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/)

Once grub is installed and the rsync is finished you can even put the rsync command on a crontab to make sure it still backs up until you are ready to test it.

Give that a shot.

GOOD LUCK!!!

---

### Post by lazerz on 2011-04-21
> **collisionystm said:**
> First things first.

Load the live cd on your server

Give the live cd a static ip addres

Open terminal


```

 
sudo apt-get install ssh
 

```This installs the SSH Server and Client.

Do the same on your Vmware if you dont arleady have SSH server installed.

Now that SSH is installed, test your connection. Go to your vmware box and run the following command : 

NOTE - the root account on the live cd should not have a password

```

 ssh root@<ipaddressofserverlivecd>

```If prompted, press yes to connect

Hopefully that was a success. The boxes can now see eachother.

On the live cd server you need to format the drive and find the path to the hard drive array you have in there. 

You can use the disk utility under System, Administration.
Format the Hard drive with EXT4 ( THIS WILL ERASE EVERYTHING ON THE DELL DRIVES)

When  its done.....

click on your hard drive on the left, and on teh right it will say the Device: /dev/***

mine is /dev/sda

On your live cd server is where you will be doing your rsync commands

type rsync --help to look at the rsync options


```

 
rsync - <options> -e /usr/bin/ssh <username>@<ipaddressofdestkop>:/* /dev/***/
 
I.E.
 
rsync -rqaHpEAXogt -e /usr/bin/ssh root@172.16.64.2:/*  /dev/sda/
 
 

```Make sure you include the colon : at end of <ipaddressofdesktop>

and make sure to include the asterisk * at the end of <pathtofolder>/

the * is a wildcard to grab everything in there

Once it is complete, you will need to install grub.

Follow this tutorial 

[http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/](http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/)

Once grub is installed and the rsync is finished you can even put the rsync command on a crontab to make sure it still backs up until you are ready to test it.

Give that a shot.

GOOD LUCK!!!


Thank you kind person for helping me when no-one else care not to... MY DELL is on another subnet....but that not the problem i would get it on the network....

I wanted to clarify myself on one thing....you said....'live-cd'? What live-cd are u exactly talking about? are u talking about ubuntu live-cd or u talking about dell-live cd? and how long the entire process would take ...........


Im going to follow ur steps , as soon i go back to my office tomorrow....i would keep u updated in meanwhile......thank u once again....

---

### Post by lazerz on 2011-04-21
[SIZE=3]i just ur advice like i use this command from the original link u sent me [/SIZE]

[COLOR=#000000][FONT=Arial]sudo rsync -av --one-file-system --exclude=/proc/* --exclude=/dev/*\
 --exclude=/sys/* --exclude=/tmp/* --exclude=/home/*\
 --exclude=/lost+found / ${WORK}/rootfs


it is like taking hours to finish...?its preparing installation but is it really suppose to take all this time...
[/FONT][/COLOR]

---

### Post by collisionystm on 2011-04-21
Yes, Ubuntu live cd.

Use a 10.04 desktop, not that 10.10 crap

---

### Post by collisionystm on 2011-04-21
> **lazerz said:**
> [SIZE=3]i just ur advice like i use this command from the original link u sent me [/SIZE]

[COLOR=#000000][FONT=Arial]sudo rsync -av --one-file-system --exclude=/proc/* --exclude=/dev/*\
 --exclude=/sys/* --exclude=/tmp/* --exclude=/home/*\
 --exclude=/lost+found / ${WORK}/rootfs


it is like taking hours to finish...?its preparing installation but is it really suppose to take all this time...
[/FONT][/COLOR]

What exactly are you trying to do? You have so many variables and command switches!

What is 
> 
/ ${WORK}/rootfs


---

### Post by lazerz on 2011-04-21
> **collisionystm said:**
> What exactly are you trying to do? You have so many variables and command switches!

What is


Well em following the instructions list down over here. The link u sent me

[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

according to the link
work is 
The WORK Directory is where our temporary files and mount point will reside.

---

### Post by collisionystm on 2011-04-21
I didn't write those instructions. I just passed them on as a resource to use.

How big is your Vmware server? Will it even fit on a dvd? Or cd for that matter

---

### Post by lazerz on 2011-04-21
> **collisionystm said:**
> I didn't write those instructions. I just passed them on as a resource to use.

How big is your Vmware server? Will it even fit on a dvd? Or cd for that matter


Em sorry . I know u have not written down these instructions....my vmware is like df -h shows me 9 gb of total and 3.0 of gb is filled up...i guess that not that much but i think rsync is doing like byte - byte copy of the file-system....but even then the time is taking seems impractical...

---

### Post by collisionystm on 2011-04-21
So I assume instead of using the way I mentioned, you are going to attempt a LIVE DVD, yes?

---

### Post by lazerz on 2011-04-21
> **collisionystm said:**
> So I assume instead of using the way I mentioned, you are going to attempt a LIVE DVD, yes?


NO sir i would never ditch ur request esp when u have went all the way to help me its just em on my home pc and em using different options right now...i dnt have phyical or remote access to my office servers/desktop....so em just testing the options which works best right now.....

---

### Post by collisionystm on 2011-04-21
lol Well, let me know which one works for you. I'd be curious to know 

Cheers

---

### Post by lazerz on 2011-04-22
> **collisionystm said:**
> lol Well, let me know which one works for you. I'd be curious to know 

Cheers

well em stuck at point 

 rsync -rqaHpEAXogt -e /usr/bin/ssh root@10.10.145.59:/*  /dev/sda1/


rsync: ERROR: cannot stat destination "/dev/sda1/": Not a directory (20)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(573) [Receiver=3.0.7]


10.10.10.2 is my vm-machine......

---

### Post by lazerz on 2011-04-22
> **lazerz said:**
> well em stuck at point 

 rsync -rqaHpEAXogt -e /usr/bin/ssh root@10.10.145.59:/*  /dev/sda1/


rsync: ERROR: cannot stat destination "/dev/sda1/": Not a directory (20)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(573) [Receiver=3.0.7]


10.10.10.2 is my vm-machine......


even when i delete the file from dev folder i then start getting
this
`rsync no space left on device

---

### Post by collisionystm on 2011-04-22
Did you format SDA1 with Disk Utility on the live cd?

---

### Post by collisionystm on 2011-04-22
Instead of SDA1 try to just do SDA when you do your rsync

---

### Post by collisionystm on 2011-04-22
> **lazerz said:**
> well em stuck at point 

 rsync -rqaHpEAXogt -e /usr/bin/ssh root@10.10.145.59:/*  /dev/sda1/


rsync: ERROR: cannot stat destination "/dev/sda1/": Not a directory (20)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(573) [Receiver=3.0.7]


10.10.10.2 is my vm-machine......


Woah didnt notice this. Sorry. 

You need to be on your LIVE CD server to run this command

And it should be 

rsync -rqaHpEAXogt -e /usr/bin/ssh root@10.10.10.2:/*  /dev/sda1/

rsync <SOURCE> <DESTINATION>

source = vmware
destination = path on live cd

---

### Post by collisionystm on 2011-04-25
Did you ever get this to work?

---

### Post by lazerz on 2011-04-25
> **collisionystm said:**
> Did you ever get this to work?


no i havent tried again....and yes i have tried the command from the live cd and specified source as my vmware machine...

there was problem formating device sda and sda1 is volume i think i can format volume but not the whole drive...it give error...i think u need to unmount before u can do that?

---

