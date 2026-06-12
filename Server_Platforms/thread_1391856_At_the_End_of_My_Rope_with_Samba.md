---
title: "At the End of My Rope with Samba"
date: 2010-01-27
forum: Server Platforms
---

### Post by RylosFan on 2010-01-27
Ok, ladies and gentlemen, I've reached a new level of frustration trying to keep a samba share working and I really hope someone might give me a bit of direction.  I'm a bit of a novice when it comes to SMB on Ubuntu, but I think I grasp the essential configuration requirements.

I've got a 9.10 Ubuntu x64 Server with samba installed and last night I stumbled across a config that got it working:

(Under Global Settings)
[RoJack Share]
        comment = RoJack Network Share
        path = /home/rojack/Share
        browseable = yes
        read only = no
        guest ok = yes

With "security = share", I wasn't terribly worried about security on this box as it's only for sharing on my LAN at home.

WORKGROUP = ROJACK (on both desktop and server)

With this config, and after setting permissions on both the home and "Share" directories to 777, I was able to browse and write to this share.  I copied about 10GB worth of data from my Karmic x64 desktop; life was good. :D

I then started messing with my fstab in the hopes I could simply automatically mount this share.  I created a mount directory for the share, made a backup of the original fstab.conf, edited fstab with no options for the samba mount, and attempted to mount.  Well, this failed, and since then I am unable to see the server on the network nor can I mount when I point Nautilus at the share.  Although, my desktop seems to be working fine; I can even get to files on it from my Mac.

I took another look at the server and after running testparm, it noted that I have share directories with names longer than 12 characters and may be an issue for Samba clients below 3.0.  

After nights of neglecting my wife and pulling my hair out, I was ecstatic to have this working only to have a functioning share for little more than 30 minutes!  

HELP!  PLEASE! :D

**I apologize ahead of time for not posting the full config from my server, I will post it once I get home this evening.

---

### Post by volkswagner on 2010-01-27
The machine you are trying to automount, is it connected via WiFi or LAN cable?

What does your fstab entry look like?

---

### Post by RylosFan on 2010-01-27
My desktop is connected via ethernet.

As best I can recollect from my fstab entry:

//pandora/home/rojack/Share  /mnt/RoJack  cifs  0 0

I forgot to mention that after the mount failed, I restored my original fstab config.

Again, I apologize for not having the configs with me.

---

### Post by Morbius1 on 2010-01-27
When you get the chance you might want to post the output of the following commands from the server:

Open **Terminal**
Type **testparm -s**
Type **net usershare info**

From the desktop:

Type **smbtree**
Type **findsmb**
Type **nmap -sT 192.168.0.100/22**
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the **desktop***[/COLOR]

[COLOR=Blue]*You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do. Once it's installed run the nmap command again.*[/COLOR]

The commands from the desktop should show us how the desktop sees the network and if we're lucky it will display error messages which will help with the diagnosis. It's odd that you had it working and then you didn't. Can't imagine any scenario in which adding a mount in fstab would affect nautilus seeing the server.

It almosit sounds as if a firewall was enabled in the interim.

---

### Post by RylosFan on 2010-01-27
Thanks, I will try that as soon as I get home and post the output!

---

### Post by RylosFan on 2010-01-27
Ok, I've attached my config from the server (smb-conf) and various outputs.

Running net usershare info on my server had no output.

I also happened to notice that my server (Pandora) is showing in "WORKGROUP" despite being set for "ROJACK".  I can also browse to this share and access files but only through "WORKGROUP".  

I am at a complete loss as to how that happened.

---

### Post by noelvh on 2010-01-27
Well I feel your pain. I have messed with samba for years and did not get it working well till I went to 9.10.

Ok attacked are my smb.conf and my nsswitch.conf bothe in text form. I spent hours on the Internet looking for the answer to this issue. Every one has some thing different that worked for them.

I have run out of time. email me off list for my how too
noelvh at gmail dot com


Problem 3 - Part 1
Open /etc/nsswitch.conf for editing with the following command:
Code:

gksudo gedit /etc/nsswitch.conf

Find the line that looks something like:
Code:

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

For this line, order IS important. You’ll need to add the “wins” option before dns, so the line reads like this:
Code:

 hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Now, save the file by clicking on "File" > "save" and close gedit.

Problem 3 - Part 2
You'll also have to install the winbind daemon in order to resolve hostnames. This is easily done with the following command:
Code:

sudo apt-get install winbind

Then, either restart networking or reboot.

---

### Post by Morbius1 on 2010-01-28
I did find one big problem:

If you look at your smb.conf you'll see this:

> #======================= Global Settings =======================

[global]

[COLOR=Blue] [RoJack Network Share][/COLOR]
        comment = Public Share
        path = /home/rojack/Share
        read only = no
        guest only = yes
        guest ok = yes

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = ROJACK
If you look at the output of testparm, you'll see a lot of this:
> Global parameter xxxxxxx found in service section!The reason that this is happening is that the [COLOR=Blue][RoJack Network Share][/COLOR] share definition is in the wrong place. smb.conf is read in such a way that everything that follows [COLOR=Blue][RoJack Network Share][/COLOR] is considered part of [COLOR=Blue][RoJack Network Share][/COLOR]. It will do that until it reaches another share definition.

Go into smb.conf and move the following to the end of the file:
> [RoJack Network Share]
        comment = Public Share
        path = /home/rojack/Share
        read only = no
        guest only = yes
        guest ok = yes Save the file and then do a [B]sudo service samba restart
[/B]

---

### Post by RylosFan on 2010-01-28
SWEET!  Thank you, Morbius1!  

Such a simple mistake and that seems to have taken care of the problem!

I can browse normally and it mounts instantly!

Thanks to you all for helping a Samba noob!

---

