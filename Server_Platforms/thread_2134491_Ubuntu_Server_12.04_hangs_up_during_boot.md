---
title: "Ubuntu Server 12.04 hangs up during boot"
date: 2013-04-11
forum: Server Platforms
---

### Post by glukoz on 2013-04-11
Hi all


I have recently installed Ubuntu Server 12.04 64bit on Sunfire X4540 server and I am experience a problem during system boot. First I will provide some details about installation process. I created one partition on /dev/sda disk and one partition on /dev/sdi disk. Both partitions take whole space on their disks. Next I created raid1 array on these two partitions (/dev/sda1, /dev/sdi1), created ext3 filesystem on it and set mount point to "/". I carried out all these step using partitioning tool included in system installation utility. The installation was accomplished successfully - in last step I installed grub on /dev/sda.

My problem is that boot process stops in the middle. When I turn server on grub is executed from /dev/sda, it correctly loads kernel from array, kernel runs using initram disk. Some messages are displayed on the screen but in one moment new messages stop appearing and nothing else happens. When I press enter then I can see that I am switched to initram shell (I can see (initram) shell prompt) - I can write commands, execute etc. I have to press ctrl+D to continue boot process and my system is fully operational after a few seconds. It is quite uncomfortable behaviour as one needs to be near the server when she wants to do reboot.

Here you can examine dmesg output: [http://justpaste.it/2dsh](http://justpaste.it/2dsh)

There is also one more thing that may be reason of this problem. In one moment during boot process, but before hang up, I can see following message

udevd[143]: timeout: killing '/sbin/modprobe -bv pci:v00001000d00000058sv00001000sd00001000bc01sc00i00'

being displayed on the screen constantly, in one message per second frequency. Such displaying lasts about one minute and boot hangs up just a few moments after it ends. Sometimes there are some other messages displayed before hang, sometimes these 'timeout' messages are last ones.

I've checked PCI modalias parameters included in modprobe command and that's what I've found:

vendor: LSI Logic
device: PCI-Express Fusion-MPT SAS

---

### Post by TheFu on 2013-04-11
No answer, but where is /boot - inside the mdadm RAID1?

---

### Post by glukoz on 2013-04-12
> **TheFu said:**
> No answer, but where is /boot - inside the mdadm RAID1?

Yes, exactly. I think that it should not cause any problem - grub loads and runs kernel properly...

---

### Post by TheFu on 2013-04-12
> **glukoz said:**
> Yes, exactly. I think that it should not cause any problem - grub loads and runs kernel properly...

I've never attempted to boot off RAID1 storage (unless it was HW RAID) - always kept /boot on a different, ext2, partition.  Sure it should work, but ...

---

### Post by glukoz on 2013-04-12
> **TheFu said:**
> I've never attempted to boot off RAID1 storage (unless it was HW RAID) - always kept /boot on a different, ext2, partition.  Sure it should work, but ...


I have another SunFire X4540 server which has Ubuntu Server 10.04 installed in exactly the same disk configuration. It boots without any problem. That is why I think this issue can be solved without splitting /boot to other partition.

---

### Post by TheFu on 2013-04-12
> **glukoz said:**
> I have another SunFire X4540 server which has Ubuntu Server 10.04 installed in exactly the same disk configuration. It boots without any problem. That is why I think this issue can be solved without splitting /boot to other partition.

I agree completely, however, with all the boot changes recently required to support 2+TB disks, 4K sectors, EFI, signed kernels, grub2, .... things might have accidentally broke between 10.04 and 12.04.  Lots of things around booting have changed, that's all I'm sayin'.

I'm certain that your google-fu exceeds mine, but [http://ubuntuforums.org/showthread.php?t=2110314](http://ubuntuforums.org/showthread.php?t=2110314) reads as similar to me.

Hopefully, someone else with more knowledge than I will respond with real help.

---

### Post by glukoz on 2013-05-08
Up

Maybe some of you found solution to this problem? Link provided by TheFu in previous post doesn't apply to my case.

---

### Post by glukoz on 2013-05-21
I've finally managed some time to investigate this problem more deeply and I've succeeded to solve it. The problem was with setting of delay during which initram script waits for root device to be recognized by kernel. By default this delay is set to 30s. It seems that it was too short because my server has a lot of disks. After delay expiration all disks weren't initialized yet, that is why root filesystem (at raid array) wasn't recognized at that time, so initram script was returning to shell. I've edited /etc/default/grub file to add new kernel parameter:

GRUB_CMDLINE_LINUX="rootdelay=200"

which sets delay time to 200s. After editing I updated grub configuration files by issuing:

update-grub

and now server boots pretty well.

---

### Post by crpeck on 2014-03-20
Ahh - thanks for posting, I ran into this today... Saved me some time and grief.

---

