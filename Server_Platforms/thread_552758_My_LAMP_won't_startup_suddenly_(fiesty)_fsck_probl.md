---
title: "My LAMP won't startup suddenly (fiesty) fsck problems?"
date: 2007-09-16
forum: Server Platforms
---

### Post by kokoroexchange on 2007-09-16
Hello everyone,

I have been running a LAMP on Feisty for about 6 months now with no problems.  

I restarted my machine today after shutting it down to move it.  When I restarted I got a message saying that the sda3 device had been mounted 35 times without being checked and then got a message that a check was being forced.  It appeared that the system was checking my hard drive.  The results now have me in a frantic panic.  After about 38 lines of what appear to be errors (inodes & blocks) I get a message saying that fsck is going to be run automatically but then an error following that saying that the system could not run it automatically and prompting me to run it manually.  The system then boots into maintenance mode and I get several lines of errors of something about apt-get not existing and prompting me to install it.

As a fairly green novice at trouble shooting I am lost.  And I need this system up yesterday!!!  Ahhhh, what to do :-(

Can anyone help?

Jason

---

### Post by kokoroexchange on 2007-09-16
Adding to my original post:

I can now run fsck and get a screen full of 'exceptions' and 2 errors.  The errors are the same but occur at different locations/blocks:

One at 840.737861 
The other at 869.065776

and the error is

Buffer I/O error on device sda3, logical block 5406805

Then I have an option to ignore the error with the following prompt

<y>?

If I type y then I get an option to rewrite with the same prompt

<y>?

If I type n then fsck is exited and I get the following line

Error while scanning inodes (number) can't read next inode.

???

Jason

---

### Post by kokoroexchange on 2007-09-16
Responding to myself again :-)

I ended up running fsck and responding y to the ignore error prompt and n to the rewrite prompt for all errors.

Was then able to finish the fsck process and restart.  I'm back up and running but still a little nervous about the problems found by fsck and what I should do about them if anything??

Definitely will be backing up my webserver content on a very frequent basis (database too) until I feel more comfortable about the situation.

Jason

---

### Post by cdenley on 2007-09-17
> Buffer I/O error on device sda3, logical block 5406805

My guess would be a hardware problem. I would test the memory using the ubuntu install cd, then if there are no errors, backup and replace the hard drive. Back it up on another Linux machine using dd. If dd fails at the same position all the time, you need to use the conv=noerror,sync options. This replaces unreadable blocks with null bytes. If it fails intermittently regardless of position, then just use conv=noerror. This will try reading a block over and over again until it succeeds. If you don't get any errors, it probably isn't the hard drive.

---

### Post by kokoroexchange on 2007-09-17
Thanks cdenley,

You are definitely way beyond me in Linux/Ubuntu knowledge but I think I can follow your instructions/advice if I do a little reading.  I'll work on it (carefully) and see if I can get to the bottom of the issue.

Jason

---

