---
title: "My server is sunk"
date: 2008-07-22
forum: Server Platforms
---

### Post by Dr Small on 2008-07-22
I had to manually run fsck on my server this morning, took almost an hour, because I had to hold in Enter, for yes. Well, now that the system is back up, alot of services are not running.

When I ran vim, I got this:
```
drsmall@mycroft:~$ vim
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
-bash: vim: command not found

```

Things don't look so good. Is there anything that I can try?

Edit, by the way. I have 12,148 files in /lost+found
Is there any way to restore those?

Dr Small

---

### Post by windependence on 2008-07-22
Yikes! what file system were you running?

-Tim

---

### Post by matthew on 2008-07-22
It sounds like a bad hard drive. Hopefully you have a good backup. If so, replace the drive, restore the backup, and you will be good to go. If you don't have a backup...well, that would be a serious bummer.

I've recovered disks after similar occurrences, but it is a ton of work and neither easy nor reliably done. Even then, the best bet is to get stuff off of it quickly before it happens again.

---

### Post by Dr Small on 2008-07-22
> **matthew said:**
> It sounds like a bad hard drive. Hopefully you have a good backup. If so, replace the drive, restore the backup, and you will be good to go. If you don't have a backup...well, that would be a serious bummer.

I've recovered disks after similar occurrences, but it is a ton of work and neither easy nor reliably done. Even then, the best bet is to get stuff off of it quickly before it happens again.
Yeah, I've been talking on IRC and vor-ubuntu and others believe it is a bad hard drive too. The thing is over 7 years old, I know. So, mom bought a new PATA 120GB hard drive to replace it.

I have no backups, but I'll just rebuild it all from Scratch. I'll backup alot of the settings first before I pull the drive though.

Thanks for your thoughts.

@windependence, it's ext3, but as I think we have all agreed now, it's a dying hard drive. The last time it wanted to do a fsck, I had to manually do it. But this time, it just really hit the iceberg, and sunk.

Oh well. Thanks again.

Dr Small

---

### Post by windependence on 2008-07-22
I was thinking maybe you could run Hiren's or something and pull off what you could get, but if the platter or actuator are going it would be dicey at best. You could try putting the drive in the freezer (don't laugh) and then sit a bag of ice on it while you try to boot it, but it looks like the data is already fried. Too bad man, I feel for ya.

-Tim

---

### Post by cariboo on 2008-07-22
I have to agree with windependence, it's amzing how much data you can retrieve after you've frozen the drive, I've down it several times and have managed to save a lot of data using this method.

Jim

---

### Post by Lord DarkPat on 2008-07-22
explain why freezing helps...I'm confused

---

### Post by cariboo on 2008-07-22
If the problem is a mechanical it tightens up the mechanical parts by freezing and they seem to work before it gets to hot. For electronics errors, it is an old technicians trick to freeze a component or componenets to get them to work if there is a heat problem. If you've got a dead hard drive laying about, give it a try you might be surprised at how well it works.

Jim

---

