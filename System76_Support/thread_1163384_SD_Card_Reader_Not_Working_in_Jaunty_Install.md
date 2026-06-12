---
title: "SD Card Reader Not Working in Jaunty Install"
date: 2009-05-18
forum: System76 Support
---

### Post by jpoRS on 2009-05-18
Hola,

I fresh installed Jaunty to fix a number of problems I was having previously, and the good news is that for the most part it went seamlessly.  The bad news is now my SD card reader won't work.  I dl'ed the S76 driver and all, but still no luck.

Thanks for the help, it is hard to sell a futon on Craigslist without pictures.
jim

---

### Post by thomasaaron on 2009-05-18
1. Which computer do you have?

2. Does the card reader work from your live CD?

3. Is it a card that worked in that machine prior to upgrading?

---

### Post by gpstar on 2009-05-18
I noticed on my bonobo, SDHC cards are not getting detected, but regular SD cards do (ie: 2gb and lower work fine), has something to do with a bug in the 2.6.28-11-generic kernel, supposely it's fixed in the 2.6.29 kernel.

[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/359323](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/359323)

---

### Post by jpoRS on 2009-05-18
Ooops.  Sorry Thomas.

1. panp41

2. (Will post after I can check)

3. Yes, it worked fine.

More information I probably should have given you:  By "not working" I meant that it isn't auto-mounting.  It did previously (Hardy-Intrepid) but now nothing happens, not even a CPU spike like I see when I connect something via USB.  I tried googling for troubleshooting but between having a busy day and not knowing what to look for, I came up with no results.  But I wouldn't be surprised at all to learn I just need to reconfigure the reader for automount or something like that.

Thanks,
jim

---

### Post by thomasaaron on 2009-05-19
Just tested on our shop machine, and it mounted fine.
Let me know what happens from a live CD.

Also, post the output of...

tail -f /var/log/syslog

...when you plug in the card, and I'll compare it to my shop machine.

---

### Post by jpoRS on 2009-05-19
tail:
```
May 19 11:17:01 Alfred /USR/SBIN/CRON[21506]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 19 11:20:01 Alfred /USR/SBIN/CRON[21523]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 19 11:30:01 Alfred /USR/SBIN/CRON[21668]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 19 11:40:01 Alfred /USR/SBIN/CRON[21818]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 19 11:50:01 Alfred /USR/SBIN/CRON[21964]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 19 11:57:46 Alfred NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake 
May 19 11:57:46 Alfred NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
May 19 12:00:01 Alfred /USR/SBIN/CRON[22124]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
May 19 12:00:01 Alfred /USR/SBIN/CRON[22123]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 19 12:07:59 Alfred kernel: [140714.701489] mmc0: error -84 whilst initialising SD card
```

I am going to take a blind leap here and guess that the "error -84 whilst initializing SD card" is the problem?

jim

---

### Post by jpoRS on 2009-05-19
Hello from 9.04 via live CD!

Not working here either though.  Frown town.

jim

---

### Post by thomasaaron on 2009-05-19
Can you check with a different card?

It could be that there is a regression with the filesystem used on that card. What do you use the card for? Is it from a camera? A Palm device?

---

### Post by jpoRS on 2009-05-19
It is from my cell phone (LG VX 9700).  Don't know if that helps.  I also can't find my other SD card so that is a no-go.

jim

---

### Post by thomasaaron on 2009-05-19
This is just a shot in the dark, but go to System > Admin > Users and Groups. Click on your username > Properties > Priveleges. Make sure ALL of the available checkboxes are selected.

If they're not, select them, log out, and log back in.

---

### Post by jpoRS on 2009-05-19
I wasn't but it was all the minor things (tape drives, connect w/modem).  Tried it anyway but no dice.

jim

---

### Post by jpoRS on 2009-05-19
I didn't think this would be relevant because it worked before, but maybe I missed a que somewhere and this is significant information:

It isn't "just" an SD card.  It is a mini SDHC in an adapter to be read by a standard SD reader.  Like I said it worked before, I even checked with you Thomas that it would work before I bought the thing.

Thanks,
jim

---

### Post by thomasaaron on 2009-05-19
I'm not finding a match for what error 84 might be. However, it is either hardware or a kernel regression.

If you're *sure* it worked *right* before upgrading it's a kernel regression. 

