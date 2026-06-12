---
title: "minimal server install + raid5"
date: 2010-02-17
forum: Server Platforms
---

### Post by dimwhit on 2010-02-17
Hi all,

After a long time I tried ubuntu(9.10) again on my fileserver, I have some remarks;
- why does a minimal server installation include X/openoffice? I don't need document conversion on a fileserver and I bet a lot of people don't. Wouldn't it be better to create a new server package and leave minimal minimal?
- low memory installs (64mb) don't work unless you configure swap by hand in between things, 64mb ram is a lot in my eyes. I mean, not to be rude but if I wanted all this I could've better installed Solaris.

That said it's stable and running fine. Since it's my home fileserver I tried to convert my previously created raid10 mirror on an adaptec 1200 card to a softraid 5 solution.
This is wat I did:
- cfdisk on /dev/sd[bcde] a primary partition of size - 300mb (in case a drive differs when I need to replace it)
- mdadm --create /dev/md0 --level=raid5 --chunk=128 --raid-devices=4 /dev/sd[bcde]1
- mkfs.ext4 -v -m .1 -b 4096 -E stride=32,stripe-width=64 /dev/md0

This works fine and creates the md0 array. I've let it rebuild parity, copied a lot of files (+500gb) to it and then I wanted to try my wake on lan. So I did a shutdown -h now.
It's neat to see wakeonlan working but afterwards my raid5 array was missing (well not completely) and I had apart from an incomple md0 also an md_d0 and some extra partitions in /dev/md

After reading these forums I got some pointers to clear the metadata which the adaptec might have left with dmraid, but I don't have dmraid installed and when I install it it says there are no raid partitions. Today I recreated the array after dding most of all the disks, fiddled with mdadm.conf and did a shutdown -h and wakeonlan to see if it was still there. Now it is but I'm unsure what happens after parity is rebuild again and I repeat the powercycling. Can someone tell my if it's okay to put an ext4 filesystem on md0 without creating a partition for it (the first disk is seen as having a filesystem while the others show as part of the raid) and if what I did is correct in the first place?

my mdadm.conf:
root@awen:/home/axel# egrep -v '^#|^$' /etc/mdadm/mdadm.conf
DEVICE /dev/sd[bcde]1
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR [email]axel@axel.truedestiny.net[/email]
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=2ed837dd:4ff4e66e:88d85794:9c783195

mdstat atm:
root@awen:/home/axel# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[4] sdd1[2] sdc1[1] sdb1[0]
      936910464 blocks level 5, 128k chunk, algorithm 2 [4/3] [UUU_]
      [========>............]  recovery = 41.1% (128544128/312303488) finish=230.7min speed=13269K/sec

unused devices: <none>

Btw.. is this speed common? There's no other activity at the moment.
All this is with clean shutdown btw, I know I should disable writecache after I'm done for the obvious reasons.

This is the output after my first try with the messed up raid5:
root@awen:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]                                                                           
md0 : active raid5 sde1[3] sdd1[2] sdc1[1]                                      
      934573056 blocks level 5, 128k chunk, algorithm 2 [4/3] [_UUU]            
                                                                                
md_d0 : inactive sdb1[0](S)                                                     
      311524352 blocks                                                          
                                                                                
sdb1 was the drive which was detected as having a filesystem (first of the set). I reverted the order on my last try (sd[edcb]1). Also there was a DEVICE partitions in mdadm.conf which I now changed to DEVICE /dev/sd[bcde]1

The network install worked great btw, this is real neat since I don't have a cdrom or floppy on my server, thanks.

---

### Post by trundlenut on 2010-02-18
err, the server version doesn't include X, did you download the right image?

---

### Post by The Real Dave on 2010-02-18
Sounds like you've used the wrong ISO. Server installs are command line only. 

[These]("http://www.ubuntu.com/getubuntu/download-server") are the ISOs you want for Ubuntu Server

Also, please consider using Bittorrent to download the ISO

[ubuntu-9.10-server-amd64.iso.torrent]("http://releases.ubuntu.com/9.10/ubuntu-9.10-server-amd64.iso.torrent")

[http://releases.ubuntu.com/9.10/ubuntu-9.10-server-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-server-i386.iso.torrent)

---

### Post by dimwhit on 2010-02-18
I didn't use an iso but the netboot images at
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/)

In tasksel I choose 'Basic Ubuntu server' and 'OpenSSH server', I thought this would be the same as installing from a cd (I don't have a cdrom nor floppy in the machine).
Linux awen 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
is wat is says when I log in together with the server status.

The raid is broken again, after a shutdown I now had:
axel@awen:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]                                                                           
md_d0 : inactive sde1[3](S)                                                     
      312303488 blocks

I'm dd-ing the complete disks at the moment but it takes ages. I didn't configure any raid on the adaptec card.

---

### Post by dimwhit on 2010-02-20
Ok, after zeroing all the drives completely, reboot, cfdisk, reboot, and recreating the raid5 array everything works fine now. It took a full day doing dd_rescue/parity rebuild :(
I also removed the openoffice + headless java and most of the x libraries but there's still a lot installed.
I did not use any desktop package, only server and openssh. If you people tell me there should not be X/openoffice when I install via the server cd why is the netboot setup different when I choose only these two in tasksel?

---

### Post by dimwhit on 2010-02-20
btw, the server never booted to a gui if that's some help, I'm fairly certain (I reinstalled) I got openoffice/lot of x libs when installing just the selected taskel tasks as mentioned above.

---

### Post by iissmart on 2010-03-22
You're not using the server kernel, that's for sure. Otherwise it would say "2.6.31-19-server". There are some nice server-centric tweaks to the kernel that you would probably benefit from.

---

