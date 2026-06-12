---
title: "Xeon (very very slow will boot) hangs at Starting up... Takes long for drive ops."
date: 2009-02-14
forum: Server Platforms
---

### Post by KamakazieX on 2009-02-14
I have a SuperMicro 6022P-6 /w a P4DP6-Q motherboard.. 

It doesnt exactly hang at starting up, but takes forever to get going after (maybe 10 minutes?) It also has this bizzare symptom whenever writing to disk. (Like installing apt updates) or any drive intensive activities.

I have not tried breaking the array and installing on a drive as-is. I would like to take advantage of dual 320 stripes. Using the server cd took a lifetime to write the install. I did update the firmware on the controller and let it run for a solid hour and some change just installing the dist-upgrade's.

I am stumped ](*,)

Can someone help me out? :-({|= ..hahaha.

*edit

There are no error messages at boot, havent checked dmesg, (its really late will do later).

Have my array setup like such:
OnBoard u160 is disabled via jumper. An addin Adaptec 2120S u320 is connected to the hotswap bays.
```
[7 Adaptec 2120S]
 ||
[0 36Gb ][3 36Gb ] HW RAID-0 = /dev/sda 72Gb - / 
[1 36Gb ][4 36Gb ] HW RAID-0 = /dev/sdb 72Gb {6.4Gb - swap, ~66Gb - /home)
[2 ---- ][5 ---- ]
```

---

### Post by redroad55 on 2009-02-15
Just a little history .. Is it a case of it was running fine and then not? what are the recent hardware changes , Software changes , firmmware changes ..Post back

---

### Post by KamakazieX on 2009-02-25
Server was pulled from a production environment, evidently nothing was wrong with it. Supposedly it was looping a Win 2003 boot when I got it. I had to scrub the drives before I could keep it.. I picked up an Intel SE7501WV2 board- but it wont fit!.. and a pair of SL79V's.. I got one in the board right now, still running like that.

Motherboard firmware will not update for some reason.
Add-in 2010S Adaptec was flashed with latest firmware.

---

### Post by KamakazieX on 2009-02-25
I mangled the hell out of the intel board I had lying around and got it to fit.

Night and day! \\:D/

I think I installed ubuntu server in record time, but it doesn't support the SL79v stepping.. it'll still boot, but I cant get it to boot the raid array after installation. I'm going to mess with it a little more and see what I can find.

In the meantime, any hardware experts think the original board is an easy fix? ..I'm usually not so optimistic, but I am really trying to hang on to this u320 backplane.

Any help would be greatly appreciated.

---

### Post by thrakkor on 2009-12-17
i installed ubuntu studio hardy on this same MB (super micro) on a good ol' ide 40 gig drive and it boots up in a decent amount of time.  currently running 1 GB memory.  clocked the cpus @ 2.4 GHz

---

