---
title: "Server on ram?"
date: 2008-03-10
forum: Server Platforms
---

### Post by pixtor on 2008-03-10
Hey!

Is it possible to use my ram as the system drive on Ubuntu Server 7.10?
I would like it to:
*Boot of a HDD and load the system into ram.
*turn of the HDD
*check for changes in the filesystem every hour and store these to hdd
*in case of a normal shutdown, write all changes to HDD

This would be great if it could be done somehow :)

thanks in advance!

---

### Post by Rhubarb on 2008-03-10
This is a good thread to start off with:
[http://ubuntuforums.org/showthread.php?t=89490](http://ubuntuforums.org/showthread.php?t=89490)

Once you've set up your ramdisk or tmpfs mount, you'd need to make up some scripts that execute on startup (to mount the ramdisk, etc).
You'd also need a script to run as a cron job to synchronise the ramdisk with the hard drive.
I can't really help you much more here as I don't have a need to do this myself.

I don't think you'd be able to turn off the hard drive, and I don't think you'd be able to mirror the entire file system over to the ramdisk, only a directory or a directory branch.

Hope this gets you started along the way.

---

