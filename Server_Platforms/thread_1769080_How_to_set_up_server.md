---
title: "How to set up server"
date: 2011-05-27
forum: Server Platforms
---

### Post by Duvrazh on 2011-05-27
I have a computer that I just ran a fresh install of 11.04 64-bit (including samba, openssh, and I think LAMP).

The computer has a 250GB os drive and 5 x 2TB drives for media storage. The problem is I don't know a damn thing about setting stuff up remotely. The system as it is has done nothing except update packages.

I need to set up an LVM across those 5 drives, share it out, and install a uPnP server on this machine (haven't tested them all but leaning towards PS3 server).

Honestly I think the easiest method would be to install gnome and use an SSH tunneled vnc session from my Windows 7 computer. The problem is I have no clue how to start on actually getting that vnc session to work. Can anyone point me in the right direction? My Google searches mostly lead to highly outdated articles, and all of those tutorials ended in error. Thank you.



PS - One of those 5 drives has a bad sector on it, and if you can tell me how to get the serial number for the drive via SSH so I can install it's replacement, that would be much appreciated also. Thank you. (computer has no video port)
:KS

---

### Post by arrrghhh on 2011-05-27
I wouldn't install GNOME.

You can forward X over SSH if you truly need a GUI app, but honestly once you get comfy with the terminal I find it typically more efficient than a GUI, and there's a lot less in the way of packages to update & worry about security with, etc.

For serial number info,
```
sudo smartctl -a /dev/sda
```Would get you what you need.  Obviously replace /dev/sda with the actual disk in question...

So if you have SSH access, are you just looking for guides on everything?

[LVM Doc](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

[Samba docs](https://help.ubuntu.com/community/Samba)

I recommend PS3MediaServer as well.  There's [a deb package](http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589) that makes it pretty easy to install and maintain.

---

### Post by Duvrazh on 2011-05-27
I'm really not comfortable with the terminal yet. I'm a million times more educated on it than I was a week ago but I'm interested in hearing how to forward X through SSH on Natty.

I think that's what I was trying to do, I have Xming installed now on my Win7 machine. It worked once, I think I got lucky. How difficult is it to forward X, and what disadvantages are there to using it?

---

### Post by Duvrazh on 2011-05-27
> **arrrghhh said:**
> 
For serial number info,
```
sudo smartctl -a /dev/sda
```Would get you what you need.  Obviously replace /dev/sda with the actual disk in question...



I tried this, and while one of my disks shows up with a bad sector in GNOME (previous install - gnome not installed currently), the command line version of these tests says that all my disks pass. I'm confused as to why there would be a different, and I'm growing further interested in using a GUI to configure everything. *shrug* Perhaps the cmd line just isn't for me, at least not right now.

---

### Post by arrrghhh on 2011-05-27
> **Duvrazh said:**
> I tried this, and while one of my disks shows up with a bad sector in GNOME (previous install - gnome not installed currently), the command line version of these tests says that all my disks pass. I'm confused as to why there would be a different, and I'm growing further interested in using a GUI to configure everything. *shrug* Perhaps the cmd line just isn't for me, at least not right now.

Well a few bad sectors wouldn't mean the disk failed to pass a SMART test...

Have you heard of Webmin?  Early on I relied heavily on it - I don't so much anymore, but I still like the way SMART data is presented in Webmin, so I keep it around mainly for that reason - to keep tabs on my hard disks so I can stay ahead of any potential failures.

Forwarding X over SSH to a Linux box is cake.  To a Windows box, it's a little more tricky, since Windows doesn't run X - but if you already have xmming installed, that's all you really need - I assume you're also using Putty in conjunction with it.  If you have a session saved in Putty, edit it and go to the Connection -> SSH -> X11 section.  Tick the 'Enable X11 forwarding' box, and put "localhost:0" in the X display location.  Make sure xmming is running, and connect to your box.  Now you won't see an X window right away, you have to run something that requires X.  So the app is still running on your server, but it's forwarding the GUI parts and using a little X server on your workstation to render the data.

Assuming that last paragraph wasn't complete Greek to you, the only downside I can think of is speed.  Forwarding X over SSH isn't so speedy, even on a LAN.  On a WAN it's downright unbearable.

---

### Post by Duvrazh on 2011-05-27
> **arrrghhh said:**
> Well a few bad sectors wouldn't mean the disk failed to pass a SMART test...

Have you heard of Webmin?  Early on I relied heavily on it - I don't so much anymore, but I still like the way SMART data is presented in Webmin, so I keep it around mainly for that reason - to keep tabs on my hard disks so I can stay ahead of any potential failures.

Forwarding X over SSH to a Linux box is cake.  To a Windows box, it's a little more tricky, since Windows doesn't run X - but if you already have xmming installed, that's all you really need - I assume you're also using Putty in conjunction with it.  If you have a session saved in Putty, edit it and go to the Connection -> SSH -> X11 section.  Tick the 'Enable X11 forwarding' box, and put "localhost:0" in the X display location.  Make sure xmming is running, and connect to your box.  Now you won't see an X window right away, you have to run something that requires X.  So the app is still running on your server, but it's forwarding the GUI parts and using a little X server on your workstation to render the data.

Assuming that last paragraph wasn't complete Greek to you, the only downside I can think of is speed.  Forwarding X over SSH isn't so speedy, even on a LAN.  On a WAN it's downright unbearable.

That sounds fantastic. I'll give it a shot and post results. Thanks Arrrghhh! :)

---

