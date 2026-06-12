---
title: "FTP/Share permissions issue"
date: 2008-11-26
forum: Server Platforms
---

### Post by Asharru on 2008-11-26
I have an Ubuntu 8.10 headless server setup on my home network with the following services installed/running:
proftpd, postfix, mysql, apache2, php, samba, squirrelmail, phpmyadmin, and all the requirements for each.

Mounted on the server are two WD NAS drives, running an ARM9 based Linux OS.

I can send/receive email fine with squirrelmail (web) and/or outlook (windows).
I can browse the web pages no problem.
I can create mail users via phpmyadmin (web) just fine.
I can ftp into the server.
I can connect to the shares from Windows.

But I cannot get the two NAS drives to auto-mount on boot. I tried entering them into fstab, but they fail to connect on a restart. Currently I have written a script that I run after the server is up:

```

mount -t cifs -o username=ftp,password= //192.168.10.12/PUBLIC /home/ftproot/downloads/nas1
mount -t cifs -o username=ftp,password= //192.168.10.13/PUBLIC /home/ftproot/downloads/nas2

```

Any help with how I should enter them into fstab would be great.

I seem to have a problem being able to get Adobe Dreamweaver to upload the web files to the /var/www folder on the server from Win XP Pro, even though the "test connection" in Dreamweaver comes back as a success.

Also, I have the accounts/passwords from the Windows boxes entered into passwd, added to the ftp-users group. I can browse/read all the directories and files in the ftproot root folder (including the NAS drives), but I cannot write to them.

What I am hoping to do is have read/write permissions from authenticated users regardless of connected location and read only permissions to all directories for non-authenticated users except to the 'incoming' folder. Any ideas on how to get this working would be great. If you need to know what I have entered in specific config files, just let me know and I will post them here (not sure which ones you would need to see).

================================================================
Network Computers:

Ubuntu 8.10 server
   1st HD partitioned to /, swap, /home
   2nd HD single partition, mounted to /home/ftproot/downloads/Storage

WD NAS #1
   Mounted to Ubuntu server as /home/ftproot/downloads/nas1
WD NAS #2
   Mounted to Ubuntu server as /home/ftproot/downloads/nas2

Windows XP Pro/Vista Dual-boot box
Windows XP Pro box
Mac 10.3 box
3 Windows XP Laptops

---

### Post by Asharru on 2008-11-27
I have the drives defined properly in fstab so they are auto-mounting now, but still having permission issues with the shares/ftp and webroot.

Anyone have any ideas what I need to change, or perhaps have a better idea of how to set it up so that anonymous internet users can only read the shares (except for an upload dir that they will have write access on) and authenticated users on the private network will have full access to the shares/ftp (for file management) and the webroot (for remote updating of the web page).

Has anyone had any success in sharing NAS drives in Ubuntu server and then adding those shares to an ftp server?

---

### Post by Asharru on 2008-11-27
After doing some more web searching, I have seen a lot of positive talk about pureftpd. I am re-creating the server with pureftpd on a laptop for now (so as not to interrupt the actual server).

Still would be willing to hear any advice on how to properly set this up, I have seen dozens of tutorials, but nothing that really deals with my setup.

---

### Post by andguent on 2008-11-29
I hit this wall once before, and I think I know where you are getting stuck. Most to all FTP daemons don't let their users jump through mount points to other file systems, or interact with symlinked directories. It actually has to do with the file system permissions, not the FTP daemons.

Read the link below, and pay special attention to 'mount --bind' sections, as I think that is what you need to do.
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html)

I might recommend:
[code]
mount -t cifs -o username=ftp,password= //192.168.10.12/PUBLIC /mnt/nas1-public
mount -t cifs -o username=ftp,password= //192.168.10.13/PUBLIC /mnt/nas2-public

mount --bind /mnt/nas1-public /home/ftproot/downloads/nas1
mount --bind /mnt/nas2-public /home/ftproot/downloads/nas2
[code]

See /etc/rc.local for a good generic place to put startup scripts. The real test is, can FTP users save files anywhere at all? Take the NAS connection out of the equation and verify your config and permissions are ok.

---

