---
title: "using old dell machine as a file server"
date: 2010-01-11
forum: Server Platforms
---

### Post by LightLink on 2010-01-11
Hey guys, very simple question here. I have an ancient dell machine that is collecting dust, I want to turn it into a personal file server, the guide I read said there should be two hard drives, one for the os and one to save files on, I only have one hard drive. Is it still possible to use this machine as a server? I hate to just have it sitting around collecting dust.

---

### Post by yeats on 2010-01-11
Depending on your needs, one hard drive should be fine, and it's very simple to add external storage if needed.  I say go for it.  If nothing else, it will be a good learning experience experimenting with server programs.

---

### Post by lukeiamyourfather on 2010-01-11
Its a good idea to use more than one disk but not a necessity. Cheers!

---

### Post by Queue29 on 2010-01-11
One drive is fine, though another one is highly recommended for keeping backups.

---

### Post by poltr1 on 2010-01-11
My experience:  Two disks are recommended, as it's easier to segregate OS and file backups.  But a server can run with only one disk.  Just be sure to back up, as Murphy's Law is part of the design spec of every hard drive.

---

### Post by cariboo on 2010-01-11
My personal file server contains 4 internal and 1 external hardrive, the OS in on a a 10Gb partition on one of the storage drives. It's been running that way for a couple years with no problems.

**Addendum**: The motherboard on my system died about 6 months ago, and was replaced with a motherboard and cpu that a friend of mine found in the local garbage dump, it's been running 24/7 ever since.

---

### Post by LightLink on 2010-01-12
I can add an external hard drive later I guess, I am mainly doing this for the experience but I need some help. The os installed just fine but now I need to be able to access the server remotely.

I have never done anything like this before and am learning as I go. I assume that the server will be hooked up to the router via ethernet cable and will be accessed remotely. The other computers in the house all run windows, how can I set it up so that I maintain the server from my windows machine? It should be noted that I did not install any packages during the installation so not sure what I will need to get for a file server. I do have putty on my windows machine but don't know how to use it.

---

### Post by lukeiamyourfather on 2010-01-12
> **LightLink said:**
> I can add an external hard drive later I guess, I am mainly doing this for the experience but I need some help. The os installed just fine but now I need to be able to access the server remotely.

I have never done anything like this before and am learning as I go. I assume that the server will be hooked up to the router via ethernet cable and will be accessed remotely. The other computers in the house all run windows, how can I set it up so that I maintain the server from my windows machine? It should be noted that I did not install any packages during the installation so not sure what I will need to get for a file server. I do have putty on my windows machine but don't know how to use it.

You'll need Samba to share files with Windows, search for that because there are literally hundreds of guides for setting up Samba that can explain it better than me. To administer the server remotely use ssh. If you have PuTTY already on Windows then open it and use the IP or hostname for the server and connect (ssh enabled by default in most Linux). It'll ask what user to login as and the password, use whatever account you setup on the machine during install of Ubuntu.

If you're not already familiar with the command line then its time to learn. Like configuring Samba, there are a lot of guides out there. This one looks nice.

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

A nice and user friendly command line text editor is "nano" which will probably do fine for editing configuration files on a server. Cheers!

---

### Post by LightLink on 2010-01-12
Well I got it set up, but I have a noob question; at night we turn off all of the computers, I have never had a server before so I'm not sure if it's ever supposed to be turned off, should it be on and running all the time or is it ok to turn it off when it is not needed?

---

### Post by pirateghost on 2010-01-13
> **LightLink said:**
> Well I got it set up, but I have a noob question; at night we turn off all of the computers, I have never had a server before so I'm not sure if it's ever supposed to be turned off, should it be on and running all the time or is it ok to turn it off when it is not needed?

a server is just another computer.  if you dont need it and want to turn it off then do so.  there is nothing that says the server must run all the time...that is up to you

if you have multiple users in the house that will all be accessing the server, then you would want to leave it on, but for learning, you can turn it off whenever you like

---

### Post by LightLink on 2010-01-13
Heh, I made the assumption it was supposed to be on all the time because every time I used the shutdown command the computer would still stay on. I am still learning new commands on the terminal every day and just discovered the wonders of poweroff, thanks for the help.

---

### Post by lukeiamyourfather on 2010-01-13
> **LightLink said:**
> Heh, I made the assumption it was supposed to be on all the time because every time I used the shutdown command the computer would still stay on. I am still learning new commands on the terminal every day and just discovered the wonders of poweroff, thanks for the help.

If you use the shutdown command do it like this.

```
sudo shutdown -h now
```

The -h option is for halt which tells it to power down after shutting down (they are two separate things) and the now option tells it to do it now (or use a delay to shut it down later).

---

### Post by tgalati4 on 2010-01-22
If you search the forums, you can probably activate your server with wake-on-lan.  I have one of my Dell servers set up that way.  I only turn it on when I need it, via a launch icon on my desktop.  That icon runs a simple script:

#!/bin/sh
# Super cheesy script to wake my server and put up a notification to that effect
#
/usr/bin/wakeonlan XX:XX:56:FE:B9:D6
sleep 3
/usr/bin/wakeonlan XX:XX:56:FE:B9:D6
sleep 3
/usr/bin/wakeonlan XX:XX:56:FE:B9:D6
sleep 2
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "GC-Development Server is Booting"  "You'll be up in 3 minutes."
sleep 200
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "GC-Development Server is Alive" "You can login now."
exit 0

---

