---
title: "HOWTO: Mount external eSATA drive with permissions."
date: 2013-07-12
forum: Tutorials
---

### Post by Bucky Ball on 2013-07-12
**My original problem:**

* Ubuntu 12.04 LTS minimal install running xfce4 as desktop manager and PcmanFM as file manager. 
* 2Tb external drive plugged in via eSATA (/dev/sdb). Can see the two partitions on it in the file manager, machine recognises the drive, but when I click a partition in file manager, I get asked for my password as I don't have permission to mount the drive.

My issue is caused by the system considering the external eSATA drive to be an internal SATA one. This thread shows how to write a udev rule to correct the issue. It appears to be a condition of the minimal install. This ancient bug appears to be fixed in more recent desktop versions as the drive is mounted with permissions when plugged in on my regular Xubuntu 12.04 LTS install. 

*_Can this thread help you? _*If you are plugging in your external eSATA drive and it does not appear in the file manager, check if the system has picked it up at all by looking in the /dev directory or issuing:

```
sudo blkid
```

Not there? Then I advise trying to figure out why and moving on, as this page can't help you. Although it's possible it might give you some clues, it's unlikely. ;)

[CENTER]*[/CENTER]

**1/ Find drive's block node.**

First, plug in the external eSATA drive and, if you don't already know its sd*, with the drive plugged in and on, issue this in a terminal:

```
sudo blkid
```

With the drive plugged in and on and, most importantly, recognised in /dev, copy and paste the command below into a terminal, changing the 'sdb' at the end with the details of your external eSATA drive: 

```
sudo udevadm info -q path -n /dev/sdb
```

If that did't supply anything, try this:

```
find /sys/devices/ -name sdb
```

You should get an output something like this:

```
/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sdb
```

Keep this information for the next step. (I opened another terminal so I could simply copy and paste it over in the next step.)

Take note of the /dev/sd* at the end of the output. It should coincide with the drive's /dev/sd* discovered by 'sudo blkid' earlier. If it doesn't, you're finding the wrong drive and need to check your 'sd*' is correct at the end of the command in the previous step. If there's no output, either the drive is not in and on, was not showing in /dev in the first place or there is a syntax error in your original command (copy and paste best).

[CENTER]*[/CENTER]
[B]
2/ Create a new udev rule for the eSATA drive. [/B]

First, create a file for the rule. Check that the rule number at the beginning is not the same as an existing rule's by checking them with:

```
dir /etc/udev/rules.d
```

We're numbering our udev rule number 10 here, in the form '10-esata.rules', but you'll need to change the rule number if a '10-' rule already exists, say '/11-esata.rules' or '/90-esata.rules'. To create the rule file:

```
sudo touch /etc/udev/rules.d/10-esata.rules
```

Next, we want to copy and paste the rule into the file. Changing the rule number of file below as required, issue:

```
sudo nano /etc/udev/rules.d/10-esata.rules
```

Replace everything between the brackets in the command below with the information you discovered with 'sudo udevadm info -q path -n /dev/sdb' in the first section then issue the command in a terminal:  
```

DEVPATH=="/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sdb", ENV{UDISKS_SYSTEM_INTERNAL}="0"
```

This needs to be on one long line. DO NOT split with a line break. Take note, the end of the command which tells the system the eSATA is NOT and internal drive is the big fish and what this is all about:

```
ENV{UDISKS_SYSTEM_INTERNAL}="0"
```

 ;)

Save and exit the file. 

[CENTER]*[/CENTER]

Plug in the external eSATA, check the file manager. You should see the partitions, probably unmounted as they were before you started any of this, but now when you click the partition icons they should mount with permissions. If not, unplug drive, reboot, get to a desktop and try again. 

Reason not to have the drive plugged in and on at boot? Because the eSATA drive will be considered an internal drive by the machine and therefore mounted without issue and we won't know if the fix worked. The point of the fix is to pick up the eSATA drive with full permissions when plugged in 'on the fly' while the system is already up.

The partitions unmount fine, too, but for me, they close the file manager as they're doing it. No biggie. I'm using PcmanFM so it might be specific to the FM.

[center]*[/center]

I spent quite some time trying to get to the bottom of this so hope this condensed version cuts your search short. For the full story and more information, these are the links that got me to the line, the Archlinux udev rules link in particular giving plenty of food for thought:

[https://wiki.archlinux.org/index.php/Udev#Mark_internal_SATA_ports_as_eSATA](https://wiki.archlinux.org/index.php/Udev#Mark_internal_SATA_ports_as_eSATA)
[http://hackaday.com/2009/09/18/how-to-write-udev-rules/](http://hackaday.com/2009/09/18/how-to-write-udev-rules/)

Many thanks to the authors and contributors there and to others here, particularly Bashing-om for their consistent, persistent and appreciated ideas, encouragement and support with this. ;)

Just a note: while researching a fix for this, I discovered this little niggle has been around for at least six years. There are bug reports and unresolved threads everywhere regarding it. While it appears to be minimal (or custom perhaps) install specific and has been fixed in a normal 'desktop' install, I'm still surprised a clear, concise, how-to for this was nowhere to be found, which is why I wrote this, in the hopes it would fill that gap. Feel free to post with improvements, suggestions, feedback.  

Good luck.

---

