---
title: "Home Server Assistance/Advice Needed"
date: 2012-12-25
forum: Server Platforms
---

### Post by slimj on 2012-12-25
Hello all,

I am an Ubuntu newbie and want to become part of your community :)

I have been using a home server for 2 years running windows home server 2003. I have now come to the stage it needs to be reinstalled and I want a change. I need to 'pool data' which I could do with WHS 'Drive Extender' and I am now being pushed into using Windows 8 as it has 'Storage Spaces'.

Personally I have had enough and want to go along the Linux route and have heard Ubuntu is the way to go.

1)Is Ubuntu the best way? 
2)Should I install the full Ubuntu or just server version?
3) What should i use to pool data - i have heard about (but dont yet understand) Logical Volume Manager and Greyhole?
4) Is there a full readme i can follow to get this up and running?
5) Will media streamers (eg. popcorn hour) pick up my media with no problems form the server?
6) As above but to can i stream to xbox?

I really appreciate any support; i really want to get away from Windows for personal use ;)

Merry Xmas all,

slim_j

---

### Post by darkod on 2012-12-25
If by "pool data" you mean using more physical disks as single logical device, then LVM should do the job for you.

For a start, I would install the Server version, not Desktop. When it reaches the step to select additional roles, select OpenSSH for remote control, and Samba for creating samba network shares.

Note that in the text menus you select the options with the Space bar, and when the selectiong is made you will usually see * next to it. Only then proceed to the next step. Hitting Enter might continue to the next step without anything selected.

As for streaming, it depends on the client device. If it only needs a network share, the created samba share should be enough. If it needs some server program running, you will have to install it too.

Are you planning to run any type of raid or not? If you do, using linux software raid might be better option than bios fakeraid.

---

### Post by spynappels on 2012-12-25
If you want to stream media to a DLNA enabled device, you'll need to run a DLNA server, you should Google minidlna, it's quite a small and simple service to run and works well.

+1 for LVM as well, it allows storage volumes to span multiple disks and makes backups easier too through snapshots.

---

### Post by superdaveozzborn on 2012-12-25
Ubuntu Server headless with ssh and ftp works for me. simple install and your on your way.

---

### Post by Zythyr on 2012-12-26
@slimj, 
I am also a newbie to Linux and was interested in installing a home server. For few weeks, I have been reading a lot of guides and learning about Linux. Here are some good websites/guides I have collected which will help you: 

[http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/) 
[http://ubuntuguide.org/wiki/Ubuntu_Quantal](http://ubuntuguide.org/wiki/Ubuntu_Quantal)
[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html) 
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by slimj on 2012-12-26
**darkod** - yes by "pool data" I mean having multiple physical disks appearing as one drive. I do need to be able to add to this though as space gets used up - will LVM manage this OK?

Thankyou for the install guidence. If I do go with this i will follow when i install. It will be network share but needs to be picked up by media players. I have used popcorn hour in the past and this would appear to pick up SMB so i am happy enough there.

I also do not plan on doing raid or any backup's. My friend has nearly the exact setup so we use each other as backups should it be needed.

**spynappels** - I just install minidlna on the server which will allow compatible streaming, sounds easy enough :)

**superdaveozzborn** - Sounds easy so far, ill look forward to having ago when i have finished moving data.

**Zythyr** - really useful links, thanks a million mate. Where are you unto in the build - I would be very interested in hearing how you progress.

Thanks all for your time and input, really great advice all round :)

---

### Post by darkod on 2012-12-26
Yes, LVM allows in future to add new physical disks to be joined to the same LVM. That's the point of it. Adding space is very easy when you have LVM.

You can do expanding online (you don't even need to shut down and boot into some live session), but for shrinking, if you ever need it, it needs to be done offline. The Logical Volume needs to be unmounted for shrinking.

---

### Post by ranger12 on 2012-12-26
Yep, it makes for a great home network. I have a dell machine running Server 12.04 with nfs, openldap, samba (as a PDC), dns and who know what else running on it. :) I have  another dell machine running Desktop 12.04 and have it configured as a client and have been running it for 4 or 5 months and I think it is super. I do not have any Windows machines currently on the network but I did have one at first so I was able to test the Sambe PDC configuration.. I also have the client hooked up to get the time from my server as well. I don't need a big powerful machine for the server since there is no gui and I like it that way. I have even downloaded some software for my iPad that allows me to login to the server and access files in my network directory.

---

### Post by Zythyr on 2012-12-26
> **darkod said:**
> Yes, LVM allows in future to add new physical disks to be joined to the same LVM. That's the point of it. Adding space is very easy when you have LVM.

You can do expanding online (you don't even need to shut down and boot into some live session), but for shrinking, if you ever need it, it needs to be done offline. The Logical Volume needs to be unmounted for shrinking.

@darkod: Are software RAID and LVM two different things? 

@slimj here is a link for software RAID. It is similar to Storage Spaces/Drive Extender on Windows. [https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html). I am currently in the process of planning for my home server. I am trying to decide if I should go with Windows or Linux or maybe both with one being virtualized.

---

