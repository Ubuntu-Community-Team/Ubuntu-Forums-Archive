---
title: "Will Ubuntu Server Meet My Needs?"
date: 2009-12-14
forum: Server Platforms
---

### Post by Phillyman on 2009-12-14
I am looking into creating a multi-use server for my home. At the current time I am looking at Ubuntu Server, FreeNas and Amahi as viable options. I love using Ubuntu Desktop and would like to stick with you guys for my home server if possible. So what am I looking to do?

Dedicated File Server - To allow my content to be viewable from all my home workstations, plus my Xbox 360 and Playstation 3. Most of my users on my home network should only be able to add files, not delete them.

Dedicated FTP Server - I need to allow people to connect to my server to upload and download files. The FTP software should be able to restrict people from connecting at certain hours and days. The software should also allow me to limit bandwidth and speeds for users. The software should also be able to "lock" down accounts after "X" wrong tries, or lock down IP's after "X" wrong tries.

Ghosting Server - I should be able to use a program like PING to create and restore backup images of my workstations.

Backup Server - It would be nice if I could have a server that reached out to my workstations and backed up their My Documents/Desktop folders.

Torrent Server - I would like my server to handle all my Torrent needs.

---

### Post by craigp84 on 2009-12-14
Hi,

Yes, ubuntu can do all of your listed tasks but it will involve some configuration / integration effort on your part to make it all work. I'm not aware of any out of the box solutions for what you're after or i would recommend one if i knew of it.

1) Dedicated File Server - This is reasonably trivial to implement, it just depends how polished you want this to be. For a small userbase, I'd probably setup 2 shares -- one the repository with all the files, which is readonly, and another the dropbox which is writeable. I'd probably just setup a cron job to poll the folder every minute in a small installation.

The script would use the rsync command to move the files from dropbox to the shared dir, refusing to overwrite files which already exist, and deleting files from dropbox once successfully in shared dir (i.e. no shared dir is full situations before deleting the source file). Optionally you could tack on extra logic here such as ensuring .mp3s are meta-tagged etc.

For serving up files to PS3 there's a few DNLA servers out there, some are briming with features like on-the-fly transcoding so you can store your files in one format but ensure they're transcoded to a PS3 compatible format when needed.

As a side note, my experience of the PS3 DNLA client is it's only mediocre. If you have even a semi-sizable music collection it's not all that comfortable a client to use.

2) This is all v common, just google this one. vsftpd is the name of a well proven FTPd server.

3) Not sure what PING is, but guessing it's similar to CloneZilla, this is trivial to setup and only requires a writeable samba share or ftp account to transfer the backup to or read it from in case of a restore.

4) Yep, easy stuff, just depends how far you want to go, you could implement bacula or something like that to backup all your windows / linux / mac clients, then maybe even export read only, hourly snapshots back to the clients for fast / simple file restores.

I call it a restore server rather than a backup server, i find the subtle change of mindset helps me see the cracks in implementations.

5) Trivial stuff, just google this one.

Hope it helps

---

### Post by toddedw on 2009-12-14
> **craigp84 said:**
> Hi,
I'm not aware of any out of the box solutions for what you're after or i would recommend one if i knew of it.


Actually, FreeNAS will do everything that he just mentioned OTB. Not dissing Ubuntu because I'm a huge fan, but for ease of setup I think FreeNAS would be the way to go for this one.

---

### Post by Xiuh on 2009-12-14
I'd suggest you scan the index page for the official 9.10 Ubuntu server documentation. The number of compiled packages for an Ubuntu server is going to have about anything you want. If it's not, compiling the source is usually straight forward enough. So far as using server with a desktop GUI, it's certainly possible to do, but highly discouraged. I think I did that a few times myself before I learned my lesson. Anyways, you might look at Xumbuntu if you're looking for a desktop view and server. I believe they have setup Samba and LAMP to fit with it.

---

