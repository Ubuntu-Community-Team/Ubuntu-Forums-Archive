---
title: "Filesystem problems with raid5+dmcrypt+lvm"
date: 2006-05-04
forum: Server Platforms
---

### Post by jtorrance on 2006-05-04
This is going to be a pretty lengthy post. Sorry for that. 

So this is what happened:

I have a server running Ubuntu 5.10 with two 120gb drives. The drives had several partitions, which where used in a raid1 setup. On top of the md devices i used a dmcrypt device to encrypt all data travelling to the raid. I used this setup for at least a year. First with a gentoo system, then with Hoary and then with Breezy and a 2.6.12-10-686 kernel.
I decided to upgrade the machine and installed a new 200gb hd. I repartitioned all drives until I had the following setup:

one 128mb boot partition on all 3 drives drives chained as a raid1
one 192mb swap partition on every drive with dmcrypt on top.
one large partition filling the rest of the 120gb drives (and most part of the 200gb drive), chained as a raid5, then a dmcrypt on top of that and a lvm vg on top of the dmcrypt device. I had 4 lvs on that vg (/, home, var, data)
The remaining 80gb of the new 200gb harddrive were used as a single partition with a dmcrypt device on top.

All filesystem were reiserfs except /boot, which was ext2.

Both of the raids were started in degraded mode and they still are degraded, since I keep a backup of my old data on the 3rd drive. Because of the following problem I didn't dare to delete the backup and include the drive in the raid setup.

After I setup everything, I started to copy all my old data to the new filesystems. After about 30 minutes I saw a reiserfs warning in the kernel log:

May  3 04:58:55 sal9000 kernel: [4310107.889000] ReiserFS: warning: is_tree_node: node level 14690 does not match to the expected one 1
May  3 04:58:56 sal9000 kernel: [4310107.889000] ReiserFS: dm-3: warning: vs-5150: search_by_key: invalid format found in block 32813. Fsck?

I cancelled the data transfer and rebooted the machine. I confirmed my setup (all partitions the correct size etc.) and checked the filesystem. Reiserfsck didn't find any problems. I resumed the data transfer and after another hour or so, the same problems appeared.

After that I had enough and changed alle filesystems to ext3. Again after some time copying all the data, ext3 got scared and mounted my root partition read-only. The errors I found in the syslog were:

May  1 19:33:32 sal9000 kernel: [4306789.582000] EXT3-fs error (device dm-3): ext3_readdir: bad entry in directory #54284: rec_len %% 4 != 0 - offset=0, inode=1851270767, rec_len=58506, name_len=72
May  1 19:33:32 sal9000 kernel: [4306789.582000] Aborting journal on device dm-3.
May  1 19:33:33 sal9000 kernel: [4306790.043000] ext3_abort called.
May  1 19:33:33 sal9000 kernel: [4306790.043000] EXT3-fs error (device dm-3): ext3_journal_start_sb: Detected aborted journal
May  1 19:33:33 sal9000 kernel: [4306790.043000] Remounting filesystem read-only
May  1 19:33:34 sal9000 kernel: [4306791.753000] EXT3-fs error (device dm-3): ext3_readdir: bad entry in directory #54284: rec_len %% 4 != 0 - offset=0, inode=1851270767, rec_len=58506, name_len=72

Again an fsck didn't find any problems. I changed some stuff in the lvm config file and tried some other things, mainly recreating all filesystems, and converting to reiserfs again, but it didn't help. As soon as there was some load on the harddrives (copying several large files and running an fcheck or updatedb) the filesystems would throw some warnings. No layers except the filesystems ever complained about something, neither the harddrives, nor the raid, nor the lvm. I reproduced this behavior now about 20 times, and it was only twice, that fsck really found something to do on the filesystems afterwards.

I didn't really know what to do, so I decided I should try Dapper and hope, that the new kernel, and the probably new lvm tools would somehow magically fix the problem. After an upgrade I booted the 2.6.15-21-686 kernel. The problem persisted. I then tried 2.6.15-22-686 which didn't help either, but produced the second major filesystem corruption I experienced. The first one was a few days ago, with an ext3 under Breezy.

I then booted the 2.6.15-22-server image, which has now been running fine for about 5.5 hours under heavy load. I don't know what the difference between the kernel images is, but from the 'uname -a' output I guess the server images are at least lacking the preempting support.

I never had any problems with the partition lying outside of the lvm.

The machine I'm using is an IBM xseries 205 server, with a P4 2.4GHz, 768 MB ECC RAM. The harddrives are two IBM Deskstar IC35L120AVV207-0 (I know, the dreaded Deathstar series, but as I said above, no hardware problems were reported) and one Samsung SP2014N.

If you have any questions or need more information/logs, I'll be glad to help.

If you tell me, there is nothing wrong with my setup and if it's not the expected behavior of the none-server kernels to eventually produce filesystem corruption in the described environment, I'm going to file a bug report in the next few days. Maybe it's an upstream kernel bug.

Thanks for the patience ;)
Kevin

---

### Post by jtorrance on 2006-05-04
Hi!

Well, it seems the server-kernel wasn't the expected solution after all. At least it took about 14 hours for the problem to reappear. Does anybody have an idea what is causing the problem? Or is anybody running a similar setup?

Thanks
Kevin

---

### Post by harper on 2006-05-18
having the exact same problem but without dmcrypt

---

### Post by jtorrance on 2006-05-18
[QUOTE=harper]having the exact same problem but without dmcrypt[/QUOTE]

Hi!

This is strange. I found a possible solution/patch in the dm-crypt mailing list ([http://news.gmane.org/gmane.linux.kernel.device-mapper.dm-crypt)](http://news.gmane.org/gmane.linux.kernel.device-mapper.dm-crypt)). I tried it a few days ago and didn't have any problems so far. If you have the same problem but without dm-crypt the problem could still lie elsewhere (lvm or raid).

Which kernel are you using? During my research I found some posts complaining about similar problems when using SMP-kernels which caused race-conditions in lvm or raid code. Maybe you could try a kernel without SMP (the -386 for instance).

Also faulty memory was sometimes the reason for the fs-corruptions. If you have the possibility (and patience) this is another thing to try. 
How easy is it for you to reproduce the problem? It sometimes took nearly a week for me to encounter it again.

Kevin

---

