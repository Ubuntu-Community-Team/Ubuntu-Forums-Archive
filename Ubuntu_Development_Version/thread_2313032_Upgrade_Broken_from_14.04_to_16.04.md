---
title: "Upgrade Broken from 14.04 to 16.04"
date: 2016-02-09
forum: Ubuntu Development Version
---

### Post by Hansih on 2016-02-09
Hi am trying to upgrade from 14.04 to 16.04 in the process I got blank screen from longer period of time so I have restarted my system and then it is not booting and in advance option there are too many recovery options.. How can I fix this .Kindly help me am attaching what is the error it is showing.

---

### Post by howefield on 2016-02-09
Thread moved to the "*Ubuntu Development Version*" forum.

You are aware that 16.04 hasn't been released and is still in development ?

---

### Post by Hansih on 2016-02-09
yeah am aware that it is still in development. Now if I want to go back to my 14.04 do I need to do fresh installation or what should I do now

---

### Post by dino99 on 2016-02-09
why not doing a fresh 16.04 install with the daily iso ?

---

### Post by Hansih on 2016-02-09
Am new to Ubuntu. If I do fresh like 15.04 will my old file will be there in my system . I have important file in my system can some one suggest me.

---

### Post by tokyobadger on 2016-02-09
I may be wrong but as 16.04 is still in development the upgrade path/mechanism from 14.04 is probably not yet implemented. As for your current options:

1) downgrade to 14.04 is basically not realistic

2) reinstall 15.04/15.10/16.04 keeping your current data if I recall correctly it is possible - [this thread outlines some options]("http://ubuntuforums.org/showthread.php?t=2057342")

3) my recommendation would be to back up your important files and then install fresh either 15.10 (15.04 is already end of life - EOL as of 2016/02/04) or 16.04 which many of us are using as a daily driver, with the caveat that it is not an official release yet; that said, it is one of the smoothest development cycles I have participated in (I always run current in-development version, latest release, latest LTS in parallel)

Other members with more experience/skill will probably add to my suggestions above if you can wait a little longer

---

### Post by howefield on 2016-02-09
> **Hansih said:**
> Am new to Ubuntu. If I do fresh like 15.04 will my old file will be there in my system . I have important file in my system can some one suggest me.

You mean you attempted to upgrade from a supported release to a development release and don't have backups of your "*important file*". Nice going. :|

15.04 is end of life so best to forget that idea. The real choices are 14.04.x or 15.10.

Given that you are new to Ubuntu (not sure if you are new to the linux environment in general) but I'd recommend a fresh install of 14.04.x

If you choose the "Something else" option when mounting the partitions to install to, you can mount the existing / partition and reuse it (but not mark it for formatting) and your existing /home should be preserved. However I strongly recommend backing up your "*important file*" beforehand.

Leave 16.04 well alone unless you are prepared for breakage or to assist in the development by reporting bugs ect. Nothing wrong with having a pristine working 14.04.x and a separate (for me, ymmv), however I have many contingencies in place for when things do go wrong. :)

---

### Post by dino99 on 2016-02-09
you might not be scared about your data if they are stored into a separate /home partition. But if they are into a home folder, then you need to backup them first, as the partition will be formatted by a fresh install.

Glance at the links below to get more knowledge.

---

### Post by zika on 2016-02-09
> **dino99 said:**
> you might not be scared about your data if they are stored into a separate /home partition. But if they are into a home folder, then you need to backup them first, as the partition [SIZE=6]**will be formatted**[/SIZE] by a fresh install. Glance at the links below to get more knowledge.Not if You do not choose that way. You can choose to preserve home (and more)... But backup is sine qua non. @OP: Use USB to boot Live and backup Your files. Chroot is a good tool for that...

---

### Post by grahammechanical on 2016-02-09
Now that we have learnt that it is never wise to power off during an upgrade to another version, there is still this situation
> is not booting and in advance option there are too many recovery options.

Each Linux kernel that was installed will have a recovery mode option. Pick one and try it. If you get to a recovery menu then you will see these options

1) Resume - resume normal boot
2) Clean - try to make free space
3) dpkg - repair broken packages
4) failsafeX - run in failsafe graphic mode
5) fsck - check all file systems
6) Grub - update grub boot loader
7) Network - enable networking
8) Root - Drop to root shell prompt

I would suggest doing option 7) Network. The machine will need to be connected to the internet and then select option 8) Root and run these commands

```
apt-get update
apt-get upgrade
apt-get dist-upgrade

```

to get back to the recovery menu type exit and at the recovery menu select option 1) Resume and see where that gets you. If you get to a login screen and working desktop, then update daily until 16.04 is officially released.

A lot will depend on how far the upgrade had got before the machine was powered off as to how successful this advice will be.

Regards.

---

### Post by zika on 2016-02-09
```
apt-get install -f
dpkg --configure -a
```[COLOR=#000000][FONT=Monaco]are likely to be neeeded. Not knowing the state of kernel and seeing picture I, still, would use chroot. Backup, before...[/FONT][/COLOR]

---

### Post by Hansih on 2016-02-09
Thanks for your response. Luckily I have windows partition of 30GB I have removed it and done fresh installation of 15.10 and then copied all my important data then totally formatted my system and done the fresh installation. Thanks for you time and your responses.

---

