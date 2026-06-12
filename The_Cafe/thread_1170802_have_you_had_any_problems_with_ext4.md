---
title: "have you had any problems with ext4?"
date: 2009-05-26
forum: The Cafe
---

### Post by mamamia88 on 2009-05-26
i was just wondering if you've had any problems with ext4 that i should no about before deciding whether or not to stick with ext3 or install ext4

---

### Post by kk0sse54 on 2009-05-26
Nope, although I'm a JFS user these days

---

### Post by mamamia88 on 2009-05-26
cool thanks

---

### Post by ibuclaw on 2009-05-26
I personally haven't had problems, but that said, I would **not** attempt to try out the ext4 filesystem with Ubuntu 9.04 as it is.

If you feel that you have a conservatively stable system that never crashes, there is certainly nothing stopping you.

I on the other hand did the following:
[LIST=1]
[*]Downloaded the 2.6.29-4 kernel
[*]Ensured that the patch which fixes the issues ext4 has with Linux Desktops was in place
[*]Compiled and rebooted, then removed the vanilla Ubuntu kernel.
[/LIST]
I do this because I'm a tinkerer by nature.

But I never put anything before a suitably robust system. Not even the smallest chance of losing data after a crash.

[EDIT]
Also bare in mind that you **cannot safely resize ext4 partitions yet**.

Regards
Iain

---

### Post by mamamia88 on 2009-05-26
well i don't really have anything worth losing and all important data on an external drive.  i'm gonna install mint 7 as soon it's done downloading figured i might as well give it a go

---

### Post by HavocXphere on 2009-05-26
No problems encountered so far.

That being said, there is nothing really mission critical on this box. Or rather everything mission critical is mirrored & on backups.

> Also bare in mind that you cannot safely resize ext4 partitions yet.
Woha...I was about to do that soon. THanks for the warning tinivole.

---

### Post by FuturePilot on 2009-05-26
Yes, I've gotten hit by the data loss bug as well as the lockup bug.

[https://bugs.launchpad.net/bugs/317781]("https://bugs.launchpad.net/bugs/317781")
[https://bugs.launchpad.net/bugs/330824]("https://bugs.launchpad.net/bugs/330824")

---

### Post by mamamia88 on 2009-05-26
i wonder if it's worth the risk.  i'm gonna have to reformat eventually when it becomes default.  might as well do it now i suppose.

---

### Post by khelben1979 on 2009-05-26
I have neither seen or tried the EXT4 filesystem so therefore my answer get's no.

I have a Debian system here which runs 24 hours a day with the EXT3 filesystem and I have never ever have had one serious problem with the filesystem from the day I installed Debian Woody on this machine a few years ago. Continued upgrades have been applied.

---

### Post by Skripka on 2009-05-26
I've been using Ext4 on Arch for several months.  There are known issues with apps as they currently written, which can result in data corruption.

I haven't lost anything...then again I've used known workarounds to minimize the possibility.

Do your homework.  Only you can know if it is worth it.

---

### Post by ibuclaw on 2009-05-26
> **HavocXphere said:**
> No problems encountered so far.

That being said, there is nothing really mission critical on this box. Or rather everything mission critical is mirrored & on backups.


Woha...I was about to do that soon. THanks for the warning tinivole.

Just takes a little homework to find out ;)

[http://ubuntuforums.org/showthread.php?t=1134978](http://ubuntuforums.org/showthread.php?t=1134978)

Regards
Iain

---

### Post by lovinglinux on 2009-05-26
There is thread that explains the possible issues and where users are discussing their experiences and posting their personal views.

[http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)

BTW, It is working fine here on my two drives (4 partitions). I'm not experiencing data loss,  even after several power failures.

---

### Post by Regenweald on 2009-05-26
No problems here either. Ext4 / and /Home. Noatime and data=writeback for a few days now also. With data=writeback, i think xserver memory usage has gone up a few megs though. Will check that out.

---

### Post by don_quixote on 2009-05-26
Ext4 and zero problems here.

---

### Post by kerry_s on 2009-05-26
i've lost 3 ext4 installs, i've gone back to using rieserfs.

---

### Post by Einsamkeit on 2009-05-26
Worked flawlessly for me since I began using it, about a month and a half ago.

---

### Post by psychok7 on 2009-09-08
i havent had a problem with it either..by the way i wanna format my external 1TB HDD to ext4 and im using ubuntu 9.04, i shouldnt have any problems right?

---

### Post by zer010 on 2009-09-08
I've been running ext4 with 9.04 for a couple months with no problems so far.

---

### Post by MikeTheC on 2009-09-08
I've not had any issues -- and it is noticeably faster -- but my Debian server runs on EXT3.

---

### Post by Paqman on 2009-09-08
Been using it since Jaunty Beta with no problems at all.

---

### Post by lovinglinux on 2009-09-08
Interesting that someone resurrected this thread, because I was thinking about doing the same, just to say that I have been using ext4 since the release of Jaunty and it has been very reliable. I even had several power failures, hard lockups and also, shrank, expanded and formatted partitions without any loss of data.

---

### Post by Newuser1111 on 2009-09-08
> have you had any problems with ext4?I didn't have any problems when I did use it.

---

### Post by Vakman on 2009-09-08
I have not had any issues. I always choose ext4 now. I use Linux Mint 7 which is based on 9.04 but still no problems, faster though :)

---

### Post by moeshroom on 2009-11-08
i've been getting filesystem errors on my ext4 / partition ever since i installed jaunty in may.  i have upgraded to 9.10 but it did not fix this.

i never lose data but it's getting old.

any ideas?

---

### Post by chris200x9 on 2009-11-08
> **lovinglinux said:**
> Interesting that someone resurrected this thread, because I was thinking about doing the same, just to say that I have been using ext4 since the release of Jaunty and it has been very reliable. I even had several power failures, hard lockups and also, shrank, expanded and formatted partitions without any loss of data.

I have tonight first time, power failure while an odt was open I just didn't lose saves I lost it all (thankfully I only had 2 sentances)

---

### Post by MasterNetra on 2009-11-08
No problems here.

---

### Post by c2006 on 2009-11-08
No problems here either, and I've been using it since around Jaunty's release.

---

### Post by Yellow Pasque on 2009-11-09
I use ext4 for my Debian/sidux filesystem. I always shut it down cleanly, but I usually get errors in the filesystem the next time I boot it. I can easily fix it with fsck, but it is very annoying.

Other partitions on that disk (ext3) don't have that problem. Hmm.

---

### Post by NoaHall on 2009-11-09
Yes. It was fine for a while, then grub started saying my / didn't exist. I updated grub, pointed it to exactly where / was, but still it said it wasn't there.

---

### Post by Grifulkin on 2009-11-09
I problem with Arch, but that was because my laptop is older and the USB ports don't work as well as they should and something got corrupted in the install, froze had to hard reset and borked the whole filesystem.

---

### Post by katakaio on 2010-06-28
I've had problems with using standby mode on my laptop. I've also had the aforementioned filesystem errors and data loss. I wasn't sure what it was, but it only started happening after a fresh install of 10.04 on ext4. Reinstalling on ext3 fixed all issues.

---

