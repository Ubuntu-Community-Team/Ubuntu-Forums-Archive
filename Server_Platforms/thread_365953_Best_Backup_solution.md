---
title: "Best Backup solution?"
date: 2007-02-20
forum: Server Platforms
---

### Post by tocleora on 2007-02-20
Sorry this is indepth but I like to provide as much info as I can when asking for help to make it easier.

My boss bought 2 300GB external drives we are going to use for backup yesterday.  Here's my setup:

1 Windows XP "Server" (probably should be backed up)
1 Windows 2000 "Server" (probably should be backed up)
1 Fedora Core 4 Server (primary focus for backup, web server and mysql data)
2 FreeBSD Servers (secondary focus for backup, company file storage)
3 Ubuntu Servers (not being used but more than likely will need to be backed up sooner than later)

I will be creating a bash script on each or one Server that will do nightly and/or weekly backups.  Unless someone can suggest a better solution.

We initially put the drives on the Windows XP Server, which formatted the drives to NTFS.  I shared one of the drives and was able to map it from the Fedora Core 4 in Gnome but don't know how to call that from the terminal.

I then moved the drives to the Fedora Core 4 Box but Fedora Core 4 won't mount the NTFS drives.  Attempted to download ntfs/fuse but don't want to spend a lot of time on that if it's not the best solution, but failed a quick install and configuration attempt.  Installed gparted but don't know if ext3 will support 300GB and have had bad luck with gparted in the past so hesitant to use it.  Since the primary backup is there and the 2 FreeBSD boxes already have samba on them (from which I can see the necessary files from the FC4 Box) I thought this would be the easiest/quickest solution.  But I might still run into the same problem of not being able to see the FreeBSD shares from the terminal.

I could put them on one of the Ubuntu servers which I figure will be easier to configure, but then I'm guessing I'd have to set up Samba on the Fedora Core 4 Box so it can see it.  Or I guess I could set up Samba on the Ubuntu box and Fedora Core 4 could see *it*.  I'm concerned with security issues doing that, but if that's how I need to do it...  All of our servers except for the Windows XP Server (which has proprietary software on it *sigh*) will be converted to Ubuntu or Debian eventually (unless someone from this group tells me I shouldn't for some reason) so something else to consider.

So I'm ultimately wide open to suggestions at this point.  Given the specs of our setup, how would you recommend we set this up?  TIA...

---

### Post by Brazen on 2007-02-20
In a pinch, I can figure out the command line jargon to work with partitions, but frankly I use Webmin 99.999% of the time to do any partition configuration.

I would suggest putting the harddrives on your file server, format them with Ext3 (it will theoretically handle up to 32TB partitions, but I've personally only used up to a 2 TB partition), then share them between linux/bsd servers with NFSv3.

Also, have you thought about how you are going to backup your MySQL databases?  You can not just file copy a running MySQL database.  You will either have to quiesce and snapshot the disk (which means it had better be on LVM volumes), or you can probably create something like a mysqladmin script to export the databases to seperate files.

---

### Post by tocleora on 2007-02-21
Yeah I was already exporting the data from the mysql database, I do a full export on Monday nights and then differencial exports the rest of the week.  I'll just move these exported .sql files to the new hard drive once I get them in place.  Ok, yeah if ext3 will handle 300GB then it would be smarter to format those to ext3 since we're for the most part Linux based.  I didn't know you could do anything partition related with webmin, so I'll check that out! Thanks!

---

