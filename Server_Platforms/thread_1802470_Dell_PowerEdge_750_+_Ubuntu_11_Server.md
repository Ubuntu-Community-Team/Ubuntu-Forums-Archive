---
title: "Dell PowerEdge 750 + Ubuntu 11 Server"
date: 2011-07-12
forum: Server Platforms
---

### Post by teslamad on 2011-07-12
I have several 1U Dell PowerEdge 750's that need Ubuntu 11 Server 32 Bit edition installed. I tried to install the first tonight and it went on flawlessly as expected with Ubuntu "most of the time". The trouble came when it rebooted. As soon as the CD was kicked out, the server rebooted, POSTd, and tried to load GRUB (which im sure it did... in fact it probably boot up completely fine), but I cant see anything. The monitor will not work with the server. Says "Cannot display the video mode." I've never had this trouble before. I have tested on several monitors, some old, others brand new so I know im not out of video resolution in terms on the monitor. I have no way (to my knowledge) to boot into text mode (which it should be doing anyways...) or anything because all I see is post. I don't get a chance to see anything Linux related. No serial console access, and this is just sitting on bench for now so no network access too. Just need the bloody local terminal! UGH! Please help me.

---

### Post by BobVila on 2011-07-12
Reboot it and hold shift while it boots up; that should dump you into the grub menu - from there you can edit the default boot option or boot into Ubuntu with serial console support.

---

### Post by teslamad on 2011-07-12
Tried your suggestion. Held shift upon boot and grub started loading. "GRUB loading.", but immediately after screen turned off again and did same thing. "Cannot display the video mode." Any other suggestions? I find it hard to believe that the onboard graphics inside this PowerEdge server cannot handle the server version of Ubuntu 11. Thanks in advance for all the help.

---

### Post by teslamad on 2011-07-27
Does no one else have any suggestions? I gotta get these servers up. Thanks ahead of time for the help.

---

### Post by teslamad on 2011-08-06
Kinda solved... Ubuntu 11 never worked, but for some reason after a second try, Ubuntu 10 LTS seemed to work in case anyone else is having a similar problem.

---

### Post by teslamad on 2013-04-14
So I revisited this issue and I now have a solution. As the current version is 12 LTS, I tested it on that, but this will probably work for my old question too which was on 11. Here's the solution:

(Ignore all "Quotes" around commands)

1.  Install Ubuntu 12 like normal
2.  Be sure to install SSH so you can access the server. You will also need to use DHCP so the server is completely auto configured at boot since you have no display yet.
3.  SSH into the server.
4.  Do a "sudo -s" to gain root privileges. 
5.  Edit this file: /etc/default/grub You can do this by typing "nano /etc/default/grub"
6.  Uncomment the following line: GRUB_GFXMODE=640x480
7.  Save and exit nano by pressing "Ctrl-X"
8.  Now run grub update by typing: "update-grub"
9.  Finally, just reboot by typing: "reboot"
10.  Cheers!

---

### Post by kmw288 on 2014-02-28
Thanks TMad.. Worked great!

---

