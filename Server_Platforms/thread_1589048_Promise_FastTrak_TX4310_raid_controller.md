---
title: "Promise FastTrak TX4310 raid controller"
date: 2010-10-05
forum: Server Platforms
---

### Post by woogy on 2010-10-05
Hello everybody,

I haven't been able to find much of anything via Google or these forums.

Basically my problem is configuring this raid controller and Server 10.04 to work together and read the existing RAID 5 array that is on the controller. It has all of the disks listed, but doesn't recognize the array as one array.

Any help?

Thanks!

---

### Post by woogy on 2010-10-06
Bumping this... hopefully that's not against the rules.

---

### Post by CharlesA on 2010-10-06
Is it actually being seen as a RAID controller or just as seperate drives?

The only drivers I found for that card were for RedHat and OpenSUSE.

I don't know if either of those will work with Ubuntu.

[Support page.]("http://promise.com/support/download.aspx?m=205&region=en-US&rsn1=19")

I also found an [ancient thread]("http://ubuntuforums.org/showthread.php?t=268570") discussing it.

---

### Post by woogy on 2010-10-08
Hi CharlesA and thanks for the reply -

It is seeing the card and detects it as a RAID controller, but it has all of the drives separate (sdb,sdc,sdd,sde). I found the drivers you listed and apparently they are compatible with the 2.4 kernel but not the 2.6 kernel, which is what I'm running.

I'll take a look at that thread you supplied me - anybody else have anything to add?

Thanks.

[EDIT] I have actually seen that thread and it didn't help me. Thanks.

---

