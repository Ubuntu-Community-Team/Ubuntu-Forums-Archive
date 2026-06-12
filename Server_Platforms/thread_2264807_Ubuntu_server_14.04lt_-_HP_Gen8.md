---
title: "Ubuntu server 14.04lt - HP Gen8"
date: 2015-02-10
forum: Server Platforms
---

### Post by Jordon_Blackstock on 2015-02-10
I am currently working with a HP microserver Gen8, 16gb RAM and 4 x 1tb HDD

I am new to ubuntu server, without GUI, and would like to know if anyone can help me.

I am trying to work with Plex server on ubuntu but i cant figure out how to enable my other 3 disks to be able to be read by plex 

my plan is to have 3 1tb hard drives and use them for different media, i.e. 1tb music 1tb films and 1tb tv programs. the reason for having them on different HDD is because my c: drive 1tb drive filled in the space of 2 days with the films and music, and I am planning to set up sickbeard to download tv programs automatically and couchpotato to download films

i am not sure if to set them up in LVM setup or buy a raid card and use them in a RAID5 configuration

---

### Post by grier-devon on 2015-02-10
This guide is for CentOs but should still work, scroll down to the part called " Create a SSH Tunnel with Putty and Firefox", this will give you access to the plex GUI for your server and from there you should be able to set what you are asking now.

[http://infoliser.com/how-to-install-plex-media-server-on-a-centos-6-x-server-and-enable-internet-access-using-ssh-tunneling-with-putty-and-firefox/](http://infoliser.com/how-to-install-plex-media-server-on-a-centos-6-x-server-and-enable-internet-access-using-ssh-tunneling-with-putty-and-firefox/)

---

### Post by darkod on 2015-02-11
If you do not plan to use any raid and a disk fails, are you ok losing all data on it? You don't need a raid card by the way, you can use mdadm linux software raid.

LVM is a nice feature that offers storage flexibility but without using raid under it, I wouldn't do it since single disk failure can possible mess up all data.

If you need that much storage I would consider getting bigger drives and using raid with or without lvm on top of it.

---

### Post by mastablasta on 2015-02-11
why not use 2x 4TB drives? and set them up in raid. if you value the data. if not you can just use what you already have. :) yeah, software raid will work fine.

---

