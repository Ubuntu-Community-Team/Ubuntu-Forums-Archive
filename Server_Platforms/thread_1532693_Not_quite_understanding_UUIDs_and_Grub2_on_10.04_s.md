---
title: "Not quite understanding UUIDs and Grub2 on 10.04 server"
date: 2010-07-16
forum: Server Platforms
---

### Post by mwallette on 2010-07-16
I'm trying to set up an Ubuntu server using 10.04 (64-bit), and running into problems after a couple of reconfigurations.  Here's the full story:

I initially built the server on a 400+GB RAID5 array, putting everything but swap in one partition.  Unfortunately, I needed to repartition, putting / in the first primary partition, swap in the second partition, /var/log in the third primary partition and /home in the remaining space on the fourth primary partition.

However, at this step, I ran into some problems with UUIDs in /etc/fstab and Grub2 (I've used Linux for about 9 years, but I'm new to Ubuntu, and I haven't used UUIDs or Grub2 on Gentoo, yet).  Consequently, I made the (probably not smart) decision to move back to the /dev/sdX notation I am familiar with.

The problem with that is that now I need even more space on /home, so I've added a Dell Powervault and a Dell PERC5/e SATA card to my server.  Now, Grub2 tries to boot from the new RAID array on the Powervault instead of the internal RAID array, so I am trying to move back to the UUID notation so that I don't have worry about /dev/sda being the internal array sometimes and the external array at other times.

I don't mind being RTFM'd, but I'm having trouble finding pointers to the documentation explaining Grub2 configuration and the UUID notation.  Does anyone have pointers to some readable, concise documentation on configuring this in Ubuntu?

Thanks!

---

### Post by oldfred on 2010-07-16
Some links, but I do not know RAID which has its own issues. The UUIDs are used as they are less likely to change, only major partition changes will change a partitions UUID.

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Understanding fstab You can use drive, UUID or label.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by capscrew on 2010-07-16
> **oldfred said:**
> Some links, but I do not know RAID which has its own issues. The UUIDs are used as they are less likely to change, only major partition changes will change a partitions UUID.

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Understanding fstab You can use drive, UUID or label.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

UUID's are used BECAUSE they don't change.  The are assigned to the partition when it is created.  If you modify the partition it will change.  You can see all the UUID's by doing this ```
sudo blkid -l

```That is an L not a 1(one)

the man page has information see```
man blkid
```

In addition you can use partition labels in fstab.

See it all [**_here_**]("https://help.ubuntu.com/community/UsingUUID"),

Sorry if I have repeated anything from above.

BTW - the reason the SATA drive is first is that it is fastest in reporting back to the kernel so it is enumerated first.

---

### Post by mwallette on 2010-07-19
Sweet -- thanks for the replies, oldfred and capscrew!

Oldfred: I'll check out the links you provided and see if they shed some enlightenment :)

Capscrew: yep, I've seen the blkid command, and added the appropriate UUID's to /etc/fstab.  I think the real hangup at the moment is figuring out how to configure grub2 to boot from the appropriate device.  I could do that in lilo or the original grub, but I haven't wrapped my head around the new grub2 configuration, yet.

---

### Post by mwallette on 2010-07-19
oldfred: your second link pointed me in the right direction.  After reading the links you provided and making some progress, I found [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") (&quot;Method 3 -- Chroot&quot;) which finally got my server booting again.

Thanks again for the help! :D

---

