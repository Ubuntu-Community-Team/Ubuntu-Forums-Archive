---
title: "It looks like someone was able to access my ftp server"
date: 2015-05-22
forum: Server Platforms
---

### Post by killercal on 2015-05-22
Hello all,

I'm new to Ubuntu server and I've setup my vsftpd.  I'm in the works of hardening but was looking at my logs with sudo vi /var/log/auth.log and saw that someone tried to accessed my server via FTP.  These lines were in my log...

vsftpd: pam_unix(vsftpd:auth): check pass; user unknown
vsftpd: pam_unix(vsftpd:auth): authentication failure; logname= uid=0 euid=0 tty=ftp ruser=anonymous rhost=82.221.105.6
vsftpd: pam_winbind(vsftpd:auth): getting password (0x00000388)
vsftpd: pam_winbind(vsftpd:auth): pam_get_item returned a password



Does this mean that someone gained access?

I looked up the IP address and its from Iceland, I'm in Canada.  That and the time stamp is at 4:50am (I was sleeping at that time!)

---

### Post by TheFu on 2015-05-23
I don't know. Are there other messages nearby?
"anonymous" means someone is just trying to connect to an open ftp site. The userid=0 stuff seems strange. Anonymous FTP has been around since the beginning of the internet for people to download free stuff.  Anonymous FTP is how companies share downloads. Those are really the only people who should till be using plain FTP - people who want to share everything with everyone in the world, no strings.

However, very few people should still be using plain FTP anymore. It should have been killed off in the early 1990s. If you only allow authenticated connections, [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) Use sftp, run fail2ban. Use keys only, never passwords. If you use passwords, you've already lost.  There are great sftp clients for every networked OS out there.

---

### Post by killercal on 2015-05-23
I do use keys to connect, but don't think its 100% completely setup as I can still access the FTP without the key but ssh needs the key.  there isn't really anything around those lines that look suspicious, just these lines...
CRON[24343]: pam_unix(cron:session): session opened for user root by (uid=0)
CRON[24343]: pam_unix(cron:session): session closed for user root

---

### Post by TheFu on 2015-05-23
root running cron stuff isn't funny, if it makes sense for root to run at those times. Check the 3+ different crontab locations.

Please re-read the link provided around the dangers of running plain FTP. If you don't intend for everyone in the world to use your FTP server - please use sftp (which is part of the openssh-server pkg) and remove/purge/deinstall vsftpd.

---

### Post by Lars Noodén on 2015-05-23
> **killercal said:**
> I do use keys to connect, but don't think its 100% completely setup as I can still access the FTP without the key but ssh needs the key.  there isn't really anything around those lines that look suspicious, just these lines...
CRON[24343]: pam_unix(cron:session): session opened for user root by (uid=0)
CRON[24343]: pam_unix(cron:session): session closed for user root

The link above posted by TheFu is worth reading.  What are your goals with FTP?  It is unlikely that you need or even want  it.  If you have SSH then you already have SFTP as part of the deal and can use that for secure file transfer, something FTP cannot do.

The CRON entries are from cron running.  It's normal and nothing to do with remote access.

---

### Post by killercal on 2015-05-24
Ok,  I will give that article a read when I get a chance later today.

As for the FTP, I need to be able to transfer files between a couple of computers for business purpose.  I would like to have is as secure as possible, I will look into the sftp with the SSH.

Thanks,

Scott

---

### Post by SeijiSensei on 2015-05-24
If you're supporting Windows client, use WinSCP.  On the server install the openssh-server package if you haven't done so already.

On Linux clients, you can often use an "sftp://" or "fish://" URL in the address field of file managers like Nautilus or Dolphin.

---

### Post by TheFu on 2015-05-24
For moving files securely between computers, **sftp**, **scp**, and **rsync** are the normal "secure" methods.  I'm assuming this isn't for backups, since there are better tools for backups that are also secure.

 Sometimes we don't actually need to transfer the files, they just need to be available from other systems. If the computers are on the same LAN, another alternative is **NFS with Kerberos**.  It really comes down to the type of use the file transfers are needed for.

---

### Post by SeijiSensei on 2015-05-24
Personally I'd rather use [sshfs]("https://help.ubuntu.com/community/SSHFS") with keys instead of futzing with Kerberos.  One of my cloud servers mounts directories from another server at a data center across the country using sshfs, and it's quite reliable.

