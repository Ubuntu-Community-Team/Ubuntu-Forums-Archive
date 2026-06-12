---
title: "Transparent gateway for FileServer"
date: 2015-02-17
forum: Server Platforms
---

### Post by mika912 on 2015-02-17
Hi,

I'm today using whs2011 with 6 disks as my main fileserver.
It's configured to suspend 10 minutes after inactivity (network, disk, apps...) and supports wake on lan.
When using my XBMC clients the wake up is transparent, but my android tab and stereo amplifier can't use the file/dlna unless I manually send a wol command.

So I'd like to add a little ubuntu box (maybe a raspberry?) to act as a fileserver gateway.
I will create shares, that will only redirect to the big fileserver ones. (and wake it up if neeeded)

I read about two possibles solutions: autofs or samba preexec.

```

[videos]
   comment = big files
   path = /mnt/bigserver/videos
   ...
   preexec = /usr/local/bin/my_wake-on-lan_and_mount_script

```


But what will happen when the server will go back to sleep? 
The autofs/preexec command will be called again? (but the mount point is still registrered)

Thanks for the help!

---

### Post by darkod on 2015-02-17
I am not a WOL expert but if you put the ubuntu box in between as you plan, do you need a WOL script at all?

The client will ask for the ubuntu samba share which will then try to contact the WHS. Wouldn't it wake it up by that action?

---

### Post by TheFu on 2015-02-17
I would be inclined to just get a WOL app for android or setup the router to send WoL events to the target automatically.

---

### Post by mika912 on 2015-02-17
[QUOTE=darkod]I am not a WOL expert but if you put the ubuntu box in between as you plan, do you need a WOL script at all?
The client will ask for the ubuntu samba share which will then try to contact the WHS. Wouldn't it wake it up by that action?
[/QUOTE]
From what I understood, it's the meaning of the preexec command: run a wol script to wakeup the WHS when clients ask for the ubuntu share.

[QUOTE=TheFu]
I would be inclined to just get a WOL app for android or setup the router to send WoL events to the target automatically.
[/QUOTE]
I want it to be transparent, without any manual operations from users (no WOL app for example)
For the router, I don't know about a working solution for auto-wol. Not sure that the local traffic can be monitored.
But I'm not a network expert ^^

---

### Post by TheFu on 2015-02-17
[http://www.dd-wrt.com/wiki/index.php/WOL](http://www.dd-wrt.com/wiki/index.php/WOL) - ddwrt provides it.

---

### Post by darkod on 2015-02-17
My point was whether a special preexec event is needed at all. If WOL by definition works with network events maybe it could work with the event ubuntu will create trying to access the WHS.

You can test this easily if you have virtual box on any desktop in the LAN. And that will help you with your preexec dilemma too.

Simply configure small basic ubuntu vm and configure the samba share to use the whs share as you want. No preexec. Then from any client try accessing the ubuntu share and see if its event will wake the whs. If it works you know what to do when configuring your ubuntu box.

---

### Post by mika912 on 2015-02-17
> **darkod said:**
> My point was whether a special preexec event is needed at all. If WOL by definition works with network events maybe it could work with the event ubuntu will create trying to access the WHS.

You can test this easily if you have virtual box on any desktop in the LAN. And that will help you with your preexec dilemma too.

Simply configure small basic ubuntu vm and configure the samba share to use the whs share as you want. No preexec. Then from any client try accessing the ubuntu share and see if its event will wake the whs. If it works you know what to do when configuring your ubuntu box.

I configured my WHS wake-on-lan only on Magic Packet, otherwise it suspends and immediately resumes (arp?)
So I guess there is a need of the preexec script.


[QUOTE=TheFu]
[http://www.dd-wrt.com/wiki/index.php/WOL](http://www.dd-wrt.com/wiki/index.php/WOL) - ddwrt provides it.
[/QUOTE]
I don't see in the link any way to wakemy WHS on demand.
The automatic wol daemon will keep the server always on, right?

---

### Post by mika912 on 2015-02-24
I confirm that if I don't restrict WOL to magic packet only, my WHS resumes immediately after suspend.
So I guess the autoexec or autofs will be the way to go!

---

