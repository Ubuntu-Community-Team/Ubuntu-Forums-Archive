---
title: "Problem installing ubuntu server in vmware"
date: 2007-02-18
forum: Server Platforms
---

### Post by sfoo on 2007-02-18
Hi,

Trying to install Ubuntu 6.10 server (AMD64) in a VMWare Server VM.. 
During the install, I get as far it loading the installation components off the CD, then I get an error:

"Failed to load installer component.
Loading console-setup-udeb failed for unknown reasons. Aborting"

The CD works fine outside of VMWare server, so something isn't working properly under VMWare.. Any ideas?

Thanks,

Shawn

---

### Post by veloce on 2007-02-19
I assume you have checked that your hardware supports 64 bit vms?

[http://pubs.vmware.com/server1/wwhelp/wwhimpl/js/html/wwhelp.htm](http://pubs.vmware.com/server1/wwhelp/wwhimpl/js/html/wwhelp.htm)

---

### Post by PetePete on 2007-02-19
and i'm assuming you've set vmware to host the 64bit ubuntu server in vmware settings?

---

### Post by sfoo on 2007-02-19
Yes and yes.
I'm running an Athlon64 Dual Core which appears to be supported. Their 64-bit check utility claims that my cpu is supported also.

Just to sanity check, I tried installing the regular x86 version, but that fails with a similar but different error:
"Loading console-setup-fonts-udeb failed for unknown reasons. Aborting"

Also, interestingly, I was trying to install an Ubuntu 6.10 vm on a 6.10 host and 6.10 isn't in the supported guest or supported host list. If I try to install 6.06, a different component fails to load:
"Loading ethdetect failed for unknown reasons. Aborting"

I really hope it's not because I have 6.10 as a host..

---

### Post by sfoo on 2007-02-19
Interesting development:

After I get the "Failed to load installer component" error,  I then go to the "Check the CD-ROM(s) integrity" option. This tells me something has a checksum error, however the installation then continues and I get past the previous point. I get all the way past setting up the initial user and password and then it fails on "Install the base system" with an error:
"The debootstrap program exited with an error (return value 255)." 

If I then go and check the CD-ROM integrity, it tells me everything is good and valid.. (but something is obviously still failing to load properly).

---

### Post by Brazen on 2007-02-19
why don't you try installing from an ISO file?

---

### Post by veloce on 2007-02-19
Agree with installing from iso, much quicker as well.

What os is the host?
Are you using vm server 1.01 or 1.00? (Wasn't the bugfix something to do with 64 bit os?)

Sorry, we only seem to be giving things to check not solutions - you're either bleeding edge or obscure issue!

---

### Post by sfoo on 2007-02-20
Checklist is good.. :) 

Installing from the iso worked. Didn't occur to me since I had the cd handy.. It's not the actual cd either, because I've since done a successful install with it (outside of vmware obviously). So there's some problem with vmware and my cd drive?!

Thanks for all the help! Much appreciated!

Shawn

---

### Post by Brazen on 2007-02-20
I think I have run into this problem before.  A cd would work fine on physical hardware, but not through VMWare.  I just chalked it up to probably some sort of latency issue that the installer has trouble with.

---

