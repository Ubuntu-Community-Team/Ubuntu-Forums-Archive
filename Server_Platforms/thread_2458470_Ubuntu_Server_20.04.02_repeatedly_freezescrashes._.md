---
title: "Ubuntu Server 20.04.02 repeatedly freezes/crashes. syslog pastebin inside."
date: 2021-02-25
forum: Server Platforms
---

### Post by ryan170 on 2021-02-25
Hello all,

I'm running Ubuntu Server 20.04.02 on an Intel NUC10i5. This is a fresh install (2 days), but this is a repeated problem; I've reinstalled Ubuntu several times, and I'm at my wits end with this.

After install, I do a few things:
[LIST]
[*]Set a static IP
[*]Edit /etc/fstab to mount my NAS drives via NFS
[*]Set up Docker/Docker Compose for Plex/SABnzbd/qBittorrent/Jackett/Radarr/Sonarr
[*]rsync
[/LIST]
 cronjob to copy the settings for those programs to the NAS as a backup

That's it. This NUC only serves as a media server for what's hosted on the NAS. It downloads media, moves it to the NAS, and then indexes it for Plex. That's all. But it keeps freezing/crashing, and I can't really understand why.

I don't think it's a hardware issue: I'm using a Kingston NVME drive and Kingston RAM (on the Intel NUC compatibility list). It might be a heat problem, but when I last checked temps, they were all ~40, which should be just fine.

This is the last bit of the /var/log/syslog before the system froze. I can't really make sense of this, but hopefully someone else can:

[https://pastebin.com/EzyQJicb](https://pastebin.com/EzyQJicb)

Thanks so much for any help! This NUC has been nothing but trouble—first I had to RMA for the ethernet port, then I swapped the cheap RAM for the good Kingston stuff, but it keeps freezing, and it seems like it might more of a software problem than a hardware problem. I'm ready to install Windows and just get on with my life, but I'm hoping someone can help me figure out what's going on with Ubuntu on this NUC. Thanks again!

---

### Post by ameinild on 2021-02-25
You have I/O errors on your NVME disk, which also causes system jobs to hang in the kernel for more than 2 minutes. I definitely think you have some kind of problem with the NVME disk - or maybe it's under extremely heavy load and can't keep up.

Also see here: [https://unix.stackexchange.com/questions/181505/what-does-task-mysqldxxx-blocked-for-more-than-120-seconds-mean](https://unix.stackexchange.com/questions/181505/what-does-task-mysqldxxx-blocked-for-more-than-120-seconds-mean)

---

### Post by ryan170 on 2021-02-25
Thank you. The NVME disk is Kingston, so it should be good, but it's not technically on the Intel NUC compatibility list; only some Intel NVME drives are "validated" according to that.

I guess I'll try to load up a USB with systemrescuecd or something like that for a drive test.

If it passes the tests, and I assume that it's just under load and can't keep up (an NVME not able to keep up?) is there some way to limit the I/O to prevent these errors?

---

### Post by ameinild on 2021-02-25
The only solutions I can come up with are either:

[LIST]
[*]Reduce "swappiness" if it's because of swap activity 
[*]Run fewer jobs that require disk I/O 
[/LIST]
But you should definitely monitor the disk I/O capacity. 
Consider using either hdparm or dd, see here: [https://askubuntu.com/questions/87035/how-to-check-hard-disk-performance](https://askubuntu.com/questions/87035/how-to-check-hard-disk-performance)

For reference, my NVME disk has the following:

[LIST]
[*]Cached reads: ~ 2000 MB/sec 
[*]Buffered reads: ~ 1000 MB/sec 
[*]Write (dd): ~ 500 MB/sec 
[/LIST]

---

### Post by ryan170 on 2021-02-28
Thanks. Adding a hdd to reduce the I/O on the NVME seemed to have cleared up that problem. I'll keep an eye on it in the future.

---

### Post by ameinild on 2021-03-01
Hi. I'm glad to hear that you've resolved the issue. 

Cheers! \\:D/

---

