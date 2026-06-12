---
title: "Using a winmodem in Virtualbox XP VM"
date: 2013-02-07
forum: Virtualisation
---

### Post by cscj01 on 2013-02-07
I have created a Virtualbox XP VM under Ubuntu 12.04. I have everything I need working except for msfax, the Fax program that comes with XP. The winmodem in my computer is a Broadcom Corporation BCM4212 v.90 56k modem. Ubuntu does not support this card.

Output from lspci -tv shows the following:> lspci -tv
-[0000:00]-+-00.0  Intel Corporation 82P965/G965 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G72 [GeForce 7300 LE]
           +-19.0  Intel Corporation 82566DC Gigabit Network Connection
           +-1a.0  Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4
           +-1a.1  Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5
           +-1a.7  Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2
           +-1c.0-[02]--
           +-1c.4-[03]--
           +-1d.0  Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3
           +-1d.7  Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1
           +-1e.0-[04]--+-03.0  Creative Labs CA0106 Soundblaster
           |            +-04.0  Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
           |            \-05.0  Broadcom Corporation BCM4212 v.90 56k modem
           +-1f.0  Intel Corporation 82801HH (ICH8DH) LPC Interface Controller
           +-1f.2  Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode]
           +-1f.3  Intel Corporation 82801H (ICH8 Family) SMBus Controller
           \-1f.5  Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode]
I noticed the winmodem card shows a |\ at the beginning of the line while most others show a +. What is the significance of the |\?

Is there a way to access the card from my XP VM?  Virtualbox gives me several options for defining a COM port: [LIST=4]
[*]Disconnected;
[*]Host Pipe;
[*]Host Device;
[*]Raw file.
[/LIST]

I have been under the assumption that Host Device might work, but my understanding is that Host Device would require VT-d to work, and my PC does not have VT-d support.  Further, I have been told that Virtualbox does not have VT-d support yet.

Any thoughts on this issue will be appreciated.  That includes confirming or disputing those items above that I believe to be true.

Thanks for any assistance or information anyone can provide.

---

### Post by cscj01 on 2013-02-18
bump

---

### Post by Habitual on 2013-02-18
> **cscj01 said:**
> I have been under the assumption that Host Device might workfor Ubuntu which "does not support this card."? 

Good luck.

---

