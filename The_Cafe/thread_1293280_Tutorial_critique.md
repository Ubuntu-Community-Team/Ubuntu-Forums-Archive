---
title: "Tutorial critique?"
date: 2009-10-16
forum: The Cafe
---

### Post by nmccrina on 2009-10-16
I wrote this how-to kind of thing about how to make an external hard drive mount read-write. It's at [[COLOR="Blue"]my blog[/COLOR]]("http://nmccrina.wordpress.com/") (Wordpress). The reason I wrote it is because I ran into a little trouble today trying to make it so I don't have to be root to write to my external hard drive. I eventually figured it out, but the information was kind of scattered all over the place, so I gathered it all together in one place. Google turned up a lot of hits regarding the mounting of external hard drives, but most of them were dealing with NTFS drives, and mine is ext4.

I'm looking for some constructive criticism, like whether there's a better way of accomplishing the same thing, or whether I can explain things clearer. Any input is appreciated. Most of all I don't want to be giving people bad advice!

---

### Post by FuturePilot on 2009-10-16
Here's my thoughts on it.

1) I'm of the belief that USB drives should not be put in fstab. Let the volume manager take care of mounting things. This is different depending on what DE you use.

2) The key step is changing the owner (not to be confused with permissions. See "man chown" for info on that). That's all that needs to be done. Once you do that you're home free. My external hard drive is Ext3. All I needed to do was change the owner from root to my user. Now I have write access to it every time it's plugged in since my user owns those files. chmod'ing the whole thing to 777 is a pretty insecure way of doing this since it gives everyone read and write access to your files.

---

### Post by wilee-nilee on 2009-10-16
All my external HD's and thumb rives have always mounted as read and write in Linux with any type of partitioning. So I would say if this is not the case it is because the Linux read of it sees something suspicious. I know some people use external drives as a home for a distribution so my experience doesn't resemble this in that all my externals are just to hold or move data.

---

### Post by nmccrina on 2009-10-16
Yeah, I see the point about the permissions vs. ownership. I will change it!

Could you explain in some more detail why using fstab isn't optimal for external drives? I completely understand sticking with the volume manager (after all, if it works why change anything?), except in cases where you wouldn't want to just use the generic /media/disk mount point. For example, I have both a big external hard drive, and a flash drive. I would want more descriptive names than just "disk". Can the volume manager accommodate this?

Thanks for your input!!!

---

### Post by FuturePilot on 2009-10-16
> **wilee-nilee said:**
> All my external HD's and thumb rives have always mounted as read and write in Linux with any type of partitioning. So I would say if this is not the case it is because the Linux read of it sees something suspicious. 

This isn't the case with any of the Linux file systems. Ext*, XFS, etc. After formating a drive with any of those a normal user can't write to it because it's owned by root.

---

### Post by nmccrina on 2009-10-16
> **wilee-nilee said:**
> All my external HD's and thumb rives have always mounted as read and write in Linux with any type of partitioning. So I would say if this is not the case it is because the Linux read of it sees something suspicious. I know some people use external drives as a home for a distribution so my experience doesn't resemble this in that all my externals are just to hold or move data.

I should have been clearer: they are mounted read/write, but only for root! So if I was going to do an rsync, for example, I would have to use sudo. Which isn't much of an annoyance, but it's still an annoyance. I changed the wording to make this a little clearer.

---

### Post by FuturePilot on 2009-10-16
> **nmccrina said:**
> Yeah, I see the point about the permissions vs. ownership. I will change it!

Could you explain in some more detail why using fstab isn't optimal for external drives? I completely understand sticking with the volume manager (after all, if it works why change anything?), except in cases where you wouldn't want to just use the generic /media/disk mount point. For example, I have both a big external hard drive, and a flash drive. I would want more descriptive names than just "disk". Can the volume manager accommodate this?

Thanks for your input!!!

If you change the label on the disk it will be mounted using the label. For example, I changed the label on my drive to "Stuff". So instead of getting automatically mounted to /media/disk it now gets automatically mounted to /media/Stuff. As to fstab being suboptimal for USB devices, it used to be that if you tried to boot up without the drive connected and it was in fstab it would kind of freak out about that. Whether that's still the case or not I don't know. I guess it really comes down to personal preference. I've always just let Gnome's volume manager take care of mounting my external drive. It's just much less hassle than having to mess around in fstab.

---

### Post by nmccrina on 2009-10-16
> **FuturePilot said:**
> If you change the label on the disk it will be mounted using the label. For example, I changed the label on my drive to "Stuff". So instead of getting automatically mounted to /media/disk it now gets automatically mounted to /media/Stuff. As to fstab being suboptimal for USB devices, it used to be that if you tried to boot up without the drive connected and it was in fstab it would kind of freak out about that. Whether that's still the case or not I don't know. I guess it really comes down to personal preference. I've always just let Gnome's volume manager take care of mounting my external drive. It's just much less hassle than having to mess around in fstab.

Ah I see. Well, I put the 'noauto' option in fstab to keep it from freaking out, but you're right, anything that saves hassle is a good thing! I'll replace the fstab part with how to set the label on a filesystem.

---

### Post by nmccrina on 2009-10-16
Well, I think it's finished. Not editing fstab dropped it to a considerably less impressive 2-step process, but hey, maybe now what took me 30 minutes to figure out this afternoon will take the next person 5 minutes! :)

Thanks for the advice guys!

---

### Post by FuturePilot on 2009-10-16
> **nmccrina said:**
> Well, I think it's finished. Not editing fstab dropped it to a considerably less impressive 2-step process, but hey, maybe now what took me 30 minutes to figure out this afternoon will take the next person 5 minutes! :)

Thanks for the advice guys!

No problem :) It looks good.

---

