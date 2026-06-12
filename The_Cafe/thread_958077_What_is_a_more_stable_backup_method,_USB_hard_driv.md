---
title: "What is a more stable backup method, USB hard drive or FTP over a LAN?"
date: 2008-10-25
forum: The Cafe
---

### Post by pyjimbo on 2008-10-25
I am curious if backing up files over a LAN using the Filezilla FTP program onto an Ubuntu server running an FTP server is more or less stable than using a USB external hard drive.

Server:
Sony Vaio
600MHz Celeron circa June 2000
160 GB Western Digital Hard Drive circa Summer 2008

USB 2.0 external hard drive:
Apricorn Aegis 160 GB circa 2008

I am not liking plugging the hard drive in and out over and over, much easier to grab them off a LAN server but I wonder about stability and file integrity. You know how FTP requires ASCII or Binary for different files when they transfer. 

The server is old but its meant for testing Wordpress themes (and the like,drupal,phpBB) and storing files.

Thanks.

---

### Post by ciscosurfer on 2008-10-25
I would say that typically the shorter the distance it has to travel, the more reliable the data transfer.  I say typically because of course there are exceptions.  So, if you can backup to something that is directly attached versus traversing a LAN environment where there is potentially traffic, I'd go with the USB option.  The OS crashes less frequently these days when pluging-and-playing (haven't seen that happen in quite some time actually...some older Red Hat releases I used to work on were notorious for doing the ol' crash-n-burn).  

In terms of speed, I doubt you'll notice much of a difference though.  As far as reliability, I think either option should suit you just fine.  My preference would be the USB option.

If you're concerned about integrity, I'd say try it both ways and see which choice fairs better.  If you're just testing wordpress themes and nothing is mission-critical, I'd say it's at your discretion which way you go.

---

### Post by pyjimbo on 2008-10-25
So if I transfer a file through FTP as an ASCII but it was a file type that required binary haven't I ruined the file? This is the case on the web at least. I have to make sure that when the files are transfered they are done so through the appropriate methods.

---

### Post by ciscosurfer on 2008-10-25
I like to use FireFTP (addon for Firefox) when I want to FTP files.  It has nice options, like allowing it to automatically select between ASCII and Binary, file intergrity checking if enabled on your server, et al.  I would caution the general use of FTP over the WAN (though you didn't say anything specifically about doing this)...in this case, I would use SFTP or SCP.  Here's your bravery test: take a few files that you are willing to part with, try it a few different ways and see what works best for you :-)

---

### Post by grim4593 on 2008-10-25
Personally I prefer having something detachable like a USB external harddrive. There is less chance of your backups going wrong. You can't accidentally delete data from a drive thats not plugged in. If you have to plug in the drive manually, then you don't have to worry about an automatic cron backup script overwriting/deleting your files as you are trying to restore some files from the backup.

---

### Post by JohnFH on 2008-10-25
You don't need to use FTP when backing up over a LAN.  You could mount a network share (see sshfs) and use rsync to copy the files.  That's a much better method than ftp.  

There's a great post in the tutorial and tips forum on how to backup your system.

---

### Post by mips on 2008-10-25
> **JohnFH said:**
> You don't need to use FTP when backing up over a LAN.  You could mount a network share (see sshfs) and use rsync to copy the files.  That's a much better method than ftp.  

There's a great post in the tutorial and tips forum on how to backup your system.

+1 I would also use something like rsync

---

### Post by koenn on 2008-10-25
The thing with backups is that you want them to be there the day you really need them.
I don't know how robust external HDDs are these days - like, if you accidentally drop them on the floor, do they still work ? Do they survive being pushed aside while writing data ? Does the data in the disk survive such treatment ?
Also, I've had some experience with copying large amounts of data to USB disks - and they seem to choke on it, as if they can't handle large volumes at relatively high speeds.
A server doesn't suffer from all that.
I'd opt for the server, but realising that if the disk there breaks, your backup is out of the window. So you might want to consider a raid, or simply mirroring the backup to a 2nd disk in the server.

