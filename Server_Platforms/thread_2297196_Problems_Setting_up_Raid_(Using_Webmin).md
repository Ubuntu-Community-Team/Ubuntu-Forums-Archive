---
title: "Problems Setting up Raid (Using Webmin)"
date: 2015-10-01
forum: Server Platforms
---

### Post by Gavin_Blackford on 2015-10-01
Hi,

I have setup a Virtual Machine (VirtualBox) before I build my Home server for real, currently I have 14.04 LTS installed with Webmin. I have setup the s/w raid with Webmin and can see the Status is clean and everything is looking good, my problem is when I try and format it as Ext4 (or Ext3 for that matter).

I am doing the following:
1. Going to Linux Raid
2. Clicking on my device (/dev/md0)
3. Set File system Type to "New Linux Native (ext4)"
4. Clicking create filesystem of type
5. Set Check for bad blocks to Yes
6. Leave everything else with defaults and clicking create

I then get the following error
```

[COLOR=#333333][FONT=Roboto]Executing command [/FONT][/COLOR]partprobe ; mkfs -t ext4 -q /dev/md0[COLOR=#333333][FONT=Roboto] ..
[/FONT][/COLOR]Error: /dev/sdb: unrecognised disk label
Error: /dev/sdc: unrecognised disk label
[COLOR=#333333][FONT=Roboto].. command complete.
[/FONT][/COLOR]
```[COLOR=#333333][FONT=Roboto]

Can anyone help?


Gavin,[/FONT][/COLOR]

---

### Post by darkod on 2015-10-01
Webmin is not an official admin tool. I would avoid configuring serious stuff like raid with it. In fact I would avoid using it at all... Any chance you want to do the raid over ssh session?

Also, did you create partitions to use? You should use partitions, not whole disks as members of the raid. It's better practice.

Make partitions, try creating the array manually and then format it. I'm sure it will work.

---

