---
title: "LVM mounts n labels mixed up"
date: 2012-08-21
forum: Server Platforms
---

### Post by padred123 on 2012-08-21
I have recently setup an Ubuntu LAMP Server with the Logical Volume Manager file system. I followed [these excellent instructions]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=191") but my mounts appear to be wrong. The setup was pretty straight forward.. What could have caused this?

heres my df -h
```
root@padreserv:/dev/mapper# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/lvg-bak   1.9G  317M  1.5G  18% /
udev                  989M  4.0K  989M   1% /dev
tmpfs                 399M  476K  399M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  997M     0  997M   0% /run/shm
/dev/mapper/lvg-root  3.8G  120M  3.5G   4% /tmp
/dev/mapper/lvg-swap  1.9G  340M  1.5G  19% /var
/dev/mapper/lvg-tmp   1.9G   60M  1.8G   4% /srv
/dev/mapper/lvg-usr   9.9G  120M  9.3G   2% /opt
/dev/mapper/lvg-var   3.8G  120M  3.5G   4% /bak
/dev/mapper/lvg-srv   949M  609M  293M  68% /usr
/dev/mapper/lvg-opt   949M   30M  873M   4% /home
root@padreserv:/dev/mapper#

```

---

### Post by darkod on 2012-08-21
It seems you selected wrong mount points for the LVs during installation.
Only the name of the LV doesn't mean anything to the system, the mount point is what matters. Naming one LV 'root' will not make it the root partition, setting up the mount point as / will make it the root partition. You have to select the correct LV and the correct mount point for it.

---

### Post by padred123 on 2012-08-21
> **darkod said:**
> It seems you selected wrong mount points for the LVs during installation.
Only the name of the LV doesn't mean anything to the system, the mount point is what matters. Naming one LV 'root' will not make it the root partition, setting up the mount point as / will make it the root partition. You have to select the correct LV and the correct mount point for it.

Ya i suppose so.. Maybe I should get some rest b4 I reinstall. :P


Sorry for mucking up the forums with dumb questions. I will try again tomorrow n report back just for the heck of it.


Thanks again!

---

### Post by padred123 on 2012-08-21
> **padred123 said:**
> Ya i suppose so.. Maybe I should get some rest b4 I reinstall. :P


Sorry for mucking up the forums with dumb questions. I will try again tomorrow n report back just for the heck of it.


Thanks again!
[FONT='.Helvetica NeueUI'][SIZE=3]
[/SIZE][/FONT] [FONT='.Helvetica NeueUI'][SIZE=3]Or should I just rename everything? Would that currupt the file structure? [/SIZE][/FONT]
[FONT='.Helvetica NeueUI'][SIZE=3]
[/SIZE][/FONT]
[FONT='.Helvetica NeueUI'][SIZE=3]Again sorry I'm somewhat new to linux...[/SIZE][/FONT]
[FONT='.Helvetica NeueUI'][SIZE=3]
[/SIZE][/FONT]

---

### Post by darkod on 2012-08-21
Not sure if you can rename the LVs but the name is not so important. Yes, it's good to have descriptive names telling you what is where, but the LV sizes are more important here.

For example, you create 100GB lvg-root and 300MB lvg-boot. The lvg-boot is much smaller because you plan it as only a /boot partition.

During the install you mix up the mount points and you end up with 300MB for / and 100GB for /boot. It's a drastic example but you get the point.

With this mix up I am not sure if the sizes are what you planned for particular mount points or not. Since this is LVM you can play around and resize LVs, but honestly I think it's much better practice to do a new install. That way you will also practice installing.

This is a brand new empty installation so you have nothing to lose by doing a new one over it. :)

---

### Post by padred123 on 2012-08-21
> **darkod said:**
> Not sure if you can rename the LVs but the name is not so important. Yes, it's good to have descriptive names telling you what is where, but the LV sizes are more important here.

For example, you create 100GB lvg-root and 300MB lvg-boot. The lvg-boot is much smaller because you plan it as only a /boot partition.

During the install you mix up the mount points and you end up with 300MB for / and 100GB for /boot. It's a drastic example but you get the point.

With this mix up I am not sure if the sizes are what you planned for particular mount points or not. Since this is LVM you can play around and resize LVs, but honestly I think it's much better practice to do a new install. That way you will also practice installing.

This is a brand new empty installation so you have nothing to lose by doing a new one over it. :)


