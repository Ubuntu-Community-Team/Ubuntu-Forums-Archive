---
title: "Ubuntu 12.10 no video input on live DVD"
date: 2012-09-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mark kirby on 2012-09-28
Hi I have been trying install Ubuntu 12.10, but as soon as it  gets past my bios and to the screen with the blinking line in the top  left, I get a no video input message on my tv (like when you turn the tv  on with nothing connected).
  I have used live dvd's of both betas, alphas and daily build all with exactly the same results.
  Has any one else had this ?
  Is there a fix ?
  Dose this mean I can never upgrade my Ubuntu again ? (12.04 works ive been using since beta)
  My pc ,while old, should run this fine 
  CPU = 2x Intel P4 HT @ 3ghz  GPU = Nvidia Geforce 310 via HDMI  RAM = 2 Gb DDR 2  HDD = 2 x 7200 rpm SATA   Please help me I use Ubuntu exclusively on my pc and would like to keep doings so. :confused:

---

### Post by grahammechanical on 2012-09-28
First of all, can you install 12.04? That is an LTS with 5 years support.

Second, the 12.10 beta 2 has just been released. I have not tested it but I intend to in a few minutes. If I get the problem that you have I shall

1) at the purple screen with accessibility options (little man with the outstretched arms) press enter.

2) select my language at the next screen. As English is the default I shall just press enter.

3) Press F6 and use the down arrow to the nomodeset option and then press Enter followed by Esc to get back to the Try-Install screen and make my choice there.

You could try the same. This is the only way I know of getting 12.10 to work as a live CD or an Install disk. I am hoping that things have improved with the 12.10 beta 2 image.

Regards.

---

### Post by mark kirby on 2012-09-28
Thanks your suggestion worked seems 12.10 is missing nvidia compatibility but heres a permanent fix

First use [grahammechanical]("http://ubuntuforums.org/member.php?u=1087323")'s solution to install

 Then follow this guide to set nomoadset in grub [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
 press boot and Ubuntu will start but run slow.

Open a terminal and install this ppa for nvidia xswat (it is not the same as 12.04)

[B][COLOR=#073763]sudo apt-add-repository ppa : org-edgers/ppa
[/COLOR][/B][B][COLOR=#073763]sudo apt-get update
[/COLOR][/B]**[COLOR=#073763]sudo apt-get install nvidia-current nvidia-settings[/COLOR]**
Now reboot and 12.10 will run fine

---

