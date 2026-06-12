---
title: "ALERT! /dev/mmcblk0p1 does not exist"
date: 2019-08-23
forum: Ubuntu/Debian BASED
---

### Post by johantonissen on 2019-08-23
[COLOR=#64676F][FONT=&quot]Hi there,[/FONT][/COLOR]
[COLOR=#64676F][FONT=&quot] [/FONT][/COLOR]
[COLOR=#64676F][FONT=&quot]I have a rockpi 4b running armbian bionic desktop legacy kernel 4.4y on a 128 GB emmc module, I'd like to use this machine as a server.
I was just tinkering around with Plex, .bashrc and crontab while all of a sudden the keyboard mapping over RDP changed (e.g. > became ;, ~ became @ etc) (indication of the problem?).
I tried to fix this by changing the system keyboard layout and running ```
[COLOR=#333333][FONT=Consolas]dpkg-reconfigure keyboard-configuration[/FONT][/COLOR]
```, this all didnt work.
I decided to reboot the machine to see if that would work. After the reboot I could not connect to either RDP or SSH so I decided to connect the machine to a HDMI monitor. This resulted in the following output:
[IMG]https://i.ibb.co/PNC05zb/IMG-20190823-183204.jpg[/IMG][/FONT][/COLOR]
[COLOR=#64676F][FONT=&quot]
Can anyone help me understand what I am seeing here and how this could have happened ? Is this even Ubuntu ? Or is this GRUB ? Where in the boot process is this ?

My guess is that the whole EMMC is diconnected but this seems very weird since I did not touch the board in any way.

I'm now thinking of solving this problem by attatching the emmc to a sd reader and backing up the etc,home,opt,root,srv,usr and var folder, reflashing the image and putting the folders back. This is however a very destructive process so I hope something less destructive is possible. I also even don't know if this is going to work since I have no idea how this problem was caused.

Can anyone help me please ?

Thanx in advance![/FONT][/COLOR]
[COLOR=#64676F][FONT=&quot] [/FONT][/COLOR]
[COLOR=#64676F][FONT=&quot]Thank you in advance[/FONT][/COLOR]

---

### Post by him610 on 2019-08-23
Not familiar with rockpi, but if it is anything like a raspberrypi then */dev/mmcblk0p1 *is the SD card where the operating system resides, and it may have  loosened in its socket, or it may have become corrupted or died.

---

### Post by johantonissen on 2019-08-24
There actually isnt a SD card in there, i run from an emmc, wich just worked in the past.

---

### Post by johantonissen on 2019-08-24
When I try to mount the EMMC using an EMMC to SD converter the mounted card cannot be opened because it's read-only. Is this a sign of a failing emmc ?

---

