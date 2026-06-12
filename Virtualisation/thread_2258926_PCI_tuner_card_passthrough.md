---
title: "PCI tuner card passthrough"
date: 2014-12-31
forum: Virtualisation
---

### Post by pauldmallett on 2014-12-31
I am attempting to detach my TV Tuner card as a prelude to setting up passthrough from Host to KVM Guest
COMMAND
~$ discover --vendor-id --model-id pci | uniq
OUTPUT
1131 7160 Philips Semiconductors SAA7160
COMMAND
$ sudo virsh nodedev-dettach pci_1131_7160
OUTPUT
error: Could not find matching device 'pci_1131_7160'
error: Node device not found
Any ideas as to why this PCI can not be found?

---

### Post by TheFu on 2014-12-31
VT-d enabled in the BIOS and kernel?

For me, it was just easier to have network-based tuners. No passthru needed.  Can record 4 hidef channels concurrently inside a KVM guest VM.  HD Homerun makes these.

---

### Post by pauldmallett on 2015-01-01
Yes, BIOS all sorted. It's not really that end of things......yet. 
Just read the second half of your post after driveling on about virsh commands.
A network tuner solves all sorts of problems,  I had better take another look. Many thanks.

---

### Post by pauldmallett on 2015-01-01
"VT-d enabled in the BIOS and kernel?"
Spoke too soon "chipset compatability" also required.
USB tuner is starting to look the better option for a virtual system, thanks again.

---

### Post by TheFu on 2015-01-01
> **pauldmallett said:**
> "VT-d enabled in the BIOS and kernel?"
Spoke too soon "chipset compatability" also required.
USB tuner is starting to look the better option for a virtual system, thanks again.

I have a USB tuner - don't bother.  USB passthru isn't perfect either.

Get the network tuner(s), you'll thank me.  I have 2 HDHR3s (out of production now) and love them. Can be used by any systems on the network and current generation models support DLNA clients, which means almost any smartphone, tablet, XBMC, and cheap player-only device can use one of the tuners.  Do that with a USB tuner?

If you need antenna connected tuner, get an HDHR4 dual tuner.
If you need CableCARD, get the HDHR-Prime triple tuner.
If you need more tuners, just add them to the network, tweak a setting, done.

---

### Post by pauldmallett on 2015-01-01
Obviously I had not understood what I was looking at first time around.
Done the reading, found UK equivalent. 
Awesome bit of kit, I think I have to have one, good call.

---

