---
title: "AOL Help Needed"
date: 2007-03-26
forum: The Cafe
---

### Post by TuxPeng on 2007-03-26
I know there are millions of how tos and posts about connecting to AOL, the most popular, PengAOL does not work for me, I need help connecting to aol, I have a Moto SB4200 Cable Modem with ethernet but AOL refuses to let the connection through, my TiVo can connect and it runs linux. I'm baffled AOL says they have to authenticate, SCREW that :'( PLEASE HELP! If any one can get PenAOL to work RIGHT and RELIEBLY please PM me and you get a cookie! :)

And P.S. No I cant change ISPs.

---

### Post by TuxPeng on 2007-03-26
Hey okay so I found this
[http://www.overclock.net/linux-unix-mac/76200-ubuntu-aol.html](http://www.overclock.net/linux-unix-mac/76200-ubuntu-aol.html)
AND AM SO HAPPY
IS that all I would have to do? How do I get my ethernet to work on linux I'm also a complete linux n00b :-l=p

---

### Post by espresso on 2007-04-19
Hey there, I had this problem for ages until very recently. You may already have seen this message in another thread, but here are the instructions that got me up and running on Ubuntu 6.06: -

> **pilgrim-online said:**
> **oneup,**

I have checked and edited the following this morning.
I cannot see anything that I have missed out but if you have problems get back to me and I will try to help.
Read the whole thing through carefully before you start.
I cannot emphasise too much the point I made in my previous post about the time involved.
In all the things I have read about this the implication is that connection happens quickly.
_**It doesn't!**_

[SIZE="4"]Modem needs to be unplugged from USB before booting into Ubuntu.[/SIZE]

[SIZE="4"]Copy to Home Folder:[/SIZE] [I downloaded in Windows and transferred by Pen Drive.]
pppoe_3.5-4ubuntu1_i386.deb
eciadsl-usermode_0.11-1_i386.deb
eciadsl-synch_bin.tar.bz2

[SIZE="4"]Install:[/SIZE]
Enter in terminal: [One at a time. As each installs several lines of text appear.]
1]  sudo dpkg -i pppoe_3.5-4ubuntu1_i386.deb
2]  sudo dpkg -i eciadsl-usermode_0.11-1_i386.deb
3]  sudo tar -xjvf eciadsl-synch_bin.tar.bz2 -C  /etc/eciadsl/

[SIZE="4"]Reboot.

Plug in modem.

Enter in terminal:[/SIZE]
sudo eciadsl-config-text

Enter as follows:
user name:  *******@aol.com
password:  ******
Provider:  other
DNS1:  205.188.146.145
DNS2:  205.188.146.145
VPI:  0
VCI:  38
Modem:  BT Voyager 105
VID1/PID1/VID2/PID2:  accept defaults
Modem Chipset:  GS7470
Synch File:  /etc/eciadsl/gs7470_synch03.bin
PPP Mode:  accept default
is DCHP used?  No
is a static ip used?  No

Mode:  VCM_RFC2364

Click Create Config.
Close terminal.

[SIZE="4"]To Start.[/SIZE] [See * below.]
Enter in terminal:  sudo eciadsl-start

[SIZE="4"]To Stop:[/SIZE]
Enter in terminal:  sudo eciadsl-stop


*May need to enter 'start' then 'stop' then 'start' again in different terminals?

[Having now been using this for some time I type sudo eciadsl-start into a terminal, leave for about 30 seconds by which time it has reached 4 out of 5 stages.
I then open a second terminal and type sudo eciadsl-stop, this is usually denied but it triggers the first terminal to connect.]
My problem now is that I upgraded to 7.04 this morning and now this method doesn't work! I think I better get back to 6.06 for now...

All the best,

espresso

---

### Post by espresso on 2007-04-20
I have since worked out how to connect using 7.04. I had to download an update from the eciadsl website. Then to access the configuration file I had to set BASH as the default shell with this command: -

```
sudo ln -sf /bin/bash /bin/sh
```

Hope this helps someone!

---

### Post by jiminycricket on 2007-04-20
I thought dash was /bin/sh in Edgy Eft as welll?  Maybe it replaced your old symlink to bash during the upgrade.

---