Touche! Now one other question(Should I start new thread??)..  How should I setup LV's for being a lamp server with a 2tb hd? Should I start small and grow the LV's as the system grows or should I allocate all the space right away?

---

### Post by darkod on 2012-08-21
The point of the LVM is that you can always grow the LVs when more space is needed. So, it's better to start small and grow them later as needed.

Further more, how LVM works goes towards starting small because you can grow the LV and the filesystem on it in live mode (while it's mounted and your server is running as normal), but you can only shrink the filesystem and then the LV when it's offline (unmounted).

So, if you make some LV too big now and you need the space later for other LVs, you will have to unmount it to shrink first the filesystem and then the LV in question.

---

### Post by padred123 on 2012-08-21
> **darkod said:**
> The point of the LVM is that you can always grow the LVs when more space is needed. So, it's better to start small and grow them later as needed.

Further more, how LVM works goes towards starting small because you can grow the LV and the filesystem on it in live mode (while it's mounted and your server is running as normal), but you can only shrink the filesystem and then the LV when it's offline (unmounted).

So, if you make some LV too big now and you need the space later for other LVs, you will have to unmount it to shrink first the filesystem and then the LV in question.


I got it now.. Thanks again!  \\:D/

---

### Post by LHammonds on 2012-08-21
> **padred123 said:**
> I got it now.. Thanks again!  \\:D/
When installing and following my instructions, make sure you match the name to the mount point.  They will not be listed in the same order every time...so following my example may have you jumping around instead of going down the list in order on your screen.

Just make sure you look at the partition you are selecting and make sure the mount matches the description.  If you get side-tracked and forget which one you are configuring, look at the top corner and it will let you know which LV you are working with (e.g. "opt" will be the one you mount to /opt, etc.)

Even though you can function with the names not matching the mount points, you don't want to do that if you can avoid it and reinstall right now.  It would be VERY confusing later on after you forget what happened during install.

As for grow as needed or assign it all now, I think darkod covered all the bases that I was going to mention.  You can grow dynamically while the system is live but it can be VERY painful if you need to shrink and could possibly cause data loss if you do.  Go ahead and give all the space the HD has to the LVM but don't assign it all immediately.  Just add enough that you need for right now and add a little whenever needed.  All those commands to do so are documented in that thread.

Have fun,
LHammonds

---

### Post by padred123 on 2012-08-21
> **LHammonds said:**
> When installing and following my instructions, make sure you match the name to the mount point.  They will not be listed in the same order every time...so following my example may have you jumping around instead of going down the list in order on your screen.

Just make sure you look at the partition you are selecting and make sure the mount matches the description.  If you get side-tracked and forget which one you are configuring, look at the top corner and it will let you know which LV you are working with (e.g. "opt" will be the one you mount to /opt, etc.)

Even though you can function with the names not matching the mount points, you don't want to do that if you can avoid it and reinstall right now.  It would be VERY confusing later on after you forget what happened during install.

As for grow as needed or assign it all now, I think darkod covered all the bases that I was going to mention.  You can grow dynamically while the system is live but it can be VERY painful if you need to shrink and could possibly cause data loss if you do.  Go ahead and give all the space the HD has to the LVM but don't assign it all immediately.  Just add enough that you need for right now and add a little whenever needed.  All those commands to do so are documented in that thread.

Have fun,
LHammonds

Ya I went down the line assuming it was in order but Thanks again for the pointers LHammonds! Third times a charm(hopefully).. :D

---

### Post by padred123 on 2012-08-22
Ok I just want to report back.. I see what I did wrong now and it was an easy fix. I didn't even have to recreate the LV's. All I had to do is change the mounts n flag to format each LV, then reinstall. 

df -h
```
padred123@padreserv:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/lvg-root  3.8G  377M  3.2G  11% /
udev                  989M  4.0K  989M   1% /dev
tmpfs                 399M  476K  399M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  997M     0  997M   0% /run/shm
/dev/mapper/lvg-tmp   1.9G   60M  1.8G   4% /tmp
/dev/mapper/lvg-bak   1.9G   60M  1.8G   4% /bak
/dev/mapper/lvg-home  9.3G  268M  8.6G   3% /home
/dev/mapper/lvg-srv   949M   30M  873M   4% /srv
/dev/mapper/lvg-usr    24G  1.1G   22G   5% /usr
/dev/mapper/lvg-var   3.8G  318M  3.3G   9% /var
/dev/mapper/lvg-opt   949M   30M  873M   4% /opt
```

---

