---
title: "How to &quot;duplicate&quot; a server"
date: 2006-08-28
forum: Server Platforms
---

### Post by kenquad on 2006-08-28
Hi all:

Here's my goal, and if anybody knows how to do this I'd appreciate any help.  I have two identical Optiplexes set up as Ubuntu servers.  One contains important data.  I want to make the other one a copy of the first (except of course the IP address) hooked up over network so that if the first server goes down, all I have to do is change the IP address on the backup system and I'm back in business.  The data on the backup system would stay 24 hours behind the primary system.  I don't know if rsync is the way to do this or Amanda or what.  ???

Kenquad

---

### Post by amo-ej1 on 2006-08-28
If you want a single copy, simply boot the blank one using a livecd, rsync the data over and install your bootloader. If you want to do this multiple times on multiple servers take a look at systemimager (which also used rsync in the back).

---

### Post by spin2cool on 2006-08-28
Yeah - you probably want rsync.  There are some good tutorials out there if you search the web

---

### Post by lamego on 2006-08-28
rsync is a good option you should should also configure a secondary "virtual" device eth0:1 on the backup system with the IP of the main system. This would allow you to get the control over the main IP by just turning the device on/off.
You should be carefull to stop the rsync when the eth0:1 is active and make sure you synchorize the main system data when it gets online.

---

### Post by jimm on 2006-08-29
Hi,

Here is how I would do it... and the way I in fact do do it!

If you have enough grunt on your two boxes (i.e. a few spare cycles), install a minimal Ubuntu server (base install +gcc+patch+make+Xlibs ... I can tell you the whole requirement if you are interested) then install VMWare server (free! from VMware.com. 

If you this right, you actually dont lose much resource using the virtualisation layer over the physical. The gain is that you get ultimate flexibility for your machines. i.e. Later on if you upgrade the host hardware you can just move the VM across without any hassles at all!

Turn your live machine into a VM (either manually or by imaging or trying this: [http://www.vmware.com/vmtn/appliances/directory/316](http://www.vmware.com/vmtn/appliances/directory/316) Not tried it myself, but worth a look) 

Then simply copy the VM over to your other server (also running vmware server), change the IP address etc and either use Rsync or some other tool to keep them in sync data wise. Or smply do a regular copy of the whole VM over to your backup server and just power the VM up when you are in need of it. You dont even need to use another IP address as long as both arent on at the same time.

Its a bit of a tangent from your question / problem, but it is a nice solution... In my humble opinion of course :)

Thanks,
James

---

### Post by kenquad on 2006-08-29
> **jimm said:**
> Hi,

Here is how I would do it... and the way I in fact do do it!

If you have enough grunt on your two boxes (i.e. a few spare cycles), install a minimal Ubuntu server (base install +gcc+patch+make+Xlibs ... I can tell you the whole requirement if you are interested) then install VMWare server (free! from VMware.com. 

If you this right, you actually dont lose much resource using the virtualisation layer over the physical. The gain is that you get ultimate flexibility for your machines. i.e. Later on if you upgrade the host hardware you can just move the VM across without any hassles at all!

Turn your live machine into a VM (either manually or by imaging or trying this: [http://www.vmware.com/vmtn/appliances/directory/316](http://www.vmware.com/vmtn/appliances/directory/316) Not tried it myself, but worth a look) 

Then simply copy the VM over to your other server (also running vmware server), change the IP address etc and either use Rsync or some other tool to keep them in sync data wise. Or smply do a regular copy of the whole VM over to your backup server and just power the VM up when you are in need of it. You dont even need to use another IP address as long as both arent on at the same time.

Its a bit of a tangent from your question / problem, but it is a nice solution... In my humble opinion of course :)

Thanks,
James

Wow, very interesting!  Thanks for posting.  I'm afraid that's a bit out of my expertise level, though....  And thanks for all the  other ideas too, everybody.

---

### Post by jimm on 2006-08-29
Hi,

VMWare isnt to hard to do (heck I figured it out :-)). Once you have the VM host installed you just treat the VM's as normal machines and handle the VM files as normal files on the host. 

Apprieciate the fact that it is a bit of a jump from your current setup :-) Something for you to play with at a later date I guess... Keep it in mind. Its a viable but often overlooked option (until recently anyway).

Thanks,
James

---

### Post by kenquad on 2006-08-29
> **amo-ej1 said:**
> If you want a single copy, simply boot the blank one using a livecd, rsync the data over and install your bootloader. If you want to do this multiple times on multiple servers take a look at systemimager (which also used rsync in the back).

Systemimager looks really cool, but I don't see a built-in feature for scheduling.  Is this pretty easy to do with Cron?

---

### Post by kenquad on 2006-09-01
amo-ej1:

I'm trying to get rolling with systemimager, but even though the client is installed, I get command not found when I try to run prepareclient.  Do you know enough about the program to have any idea why this is happening?

Thanks,
Kenquad

---

### Post by Useless on 2006-09-02
[Here is a really simple how to for the rsync set up to mirror a website]("http://howtoforge.com/mirroring_with_rsync").  I have used it and it works great.  This website is also good for other how tos.

---

