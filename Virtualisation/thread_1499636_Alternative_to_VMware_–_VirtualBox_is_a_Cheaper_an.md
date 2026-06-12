---
title: "Alternative to VMware – VirtualBox is a Cheaper and efficient solution in Ubuntu"
date: 2010-06-02
forum: Virtualisation
---

### Post by swamytk on 2010-06-02
VirtualBox is a cheaper virtualization solution than VMware. Apart from the cost it has a nice GUI to manage the virtual machines and also it supports wide range of operating systems. Virtualbox can run in Windows, Linux, Mac OS X and OpenSolaris and also it supports most guest operating systems except Mac OS X. Let&#8217;s see how to get it done in Ubuntu. My Ubuntu system is 10.04 Lucid.

Installation is straight forward &#8211; Ubuntu main menu -> Applications -> Accessories -> Terminal. Enter the following command to get Virtualbox installed in your machine.

Continue reading here: [http://karuppuswamy.com/wordpress/2010/06/02/alternative-to-vmware-virtualbox-is-a-cheaper-and-efficient-solution-in-ubuntu/](http://karuppuswamy.com/wordpress/2010/06/02/alternative-to-vmware-virtualbox-is-a-cheaper-and-efficient-solution-in-ubuntu/)

---

### Post by HermanAB on 2010-06-02
Uhh, to be fair and no, I do not work for VMware:

Clearly you have never heard of VMware Player.  It is Free and does everything Virtualbox does.

So, unless you want to argue that Free is somehow cheaper than Free or that one GUI is remarkably different from another GUI...

---

### Post by swamytk on 2010-06-02
> **HermanAB said:**
> 
Clearly you have never heard of VMware Player.  It is Free and does everything Virtualbox does.


I have used VMware some times before. It did not support Creating/Editing virtual machine. I was only able to play the prebuilt images.  After your comment I checked with VMWare and understood that latest version supports creating/editing virtual machines. Thanks!

---

### Post by dragos2 on 2010-06-02
> **HermanAB said:**
> Uhh, to be fair and no, I do not work for VMware:

Clearly you have never heard of VMware Player.  It is Free and does everything Virtualbox does.

So, unless you want to argue that Free is somehow cheaper than Free or that one GUI is remarkably different from another GUI...

Vmware player was not supporting bridged networking when I gave up using it. Also Vmware Workstation is the real VirtualBox competitor but it is not free.

---

### Post by dragos2 on 2010-06-02
> **HermanAB said:**
> Uhh, to be fair and no, I do not work for VMware:

Clearly you have never heard of VMware Player.  It is Free and does everything Virtualbox does.

So, unless you want to argue that Free is somehow cheaper than Free or that one GUI is remarkably different from another GUI...

Vmware player was not supporting bridged networking when I gave up using it. Also Vmware Workstation is the real VirtualBox competitor but it is not free. Also Parallels Desktop for Mac
seems to work smooth, but I did not used it.

---

### Post by dcstar on 2010-06-03
> **dragos2 said:**
> Vmware player was not supporting bridged networking when I gave up using it.


VMware Player fully supports bridged networking.

I wish people like the OP - who is basically trolling for traffic to his website - would actually know what they are talking about before posting their "facts".

---

### Post by fjgaude on 2010-06-03
I can attest that Player does both NAT and Bridged along with Host-only networking.

I know of no better non-LAN product that is free than VMPlayer.

---

### Post by littlepeon on 2010-06-06
VMWARE has been in the game longer and has better support (larger user base)than Virtualbox.

Good article, but please stop spreading FUD (fear uncertainty and doubt) about VMWARE--you do NOT know what you are talking about!

VMWARE player is free. they have workstation and server editions also.

VMware Player is a stripped-down version of workstation, so it offers the same virtual hardware as Workstation. In the latest version it can both create and edit virtual machines while it earlier was only possible to run pre-built VMs.
VMware Server is meant for creating and editing virtual machines and running server-like loads. It is optimized for IO rather than interactive use on the local terminal. Desktop intensive (graphical) applications will not have too good performance when viewed through the interface provided in VMware Server as all requests go through the network (even when you're working locally). Server usually provides older or same generation of virtual hardware as Workstation or Player. Server is a free product. VMware Server cannot be installed at the same time with Workstation/Player. This is most likely due to conflicting, different kernel modules and cannot be circumvented.

---

### Post by stans on 2010-06-21
I love vmplayer because it is so much more faster than virtualbox, and much easier to use. I have an XP guest, and an OpenSolaris guest.

---

