---
title: "Is ext4 ready for everyday use?"
date: 2009-09-20
forum: The Cafe
---

### Post by chessnerd on 2009-09-20
It was officially released last year, but I'd heard that ext4 was still having a few problems and that ext3 was recommended for most machines because of its stability. The thing is, ext4 seems like a really big improvement over ext3 and I would like to start using it, but I don't want to compromise the stability of either of my computers for the sake of new features. So, I'd like to know your opinions about the ext4 file system:

Do you think that ext4 is stable enough now that I could implement it when I upgrade to Karmic later this year, or should I keep waiting for it to improve?

---

### Post by scragar on 2009-09-20
I've been using ext4 for quite a while since I switched to arch linux, I've not had any crashes or stability problems.

---

### Post by pwnst*r on 2009-09-20
i use it everyday.  so, yes.

---

### Post by HappyFeet on 2009-09-20
I've been using it since March with no problems.

---

### Post by RiceMonster on 2009-09-20
I use it on both my computers. No problems here.

---

### Post by dragos240 on 2009-09-20
Same, my archbox is ext4. No issues.

---

### Post by kevin11951 on 2009-09-20
ext4 is now the standard on karmic, so ready or not you will be using it (unless you manually change it, of course)

---

### Post by CharmyBee on 2009-09-20
EXT4 hasn't seen a year of thorough proven stable use so I wouldn't bet my life on it.

---

### Post by MasterNetra on 2009-09-20
Aye, the issues are supposedly may occur if the computer improperly get turned off (power outage, force off, etc) and something about possible corruption with large files or something another from it being forced off, anywho, yea it's good for everyday use.

---

### Post by Exodist on 2009-09-20
I will prob stay with Ext3 for another year. Just to be safe.
I also havent read up on any of the new features for Ext4 yet to see how it cometes with Ext3 and ReiserFS.

---

### Post by dragos240 on 2009-09-20
I used to use ext2 for a while, it worked, but when there was a manual power off, it took a while to boot. Journaling filesystems are the way to go.

---

### Post by Skripka on 2009-09-20
> **chessnerd said:**
> It was officially released last year, but I'd heard that ext4 was still having a few problems and that ext3 was recommended for most machines because of its stability. The thing is, ext4 seems like a really big improvement over ext3 and I would like to start using it, but I don't want to compromise the stability of either of my computers for the sake of new features. So, I'd like to know your opinions about the ext4 file system:

Do you think that ext4 is stable enough now that I could implement it when I upgrade to Karmic later this year, or should I keep waiting for it to improve?

The problem is NOT Ext4.


The problem is the app/DE devs who sit on their tails and don't rewrite their apps to take into account delayed allocation.  Ext4 is fine, and works like it should.  It is apps that are the problem.

---

### Post by lovinglinux on 2009-09-20
I have been using ext4 on all partitions since Jaunty release without any issues. Power supply here is not very reliable and the energy has been cut off several times in this period, but I haven't lost anything. Works great IMO.

---

### Post by RiceMonster on 2009-09-20
> **Skripka said:**
> The problem is NOT Ext4.


The problem is the app/DE devs who sit on their tails and don't rewrite their apps to take into account delayed allocation.  Ext4 is fine, and works like it should.  It is apps that are the problem.

didn't kernel 2.6.30 have a patch for that though?

---

### Post by Skripka on 2009-09-20
> **RiceMonster said:**
> didn't kernel 2.6.30 have a patch for that though?

I think it did, but that patch lowered Ext4 performance IIRC, in exchange for lessening hard-reboot issues with software that hadn't or haven't yet taken delayed allocation into account...even then I was under the impression it was a stop-gap measure until idle devs fixed their code.

---

### Post by pwnst*r on 2009-09-20
> **CharmyBee said:**
> EXT4 hasn't seen a year of thorough proven stable use so I wouldn't bet my life on it.

if you're betting your life on your HDD, i suggest backing up.

---

### Post by jrusso2 on 2009-09-20
If I had anything mission critical or important I would not use it.

