---
title: "Please recommend a virtual enviroment for Windows"
date: 2011-02-21
forum: Virtualisation
---

### Post by Hioushi on 2011-02-21
Greetings everyone. I'm new in the Ubuntu community but certainly not in GNU/Linux in General. 

I've been mostly a Slackware user, and most recently openSuse, but I must say I fell in love with Ubuntu 10, it's everything I always wanted a distro to be. 

After a short introduction, I'd like your help in this. I'm running Ubuntu in a remote server, where I only have ssh access (no X), and I need Windows running virtually on it. I'd like to know which environment I should choose for this, Xen, VirtualBox, VMWare?.

I'm looking for the most Ubuntu-supported alternative, which allows me to install and run using only the console.

I'd appreciate any help you could provide.

Best regards.

---

### Post by HermanAB on 2011-02-21
Howdy,

You need the kernel headers, binary utilities and GCC.  If those are configured properly, then you can install any of the above.  Virtualizers are mature and all solve the same problem, so the result is the same too.  Pick your poison...

---

### Post by zzztownsend on 2011-02-25
i found virtualbox very easy to install and use headless. I've been using the PUEL version which  been very reliable, but not open source. I have found the RDP connection very useful as I seem to have no end of problems trying to VNC to a server - shift keys not working, now left mouse button not working. Very aggravating.

The RDP is handy as rdesktop on the client also supports local sound.

At the 3.2.x versions I had to use PUEL version because the RDP support is only in that version. I have read that this may have changed with 4.x which I think gives the base install as open source and I guess you have to get the closed source extensions for RDP and remote USB etc. I have seen there's a PPA for this already.

Good support forum at virtualbox.org as well.

Cheers

matt

---

### Post by CharlesA on 2011-02-25
> **zzztownsend said:**
> 2.x versions I had to use PUEL version because the RDP support is only in that version. I have read that this may have changed with 4.x which I think gives the base install as open source and I guess you have to get the closed source extensions for RDP and remote USB etc. I have seen there's a PPA for this already.

You don't need a PPA to get the closed source extension, you can just download and install them off the virtualbox website. :)

---

### Post by Hioushi on 2011-02-25
Thank you,

Yes, VirtualBox was my first choice to try and I'm very happy with it so far, it runs great headless and was very easy to setup. The documentation is great.

Regards.

---

