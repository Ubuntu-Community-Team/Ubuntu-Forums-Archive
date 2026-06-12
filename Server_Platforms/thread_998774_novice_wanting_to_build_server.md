---
title: "novice wanting to build server"
date: 2008-12-01
forum: Server Platforms
---

### Post by wordmaster on 2008-12-01
Hello,

I am just beginning to poke around in Ubuntu desktop, but I have a rather unique situation at work and intend to build a computer and install ubuntu server.

I have an old server running Netware 3.12 and servicing about 15 workstations running 98SE. Its main purpose is to give access to a custom written DOS program that takes care of every aspect of running the plant except for accounting. It gives access to MAS 90 for accounting.

I have been spoiled by Netware. It just sets there and runs. Haven't done anything to it for about 8 years. However, the server is getting old and 3.12 won't support modern hardware.

Soooo, the best thing I can come up with to replace it is ubuntu server. 

I intend to build a computer using an Asus mb M2N68-VM. An AMD Athlon 64 X2 5400 processor and 4 gigs of PC6400 ram with two 500 GB Sata drives in a raid backup configuration.

I want to be able to run the DOS program and the MAS90 program and access with 98se workstations.

With this in mind I have some questions. BTW, I am new to Linux but not to computers. Started with RS-DOS and OS-9 on a COCO 3 in the 80's, worked through DOS, windoze and a little netware over the years.

First, will ubuntu server work well with the computer configuration above?

Second, what will I need on the 98se workstations for them to work with the server. Currently, for the DOS program, I just open a DOS window, go to drive F and type in a batch file that fires up the program. For Mas90 there is a loader program that accesses the server and you really never know it is not running on your desktop. How will accessing these on the ubuntu server differ?

As a know-nothing newbie, what will be my major problems in setting up the server?

Thank you kindly for any and all help you can give.

---

### Post by Philio on 2008-12-01
It sounds like your dos program is just simply a network share which the Windows 98 machines have attached as network drive F. I assume this was probably set up with a Netware login script?

You should be able to replicate this functionality with Samba, it supports domain logins and file sharing. There are other packages you could use as well but considering Samba will do both it's probably easier to stick to that.

I've had something similar setup myself, but it was years ago! I can't really remember specifics but it can definitely be done this way.

How does the Sage application work? Is it a client/server setup?

---

### Post by shizakapayou on 2008-12-01
You can indeed setup file sharing (and even a Windows domain) using Ubuntu server.  I have mine setup with a login script to automatically map any shares the user has access to.

Sage may be a bigger problem, as it's usually a client/server setup.  If the DOS program is just in a network share but executed by the client, that shouldn't be a problem.  I'd look into MAS90 carefully though.

---

