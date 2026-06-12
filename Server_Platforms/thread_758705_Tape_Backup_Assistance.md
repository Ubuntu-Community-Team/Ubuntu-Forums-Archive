---
title: "Tape Backup Assistance"
date: 2008-04-18
forum: Server Platforms
---

### Post by Chent on 2008-04-18
Hello All,

I recently installed 7.10 server edition on a Dell server with a DAT72 tape drive, and I can't seem to get the tape drive to work.

I've done a bit of research, and from the server I can see the hardware is detected but I can't seem to configure it and I just don't have the time at this point to keep trying :)

I was wondering if someone in the community would be willing to help out with getting the drive working and setting up a backup schedule.

I'm willing to compensate for any help with this!

Thanks,

Paul

---

### Post by HermanAB on 2008-04-18
SCSI tape?

Does the SCSI driver show up:
$ lsmod

Does the 'tape' device show up in /dev?
$ ls /dev

Are the 'mt' magtape utilities installed?

Cheers,

Herman

---

### Post by mmichalik on 2008-04-18
Here is a good website that might help out as well.

[http://nic.phys.ethz.ch/readme/80](http://nic.phys.ethz.ch/readme/80)

It lists a lot of the CLI commands to use with your tape drive.

---

### Post by Chent on 2008-04-19
Hi Herman, thanks for the reply.

I believe the SCSI driver is loaded, the following shows up from lsmod:
aic79xx               282072  0
scsi_transport_spi     25344  1 aic79xx

The 'tape' device does show up in /dev as well.

I also installed the mt utilities as well.

It seems as though all the pieces are there, I just don't know where to turn next for setting up a simple daily backup.

Will something like bacula work?

Thanks for the assistance!

PP

---

### Post by koenn on 2008-04-19
you can use 'tar" to write to a tape
here's a simple example
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm#tape](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm#tape)

for a daily backup, you'd just create a cronjob around tar.

that should keep you safe will you look for a more elaborate solution, should you still need one.

---

### Post by Chent on 2008-04-20
Hi there,

So based on what has been posted here so far, the tape drive should just work if I use some of the commands provided here?

---

### Post by ikonia on 2008-04-20
dat drives will show up normally as "st" devices in /dev

so if its only 1 device on the card then an 

"mt -f /dev/st0 status" should show if the device is there and it's current status.

from that you should be able to write to the device using tar/cpio/backup software such as amanda.

---

### Post by Chent on 2008-04-21
I'd like to thank everyone again for the assistance!

Here is the result of the mt status command - does it look OK??

[I]administrator@stella:~$ sudo mt -f /dev/st0 status
SCSI 2 tape drive:
File number=0, block number=0, partition=0.
Tape block size 512 bytes. Density code 0x47 (TR-5).
Soft error count since last status=0
General status bits on (41010000):
 BOT ONLINE IM_REP_EN[/I]

I tried the following command as well:

*sudo tar czf  /dev/st0 /home/administrator*

and then

*sudo tar -tvf /dev/st0*

And I got a list of files from tape! Success!

The last piece of the puzzle would be to get a proper program in place. Is there a program that anyone could recommend that would allow ease of backup administration for a non-technical user, ie with a GUI and no CLI needed... possibly with email notifications of success/failures...

I noticed that webmin has a module for Bacula, this would be ideal - any other solutions I should be aware of?

Again, I'd like to thank everybody for helping me get this to work!

---

### Post by koenn on 2008-04-21
Bacula looks like a good backup program, although maybe a little overkill for a simple file backup of 1 PC.
I had a look at it once but my 6.06 couldnet provide all dependencies for for the latest Bacula, and the older Bacula versions seemed buggy. 

I've come across quite a few backup questions and sollutions on these forums, maybe you just have to do a search
[http://www.google.be/search?q=site%3Aubuntuforums.org+backup&btnG=Google+zoeken&meta=](http://www.google.be/search?q=site%3Aubuntuforums.org+backup&btnG=Google+zoeken&meta=)

---

