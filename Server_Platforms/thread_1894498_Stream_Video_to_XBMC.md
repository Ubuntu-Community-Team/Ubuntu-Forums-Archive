---
title: "Stream Video to XBMC"
date: 2011-12-12
forum: Server Platforms
---

### Post by neerg21 on 2011-12-12
Hey folks,

I recently made the switch to become a fulltime Ubuntu user, but I've been having problems getting my jail broken apple tv 2 with XBMC installed to receive video from my ubuntu 11.10 laptop.

When I was in windows, it was as simple as turning file sharing on. I've tried right clicking on the folder and turning sharing on which install samba, that didn't work. I also tried ushare for plung and plag, that also did nothing. I couldn't find any tutorials specifically for Ubuntu 11.10 streaming to XBMC.

If someone is aware of one I would love to read it, or if someone has an easy way (fairly new to linux) I would appreciate that as well.

Thanks in advanced,

Neerg21

---

### Post by arrrghhh on 2011-12-12
How do you want to stream?  Via samba or UPNP?

I know nothing about Apple TV, so I can't really help you there...

If you establish how you'd like to stream, we can work on the logistics.  Also, are you running Ubuntu Desktop?  If yes, you posted in the Server section - so help in this section will be geared towards CLI commands (no GUI) ;).

---

### Post by rubylaser on 2011-12-12
With Pre-Eden (nightly) builds of XBMC, NFS is available in the Add Video Source dialog.  I use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") with all of my XBMC clients.  If you're running a Dharma build of XBMC, you'll just need to create a path and mount the NFS share per the Ubuntu wiki.

---

### Post by neerg21 on 2011-12-12
I was afraid this was the wrong section of the forum, sorry about that.

I am running Ubuntu desktop, and to be honest it doesn't matter to me how I get the video to the apple tv, all I'm looking for is the simplest way of getting it there. I keep all my videos itn home/user/Videos, and I want the XBMC on my apple tv to be able to watch videos from this folder.

Thanks for the replies, hopefully that will help answer what you asked, lol, I'm still fairly new to the linux world.

---

### Post by arrrghhh on 2011-12-12
> **neerg21 said:**
> I was afraid this was the wrong section of the forum, sorry about that.

I am running Ubuntu desktop, and to be honest it doesn't matter to me how I get the video to the apple tv, all I'm looking for is the simplest way of getting it there. I keep all my videos itn home/user/Videos, and I want the XBMC on my apple tv to be able to watch videos from this folder.

Thanks for the replies, hopefully that will help answer what you asked, lol, I'm still fairly new to the linux world.

I didn't even think NFS was an option - NFS is by far a better protocol, and IMHO easier to setup/maintain than samba is.

So I would setup NFS between the Apple TV box and your server.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

That's the Ubuntu community doc on NFS.  Good luck with the client config!

---

### Post by RealityMaster on 2011-12-12
I've had all sorts of issues using other protocols, the only one that seems to work is NFS. 

Mount your media via fstab, then load it into XBMC.  This is the only way I've got rid of hanging, lock-ups, missing media, and a plethora of other issues....

The only disadvantage with this is if you've been using it for a while and want to keep your ratings and play counts.  If this is the case, I've read you can use an SQL database to back it up, but I haven't tried it.

---

### Post by rubylaser on 2011-12-12
If you don't have a MySQL database setup, you can just export the nfo files as individual files via Settings > Video > Export.  The .nfo files contain playcount, date added, watched status, etc. Personally, I use a MySQL database for all my XBMC clients ([Openelec]("http://openelec.tv/")) with a shared NFS thumbnail directory, so that all clients stay in sync.  If works really well.

---

### Post by arrrghhh on 2011-12-12
> **rubylaser said:**
> If you don't have a MySQL database setup, you can just export the nfo files as individual files via Settings > Video > Export.  The .nfo files contain playcount, date added, watched status, etc. Personally, I use a MySQL database for all my XBMC clients ([Openelec]("http://openelec.tv/")) with a shared NFS thumbnail directory, so that all clients stay in sync.  If works really well.

That sounds nifty.  Some day I'll get around to setting up OpenELEC boxes...

---

### Post by 1serveyou on 2011-12-13
> **arrrghhh said:**
> That sounds nifty. Some day I'll get around to setting up OpenELEC boxes...
 
 
Completely agree... I have an extra mac mini laying around I might try this on. I wish I had more time right now to try it.

---

