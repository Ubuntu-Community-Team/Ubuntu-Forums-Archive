---
title: "fsck runs even when shutdown cleanly"
date: 2013-09-17
forum: Ubuntu Development Version
---

### Post by santosh83 on 2013-09-17
Hi all,

I've noticed by turning of the plymouth splash screen that fsck runs (with the usual "INFO: recovery required on...") on my / filesystem even though the system shuts down cleanly without any apparent problems. This is lubuntu 13.10 beta1 here. Are there any specific log files I can inspect to find out if in fact the shutdown was clean or not? Thanks.

---

### Post by cariboo on 2013-09-17
Could it be related to the problem in this thread:

[http://ubuntuforums.org/showthread.php?t=2175010](http://ubuntuforums.org/showthread.php?t=2175010)

because if you are getting random lockups, how are you shutting the system down cleanly?

---

### Post by santosh83 on 2013-09-18
Of course I do expect fsck to run those times I hit the reset button! ;-)

But there are times when it doesn't lockup till I shut down, and the messages printed to the console till the final moment seem normal to me, yet when I boot again it runs the filesystem check. I'll investigate the issue a little more and report back thanks.

In any case because the shutdown seemingly did happen normally till final stages fsck doesn't find orphan inodes and such, as it does when I boot after a real lockup. Seems to be a minor bug...

---

### Post by zika on 2013-09-18
Do You, by any chance have file forcefsck in Your /...?
If You do, just erase it...

---

### Post by santosh83 on 2013-09-18
> **zika said:**
> Do You, by any chance have file forcefsck in Your /...?
If You do, just erase it...

Nope I just checked.

What's more just now I'd restarted cleanly after installing the latest updates, and there were no error or warning messages I could see, yet "INFO: recovery required..." on boot up!

I hope this is resolved by the time we come to final release.

Is there any log for the shutdown process, which I could inspect to see if the filesystems were cleanly unmounted or not? The messages flash by too quickly on the console...

---

### Post by zika on 2013-09-18
```
sudo tune2fs -l /dev/???|grep Check
```
Just to see what is set...
???=Your HDD
I think that this bug struck me also, eventhough I have this value set to 0(=none)...

---

### Post by santosh83 on 2013-09-18
> **zika said:**
> ```
sudo tune2fs -l /dev/???|grep Check
```
Just to see what is set...
???=Your HDD
I think that this bug struck me also, eventhough I have this value set to 0(=none)...

Doing for my / partition:
sudo tune2fs -l /dev/sda3|grep Check

gives:
Check interval:           0 (<none>)

For comparison doing this on my 10.10 partition (sda1) gives:
Check interval:           15552000 (6 months)

Doing for the whole HDD:
sudo tune2fs -l /dev/sda|grep Check

gives:

tune2fs: Bad magic number in super-block while trying to open /dev/sda
Couldn't find valid filesystem superblock.

---

### Post by zika on 2013-09-18
> **santosh83 said:**
> Doing for my / partition:
sudo tune2fs -l /dev/sda3|grep Check

gives:
Check interval:           0 (<none>)

For comparison doing this on my 10.10 partition (sda1) gives:
Check interval:           15552000 (6 months)

Doing for the whole HDD:
sudo tune2fs -l /dev/sda|grep Check

gives:

tune2fs: Bad magic number in super-block while trying to open /dev/sda
Couldn't find valid filesystem superblock.Yeap, the same thing...
It is bug somewhere else, I'll try to find, if I find time...

---

### Post by VMC on 2013-09-18
Did you check "/var/log/fsck" logs. Mine says ```
(Nothing has been logged yet.)
```

---

### Post by amjjawad on 2013-09-20
Hi,

Please try to download and install the latest daily build and report back, thank you!

---

### Post by santosh83 on 2013-09-20
> **VMC said:**
> Did you check "/var/log/fsck" logs. Mine says ```
(Nothing has been logged yet.)
```

Here too I find the same message in both 'checkfs' and 'checkroot.'

> **amjjawad said:**
> Hi,

Please try to download and install the latest daily build and report back, thank you!

Just confirming... is this what I want?
[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

The plain 'daily' is the same as this except the installer is the alternate one right?

---

### Post by amjjawad on 2013-09-20
> **santosh83 said:**
> Just confirming... is this what I want?
[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

Yes :)


> The plain 'daily' is the same as this except the installer is the alternate one right?

[http://cdimage.ubuntu.com/lubuntu/daily/current/](http://cdimage.ubuntu.com/lubuntu/daily/current/)

Correct :)

Daily Live = The desktop version (the normal one)
Daily = Alternate 

Thank you!

For more information about testing:
[https://wiki.ubuntu.com/QATeam](https://wiki.ubuntu.com/QATeam)

Lubuntu:
[https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing)

If you have Qs regarding testing, please, let us know ;)

---

### Post by JMB74 on 2013-09-20
Had this on 3 separate laptops since raring, and does not seem to do any harm as far as I can see. Annoying though...

---

### Post by santosh83 on 2013-09-20
> **JMB74 said:**
> Had this on 3 separate laptops since raring, and does not seem to do any harm as far as I can see. Annoying though...

I read somewhere that when a FS is unmounted during shutdown/restart, a bit on it (marking it as 'dirty') is 'cleared', so perhaps what's happening here is the FS code is failing to clear this bit even on a clean unmount...

As you said, nothing actually happens during recovery in such cases (as opposed to after an actual crash), but rather unsettling to see the message though.

---

