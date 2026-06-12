---
title: "/dev/sdc1 will be checked for errors at next reboot"
date: 2011-02-14
forum: Server Platforms
---

### Post by big_sigh on 2011-02-14
Hi

Everytime i log into my server, I get the message Displayed "/dev/sdc1 will be checked for errors at next reboot"

However, despite many reboots this message does not clear.

I cannot run FSCK on this partition as it is the boot partition.

I would like the device to get checked at reboot, any ideas how I can trigger this check , and that might clear the message :-)

Thanks

Si

---

### Post by vanadium on 2011-02-14
If it is mounted to root (/) then
```

sudo touch /forcefsck

```
will trigger the check on next reboot. In general, you put this file (forcefsck) in the root of the partition you want to be checked.

---

### Post by big_sigh on 2011-02-14
Many thanks, 

I tried that on both / and /boot, but still see the report.

I only see sdc1 mentioned on /boot.

Any ideas please :-)

thanks



~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/emeaserver-root
                       53G  5.8G   45G  12% /
none                  1.9G  700K  1.9G   1% /dev
none                  1.9G     0  1.9G   0% /dev/shm
none                  1.9G  628K  1.9G   1% /var/run
none                  1.9G  4.0K  1.9G   1% /var/lock
/dev/ida/c0d0p1       338G  143G  178G  45% /raid/1
/dev/sdc1             228M  180M   36M  84% /boot
/dev/mapper/raid0
                      214G   85G  119G  42% /raid/0
/dev/mapper/lvm_md1-raid2
                      135G  100G   29G  78% /raid/2

---

### Post by vanadium on 2011-02-14
Such configuration is not familiar to me. You may try to check whether the partition is effectively checked or not, and whether the check proceeded normally. There are logs under /var/log/fsck. If that is the case, then there is only the problem with this message appearing, but it could not do harm.

---

### Post by talishka on 2011-06-21
No news about this behaviour? i'm havin the same issue, i tried to force the check but it is impossible..

---

### Post by brettg on 2011-06-21
This could be the motd bug where the system has already done the fsck check but the message is still stuck in you motd.tail file. 

Try deleting /etc/motd.tail and then restart

---

### Post by Intangir on 2012-04-17
this apparently still goes on

i checked my fstab, it has non-zero values for the check field

but it wont check them, it tells me ALL of my volumes will be checked but has never checked a single one ever. the fsck logs say none have ever occured

also im using a raided boot and raided volumes

---

### Post by bzhao on 2012-10-16
I also met the same problem but the reported partition is not the partition mounted to /

  After rebooting serveral times, the problem is still there. And then I remove the the failure info in /etc/mtd file, and then I reboot.  The problem sound have gone!

---

### Post by santhony on 2012-10-16
I'm having this same issue on my raid5 /dev/md127..

It keeps saying on next boot it will be check...

---

### Post by jringoot on 2012-11-13
I had this too:

I booted with 0 and 1 as sixth field for the / partition in /etc/fstab, that made no difference.
There was no /etc/motd.tail, removing /etc/motd gave back the same message (fsck at next reboot) after reboot.

It took an "apt-get update && apt-get upgrade" + "apt-get install libgnome2-0 linux-headers-server linux-image-server linux-server linux-tools" + a touch /forcefsck and a reboot to resolve it, it is now on 
Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-33-generic x86_64)

---

### Post by razor7 on 2012-12-18
Hi, here is a bug report [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/692355](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/692355)

---

### Post by deadsea on 2013-04-20
Here is the command line that actually fixes the problem for me.  It removes the file with the future timestamp and forces the entire motd file to be regenerated.

[FONT=Courier New]sudo rm /sudo bash -c 'rm /var/lib/update-notifier/fsck-at-reboot && for file in /etc/update-motd.d/*; do $file; done > /var/run/motd' && cat /etc/motd[/FONT]

---

### Post by banjopotato on 2013-05-11
I keep getting this same problem. The file's time stamp is accurate and boot.log shows that fsck did run on last boot. But I still get the message "/dev/sda1 will be checked for errors at next reboot" every time I ssh to my machine.

The command in that last post resulted in an error:

```
$ sudo rm /sudo bash -c 'rm /var/lib/update-notifier/fsck-at-reboot && for file in /etc/update-motd.d/*; do $file; done > /var/run/motd' && cat /etc/motd
rm: invalid option -- 'c'
Try `rm --help' for more information.
```

---

### Post by matt_symes on 2013-05-11
> **banjopotato said:**
> I keep getting this same problem. The file's time stamp is accurate and boot.log shows that fsck did run on last boot. But I still get the message "/dev/sda1 will be checked for errors at next reboot" every time I ssh to my machine.

The command in that last post resulted in an error:

```
$ sudo rm /sudo bash -c 'rm /var/lib/update-notifier/fsck-at-reboot && for file in /etc/update-motd.d/*; do $file; done > /var/run/motd' && cat /etc/motd
rm: invalid option -- 'c'
Try `rm --help' for more information.
```

I think the poster meant to post this (as the above looks like a typo)

```
sudo bash -c "rm /var/lib/update-notifier/fsck-at-reboot && for file in /etc/update-motd.d/*; do $file; done > /var/run/motd"
```

Kind regards

---

### Post by codeFX on 2013-07-07
```
 /usr/lib/update-notifier/update-motd-fsck-at-reboot --force
```

It seems, when using the --force parameter, it forces the update of the MOTD fragment.

---

