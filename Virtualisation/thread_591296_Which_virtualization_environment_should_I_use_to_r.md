---
title: "Which virtualization environment should I use to run XP?"
date: 2007-10-25
forum: Virtualisation
---

### Post by mjpatey on 2007-10-25
I have one single, lone piece of software that I need to run in Windows (Wine doesn't handle it reliably), and have tried running it on a virtual XP machine in VirtualBox.  It's a little slow in VirtualBox, but the major drawback for me is it crashes a lot, and I have to restart the virtual machine several times in a session.

If VirtualBox is out, would VMWare be my only other serious choice, or are there others I should consider?

Thanks for any input you may have!

-Mark

---

### Post by jshurst on 2007-10-25
Personally I think VMWare is the best virtualization software out there.  Not sure if it is in the Ubuntu repositories for Gutsy yet though (I know it wasn't a few days ago) but you can still install it.

J

---

### Post by mjpatey on 2007-10-25
So how does it work?  With VirtualBox, there was one program to download and run.  For vmware, there's Server and Player.  I can find nothing on their site about what I need to run WinXP in a VM in Ubuntu.

Any ideas?

-M.

EDIT:  Actually, it now offers:  VMware Workstation, VMware ACE, VMware Virtual Desktop Infrastructure, and VMware Player.  I have no idea which of these I need!

---

### Post by kellemes on 2007-10-25
If Virtualbox isn't working for you this is the best option in terms of speed!
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo?highlight=%28qemu%29]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo?highlight=%28qemu%29")

---

### Post by mjpatey on 2007-10-25
Thanks for the QEMU advice, but the Howto alone is giving me the willies.  Too many steps, and if it ever breaks, I'll never know how to fix it!

I just installed VMWare Player, and all it does is let you run existing VMs... so I downloaded VMWare Workstation, on the hunch that it might let me make the VMs myself, and it does!  So once I find my Windows install disc, I'm off ot the races.

I have to say, for anyone interested in doing this... in order to download the VMWare software, you have to go through the most awful registration process I've ever experienced.  Just try and leave one of the fields blank and you'll see what I mean.  When you go back and fix it, their UI has reset certain (but not all) other fields to their defaults, and the bottom line is you have to check every one over again before being allowed to proceed.

Sorry, I'm having a Bad Day.  I'll report back with any success/failure stories!

-Mark

---

### Post by Shazaam on 2007-10-25
Have you tried this website yet?

[http://www.easyvmx.com/](http://www.easyvmx.com/)

---

### Post by veloce on 2007-10-25
> **mjpatey said:**
> Thanks for the QEMU advice, but the Howto alone is giving me the willies.  Too many steps, and if it ever breaks, I'll never know how to fix it!

I just installed VMWare Player, and all it does is let you run existing VMs... so I downloaded VMWare Workstation, on the hunch that it might let me make the VMs myself, and it does!  So once I find my Windows install disc, I'm off ot the races.

I have to say, for anyone interested in doing this... in order to download the VMWare software, you have to go through the most awful registration process I've ever experienced.  Just try and leave one of the fields blank and you'll see what I mean.  When you go back and fix it, their UI has reset certain (but not all) other fields to their defaults, and the bottom line is you have to check every one over again before being allowed to proceed.

Sorry, I'm having a Bad Day.  I'll report back with any success/failure stories!

-Mark

You want vmware server.  workstation isn't free - so will disable itself at some stage. Server allows you to create and play vms (and connect to vms on other servers).

Yes the registration process is ghastly.  So when getting licenses, get 5 - make sure you save them somewhere that you can find them in 6 months.

You will also need a valid xp license so that you can authenticate it (and run xp legally).  

good luck.

---

### Post by AndyCat on 2007-10-26
Why dont you run VMware server... I have it working perfectly coz i still use 2 programs that wont run with wine

---

### Post by mjpatey on 2007-10-26
OK, I created my XP VM with VMWare Workstation (a program which will de-activate at some point) and can use it in VMWare Player.  Playing back in VMWare Player works great!

If I'm not mistaken, my VMWare Player will never expire, right?  But my ability to create VMs will (when my Workstation copy expires).  However, the VM I created will live on for as long as I continue to play it in VM Player.  Is that right?

You know, I have to say, although this is working (YAY!!!), this makes a really good argument for the simplicity of Free Software.  :-)

Shazaam, I hadn't heard of easyvmx... it looks like a free (as in beer, at least) program that would do what VMWare Workstation did for me, allowing me to create the VM to play back in VM Player.  It looks to be web-based?  Interesting.  Thanks for the info!

Thanks to all who contributed here; I learned a lot!  So far, it seems to me that VMWare Player is running my XP install faster and more glitch-free than VirtualBox did.  VirtualBox is probably on to a new version, so it's probably not a fair comparison.

---

### Post by jespdj on 2007-10-26
Listen to what the people above are saying: You want VMWare **Server**, which is free for personal use (does not expire like Workstation), and which allows you to create virtual machines yourself.

---

