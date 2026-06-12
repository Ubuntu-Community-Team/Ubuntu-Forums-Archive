---
title: "mdadm music corruption?"
date: 2010-12-19
forum: Server Platforms
---

### Post by mons00n on 2010-12-19
Hi everyone. I've been building my digital music collection for some time and used to house it on a local drive with no quality issues. A while back I built myself a file server using ubuntu and mdadm in a raid1 configuration to protect against potential drive failure. 

I link my iTunes library to the music files via a samba share and everything works great on the surface. I've started to notice that random songs are becoming corrupted with pops clicks and silent pauses. I'll even re-download an album and notice that it's corrupted a few weeks later. Now I'm at a loss to what is causing this issue; I ignored it at first but it seems to be getting worse and more widespread as time goes on. 

Do you think this could be caused by mdadm?  It reports that all is fine via 'cat /process/mdstat' but I wouldn't know where to look or what to look for if there were syncing issues. The other possibility is that I have iTunes set to keep my music folder organized for me, but I've never heard of it actually corrupting the files it shuffles around. 

The bottom line is that my library is getting crappier as time goes on and I cannot stand for that!  So any ideas on possible solutions would be greatly appreciated. Thank you all for your time.

---

### Post by windependence on 2010-12-19
I don't think mdadmin is corrupting your files. Are the two drives exactly the same or different manufacturers?
 
-Tim

---

### Post by mons00n on 2010-12-19
> **windependence said:**
> I don't think mdadmin is corrupting your files. Are the two drives exactly the same or different manufacturers?
 
-Tim

The drives are exactly the same model & size.  1TB WD Caviar Blacks if I remember correctly.  I haven't found that any other files are corrupted, so the more I think about it the more I want to blame iTunes.  But then again I never had any corruption when iTunes managed my music locally...which leaves me scratching my head.

---

### Post by windependence on 2010-12-19
Have you noticed if the file size changes at all? 
 
-Tim

---

### Post by mons00n on 2010-12-19
> **windependence said:**
> Have you noticed if the file size changes at all? 
 
-Tim

It's really random which songs end up corrupting so I haven't taken notice.  I'll try and look at some of my current corrupted music and do some comparisons to fresh downloads when I get off work.  What are your thoughts on if the file size has or has not changed?

---

### Post by windependence on 2010-12-19
Interesting....you don't seem to be the only one having this problem.
 
[http://serverfault.com/questions/89069/file-corruption-on-mdadm-raid1-array-no-filesytem-corruption-however](http://serverfault.com/questions/89069/file-corruption-on-mdadm-raid1-array-no-filesytem-corruption-however)
 
I'll get heat for this but I am a big fan of hardware RAID. Real hardware RAID 1 cards are pretty cheap now. I didn't think software RAID was corrupting your files but now I'm not so sure.....
 
Doing more research.....
 
 
-Tim

---

### Post by mons00n on 2010-12-21
does anyone else have any suggestions or ideas?

I don't have multiple versions of the corrupted songs so I cannot do the file size comparison =/

---

### Post by doogy2004 on 2010-12-21
Try downloading the songs then get an MD5 hash on all of them.  Then when you start to experience problems with the files, run an MD5 on them again and compare the second MD5 to the original.  If the MD5s are the same the problem is not with the software raid or your hard disks.

---

