---
title: "Ubuntu Server backups"
date: 2010-11-30
forum: Server Platforms
---

### Post by smileybri on 2010-11-30
Hello!

I have been asked to get up to speed on an Ubuntu file server that is being used in a Mac graphic design shop. I was able to access the server from another station via SSH and I can see the two USB backup drives under a /media directory.

What I can't seem to tell is what program is doing the backups, what it's configuration is, how it is being scheduled. I am familiar with Linux in a Web Server environment and I looked in "crontab -l" for the user I was logged in as as well as for root but the cron is empty.

I have no documentation for the setup. I am not that comfortable with the CLI but I can get around a little. You might expect that I know only enough to navigate a file system, change permissions or ownership of files and follow directions to compile a program and install in place (all things one would do on a Web Server).

What are some things I could do to try and learn how these backups are being done, so that I can verify they are working as they are configured and make changes as needed?

How would any of you take over and get up to speed in such a situation?

Thanks!

---

### Post by ikonia on 2010-11-30
I would look on the backup drives at what format the backups where in, as this will give you an idea to the method being used to back up.

I'd look at the date stamps to work out if this was a regular job or a manual invoked one.

I would then work back, looking at the cron.weekly file for example depending on the date stamps.

---

### Post by smileybri on 2010-11-30
Thanks for your reply!

The data on the drives is folders and files. Not compressed or in file format. One of the drives seems to have all of the newer data on it, while the other is older data, but the business owner thought they were both supposed to be the same. 

I can tell you that a file they had saved to the server on Friday was in the backup on Monday. I will check if that is the same day to day or weekly as you suggested.

This is one of those incidents where having a GUI is certainly preferred, I would think. At least one could poke around and look for applications that might have been used to do the backup, or something installed that is not part of the default install the might have been a find.

The CLI feels so like flying blind and guessing.

---

### Post by mdlueck on 2010-11-30
I have been using the xfs filesystem since 2004 which has built-in storage management tools (aka backup/restore). I highly suggest the combination.

We backup to USB HDD storage, which at present is why I am at ubuntuforums.org! There seems to be trouble attaching USB HDD's to 10.04.

Anyway, I have built with ooRexx a simple program to automate running xfsdump. It reads a simple config file, then builds the correct command line syntax to do each of the backup jobs specified. The script also creates a date-encoded directory on the USB HDD to store the backups in.

Throw-together code, but is most reliable.

---

### Post by rubylaser on 2010-11-30
I would guess that the mac clients are "pushing" the backups to the server, unless the server is also acting as a fileserver for the Macs. I would guess the Macs are using chronosync, or rsync via their crontabs to push to the Ubuntu server.  I'm not a big fan of this method, because you're not leveraging the coolness of Timemachine on the Macs.

If it's only acting as a backup server, I normally use one of my macs to iscsi mount the shares from the Ubuntu box and share them out via AFP for Timemachine.  Or, you could use netatalk and avahi to make the Ubuntu box a Timemachine share.  This way the users can restore their own files, and you can recover machines all with a nice GUI.

This is a great tutorial for the second option I mentioned.
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

I have an Ubuntu fileserver for our 20 person all Mac, Marketing Department.  If this didn't make sense, or if you'd just like to leave it the way it is, and understand it better, please let me know.

---

### Post by SeijiSensei on 2010-11-30
If the backups are happening via cron, here are the places to look:

/etc/cron.[hourly|daily|weekly]

/etc/crontab - basic file that cron reads each minute; by default it just calls the scripts in /etc/cron.hourly, etc.

/var/spool/cron/root - root's "personal" crontab

Maybe you should browse /var/log as well.  You might find a log file or two that can give you some hints.  All my backup scripts keep logs, but YMMV.

---

### Post by smileybri on 2010-11-30
Thanks. That gives me more than I had to go on prior to posting. I don't know when I will get in front of the server again, but will update this thread with my findings as well as more questions, no doubt. 

The Ubuntu server is a file server that the Macs store all the data they are working on. The server is doing backups to two USB hard drives - I just don't know how yet.

Thanks again, I will get back to you all when I have a chance to try your suggestions.

---

