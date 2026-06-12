---
title: "Working on my triple boot"
date: 2009-06-12
forum: The Cafe
---

### Post by Vostrocity on 2009-06-12
For the past 3 months I'd been running Ubuntu on a tiny 10GB partition of my 120GB HDD. It was actually an emergency since Vista, which took around 100GB, suddenly got corrupted (can't log in). At first, I was planning on fixing the problem because I had a ton of programs and customizations, but then I got the hang of Ubuntu and decided to ditch Vista. :D So yesterday I copied over all of my files to an external HDD, took a screenshot of my Program Files folder (so I remember which programs I'll need when I install Windows 7), put in my gParted Live CD, and erased the whole partition. In fact I erased every partition (I had a ton of little useless ones and blocks of free space) and consolidated it into one 50GB NTFS for my personal files and three 20GB partitions for my planned triple boot. I totally forgot to look up which file system OS X uses, so I just guessed JFS, which was wrong since it really uses HFS+. :( I'll be fixing that later. The first thing I'm going to do, as soon as I figure out the GRUB issue, is install Windows 7. OSx86 will take a bit of time, so I'll do that later when I have time. But it definitely is possible as I've seen a couple people over on their forums with the same computer as me.

Sorry for that long story, a couple questions now.
-Why does gParted running in Ubuntu show the mounted partitions as locked and the unmounted ones with a warning symbol? I need to change a label and can't (unless I use the Live CD).
-Yes the GRUB issue. Is there some simple way that I can just burn a CD with a GRUB installer on it and be done?
-Any suggestions on anything?

[IMG]http://i43.tinypic.com/2eluxds.png[/IMG]

---

### Post by linuxguymarshall on 2009-06-13
They are locked because you can't modify a mounted partition. And I may be wrong here but the other ones ave '!' marks because they are not supported partition types or something along those lines.

As for the GRUB issue, there are installers but personally I would recommend just editing the GRUB from Ubuntu manually as it is soo much easier. 

An my suggestion is **BACKUP YOUR GRUB, BACKUP IMPORTANT FILES**

That is the best advice I can give from last year when I set up a quad-boot of Windows XP, Ubuntu, OSX-x86, and Solaris

---

### Post by Vostrocity on 2009-06-13
-Oh yea, I figured out that gParted in Ubuntu supports way less file systems than gParted on a Live CD.
-How do I backup GRUB or "edit the GRUB from Ubuntu manually"?

---

### Post by Vostrocity on 2009-06-13
And also how do I get rid of the Home and Desktop links in the Places menu without deleting the actual thing? I deleted the four other folder links and replaced them with bookmarks of the four folders on my Files partition, but I don't want to actually delete my Home folder and Desktop.

---

