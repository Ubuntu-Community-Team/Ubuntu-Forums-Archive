---
title: "Simple command line backup"
date: 2006-11-29
forum: Server Platforms
---

### Post by MikkyX on 2006-11-29
Hiya folks,
Recent Ubuntu convert here with a question about the best way to go backing up my websites etc.

At our office we have a 300gb USB HD connected to our Windows 2000 development server, which is used to backup all our websites from the Windows box AND it's also meant to be backing up the Linux box as well.

At the moment I'm using a tar.gz file of the /var/www folder and copying it across manually from within Windows having mapped a network share to our drive. I do it manually because our automated backup software on Win2k wouldn't, for some reason, copy the files every time it was meant to.

What I need to do (and I only have the command line to play with here) is .tar.gz the websites, mysqldump all the databases, and then copy this lot onto the USB HDD (which is mapped as a network share) on a nightly basis. The USB drive is NTFS, support for which I believe is still quite shaky on Linux - so I'd rather create the files on Linux and then use Windows for the copy *if I can get it to work reliably*.

Anyone got any suggestions? Cheers. :)

---

### Post by ciscosurfer on 2006-11-29
Welcome to the Forums!

You can try adding support on your Ubuntu drive for read/write access to your NTFS drive using either NTFS-3g or fs-driver ([this page may be of assistance]("http://ubuntuforums.org/showthread.php?t=217009"))  This will allow you to write to the networked drive.

Otherwise, you can backup your web site yourself onto a rewritable disc and use it over and over again (although, rw sort of bite...write once media is usually recommended).

Another option might be to compress your files and your mysqldump and email it to yourself (like gmail -- either as an attachment or by using gspace [converts your gmail space to storage space]).

Yet another option might be to simply backup your own files on your Ubuntu box using the backup and restore software that you can grab from the repositories.  This way you'll have your own backup.  This works well on 2 fronts:[LIST=1]
[*]If the networked drive fails for some reason, you'll have your backup handy
[*]You won't have to consider the first option above regarding drivers, etc., to allow for read/write access to the NTFS-networked drive.[/LIST]As a side note, what backup solution is your company using at the moment.  There are others out there that seems to take all filesystems into account (although, off the top of my head, I can't recall what they are).

EDIT: Have you tried to .zip your .tar.gz file yet?  Perhaps the Win2K software doesn't like the .tar.gz foramat.  I don't know if this will work well or not, but It's worth a try.

---

### Post by elst on 2006-11-29
If the Windows server offers access to the USB drive as a network share then you can simply run a shell script on the Linux box that copies files to the share over a SMB/CIFS ("Windows File Sharing") connection. The smbmount and smbclient utilities enable a Linux system to do the actual file uploads to a Windows share. Any script in /etc/cron.daily/ will automatically be run at 4am each day.

The NTFS support in Linux really only matters if you directly attach a drive to the computer. In this case the Linux box is just passing files to the Windows server, and it is Windows that reads and writes to the USB drive.

---

