---
title: "Ubuntu 6.06 server crashes randomly"
date: 2008-07-23
forum: Server Platforms
---

### Post by williwau on 2008-07-23
Hi!

I have a pentium3/compaq PC and have permament problems with system crashes/freezes. I tried installing kubuntu 7.04 (worked), freezed regularly after 1 hour (reboot ok, then again freezing). installation of kubuntu 7.10 and 8.04 did not work (stuck at 15% of installation progress).
now I switched to install 6.06 server. installation worked very fine but the system crashed after about 4 hours. but now I was able to see that during crashing the system issued a lot of messages on the console! (gives me hope...)
this is where I need help:
I did not find a lotfile containing messages immediate before crash (syslog looked fine also kern.log). is there a configuration to be made or where do I find the messages.
and after having found the messages, I'm sure I'll be here again to get help in interpreting them.

thanks a lot in advance!

williwau (austria)

---

### Post by cariboo on 2008-07-23
Look at the logs in /var/log, especially daemon, messages, dmesg and syslog.

Jim

---

### Post by williwau on 2008-07-24
Thanks Jim,
all logs looked quite normally. no entries at crashtime. only evms-logs were logging loads of errors.
today I gave totally frustrated up and switched to opensuse - (I know that does not help against hardware defects, but all versions of ubuntu behaved strange on that PC).

williwau

---

### Post by tinny on 2008-07-24
> **williwau said:**
> Thanks Jim,
all logs looked quite normally. no entries at crashtime. only evms-logs were logging loads of errors.
today I gave totally frustrated up and switched to opensuse - (I know that does not help against hardware defects, but all versions of ubuntu behaved strange on that PC).

williwau

When reinstalling Ubuntu you where doing a completely clean install right?

E.g. Format the disk first?

You could insect your hard disk by using "fsck" or "badblocks".

Also, can you see the CPU temperature in your BIOS? (Wait till the computer has been running for a while)

Be interesting to know if openSUSE works better for you... :(

---

### Post by williwau on 2008-07-25
Hi Tinny,

yes, I was doing a complete clean install formatting all concerned partitions. I yesterday installed suse11.0+xfce; worked fine (just one crash during install when trying to change network interface :-( - but resume was splendid!); 
observations: 
- suse's installation suggestion would wipe off everything :-)
- did it manually: my vgs/lvm were recognized and could be mounted perfectly
- german umlauts processed correct in filenames!
- speed quite good.

But: now I'm sure it's a hardwareproblem, has hangup after 3-4 hours of operation (ubuntu was seemingly not the source of problem). next step will be to move all hdds to another box (AMD1200) and see what's happening. if you're interested in results, let me know.

cheers

williwau

---

### Post by /etc/init.d/ on 2008-07-25
You might want to run memtest86+ to check for a RAM problem.  Press Esc when you see the countdown from the GRUB loader, then select the memtest86 option.

Leave it run for at least two hours and see if it reports any errors.

If the system crashes during the test, you definitely have a hardware problem.

---

