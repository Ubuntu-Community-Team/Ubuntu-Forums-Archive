---
title: "Ubuntu 12.04 network problem."
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nightwalkerkg on 2012-04-05
I have installed ubuntu 11.10 and upgraded to 12.04,since the upgrade i can't connect to the internet.I have used a live cd to check if the problem is because of the upgrade but it's not working in a live cd eather,but when i use a 11.10 live cd evrything is working! I have a DSL modem connected via ethernet cable to TP-LINK TF-3200 network card.I also have a VIA-Rhine network card,but it's not working and i don't use it.How do i fix it? Thanks in advance.

---

### Post by kc1di on 2012-04-05
can you please post the out put of this terminal command
```
lspci
```
thanks

---

### Post by nightwalkerkg on 2012-04-05
Here you go.
```
nightwalkerkg@Nightwalkerkg:~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0c.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
00:0d.0 Communication controller: LSI Corporation LT WinModem (rev 02)
00:0e.0 Ethernet controller: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY (rev 31)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AS [Radeon 9550]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AS [Radeon 9550] (Secondary)

```

---

### Post by kc1di on 2012-04-05
Thank you My question is do you have the used network card tuned off in bios?
in not you should start there.

Of course 12.04 is still in beta and may not fully support all controllers yet. but I would find it hard to believe that your VIA controller is not supported yet.

---

### Post by nightwalkerkg on 2012-04-05
I ll' check but i think that is not disabled in bios because i am using it normaly under windows xp.I forgot to mention that i have a dual boot,and that the network manager is reporting : "Device not ready!" Thanks for the reply.

---

### Post by Redcard on 2012-04-05
Yeah, I'm running into this too now.  Suddenly network-manager can't seem to see the network, and the card isn't picking up .  It is visible in ifconfig and it is loaded.. it's just not working.  It was working last night.

---

### Post by dino99 on 2012-04-05
install wicd via synaptic, it works smoother than network-manager

---

### Post by Redcard on 2012-04-05
How?  I can't get on the internet :D

---

### Post by VinDSL on 2012-04-05
> **nightwalkerkg said:**
> I have a DSL modem connected via ethernet cable to TP-LINK TF-3200 network card.I also have a VIA-Rhine network card,but it's not working and i don't use it.How do i fix it? Thanks in advance.
I had a problem, for several weeks, with >= Linux 3.2 not recognizing the pseudo, southbridge-driven, onboard LAN device on this  computer.

The intermediate fix was to uninstall network-manager, and install Wicd, as dino99 recommended.

The long-term fix, was to install a NIC that Linux 3.2 / 3.3 supported... in my case a Netgear with a real DEC "Tulip" chipset, e.g. none of this cheapskate, pseudo device nonsense.

Network-manager works fine now!

I strongly suspect they removed support for many older LAN devices, in the most recent Linux kernels and/or Ubuntu Precise and/or the ancillary apps.

I would:
[LIST]
[*]Run Wicd instead of network-manager (which I did)
[*]Switch to a different LAN card (which I also did)
[/LIST]

Both methods worked for me.

---

### Post by VinDSL on 2012-04-05
> **Redcard said:**
> How?  I can't get on the internet :D
Heh!

How did you post that, without a connection?!?!?  :D

---

### Post by Redcard on 2012-04-05
> **VinDSL said:**
> Heh!

How did you post that, without a connection?!?!?  :D

Phone :D

---

### Post by cariboo on 2012-04-05
If you remove network-manager, you should still be able to connect to your router/modem manually using the following command:

```
sudo dhclient ethX
```

where ethX is your network device.

---

### Post by Redcard on 2012-04-05
Yeah, tried that as well, and it just hung.  Oh well.  Might be the network card is going away, it's a JMicron (uses jme.o)

---