Search the forum and the Fedora one for examples of lost data with ext4.

---

### Post by northwestuntu on 2009-09-21
ive had data loss with ext4.

---

### Post by samjh on 2009-09-21
Yes, it's ready.  But I use ext3 for really important stuff, like my /boot directory (along with backing up, obviously).

---

### Post by stwschool on 2009-09-21
Seems fine to me. Been using it since 9.04 came out without headaches. Always back up your data, and you'll be fine, especially as linux is generally very quick to setup again from scratch if you need to.

---

### Post by hoppipolla on 2009-09-21
I'm still on Ext3, but that's mainly through my own mistake - I should have changed it to 4.

It doesn't seem perfect but yeah, depends what you're using it for :)


... So, how often are upgrades released? Does it like, patch and update itself? I'm not sure how filesystems work in this respect :)

---

### Post by Slug71 on 2009-09-21
Been using Ext4 since it entered Jaunty development and had absolutely no issues so far. Used on all partitions too.

So yes it is ready. Will be default in Karmic.

---

### Post by Simian Man on 2009-09-21
> **samjh said:**
> Yes, it's ready.  But I use ext3 for really important stuff, like my /boot directory (along with backing up, obviously).

/boot is the last example I'd pick of "really important stuff".

I have been using ext4 for ~8 months and have had no problems at all.

---

### Post by samjh on 2009-09-21
> **Simian Man said:**
> /boot is the last example I'd pick of "really important stuff".
Bad wording my part.  Important among things I DON'T back up (I only back up my /~ directory).  Should've really said the primary partition which contains / and/or /boot.

---

### Post by hellion0 on 2009-09-21
I've been using ext4 on my laptop since about July, and no problem so far.

If it's stable enough, I'll move up to it on my desktop when the next LTS comes out.

---

### Post by JeevesBond on 2009-10-29
I've had data loss with EXT4, following two power outages in short succession.

Luckily I had backups, so didn't lose much work. If you're going to use EXT4 make sure you have backups.

In fact, just make sure you have backups, full stop.

---

### Post by Icehuck on 2009-10-29
Until this aspect gets resolved, I won't even consider using it as a file system. I will not beta test a file system that is pushed as the default for a release.

> Possible corruption of large files with ext4 filesystem

There have been some reports of data corruption with fresh (not upgraded) ext4 file systems using the Ubuntu 9.10 kernel when writing to large files (over 512MB). The issue is under investigation, and if confirmed will be resolved in a post-release update. Users who routinely manipulate large files may want to consider using ext3 file systems until this issue is resolved. (453579)

From [http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

I won't even mention all the other problems EXT4 has.

---

### Post by gjoellee on 2009-10-29
I have used Ext 4 since the 2.6.27 kernel. Never had any problems with it.

---

### Post by MellonCollie on 2009-10-29
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

> [SIZE="5"]Possible corruption of large files with ext4 filesystem[/SIZE]

There have been some reports of data corruption with fresh (not upgraded) ext4 file systems using the Ubuntu 9.10 kernel when writing to large files (over 512MB). The issue is under investigation, and if confirmed will be resolved in a post-release update. Users who routinely manipulate large files may want to consider using ext3 file systems until this issue is resolved. [(453579)](https://bugs.launchpad.net/bugs/453579)

---

### Post by lovinglinux on 2009-10-29
> **JeevesBond said:**
> I've had data loss with EXT4, following two power outages in short succession.

Luckily I had backups, so didn't lose much work. If you're going to use EXT4 make sure you have backups.

In fact, just make sure you have backups, full stop.

I have a lot of power outages here and I never have lost anything. Anyway, backups are indeed strongly advised.

---

### Post by RiceMonster on 2009-10-29
Still no problems here.

---

### Post by Sporkman on 2009-10-29
> **Exodist said:**
> I also havent read up on any of the new features for Ext4 yet to see how it cometes with Ext3 and ReiserFS.

Wikipedia gives a good description of the new features:

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

