---
title: "for karmic is a update ok or clean install"
date: 2009-10-28
forum: System76 Support
---

### Post by eddietours on 2009-10-28
which one should be better

---

### Post by AZ_RUNE on 2009-10-28
While many people have done version upgrades with success. I have read all to often where some "x" factor component has caused it to fail. ](*,)  When succesfull they should be posted so others can see if their hardware might make the grade.  I will always back my stuff up and perform a fresh install of the new distro.

YMMV 8)

Later,
[email]arizona.rune@gmail.com[/email]

---

### Post by bribera on 2009-10-28
I've gone both routes, and I'm still up in the air about which one is better.

I have a laptop that's been only upgraded since Edgy. I hit various X configuration problems like AZ_RUNE mentioned, but these seem to get easier and easier with each upgrade. I also have done some pretty risky upgrade paths (i.e. pointing my repos at the beta release and upgrading) instead of simply using the upgrade tool, and this could have caused my problems. However, fixing them has proved invaluable, as I now feel really comfortable editing my xorg.conf. I don't know of any specific snags in the current upgrade path.

Clean installs tend to avoid those snags, but it's also a pain to get your configuration back. Unless you have a repository of configurations and packages, it'll take a while to get the same functionality out of a box that you just wiped.

---

### Post by Dark_Stang on 2009-10-28
I always recommend clean install. Upgrades are usually successful but if it fails you're just going to have even more headaches. Every 6 months or so I do a clean install with the latest Ubuntu release.

---

### Post by bribera on 2009-10-28
Another important consideration is your filesystem type.

New Karmic installations will default to EXT4; if you simply follow the upgrade path, I believe you'll stay with whatever partition scheme you already have.

---

### Post by jdb on 2009-10-28
> **bribera said:**
> Another important consideration is your filesystem type.

New Karmic installations will default to EXT4; if you simply follow the upgrade path, I believe you'll stay with whatever partition scheme you already have.

Anyone know if the ext4 issues have been resolved???

jdb

---

### Post by bribera on 2009-10-28
> **jdb said:**
> Anyone know if the ext4 issues have been resolved?

Anecdotally, I've been running it without problems. I have [disabled barrier writes]("http://phoronix-test-suite.com/pipermail/trondheim-pts_phoronix-test-suite.com/2009-March/000101.html"), which is a little risky in terms of data integrity, but I haven't had any trouble thus far. Then again, I'm running it on a laptop, so my risk of unclean shutdown due to power loss is greatly reduced.

I didn't see issues before disabling barriers either.

---

### Post by arepaking on 2009-10-28
> **jdb said:**
> Anyone know if the ext4 issues have been resolved???

jdb

I have been using EXT4 since 9.04 and I never found an issue with it...

---

### Post by gamerchick02 on 2009-10-28
I did an upgrade from Jaunty.  Things are going just fine for me, and I like it.

I've done reloads and updates... Every few releases I do a clean install.  I'm not sure if it's the best route to go, but it's worked for me.

There are no guarantees, unfortunately.  Do what you think is the best for you right now.

Oh, and I don't use ext4.  I might later on if it proves to be more stable.

Amy

---

### Post by betrunkenaffe on 2009-10-29
I don't install alot of software on the computer. Cairo dock, Compiz (ccsm itself), etc. Of that which I don't get from repos, I keep a copy of the deb in my home folder. I always do a clean install because I find it significantly faster than an upgrade and in my experience, more stable.

For Karmic I set up my / as ext4 and my /home as ext3. I figured the majority of the time savings on boot would be from / accesses rather than /home ones. I didn't want my /home on ext4 out of concern of data loss.

---

### Post by vgrisham on 2009-10-29
@ JDB

I've been using EXT4 for nearly a year now and it's been fine on both my laptop and tower. When I bought my Pangolin last spring (used on eBay), I had a weird disk issue right after installing Jaunty, but I think it had more to do with Linux's still somewhat sketchy hibernate and wake systems. Since that time, it's been smooth sailing. I haven't had the slightest hiccup on my tower.

---

### Post by eddietours on 2009-10-31
just wanted to say l upgrade to Karmic everything is ok am so happy everything work's fine :p

---

### Post by werewolves on 2009-10-31
Did the upgrade from Jaunty to Karmic last night on my Daru2.  Not a single problem that I have seen yet.  I used EXT4 when I installed Jaunty 6 months ago, and it hasn't given me any issues.

The best part is that the Daru2's hibernate and screen dimming issues seem to have been solved my Karmic.

---

