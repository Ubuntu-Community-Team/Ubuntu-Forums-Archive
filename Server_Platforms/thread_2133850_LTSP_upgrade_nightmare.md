---
title: "LTSP upgrade nightmare"
date: 2013-04-09
forum: Server Platforms
---

### Post by lykwydchykyn on 2013-04-09
Yesterday I upgraded my ltsp system from Lucid to Precise.  I had tested the upgrade on a test system, and everything had seemed ok there, but now I'm getting bitten by all sorts of trouble.  If anyone can help me with any of these, my sanity would thank you:

Quick background:
- I have about 15 zotac zbox thin clients, model HD-ID11 with 1 GB ram, atom 1.66 cpu, and NVIDIA Ion graphics with 512Mb ddr3 vram.
- I have another 10 or so that are old pentium 3 GeTAC ruggedized laptops.  They boot with an rt8139 network card (this is relevant, see problems)

Problems:

- **wakeonlan no longer works** on the zotacs.  We have a script that tells the them to halt every night (via ssh), then sends out wakeonlan packets before opening to turn them on.  It failed to wake a single client.  I installed etherboot, and whipped up a quick etherboot script.  This, perplexingly, woke about half the zotacs.  They are all identical models.

- **The laptops freeze up on warm reboot**.  The getacs lack wake-on-lan so  were merely rebooted each night.  Now I find that if I warm-reboot them, they lock up during the pxe boot process (see attached picture).  They boot fine with a cold boot.

- **Video on the zotacs is sluggish**.  All they do is display a simple web page in a QTWebkit widget.  Under lucid, I used the nv driver, now Precise uses nouveau even if I specify nv.  Attempts to get nvidia proprietary drivers running in the chroot on my test system failed.

- **The mouse fails on the zotacs** sometimes after a warm reboot.  A cold boot fixes this.

- **Random log spamming**: One zotac keeps spamming the logs with this message:
```

[drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainer is 142
Raw EDID:
(8 lines of hex data)
nouveau 000:03:00.0: DVI-I-1: EDID block 0 invalid
[drm]nouveau 0000:03:00.0: DDC responded, but no EDID for DVI-I-1

```

Another zotac keeps spamming with this:
```

usb 3-1: USB disconnect, device number XX
usb 3-1: new low speed USB device number YY using uhci_hcd
input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input556

```
Where XX is a number that keeps incrementing every minute or so, and YY is XX+1.   

Any help anyone can offer is much appreciated.

---

### Post by lykwydchykyn on 2013-04-18
Well, an update:

- I've given up hope for the old getac laptops, I'll be replacing them soon.

- I managed to make a client image with nvidia-current installed.  I thought it would improve video performance but it doesn't seem like it is.  Sad, the old 'nv' driver actually did a decent job with this.

- I managed to fix WOL for the zotacs by installing the r8168 driver from realtek.  Problem is, I've got some new zotacs in with a slightly different realtek chip that doesn't like the r8168 driver _at_all_.  Works with the r8169 included in the kernel, but no WOL.

Logs are filled with less junk now, but I still get the mouse problems on the Zotac.

Still be happy to get any advice you can give.... thanks.

---

