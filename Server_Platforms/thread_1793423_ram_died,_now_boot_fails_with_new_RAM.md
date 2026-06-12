---
title: "ram died, now boot fails with new RAM"
date: 2011-06-29
forum: Server Platforms
---

### Post by SpyruleUp on 2011-06-29
Hello,

 I'm trying to reboot a ubuntu (10 I think) server, and it hangs with the following :

(some spots I was too lazy to copy (specifically the file count and block counts)

--------------
fsck from util_linux_ng 2.17.2
/dev/sda1 : clean 205/124496 files
/dev/mapper/victoria-root : clean ###/#### files
error -1 (Unknown error 18446744073709551615) opening credential file ~/.credentials
mountall mount /var/www/drupal/sites/website/proserv [658] Terminated with status 1
modem_manager : Loading plugin "Longcheer"
modem_manager : Loading plugin "Option high-speed"
modem_manager : Loading plugin "TOO MANY TO LIST"
mountall mount /var/www/drupal/sites/website/proserv [905] Terminated with status 1

------------------------

and that's where it hangs, I tried grubs recovery boot, but it hangs with the exact same error.


I know how to get around a linux box, but I'm MILES from having experience troubleshooting linux, so ANY help is hugely apreciated.

Thanks in advance.

 Spyrule

---

### Post by SpyruleUp on 2011-06-29
anybody?

---

### Post by CharlesA on 2011-06-29
You said RAM died? Does it boot if you take the new RAM out?

It looks like it is failing to mount a drive.

Can you post the output of these after going into recovery mode and getting a root shell:

```
blkid -c /dev/null
```

```
cat /etc/fstab
```

---

### Post by SpyruleUp on 2011-06-30
For recovery mode, are you referring to GRUB's boot recovery mode, or some other method ?

 If it's the boot loader option that says (recovery) besides it, it doesn't work as well, same problem.

---

### Post by volkswagner on 2011-06-30
Do you have added drive getting mounted at boot.
  

The recovery mode is found in the Grub boot menu not Grubs's recovery.  If you don't see operating system choices at boot, you will need to hit the shift key while booting to get menu choices.  There should be at least two choices for regular boot and single user mode, there may be old entries from older kernels and also memtest.

Should look like this:

[IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.chainload.grub.sm.png[/IMG]


If you have drives not necessary for the file system perhaps you can boot a live CD if Recovery mode does not work.
Boot the live CD and edit your /etc/fstab on you / partition, not the one on the live CD.

Comment out any mount points that are not necessary for the system to boot. 

Particularly is this a separate mount point?
```
/var/www/drupal/sites/website/proserv
```

---

### Post by SpyruleUp on 2011-06-30
When I do the shift boot into the Grub menu I get 4 options :

1) Ubuntu ###
2) Ubuntu ### (Recovery mode)
3) memtest 86+
4) memtest 86+(test version.. or something like that)

If I attempt to run #2, it fails at the same location.

trying to boot to live cd now... if it doesn't work, I'll let you know.

Thanks in advance again,

 Spyrule.

---

### Post by SpyruleUp on 2011-06-30
oh this gets even better... my current ISO is corrupt. Download again... :roll:

---

### Post by SpyruleUp on 2011-06-30
Thanks for the help guys,

Turns out it WAS a permanent mount that was causing the problem.

What it was dying on was the .credentials file that had become corrupted. 

the steps I had to take :

1) download and install LVM2 in my liveCD (since that's how the system was setup)

2) mount said partition
3) Find and edit the etc/fstab, and remove the offending line
4) Noted that IN that line from above, is where the corrupted /.credentials file was being called from.. so I deleted it as well!
5) Rebooted, and voila! we're good to go.  I now have to re-create that mount, since it's where our CRM stores physical files, but again I think it was the credentials file that was pooched.

Thanks again guys.

---

