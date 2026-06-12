---
title: "server OS to fit on a 540 MB hdd"
date: 2007-10-09
forum: Server Platforms
---

### Post by Mr.Ganja on 2007-10-09
I have a server club at my high school, for the fun of it and I have a very old machine, 500mhz, 128 MB ram, and the biggest problem a 540 MB hard drive. I just want this to be a proxy server but I do not know what OS to put on it. I tried Ubuntu Server 6.06 LTS, the Install failed because there was no more room on the drive. 
My question is: is there an OS that will fit on this computer? Or is there a way of making Ubuntu run on it. I kind if want the latter because I want Ubuntu on all the servers.

Thanks in advance, 

There is no real reson to have proxy server on it but I just want to make every thing I can think of in order to learn how to manage servers. 

A gui would be nice but I am not hoping for much in this area.

---

### Post by HermanAB on 2007-10-10
About the only thing that will run on that is Puppy Linux.  If Puppy won't install, try Damn Small Linux.

Cheers,

H.

---

### Post by netlogic on 2007-10-10
List of mini distros
[http://www.linuxlinks.com/Distributions/Mini_Distributions](http://www.linuxlinks.com/Distributions/Mini_Distributions)

DSL & Puppy are tiny efficient DesktopOS.I believe they don't have a Squid package, so you have to compile it yourself. You can use Arch, but it is a bit difficult to install and get it working. Arch has an option to install exactly what you need. You can also try Slackware and FreeBSD. All of them will work, but it won't be easy. SmoothWall LTD used to be under 500megs, but it is one gig now. You should also check Devil-Linux has a squid package.

---

### Post by netlogic on 2007-10-10
I just remembered. It is late and trying to finish up. Look for Debian net install iso at debian.org. Ubuntu came from Debian, so you should feel right at home. It will only install the kernel, essentials, and very basic networking. It should be around total of 380megs, 80megs for your swap, and rest for your var so you can try out squid. I highly recommend getting a bigger drive.

---

### Post by MJN on 2007-10-10
I agree - it would surely be better putting your efforts not into looking for a small distro but looking for a bigger HDD!
 
There must be one knocking around somewhere for free... heck if I were a little nearer (I note you're based in Antarctica - nice![1]) I'm sure I'd have an old 10GB drive somewhere.
 
Whilst different distros may have similar cores it's got to be of benefit sticking to the one you know and love!
 
Mathew
 
[1] Ah.. the penny just dropped with 'Tux City'... so you're not from Antarctica then?! That'd explain the apparent misspelling...

---

### Post by Mr.Ganja on 2007-10-11
> **MJN said:**
> 
 
[1] Ah.. the penny just dropped with 'Tux City'... so you're not from Antarctica then?! That'd explain the apparent misspelling...

My veil of secrecy has been penetrated!:lolflag:

you are right, I should get a bigger drive, but would you think that FreeBSD be a good temporary solution? (Until I can find a HDD)

The net install of Debian seems a good Idea, I will look into it.

Thank you for your suggestions, and if there are any more then I would appreciate hearing them.

---

### Post by netlogic on 2007-10-11
If you are very comfortable with UNIX, FreeBSD should be good, but if you a hardcore Unix user, try Debian net install. It should the same command lines. BSD will feel very foreign if you haven't used other UNIX besides Debian based distros.

---

### Post by netlogic on 2007-10-11
I looked up devil-linux
Just use that. It fits your bill.
[http://www.devil-linux.org/product/features.php](http://www.devil-linux.org/product/features.php)
If you aren't familiar with iptable, you can use fwbuilder. It is similar to Checkpoint firewall. They have it for Windows and Linux desktop and transfer the configuration.
Have fun!

---

