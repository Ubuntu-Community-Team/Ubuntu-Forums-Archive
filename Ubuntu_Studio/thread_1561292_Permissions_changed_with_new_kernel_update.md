---
title: "Permissions changed with new kernel update"
date: 2010-08-26
forum: Ubuntu Studio
---

### Post by stinkeye on 2010-08-26
Hi,
I installed ubuntu studio yesterday and all was working fine using the 
2.6.32-21-generic kernel.
Tested Jack with Rakarrack. Plugged the guitar in. All good.

Then I ran update manager which installed about 200mb of updates
including the 2.6.32-24-generic kernel.

Now when I login I can't restart or shutdown, can't mount internal drives
and I cant even authenticate Users and Groups to check my permissions.

If I restart using the previous 2.6.32-21-generic kernel all is ok again.

I'm running the 2.6.32-24-generic kernel on my other computer in a standard
Ubuntu install and haven't had these problems.

Is there something left out of the ubuntu studio iso that would cause this.

---

### Post by bluesscream on 2010-08-26
I never was lucky with ubuntustudio and kernel 2.5.32-24, not geneneric nor preempt. Not even my soundcard was found. Of actual 2.6.32 updates only 2.6.32-24-lowlatency  from falkTX ppas reliably did the job for me. I'd liked to report the bug, but in the moment I have no virginal install, only heavily customized ones, so that my reports would be rejected. I guess there are version incompatibilities related to alsa and firmwares since 2.6.32-22. Newer kernels (2.6.33,34,35,36rc series) more or less all support my hardware, jackd in realtime mode, rakarrack etc.

---

### Post by stinkeye on 2010-08-27
I've got it booting with the 2.6.32-24-generic kernel now.
During install it couldn't configure my wireless network so I chose to skip that part.
I think this may be where certain packages aren't installed.
I have to blacklist the rt2800usb driver, for my wireless to work.

I had to install a couple of packages and dependencies to do with policykit and network-manager from the live cd. /media/cdrom0/pool/main/n/network-manager-applet

Still can't activate compiz even though in jockey it shows 
the current nvida driver is installed.

Compiz is running on the same machine in an Ubuntu install.
Would be nice to be able to rotate the cube to different music
applications but seeing as the sound works properly with Jack
I'll just have to use Metacity. 
Is there a package that is needed for nvidia drivers when you install a new kernel?

 


.

---

