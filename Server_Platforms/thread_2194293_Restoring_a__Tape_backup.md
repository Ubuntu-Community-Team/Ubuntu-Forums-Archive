---
title: "Restoring a  Tape backup"
date: 2013-12-17
forum: Server Platforms
---

### Post by devin0 on 2013-12-17
Ive got a couple of tape on hand used to backup files from our old server, and im looking to get the files off. 


I am unsure of how the previous admin went about backing things up, or as to what software was used. All i know is a linux machine was the main machine used, and unix directories are listed on the tape label.

I have tried using "tar -tvf /dev/st0" as well as "tar -tzvf /dev/st0" to get a listing of whats on there, to no luck, i get enexpected end of stream io errors.
Mabe tar wasnt even used? How do i determine what was used to back up the tape?

Any help is very much appreciated.

---

### Post by SeijiSensei on 2013-12-17
Let's see if you can talk to the drive.

Linux has a command called "mt" that lets you interact with tape drives. Try a retensioning first:

```
sudo mt -f /dev/st0 retension
```

The tape should spin out to the end of the reel then rewind.  If that works, at least you know that you have a functioning drive that Linux can talk to.

mt has commands that let you move through the tape one file at a time.  You might also see what the status command reports. See "man mt" for command details.

You should probably run all your tape commands with "sudo" to avoid any permission issues.

---

### Post by devin0 on 2013-12-18
I tried the command nothing happens. It finishes instantly and no activity with the tape drive. I am able to go to the end of media and rewind it though.
The drive I'm using is known working, I used it just earlier today to backup / restore data with tar.
I know to run all the tape drive related commands as root.
Here is the output of the mt status command.
```

root@fcarray:~# mt -f /dev/st0 status
drive type = 114
drive status = 620757504
sense key error = 0
residue count = 0
file number = 0
block number = 0

```

Is there any way to do a raw dump of the tape and work from that? I worry that all the seeking around the tape with mt will make it go bad, and it has to have been sitting for like 5 years without use.

---

