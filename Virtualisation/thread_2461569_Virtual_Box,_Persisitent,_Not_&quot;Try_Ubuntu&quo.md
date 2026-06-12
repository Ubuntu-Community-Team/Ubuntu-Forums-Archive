---
title: "Virtual Box, Persisitent, Not &quot;Try Ubuntu&quot;"
date: 2021-05-03
forum: Virtualisation
---

### Post by webmanoffesto on 2021-05-03
I want to run an installation of Ubuntu in Virtual Box. I used the Ubuntu iso to create the VM. But now each time I start it I get the "install Ubuntu" or "try Ubuntu" message. How do I make this more like a real install; where I don't need to select "try" or "install"? Should I click on "install"? I want to make sure that, if so, that this "install" is only happening in the VM area, and I'm not messing with my whole computer. This is all happening within Virtual Box, but I want to be sure.

I had problems with using a VirtualBox Ubuntu image (maybe it was an OVF? or VDI?). The virtual box didn't go through my VPN, even though the computer did use the VPN. How would I change that?
I think I used the VDI here [https://www.osboxes.org/ubuntu/](https://www.osboxes.org/ubuntu/).
But I also found some here [https://www.linuxvmimages.com/images/ubuntu-2004/](https://www.linuxvmimages.com/images/ubuntu-2004/).

---

### Post by TheFu on 2021-05-03
Install it.
The great thing about using VMs is that only virtual hardware is used.  So, setup a virtual disk, virtual CPU(s), virtual RAM, virtual VideoRAM, virtual disk controller(s) and virtual networking.  Those will be the only things the VM can see, unless you go way, way, out of your way to allow access to the host computer.  BTW, don't do that, it is a security nightmare, though people do sometimes share the host storage directly in this way. For accessing storage, I always use network protocols between hosts and VMs.  That way, it is clear what is and isn't being shared. This prevents bypassing normal protections.

Most people prefer to use the Oracle VirtualBox packages, not those included in Ubuntu.

As for VPNs, you'll need to setup the guest VM to use a VPN, if that is your desire.  For almost everything, a VM can be considered a normal physical host and should be treated that way.

I'd always recommend against downloading software from untusted sources.  Both the links you've provide would be "untrusted" in my book.  They are random websites, unconnected with Canonical.  It takes 10 minutes to perform an install of any Ubuntu OS. Don't overthink it.

Long ago, when I used virtualbox, I wrote an article about setting up a VM for the best performance: [https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)  Hope you find it helpful.  Obviously, it is a little dates, but most things haven't changed.  To get the guest additions working should be much easier these days. The steps in my article shouldn't be needed, I'd hope.

---

### Post by slickymaster on 2021-05-03
*Thread moved to **Virtualisation**.*

---

### Post by webmanoffesto on 2021-05-03
> **TheFu said:**
> Most people prefer to use the Oracle VirtualBox packages, not those included in Ubuntu.
Do you mean these ones?
Pre-Built Developer VMs (for Oracle VM VirtualBox)
[https://www.oracle.com/downloads/developer-vm/community-downloads.html](https://www.oracle.com/downloads/developer-vm/community-downloads.html)

---

### Post by deadflowr on 2021-05-03
> **webmanoffesto said:**
> Do you mean these ones?
Pre-Built Developer VMs (for Oracle VM VirtualBox)
[https://www.oracle.com/downloads/developer-vm/community-downloads.html](https://www.oracle.com/downloads/developer-vm/community-downloads.html)

I'm sure TheFu was referring to using Virtualbox directly from Oracle instead of Virtualbox from the Ubuntu repositories.
See: [https://www.virtualbox.org/wiki/Linux_Downloads]("https://www.virtualbox.org/wiki/Linux_Downloads")
Basically you add the Oracle Virtualbox repository and then install it, which will install the version from oracle, and then it'll get any updates from them as well.

---

### Post by webmanoffesto on 2021-05-03
Okay, the instructions say "Add the following line to your /etc/apt/sources.list. According to your distribution, replace '<mydist>' with 'eoan', 'bionic', 'xenial', 'buster', 'stretch', or 'jessie' (older versions of VirtualBox supported different distributions): "

If I'm on Ubuntu 20.04 LTS, which is Focal Fossa
Do I replace <mydist> with "fossa" or with "focalfossa"?

---

### Post by deadflowr on 2021-05-03
focal
like
```
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian **focal** contrib
```
Ubuntu's codenames are always the adjective.
The animal part is fun.

---