Have a look at this...
[http://www.google.com/search?q=jaunty+sdhc+cards+no+longer+work&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=jaunty+sdhc+cards+no+longer+work&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Just out of curiosity, did you use ext4 formatting or ext3 (when you re-imaged).

---

### Post by jpoRS on 2009-05-19
I hadn't messed with anything for probably a month, and the card read before that, so I am pretty sure that it worked, but I am not "I tried it the day before I installed Jaunty" *sure*.

So if it is kernel regression . . . now what?  Recompile?

jim

[edit]oops.  ext3.  I didn't know enough about ext 4 to try it.[/edit]

---

### Post by thomasaaron on 2009-05-19
It looks like there are some bug reports already out on it. I'll research them and see if a pertinent one is already filed. If not, we can file one. Other wise, it probably will be fixed soon in an update.

---

### Post by agrteknolan on 2009-05-19
I had this same issue.

The kernel shipped with Jaunty for some reason or another stopped support 25hz SD cards. Upgrading to .29 fixes this.

There we go:
[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

---

### Post by jii on 2009-05-22
Allow me to propose a more elegant solution.

How much you want for that futon?

---

### Post by tallthom on 2009-06-05
I'm also having SD card reader issues on the following notebook.

HP Pavilion zt3000 CTO.  

The card mounts sometimes and sometimes it does not mount.  During the times when it mounts, if I try to access the files (i.e. copy them to the desktop or just view them), the system is really slow and then eventually unmounts the card.  The hardware access light flickers and such.

SD card is 1.0 GB (just in case that helps).

> Jun  5 22:59:21 Frodo kernel: [479394.655762] mmc0: problem reading switch capabilities, performance might suffer.
Jun  5 22:59:21 Frodo kernel: [479394.657857] mmc0: new SD card at address e624
Jun  5 22:59:21 Frodo kernel: [479394.681328] mmcblk0: mmc0:e624 SD01G 968 MiB 
Jun  5 22:59:21 Frodo kernel: [479394.681457]  mmcblk0: p1
Jun  5 22:59:36 Frodo kernel: [479409.699442] mmc0: card e624 removed
Jun  5 22:59:42 Frodo kernel: [479414.959612] mmc0: problem reading switch capabilities, performance might suffer.
Jun  5 22:59:42 Frodo kernel: [479414.961709] mmc0: new SD card at address e624
Jun  5 22:59:42 Frodo kernel: [479414.968620] mmcblk0: mmc0:e624 SD01G 968 MiB 
Jun  5 22:59:42 Frodo kernel: [479414.968788]  mmcblk0: p1
Jun  5 22:59:43 Frodo hald: mounted /dev/mmcblk0p1 on behalf of uid 1003
Jun  5 23:00:26 Frodo kernel: [479459.144383] mmc0: Card removed during transfer!
Jun  5 23:00:26 Frodo kernel: [479459.144390] mmc0: Resetting chip
Jun  5 23:00:26 Frodo kernel: [479459.144801] mmcblk0: error -123 sending read/write command
Jun  5 23:00:26 Frodo kernel: [479459.144805] end_request: I/O error, dev mmcblk0, sector 49728
Jun  5 23:00:26 Frodo kernel: [479459.144808] end_request: I/O error, dev mmcblk0, sector 49736
Jun  5 23:00:26 Frodo kernel: [479459.144811] end_request: I/O error, dev mmcblk0, sector 49744
Jun  5 23:00:26 Frodo kernel: [479459.144814] end_request: I/O error, dev mmcblk0, sector 49752
Jun  5 23:00:26 Frodo kernel: [479459.144817] end_request: I/O error, dev mmcblk0, sector 49760
Jun  5 23:00:26 Frodo kernel: [479459.144819] end_request: I/O error, dev mmcblk0, sector 49768
Jun  5 23:00:26 Frodo kernel: [479459.144822] end_request: I/O error, dev mmcblk0, sector 49776
Jun  5 23:00:26 Frodo kernel: [479459.144825] end_request: I/O error, dev mmcblk0, sector 49784
Jun  5 23:00:26 Frodo kernel: [479459.144827] end_request: I/O error, dev mmcblk0, sector 49792
Jun  5 23:00:26 Frodo kernel: [479459.144830] end_request: I/O error, dev mmcblk0, sector 49800
Jun  5 23:00:26 Frodo kernel: [479459.144832] end_request: I/O error, dev mmcblk0, sector 49808
Jun  5 23:00:26 Frodo kernel: [479459.144835] end_request: I/O error, dev mmcblk0, sector 49816
Jun  5 23:00:26 Frodo kernel: [479459.144838] end_request: I/O error, dev mmcblk0, sector 49824
Jun  5 23:00:26 Frodo kernel: [479459.144840] end_request: I/O error, dev mmcblk0, sector 49832
Jun  5 23:00:26 Frodo kernel: [479459.144843] end_request: I/O error, dev mmcblk0, sector 49840
Jun  5 23:00:26 Frodo kernel: [479459.144845] end_request: I/O error, dev mmcblk0, sector 49848
Jun  5 23:00:26 Frodo kernel: [479459.144882] mmcblk0: error -123 sending read/write command
Jun  5 23:00:26 Frodo kernel: [479459.144885] end_request: I/O error, dev mmcblk0, sector 49856
Jun  5 23:00:26 Frodo kernel: [479459.144888] end_request: I/O error, dev mmcblk0, sector 49864
Jun  5 23:00:26 Frodo kernel: [479459.144891] end_request: I/O error, dev mmcblk0, sector 49872
Jun  5 23:00:26 Frodo kernel: [479459.144894] end_request: I/O error, dev mmcblk0, sector 49880
Jun  5 23:00:26 Frodo kernel: [479459.144896] end_request: I/O error, dev mmcblk0, sector 49888
Jun  5 23:00:26 Frodo kernel: [479459.144899] end_request: I/O error, dev mmcblk0, sector 49896
Jun  5 23:00:26 Frodo kernel: [479459.144902] end_request: I/O error, dev mmcblk0, sector 49904
Jun  5 23:00:26 Frodo kernel: [479459.144904] end_request: I/O error, dev mmcblk0, sector 49912
Jun  5 23:00:26 Frodo kernel: [479459.144907] end_request: I/O error, dev mmcblk0, sector 49920
Jun  5 23:00:26 Frodo kernel: [479459.144910] end_request: I/O error, dev mmcblk0, sector 49928
Jun  5 23:00:26 Frodo kernel: [479459.144912] end_request: I/O error, dev mmcblk0, sector 49936
Jun  5 23:00:26 Frodo kernel: [479459.144915] end_request: I/O error, dev mmcblk0, sector 49944
Jun  5 23:00:26 Frodo kernel: [479459.144918] end_request: I/O error, dev mmcblk0, sector 49952
Jun  5 23:00:26 Frodo kernel: [479459.144920] end_request: I/O error, dev mmcblk0, sector 49960
Jun  5 23:00:26 Frodo kernel: [479459.144923] end_request: I/O error, dev mmcblk0, sector 49968
Jun  5 23:00:26 Frodo kernel: [479459.144925] end_request: I/O error, dev mmcblk0, sector 49976
Jun  5 23:00:26 Frodo kernel: [479459.144946] mmcblk0: error -123 sending read/write command
Jun  5 23:00:26 Frodo kernel: [479459.144948] end_request: I/O error, dev mmcblk0, sector 49984
Jun  5 23:00:26 Frodo kernel: [479459.144951] end_request: I/O error, dev mmcblk0, sector 49992
Jun  5 23:00:26 Frodo kernel: [479459.144954] end_request: I/O error, dev mmcblk0, sector 50000
Jun  5 23:00:26 Frodo kernel: [479459.144957] end_request: I/O error, dev mmcblk0, sector 50008
Jun  5 23:00:26 Frodo kernel: [479459.144959] end_request: I/O error, dev mmcblk0, sector 50016
Jun  5 23:00:26 Frodo kernel: [479459.144962] end_request: I/O error, dev mmcblk0, sector 50024
Jun  5 23:00:26 Frodo kernel: [479459.144965] end_request: I/O error, dev mmcblk0, sector 50032
Jun  5 23:00:26 Frodo kernel: [479459.144967] end_request: I/O error, dev mmcblk0, sector 50040
Jun  5 23:00:26 Frodo kernel: [479459.144970] end_request: I/O error, dev mmcblk0, sector 50048
Jun  5 23:00:26 Frodo kernel: [479459.144972] end_request: I/O error, dev mmcblk0, sector 50056
Jun  5 23:00:26 Frodo kernel: [479459.144975] end_request: I/O error, dev mmcblk0, sector 50064
Jun  5 23:00:26 Frodo kernel: [479459.144978] end_request: I/O error, dev mmcblk0, sector 50072
Jun  5 23:00:26 Frodo kernel: [479459.144980] end_request: I/O error, dev mmcblk0, sector 50080
Jun  5 23:00:26 Frodo kernel: [479459.144983] end_request: I/O error, dev mmcblk0, sector 50088
Jun  5 23:00:26 Frodo kernel: [479459.144985] end_request: I/O error, dev mmcblk0, sector 50096
Jun  5 23:00:26 Frodo kernel: [479459.144988] end_request: I/O error, dev mmcblk0, sector 50104
Jun  5 23:00:26 Frodo kernel: [479459.145006] mmcblk0: error -123 sending read/write command
Jun  5 23:00:26 Frodo kernel: [479459.145008] end_request: I/O error, dev mmcblk0, sector 50112
Jun  5 23:00:26 Frodo kernel: [479459.145011] end_request: I/O error, dev mmcblk0, sector 50120
Jun  5 23:00:26 Frodo kernel: [479459.145014] end_request: I/O error, dev mmcblk0, sector 50128
Jun  5 23:00:26 Frodo kernel: [479459.145017] end_request: I/O error, dev mmcblk0, sector 50136
Jun  5 23:00:26 Frodo kernel: [479459.145019] end_request: I/O error, dev mmcblk0, sector 50144
Jun  5 23:00:26 Frodo kernel: [479459.145022] end_request: I/O error, dev mmcblk0, sector 50152
Jun  5 23:00:26 Frodo kernel: [479459.145025] end_request: I/O error, dev mmcblk0, sector 50160
Jun  5 23:00:26 Frodo kernel: [479459.145028] end_request: I/O error, dev mmcblk0, sector 50168
Jun  5 23:00:26 Frodo kernel: [479459.145030] end_request: I/O error, dev mmcblk0, sector 50176
Jun  5 23:00:26 Frodo kernel: [479459.145033] end_request: I/O error, dev mmcblk0, sector 50184
Jun  5 23:00:26 Frodo kernel: [479459.145036] end_request: I/O error, dev mmcblk0, sector 50192
Jun  5 23:00:26 Frodo kernel: [479459.145038] end_request: I/O error, dev mmcblk0, sector 50200
Jun  5 23:00:26 Frodo kernel: [479459.145041] end_request: I/O error, dev mmcblk0, sector 50208
Jun  5 23:00:26 Frodo kernel: [479459.145043] end_request: I/O error, dev mmcblk0, sector 50216
Jun  5 23:00:26 Frodo kernel: [479459.145046] end_request: I/O error, dev mmcblk0, sector 50224
Jun  5 23:00:26 Frodo kernel: [479459.145048] end_request: I/O error, dev mmcblk0, sector 50232
Jun  5 23:00:26 Frodo kernel: [479459.145065] mmcblk0: error -123 sending read/write command
Jun  5 23:00:26 Frodo kernel: [479459.145068] end_request: I/O error, dev mmcblk0, sector 49728
Jun  5 23:00:26 Frodo kernel: [479459.145349] mmc0: card e624 removed
Jun  5 23:00:26 Frodo kernel: [479459.145475] mmcblk0: error -123 sending read/write command
Jun  5 23:00:26 Frodo kernel: [479459.145507] mmcblk0: error -123 requesting status
Jun  5 23:00:26 Frodo kernel: [479459.145515] end_request: I/O error, dev mmcblk0, sector 800
Jun  5 23:00:26 Frodo kernel: [479459.145521] __ratelimit: 1 callbacks suppressed
Jun  5 23:00:26 Frodo kernel: [479459.145524] Buffer I/O error on device mmcblk0p1, logical block 551
Jun  5 23:00:26 Frodo kernel: [479459.145527] lost page write due to I/O error on mmcblk0p1
Jun  5 23:00:26 Frodo hald[2532]: forcibly attempting to lazy unmount /dev/mmcblk0p1 as enclosing drive was disconnected
Jun  5 23:00:26 Frodo hald: unmounted /dev/mmcblk0p1 from '/media/disk' on behalf of uid 0



In the above case, the disk showed up, then I tried copying to the desktop, then it crashed.

Let me know how else I can troubleshoot it.

Thanks in advance.

---

### Post by thomasaaron on 2009-06-05
tallthom, we only support System76 computers.

However, it sure looks like you have a bad SD card. That's a lot of sector-related errors. Have you tried a few different SD cards? If so, your card reader is probably hosed.

---

### Post by jpoRS on 2009-06-05
> **jii said:**
> Allow me to propose a more elegant solution.

How much you want for that futon?

Haha!  I am sorry jii but I actually sold it without pictures.

---

### Post by tallthom on 2009-06-06
Sorry, Thomas.  I completely missed the top of the forum.  I guess I can go back to "rookie ubuntu forum user." (as if I ever left that role!)

But I did look at your company homepage...  nice!

---

