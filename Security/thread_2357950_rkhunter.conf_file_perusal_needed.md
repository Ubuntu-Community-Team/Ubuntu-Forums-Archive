---
title: "rkhunter.conf file perusal needed"
date: 2017-04-07
forum: Security
---

### Post by SciGuy1872 on 2017-04-07
Hi.  I have installed chkrootkit and rkhunter because I figure a Linux machine without is like a Windows computer without a virus scanner and malwarebytes.
I have edited files for rkhunter since seeing a Community Wiki: [viewing]("https://help.ubuntu.com/community/RKhunter#preview").  I was wondering if someone could view my editing and give advice:

[LEFT]

[SIZE=3][COLOR=#333333][FONT=inherit]**/etc/rkhunter.conf**[/FONT][/COLOR][/SIZE][/LEFT]
[SIZE=3]
[COLOR=#333333][FONT=Ubuntu]By instructions of the Wiki--"un-comment the related ALLOWHIDDENDIR and ALLOWHIDDENFILE lines".[/FONT][/COLOR][/SIZE]

  ```
[LEFT]ALLOWHIDDENDIR=/etc/.java[/LEFT]
ALLOWHIDDENDIR=/etc/.git
ALLOWHIDDENDIR=/dev/.lxc
ALLOWHIDDENDIR=/dev/.udev
ALLOWHIDDENDIR=/dev/.static
ALLOWHIDDENDIR=/dev/.initramfs


ALLOWHIDDENFILE=/usr/share/man/man1/..1.gz
ALLOWHIDDENFILE=/usr/bin/.fipscheck.hmac
ALLOWHIDDENFILE=/usr/bin/.ssh.hmac
ALLOWHIDDENFILE=/usr/lib/.libfipscheck.so.1.1.0.hmac
ALLOWHIDDENFILE=/usr/lib/hmaccalc/sha1hmac.hmac
ALLOWHIDDENFILE=/usr/lib/hmaccalc/sha256hmac.hmac
ALLOWHIDDENFILE=/usr/sbin/.sshd.hmac
ALLOWHIDDENFILE=/usr/share/man/man5/.k5login.5.gz
ALLOWHIDDENFILE=/usr/share/man/man5/.k5identity.5.gz
ALLOWHIDDENFILE=/etc/.gitignore
ALLOWHIDDENFILE=/etc/.bzrignore
ALLOWHIDDENFILE=/etc/.etckeeper
```

Like the Wiki said again, I made the Autogen line edit to: **/etc/default/rkhunter **[COLOR=#333333][FONT=inherit]

"Torun [/FONT][/COLOR][COLOR=#333333][FONT=inherit]**rkhunter--propupd**[/FONT][/COLOR][COLOR=#333333][FONT=inherit],automatic after software updates, add theline [/FONT][/COLOR][COLOR=#333333][FONT=inherit]**APT_AUTOGEN="yes"**[/FONT][/COLOR][COLOR=#333333][FONT=inherit] to [/FONT][/COLOR][COLOR=#333333][FONT=inherit]*/etc/default/rkhunter*[/FONT][/COLOR][COLOR=#333333][FONT=inherit] (thisgets read by [/FONT][/COLOR][COLOR=#333333][FONT=inherit]*/etc/apt/apt.conf.d/90rkhunter*[/FONT][/COLOR][COLOR=#333333][FONT=inherit])".[/FONT][/COLOR]
```
# Set this to yes toenable automatic database updates
# (default: false)
APT_AUTOGEN="yes"
```I'm also wondering if there is some other malware on this computer that necessitates a fresh install:

[COLOR=#333333][FONT=Ubuntu]SoftwareUpdater installed two GRUBS, but I only have one drive.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]TheDisk utility, or program, shows: /dev/sda1 (150GB, Bootable) and/dev/sda2 (4GB and an Extended Partition) and the /dev/sda5 Swap partition of 4GB.  I have an SSD that onlycontains Ubuntu Mate—so I should have a Bootable partition and aSwap partition, I think?  I haven’t done any partition work since Iinstalled Mate on this drive.

Results of RKHunter:

[/FONT][/COLOR]```
Warning: Suspicious file types found in /dev:[19:35:11]          /dev/shm/pulse-shm-3542474028: data
[19:35:11]          /dev/shm/pulse-shm-976301516: data
[19:35:11]          /dev/shm/pulse-shm-4096120404: data
[19:35:11]          /dev/shm/pulse-shm-1728456032: data
[19:35:11]          /dev/shm/pulse-shm-3058155598: data
[19:35:11]          /dev/shm/pulse-shm-3098095716: data
[19:35:11]          /dev/shm/pulse-shm-2826839687: data
[19:35:11]          /dev/shm/pulse-shm-2090505592: data
[19:35:11]          /dev/shm/pulse-shm-3971778385: data
[19:35:11]          /dev/shm/pulse-shm-3115748498: data
[19:35:11]          /dev/shm/pulse-shm-4269557501: data

[19:35:11]          /dev/shm/pulse-shm-2079646449: data
```[COLOR=#333333][FONT=Ubuntu]


Thanks for your advice and help.[/FONT][/COLOR]

---

### Post by CharlesA on 2017-04-07
Usual false positives.. If you really want to deal with it, add the config option to ignore pulse-shm.

See here:
[https://sourceforge.net/p/rkhunter/mailman/message/25538705/](https://sourceforge.net/p/rkhunter/mailman/message/25538705/)

---

### Post by Irihapeti on 2017-04-07
In the 10 years I've been on the forums, I've never seen a single person find malware with rkhunter or chrootkit. But I've seen a lot of panic arise on account of false positives. To me, it seems of dubious value. It might be of use on some kinds of server, but not on a desktop.

---

### Post by SciGuy1872 on 2017-04-08
Thanks for the answers--so there's nothing suspicious about Software Updater installing two GRUBs when I only have one drive containing Mate?   When I use the program, Disks, I see that this one drive is divided by bootable partition, Swap partition, and another partition of 4GB that is labeled as an Extended Partition.  I thought a fresh install would result just in the bootable and swap partitions?

---

### Post by Irihapeti on 2017-04-08
What is the reason that you think that Software Updater has installed two GRUBs? If we saw that, we might be able to tell you what's happening.

---

### Post by deadflowr on 2017-04-08
> **SciGuy1872 said:**
> Thanks for the answers--so there's nothing suspicious about Software Updater installing two GRUBs when I only have one drive containing Mate?   When I use the program, Disks, I see that this one drive is divided by bootable partition, Swap partition, and another partition of 4GB that is labeled as an Extended Partition.  I thought a fresh install would result just in the bootable and swap partitions?

Most likely extended = swap
Extended partition are just primary partitions that can contain logical partitions of which Ubuntu places the swap partition.
Ubuntu has done it that way for a long time.

Typical out of the box partitioning scheme is /dev/sda1=/, /dev/sda2=Extended, and then /dev/sda5=swap, which is actually a logical partition which is actually housed inside the /dev/sda2 extended partition.

This is really part of the more legacy MBR partitioning, as oppose to the newer gpt partitioning.
(MBR partition allow only 4 primary partitions, but that can be extended by setting one primary as an extended partition which can then contain a large multitude of logical partitions.
GPT does away with that non-sense, allowing you to have a larger multitude of primaries without the need for an extended partition to contain logical partitions)

Hope that make sense.

It's a rather armchair explanation...

---

### Post by SciGuy1872 on 2017-04-08
Okay, the post from deadfowr appeared after I first posted this--so the partitions are normal--are the two GRUBs? 

I ran the Software Updater and after clicking Install (I think that was when the screen gave me the unusual dialog box), I was presented with an option to tick two boxes.  I ticked both boxes because on that window, it mentioned that it may not boot if GRUB was not present. I only have one OS (Mate) and I don't mess with partitions.

Maybe I'm losing my mind :(

---

### Post by Irihapeti on 2017-04-08
Maybe it asked you for /dev/sda or /dev/sda1?

The former is definitely preferred, but if you installed both and you can still boot normally, I'd not be too worried. Unless of course someone with more experience says so.

Chances are excellent that everything is fine. But it's normal to worry a bit if you're not used to this, and especially if you've spent a lot of time with Windows.

Make sure that you have backups, in case stuff goes wrong. Then you can recover from pretty much anything, if necessary.

---

