---
title: "Seperate /home partition was a lifesaver!"
date: 2006-10-15
forum: The Cafe
---

### Post by PathSpace on 2006-10-15
This morning, my system would not boot up; it had a kernel panic.  This was probably due to the fact that the power went out at my place last night.  At any rate, I had to reinstall...the system would not even boot up.

Anyways, I had partitioned my system with a separate /home partition the last time I had installed it, just in case of a situation like this one occuring.  What a lifesaver!!  :)  All of my files were there waiting for me, as well as all of my settings.  Even my bookmarks in Firefox were intact.

If anyone ever has to do a fresh install for any reason, or just wants to, I recommend highly to partition with a separate /home partition.  It's such a big help if anything goes wrong.

p.s.-If I were to install another Linux distro on this HD, could they both share my /home partition?  Just wondering.

---

### Post by aysiu on 2006-10-15
I would not share a /home between two distros. The config storage approach may be a bit different.

I think what's most important is that you have a live CD handy. With a live CD, you can always *create* a separate /home if you don't already have one:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by ComplexNumber on 2006-10-15
> I would not share a /home between two distros. The config storage approach may be a bit different.neither would i. it sometimes has some nasty side effects such as deleting all the invisible "." files. i'm not exactly certain if thats what it does, but i remember that i did try it one, and everything went pear shaped, but it was something along those lines. and besides, different distros are set up differently. for example, fedora uses bash_profile to store the user's PATH variable. i think it may be mandriva that uses .bashrc for the same (mandriva also uses the PKG_CONFIG_FILE variable which fedora doesn't seem to). suse doesn't store the user's PATH variable in either (i think).





as for using a separate home partition, i've always advocated that as a good linux habit to get into.

---

### Post by argie on 2006-10-15
Alas, this didn't strike me at the time I installed Ubuntu on this computer. Now I have lots of stuff that I'm just too scared to loose. I did do a  different /home partition for my other computer too (I even formatted it XFS, just to see how that went, for some reason I needed an ext3 /boot partition.)

> **aysiu said:**
> I would not share a /home between two distros. The config storage approach may be a bit different.

I think what's most important is that you have a live CD handy. With a live CD, you can always *create* a separate /home if you don't already have one:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This will sure help. It's just positively wonderful to find out that someone's worked out a solution just when you thought "Aw, I wish I'd done that" :)

I'll do it when Edgy comes out, then even if it fails, the thrill of a new version of the OS will keep me going :D It won't be enough for my dad though, so all his files go into the windows drive before that. (yes, I'm one of those poor souls who must keep his windows partition for his mom whose colleagues insist on embedding videos in powerpoint presentations)

---