### Post by ghostworkz on 2008-12-01
Most of my clients have a linux pdc with samba.  You can pretty much do anything you need to do with ubuntu as the server.  Just depends on how complicated you make it.  I suggest looking at [http://www.howtoforge.com](http://www.howtoforge.com)
They have some great tuts on how to setup various servers.

---

### Post by volkswagner on 2008-12-01
I was wondering if you considered running it in a virtual machine, since your new hardware seems up to the task.

I see your thread.

[http://www.computing.net/answers/netware/machine-for-netware-312/5685.html]("http://www.computing.net/answers/netware/machine-for-netware-312/5685.html")


I guess you did.  

I love google.

---

### Post by CrucifiedEgo on 2008-12-01
RAID != Backup.  With a backup, rm -rf /home can be fixed, with RAID, it's already written out.  What I generally recommend, if uptime is a huge concern, is 2-disk RAID1, and a 3rd identical disk to rsync to nightly.  if you can deal with a couple hours of downtime, then two disks is fine (skip the raid)

---

### Post by wordmaster on 2008-12-01
> **Philio said:**
> It sounds like your dos program is just simply a network share which the Windows 98 machines have attached as network drive F. I assume this was probably set up with a Netware login script?

You should be able to replicate this functionality with Samba, it supports domain logins and file sharing. There are other packages you could use as well but considering Samba will do both it's probably easier to stick to that.

I've had something similar setup myself, but it was years ago! I can't really remember specifics but it can definitely be done this way.

How does the Sage application work? Is it a client/server setup?

Yes, once you go to F drive either in a DOS prompt or in explorer, you can view and access everything on the server just as if it were another drive on your desktop. If it is an execution file, you can double click to start it in windoze. The only program that needs any login other than "user" is the mas90 stuff.

The Mas90 folders are hidden unless you are logged in with supervisor privileges. Unless you first log in to the server, the mas90 starter will not allow you to start the program, ie. it doesn't "see" the folder.

---

### Post by wordmaster on 2008-12-01
> **shizakapayou said:**
> You can indeed setup file sharing (and even a Windows domain) using Ubuntu server.  I have mine setup with a login script to automatically map any shares the user has access to.

Sage may be a bigger problem, as it's usually a client/server setup.  If the DOS program is just in a network share but executed by the client, that shouldn't be a problem.  I'd look into MAS90 carefully though.


Well, I am not sure of the inner workings of netware, but you do have to have the desktop in DOS mode to run the DOS program.

As near as I can tell, the desktop is actually running either a DOS or windoze program, the server just makes it accessible just as if it were on a drive on the desktop.

Of course you can limit what programs certain users can access, but assuming you have "supervisor" access, all is open on the server just as if it were an f drive installed in the desktop.

---

### Post by wordmaster on 2008-12-01
> **ghostworkz said:**
> Most of my clients have a linux pdc with samba.  You can pretty much do anything you need to do with ubuntu as the server.  Just depends on how complicated you make it.  I suggest looking at [http://www.howtoforge.com](http://www.howtoforge.com)
They have some great tuts on how to setup various servers.

Thank you for the url. I will check it out. I want to keep it just as simple as possible. The server, once set up, does not even need internet access as all desktops get internet directly from a hub. I just want to be able to run the two programs and to use the server if needed to copy stuff from a desktop to the server and back to another desktop or store setup programs, etc. on the server to use on desktops.

---

### Post by wordmaster on 2008-12-01
> **volkswagner said:**
> I was wondering if you considered running it in a virtual machine, since your new hardware seems up to the task.

I see your thread.

[http://www.computing.net/answers/netware/machine-for-netware-312/5685.html]("http://www.computing.net/answers/netware/machine-for-netware-312/5685.html")


I guess you did.  

I love google.

Yep, the more I looked into running 3.1 novell on a virtual machine, the more confused I got and the more people I found who had problems trying to do so.

---

### Post by wordmaster on 2008-12-01
> **CrucifiedEgo said:**
> RAID != Backup.  With a backup, rm -rf /home can be fixed, with RAID, it's already written out.  What I generally recommend, if uptime is a huge concern, is 2-disk RAID1, and a 3rd identical disk to rsync to nightly.  if you can deal with a couple hours of downtime, then two disks is fine (skip the raid)

Sorry, guess I should have said mirrored raid so if a drive dies, I can restart the computer with the one that is still alive and go right on from where it stopped.

---

### Post by Philio on 2008-12-01
> **wordmaster said:**
> Sorry, guess I should have said mirrored raid so if a drive dies, I can restart the computer with the one that is still alive and go right on from where it stopped.

Ideally your backup should be a separate machine or off site!

In the unlikely event something were to happen that knocked out both your RAID drives, it would probably kill the backup drive as well.

---

### Post by Philio on 2008-12-01
> **wordmaster said:**
> Yes, once you go to F drive either in a DOS prompt or in explorer, you can view and access everything on the server just as if it were another drive on your desktop. If it is an execution file, you can double click to start it in windoze. The only program that needs any login other than "user" is the mas90 stuff.

The Mas90 folders are hidden unless you are logged in with supervisor privileges. Unless you first log in to the server, the mas90 starter will not allow you to start the program, ie. it doesn't "see" the folder.

Samba will do what you want here. Best bet is probably to look for a guide, the howtoforge site mentioned is good. Search for 'samba domain server' or something similar.

---

### Post by dipeshmehta on 2008-12-03
Hello,

We had similar setup with NetWare 4.01 Server and clients running Win98 / WinXP.  About a month back we switched over to Ubuntu 8.04 Server.  It works fine, with all our existing setup.  Apartfrom this we now have setup our own internal mail server, chat server and planning for lots of other stuff.

Howtoforge and Ubuntu Documentations are really a good place for help.

My post is just to encourage you.

Dipesh

---

### Post by wordmaster on 2008-12-03
> **Philio said:**
> Ideally your backup should be a separate machine or off site!

In the unlikely event something were to happen that knocked out both your RAID drives, it would probably kill the backup drive as well.


I currently have a hard drive that has a backup of the server. On a daily basis I use a hard drive hot swap in my desktop and back up certain folders both on my desktop and on the server each night and swap hard drives so that I have 12 backups of those folders at any time. 

Will this work with the ubuntu as well?

---

### Post by wordmaster on 2008-12-03
> **Philio said:**
> Samba will do what you want here. Best bet is probably to look for a guide, the howtoforge site mentioned is good. Search for 'samba domain server' or something similar.

Thank you. I will check into samba.

---

### Post by wordmaster on 2008-12-03
> **dipeshmehta said:**
> Hello,

We had similar setup with NetWare 4.01 Server and clients running Win98 / WinXP.  About a month back we switched over to Ubuntu 8.04 Server.  It works fine, with all our existing setup.  Apartfrom this we now have setup our own internal mail server, chat server and planning for lots of other stuff.

Howtoforge and Ubuntu Documentations are really a good place for help.

My post is just to encourage you.

Dipesh

Thank you. Did you use Samba? Also did you have to use Wine?

---

### Post by wordmaster on 2008-12-03
Hello,

Just wonder if ubuntu can detect, setup proper software and drivers, etc. on the hardware I want to use? The hardware is:

Asus mb M2N68-VM. An AMD Athlon 64 X2 5400 processor and 2 gigs of PC6400 ram with two 500 GB Sata drives in a mirrored raid configuration. The mb has onboard video, audio, and lan.

---

### Post by dipeshmehta on 2008-12-04
> **wordmaster said:**
> Thank you. Did you use Samba? Also did you have to use Wine?

Yes, we use Samba.  but wine is not required for us.

I would suggest you to use webmin, for webbased configuration of linux server, its great tool for newbies in linux world.

---

### Post by henrik65 on 2008-12-07
> **wordmaster said:**
> Hello,

Just wonder if ubuntu can detect, setup proper software and drivers, etc. on the hardware I want to use? The hardware is:

Asus mb M2N68-VM. An AMD Athlon 64 X2 5400 processor and 2 gigs of PC6400 ram with two 500 GB Sata drives in a mirrored raid configuration. The mb has onboard video, audio, and lan.

I have a very similair spec and Ubuntu 8.10 worked for about two weeks, then won't boot. If have found a fair amount of people with the same problems. Perhaps you should hold off the purchase for a while or choose a motherboard many others are using.
I'm over in
[http://ubuntuforums.org/showthread.php?t=1003696](http://ubuntuforums.org/showthread.php?t=1003696)
where I get some help.

---