and +1 for rsync in stead of ftp or any other transfer protocol : reliable, efficient (incremental backups, ...), lots of options.

---

### Post by Dr Small on 2008-10-25
I back my data up to my server via SFTP or SCP, and it has always worked well for me. Besides, it's on the network, and easily accessible.

---

### Post by mips on 2008-10-26
> **koenn said:**
> 
Also, I've had some experience with copying large amounts of data to USB disks - and they seem to choke on it, as if they can't handle large volumes at relatively high speeds.



That I experience a lot. The problem lies with USB and not the disk itself. USB simply cannot sustain consistent high data rates, it chokes badly. Firewire & eSata would be a much better option than USB for external storage, unfortunately this is not implemented on all computers which is sad.

---

### Post by fatality_uk on 2008-10-26
rSync is superb.
Check out the examples here [http://samba.anu.edu.au/rsync/](http://samba.anu.edu.au/rsync/)
All you need!!

---

### Post by koenn on 2008-10-26
> **mips said:**
> That I experience a lot. The problem lies with USB and not the disk itself. USB simply cannot sustain consistent high data rates, it chokes badly. Firewire & eSata would be a much better option than USB for external storage, unfortunately this is not implemented on all computers which is sad.
glad to see that confirmed.
I found you can work around it by using something like
 rsync --bwlimit=20000 (KBytes/sec) 

Takes a while if your copying gigabytes of data, but it least it works. 
I use it to backup a backup server (while waiting for a tape-based solution to arrive)

---

### Post by mips on 2008-10-26
> **koenn said:**
> glad to see that confirmed.
I found you can work around it by using something like
 rsync --bwlimit=20000 (KBytes/sec) 

Takes a while if your copying gigabytes of data, but it least it works. 
I use it to backup a backup server (while waiting for a tape-based solution to arrive)

I'm actually keen on hacking my WD external so I have direct access to the Sata port while still keeping the USB port. Should have initially purchased a drive with extra firewire & esata though.

---

### Post by billgoldberg on 2008-10-26
> **pyjimbo said:**
> I am curious if backing up files over a LAN using the Filezilla FTP program onto an Ubuntu server running an FTP server is more or less stable than using a USB external hard drive.

Server:
Sony Vaio
600MHz Celeron circa June 2000
160 GB Western Digital Hard Drive circa Summer 2008

USB 2.0 external hard drive:
Apricorn Aegis 160 GB circa 2008

I am not liking plugging the hard drive in and out over and over, much easier to grab them off a LAN server but I wonder about stability and file integrity. You know how FTP requires ASCII or Binary for different files when they transfer. 

The server is old but its meant for testing Wordpress themes (and the like,drupal,phpBB) and storing files.

Thanks.

Backup up to an external usb drive will be a lot faster. 

Or do the small backups over ftp and back up to usb once a month or something.

---

### Post by koenn on 2008-10-26
> **mips said:**
> I'm actually keen on hacking my WD external so I have direct access to the Sata port while still keeping the USB port. Should have initially purchased a drive with extra firewire & esata though.
Hardware hacking isn't really my thing, I always end up breaking stuff so it becomes a hobby I can't afford :)

---

### Post by Trail on 2008-10-29
+1 SCP, RSYNC
-1 FTP. Too annoying (and old I might add).

---

### Post by pyjimbo on 2008-10-30
> **billgoldberg said:**
> Backup up to an external usb drive will be a lot faster. 

Or do the small backups over ftp and back up to usb once a month or something.

This is what I planned on doing, having a backup of the backup. I have also learned that lowering my consumption of downloadable content makes things easier. You know don't create work for yourself.

---

### Post by pyjimbo on 2008-10-30
Great responses from everyone. I'll save this thread and refer to it in the future about rsync and SFTP, great stuff. Thanks.

---

