---
title: "Super Newbie questions"
date: 2009-04-12
forum: Server Platforms
---

### Post by FoFa on 2009-04-12
Wanted to spread my wings past windows, and I needed a server mostly for data storage, but also for some shared things on my home network.
Since I have an older PC sit'n around not doing anything, a dual CPU (not dual core) 32 bit currently with Windows XP loaded on it, I figured I could setup an Ubuntu server and use it for that.
I D/L the 8.1 (or was 8.10, the current on as of today) server iso and burned it to a CD.

I am guessing I need to hook up a monitor, keyboard and mouse the PC and just install it.

Do I need it hooked  to my router when I do that?

Once Ubuntu server is setup, how can I remote to it with my current Windows XP PC to manager it, it won't have a monitor/keyboard/mouse hooked to it at that time.
Something like Windows remote desktop?

It only has a 160 GB drive in it today, if i want to add a large drive for data storage later, how hard it is to configure the drive after it is installed? Is there any limitions on drive size using the 32 bit version?

Thanks

---

### Post by cariboo on 2009-04-12
> I am guessing I need to hook up a monitor, keyboard and mouse the PC and just install it.


You need a monitor and keyboard to do the initial setup. Once you have the server setup to your liking you can unhook the monitor and keybpord, then put your server wherever you want. 

> Do I need it hooked to my router when I do that?


You don't need to have network acces to install the server, but I would suggest you do, as there are quite a few updates that should be done after installation.

> Once Ubuntu server is setup, how can I remote to it with my current Windows XP PC to manager it, it won't have a monitor/keyboard/mouse hooked to it at that time.
Something like Windows remote desktop?


I use ssh and sftp to manage my server. The server installation does not install a desktop, so rdp isn't possible. I would suggest you have a look at [webmin]("http://webmin.com/") as a means of managing your server, it is web based.

> It only has a 160 GB drive in it today, if i want to add a large drive for data storage later, how hard it is to configure the drive after it is installed? Is there any limitions on drive size using the 32 bit version?


I have added a couple of hard drives to my server since I initially set it up. You will have to add the drives to /etc/fstab if you want them to be mounted on start up. The last drive I added was an external usb (750Gb) that I use for backups. I just plugged it in created a mount point and mounted the drive. I haven't bothered with setting it to mount automatically as I haven't found a need to restart the server since adding it. BTW I have my server connected to a ups, so short power outages are not a problem. Anything longer than an hour though and the server shuts down and reboots automagically when the power is restored.

Jim

---

### Post by ugm6hr on 2009-04-12
Ubuntu is a good choice, but I suspect that you will find FreeNAS (FreeBSD-based) much easier.

I have recently done something very similar, and after experimenting with Ubuntu Server, I went with FreeNAS for simplicity, and the easy Web GUI.

Additionally, it is *possible* to install it with just a keyboard (i.e. no monitor), or even without that if your network gateway is on 192.168.1.1

Check the link in my sig for further references (still a work in progress).

---

### Post by hyper_ch on 2009-04-12
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by FoFa on 2009-04-13
Thanks, just the direction I was looking for.

---

