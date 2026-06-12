---
title: "Is ext4 stable with Ubuntu 9.10"
date: 2009-10-29
forum: The Cafe
---

### Post by Dark Aspect on 2009-10-29
Hello all

So I was thinking about upgrading to the new Ubuntu that was released today since everyone seems to have positive experiences with karmic. However, I have been thinking; should I use ext3 or ext4 for my filesystem? I have some semi-important data that I would like to keep and I've been under the influence that ext4 is not very stable.

Is ext4 more stable now than its previous release with Ubuntu 9.04? I've always used ext3.

---

### Post by Technoviking on 2009-10-29
I have been using ext4 in Ubuntu 9.04 with no problems. You should be fine.

T-V

---

### Post by FuturePilot on 2009-10-29
[http://www.ubuntu.com/getubuntu/releasenotes/910#Possible%20corruption%20of%20large%20files%20with%20ext4%20filesystem]("http://www.ubuntu.com/getubuntu/releasenotes/910#Possible%20corruption%20of%20large%20files%20with%20ext4%20filesystem")

---

### Post by bibekdai on 2009-10-29
I have been using ext4 since ubuntu 9.04 and I am also using ext4 on 9.10, I have not had a problem, so you can back up your data and probably give it a try.

---

### Post by blueshiftoverwatch on 2009-10-29
From what I've heard the only possible problems ext4 has have to do with an increased potential for data loss during power interruptions while writing data to the hard drive. But even still, how often does that actually happen? It's not going to keep me up at night.

---

### Post by Icehuck on 2009-10-29
I would just use EXT3 and not worry about it. You are already having doubts and file systems need to be reliable. I wouldn't trust the, "it works for me" crowd when it comes to my data.

---

### Post by pythonscript on 2009-10-29
Karmic seems to be a testing ground for many of the features that will be completely integrated into the next LTS (Ubuntu 10.04 Lucid Lynx), and ext4 seems to be among these. If you're *at all *worried, just stick with ext3. I haven't noticed any sizeable difference between the two (of course, I have only been using ext4 for about a week since I installed the RC) but I simply don't want to take the risk with my primary system and it's data.

---

### Post by Dark Aspect on 2009-10-29
> **Icehuck said:**
> I would just use EXT3 and not worry about it. You are already having doubts and file systems need to be reliable. I wouldn't trust the, "it works for me" crowd when it comes to my data.

Well if what blueshiftoverwatch is saying is true than I wouldn't have a problem since I am using UPS to power my PC. However, I have decided that I am too worried about my data so I will use ext3 for now. I would like the extra speed but I think my data is to critical for something that "might" not work.

> **pythonscript said:**
> Karmic seems to be a testing ground for many of the features that will be completely integrated into the next LTS (Ubuntu 10.04 Lucid Lynx), and ext4 seems to be among these. If you're *at all *worried, just stick with ext3. I haven't noticed any sizeable difference between the two (of course, I have only been using ext4 for about a week since I installed the RC) but I simply don't want to take the risk with my primary system and it's data.

So if I am understanding this right - I should be able to use ext4 on the next LTS release without a problem?

---

### Post by kaibob on 2009-10-29
It appears that the OP has made a decision, but I'll throw in my 2 cents anyways.

I did a fresh install of the release candidate and decided to go with ext4. I don't know if it's ext4 or something else but Ubuntu 9.10 is more responsive than jaunty on my machine. The only problem I encountered was that the standard version of Clonezilla would not work. Fortunately, there is a karmic-based version of Clonezilla that works fine.

---

### Post by Crunchy the Headcrab on 2009-10-29
ext4 worked great under the alpha/beta for me.

---

### Post by arashiko28 on 2009-10-29
I've used the ext4 since I upgraded to 9.04, works fine, just do a backup of everything because all of the disk will be deleted.
I've noticed no changes, actually since 9.04 upgrade, it has become faster. :D

---

### Post by Icehuck on 2009-10-29
> **Dark Aspect said:**
> Well if what blueshiftoverwatch is saying is true than I wouldn't have a problem since I am using UPS to power my PC. However, I have decided that I am too worried about my data so I will use ext3 for now. I would like the extra speed but I think my data is to critical for something that "might" not work.

The problems are not just related to power loss. For example there is the bug where it's possible to corrupt data when manipulating files over 500MB.

> So if I am understanding this right - I should be able to use ext4 on the next LTS release without a problem?

It all depends on how many bugs get reported and fixed and that there are no regressions. It's tough to say if EXT4 will work fine then as well.

---

### Post by toupeiro on 2009-10-29
I actually have noticed an IO error since moving my wow installation to an EXT4 formatted drive with some of the larger game files, and it will intermittently lock up on me.  It has not caused any corruption, but I've definitely seen the impact and since moved the game back to a partition with ext3.

---

### Post by NJC on 2009-11-19
Power loss has corrupted my Firefox/Thunderbird profiles - they reside on a vfat partition but the programs are on Ubuntu 9.10 Ubuntu 9.10 ext4. Not sure if this is connected to ext4.

---

