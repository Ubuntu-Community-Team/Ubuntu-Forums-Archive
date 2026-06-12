---
title: "eth0 missing from server network connections"
date: 2009-01-11
forum: Server Platforms
---

### Post by College_Trained on 2009-01-11
Hey all,
So I just set up my first server! Anywayz, it was working perfectly fine earlier this week and I'm not sure what happened but the server could no longer get an internet connection. I convinced myself that if I reinstalled the server everything would be back to normal (I didn't have anything on it to begin with). Well when I started the reinstall, it didn't see my NIC card at all. (I got it to recognize the NIC maybe once or twice during the large number of times I booted that cd after reseating the card itself. But between that and the "can't find the codename for this release" error, i figured it was best to try to solve that problem after I had successfully installed.) So I told myself that it could probably be fixed after the install was completed.
Anyways, now I am stuck with a brand new OS install but no network.

If anyone has had any experiences like this and knows how to fix it, all info would be of tremendous help.

Thanks,
College_trained

-EDIT: I am using Ubuntu 8.10 server.

---

### Post by volkswagner on 2009-01-11
What is the card you are using?

What is the output of 

```
lspci
```

---

### Post by College_Trained on 2009-01-11
I pulled the card out and it is a network extreme nc100.

The output of lspci is:
> 00:00.0 Host bridge:Intel Corporation 440BX/2X/DX - 82443BX/2X/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/2X/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0c.0 Multimedia Audio Controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
00:0e.0 Communication conroller: Agere Systems 56k WinModem (rev 01)
00:0f.0 Mass storage controller: Promise Technology, Inc. PDC20262 (FastTrak66/Ultra66) (rev 01)
00:10.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:00.0 VGA compatable controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

Now apparently it is recognizing my NIC after reseating it. But if you could let me know what to do if I ever have this problem again, that'd be great.

---