---

### Post by killercal on 2015-05-24
I will be using Windows machines to upload/download files from my Ubuntu server.  One person does have an Mac, but I'm sure that will still work?

The FU, I haven't looked into backing up files, but what do you suggest for doing that?

---

### Post by Lars Noodén on 2015-05-25
On OS X you have Cyberduck and FileZilla in addition to the text based clients.  For Linux the choice includes Nautilus, Thunar, Dolphin, PCManFM and FileZilla in addition to the text based clients.  Those still on the other OS have WinSCP and FileZilla.  They all will work to connect to your SSH server and transfer files back and forth.

---

### Post by TheFu on 2015-05-25
> **killercal said:**
> I will be using Windows machines to upload/download files from my Ubuntu server.  One person does have an Mac, but I'm sure that will still work?

The FU, I haven't looked into backing up files, but what do you suggest for doing that?

The official stance: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
I use rdiff-backup after trying many different solutions over the years. [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)  None are perfect.  **duplicity** may become perfect, someday. I don't like the way it chunks files together and restoring 1 file is more than a copy and end-users cannot self-serve the restore. I don't have any use for a GUI backup too. crontab doesn't like GUIs and backups that aren't automatic are a total FAIL in my book.

Make certain whatever tool you chose captures permission changes over time, many solutions do not. A mirror is NOT enough for a backup. You need to be able to restore yesterday, last week or last month and don't want 50x the storage used if you keep 50 days of backups.  For 60days of backups, I generally see 1.15x the original storage.

Can't help with windows - don't use it much. Find it extremely frustrating when forced to use it.

---

### Post by killercal on 2015-05-25
> **TheFu said:**
> 

Can't help with windows - don't use it much. Find it extremely frustrating when forced to use it.

Thanks for that information!

As for the Windows, I have to used it for the software I'm using for work.  I tried to install some of them in Linux Mint and use WINE but it would keep crashing.

---

### Post by TheFu on 2015-05-25
> **killercal said:**
> Thanks for that information!

As for the Windows, I have to used it for the software I'm using for work.  I tried to install some of them in Linux Mint and use WINE but it would keep crashing.

I use windows for 4 specific things.
* quicken (no viable alternative)
* video editing (really just commercial removal)
* tv recording (7MC just works)
* hidef video recording (presentations/other inputs) - HW drivers only available for Windows.

and about once a year, Visio.  For about a decade, used visio almost daily for my job. Haven't found any alternative for it either, but it is less and less important for my zero-job life.

I use VMs for most windows software - except the hidef video recording. That only works on 1 laptop - which must be portable.

---

### Post by mastablasta on 2015-05-25
> **TheFu said:**
> . I don't have any use for a GUI backup too. crontab doesn't like GUIs and backups that aren't automatic are a total FAIL in my book.


Some GUI backup tools use GUI just to help you setup a script and then add it to chron. still beats CLi as far as "user friendliness" goes.  Areca for example will create commands (kind of batch job) and then all you do is add that file to Windows Task scheduler or what is it called. and that's it.

I kind of like it as it will transfer compressed file or uncompressed ones - e.g. jpeg mp3 etc. are already compressed (much easier to restore).

---

### Post by TheFu on 2015-05-25
> **mastablasta said:**
> Some GUI backup tools use GUI just to help you setup a script and then add it to chron. still beats CLi as far as "user friendliness" goes.  Areca for example will create commands (kind of batch job) and then all you do is add that file to Windows Task scheduler or what is it called. and that's it.

Isn't "chron"  different from "cron"?  1 is for time synchronization ... on another OS?

The main issue I have with GUI backup tools, is the lack or difficulty to get complete flexibility for what is backed up.  If you have a long list of *include* and longer list of *exclude* regex, having a backup script just makes more sense.  Plus, GUIs don't run on servers without adding bloat, sucking disk space, and hogging RAM.  If you have 1 server, perhaps that doesn't matter much. When you have 50 - 10,000 servers it is a completely different story. The difference in cost is significant.  If you ever WANT to run servers (and make a living at it), learn the script method. Dump the GUIs.  Of course, if you plan to have 1 "server" at home, it doesn't really matter, provided it works.

---

