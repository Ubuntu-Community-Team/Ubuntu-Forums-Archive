---
title: "[SOLVED] Server network settings"
date: 2008-07-03
forum: Server Platforms
---

### Post by sp0nge on 2008-07-03
Hello to all! 

I have recently installed the 8.04 server edition on a spare machine that I want to use as a testing ground for hosting my own websites. 

I found a [tutorial]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3") that walks me through setting everything up the way I think I want it (for now) but I'm running into some issues.

I'm working to configure the file "/etc/network/interfaces" and I have some changes for my network I'm using the following: 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.199
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

I think that is correct for my current router setup. 

My problem is that I have never used VIM before and when I try to save the changes, I get a red bar along the bottom of the screen saying "E45: 'readonly' option is set (add ! to override)". I have tried every command I can find that will save the changes and have added the "!" both at the beginning and the end but am unable to save the settings. I finally got some progress. After I edited the file, I <esc> to command mode and then type ":w!" which gives me: 

```
"/etc/network/interfaces" E212: Can't open file for writing
Press ENTER or type command to continue
```

Please help point me in the right direction.

---

### Post by Titan8990 on 2008-07-03
IMO nano is the way to go. VIM is more of a "standard" so it is good know how to use it.

To save and quit and vi would be:

:wq  

(write and quit)

To me it sounds like you may not have permissions to edit the file. Are you root?

---

### Post by sp0nge on 2008-07-03
I appreciate your opinion. I have only played with VIM and Gedit briefly. 

I am not logged into the root account but I had done su a few lines before I edited the file. Do I need to be logged into the root account or need to su each command? I was under the impression that the su lasted for a period of time.

---

### Post by ixus_123 on 2008-07-03
either way will do.

As the poster above said, nano is a lot easier but it's very good to get used to using vi - this is because it's pretty much available on all linux systems, when nano is not.

in vi, pressing "i" will get you to insert mode where you can add / delete text.

once you have made your changes, hit ESCAPE, then :  

this will give you a prompt at the bottom of the screen

wq!  - that will Write and Quit

just quit if you messed up the file and don't want to save your changes.

Don't forget to restart networking when you've made your changes so they take effect

The cool thing is that wont log you out of a SSH session - not quite sure how that works :)

---

### Post by ixus_123 on 2008-07-03
to run as root type


sudo su

or to enable you to log in as root:

sudo passwd root

  - enter password
 - repeat, repeat

su - (logs you in as root)

now you can edit your file

---

