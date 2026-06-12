---
title: "How do I image my windows disk?"
date: 2008-11-14
forum: Windows
---

### Post by last1 on 2008-11-14
OK so I need some help doing imaging for a windows hard drive. I haven't used windows in years (thanks to you guys!) and I think I'm not familiar with what to do. It's different than imaging a linux drive, isn't it? Because I'd already tried booting into a systemrescue livecd and making an image of the whole disk using partimage, but it didn't work when it came time to restore the disk to that image. It wouldn't boot at all. I don't know if it's just some thing that I needed to do to a bootloader or something (I'd have thought the image would have taken care of that but maybe I'm wrong?) or if I need a special windows-only application to do this right. 

For simplicity, both systems have their own bootloader on their own disk, and I just boot into windows by changing the hard drive boot sequence. I would have thought that with such a simple setup like this, one where I wouldn't even have need to change the bootloader, that the partimage method I'd used would have worked, if indeed it was a bootloader problem. 

So what the deal, yall? Any advice?

---

### Post by Vince4Amy on 2008-11-14
You could use PING [http://ping.windowsdream.com/](http://ping.windowsdream.com/)

It will create a backup image of your hard drive which you can save to another location on your disk, or on another physical disk, on a network or perhaps burn to CD/DVD (Not sure on the burning one)

Oh I misread the part where you said you've already used partimage. I'll keep this here for reference.

---

### Post by jaqie on 2008-11-15
1) you arent trying to run one licensed OS copy on two comps are you? no? good.
2) the SID needs changed so that things don't go wonky.
3) boot the proper windows install CD, wait for it to give you the option to go to a system recovery console. Do such.
4) fixmbr
3) for good measure check out bootcfg too

---

### Post by last1 on 2008-11-15
hey jaqie couple questions for you, if i'm restoring from an image that is the exact same as the current system, then why would this restored copy respond any differently to the SID than the current system? anyway besides that, what happens if i don't run the recovery console and fixmbr, will it boot at all? if not, maybe my partimage backup worked after all and I just didn't do this one thing. man, that would be somethin. 
Oh and if i just used norton ghost does it do this kinda stuff automatically or would i still need to do mundane commandline stuff to get it back up and running? because i just got a copy of it but it's cracked and i'd rather not get virused out in my attempt to back it up in case of getting virused out. kinda defeats the point if i did that, but on the other hand i'm all in favor of any approach that means less work for me. and also i'm just really scared of using partimage and not ending up with a working system again when actually going to use the backup, since it already ended badly once. so not much room for experimentation since my system right now actually works and i'd like it to you know, stay that way.. what you think should i give ghost a try or is it even that much better at functionally doing things in a better way than partimage?

---

### Post by maybeway36 on 2008-11-16
You could try using dd + gzip. IT would restore the image exactly, but the HDs would need to be the same size.
```
dd if=/dev/hda|gzip>file.imz
gzip -cd file.imz|dd of=/dev/hda
```

---

### Post by last1 on 2008-11-17
That's another thing I was wondering about. When they need to be the same size, does that mean they need to be the same size down to the byte?

---

### Post by elj4176 on 2008-11-17
I just tried using dd and gzip (version 1.3.3) and it quits after 2 GB. Am I missing a parameter in the command line? Here is the command I used:

dd if=/dev/sdb | gzip > /mnt/networkdrive/backup.gz

---

### Post by cdtech on 2008-11-17
Sounds like file size limitations which is explained here:
[http://wiki.linuxquestions.org/wiki/Dd](http://wiki.linuxquestions.org/wiki/Dd)

---

### Post by elj4176 on 2008-11-17
I was just going to link to that page. On the gzip.org page it says that the size limitations should not be a problem with the version I am using.

For those that do not want to look up the answer here is the command I'm using with success:

dd if=/dev/sdb | gzip -c | split -b 2000m - /mnt/networkdrive/bu.img.gz

It is splitting the backup image into 2 GB chunks. To restore these files:

cat /mnt/networkdrive/bu.img.gz.* | gzip -dc | dd of=/dev/hdb

---

