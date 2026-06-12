---
title: "ubuntu server 10.04 LTS x64  USB ports error and PCSC"
date: 2013-06-11
forum: Server Platforms
---

### Post by tester100 on 2013-06-11
Hi guys 

quick question.

i have got a PC SERVER I7 3.3 quadcore  with assus p7xxx motherboard

it comes with 6 USB ports 2.0 and 2 usb 3.0 at the back

now i have use several USB devices, i mean alot

so i was trying to transfer all USB devices into 1 machine as i have 2 machines running for the same purpose now..

and as this machine is good enough to run both i tried, problem is 

so i have alot of PCSC card readers, but unforntunatelly ubuntu only recognizes maximum of 16 USB ports

i have 4 hubs of 4 ports connected onto 4 of the USB 2.0 ports

up to 16

then i have a few more devices pcsc for testing when i try to plug anything over 16 devices i keep getting SCard errors and it won´t recognize either the device hooked up on the other USB ports.. and also on PCSC all the readers devices get lost and give me erros information.

as anyone else tried this?


any info to why ubuntu limits usb port devices?? or is it a Pcscd driver issue i´ve tried with several pcscd from 1.5.3 all the way up to 1.8.xx

if i remove extra USB devices and card readers pcsc if i do a pcsc_scan again i can now see all my devices listed

actually it can handle 16 devices........and work with them but on the pcsc_scan it starts already giving erros on scard.....

could it be something specific on the pccscd drivers itself???

> PC/SC device scanner
V 1.4.16 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.5.3
Scanning present readers...
0: OmniKey CardMan 3121 00 00
1: OmniKey CardMan 3121 01 00
2: OmniKey CardMan 3121 02 00
3: OmniKey CardMan 3121 03 00
4: OmniKey CardMan 3121 04 00
5: OmniKey CardMan 3121 05 00
6: OmniKey CardMan 3121 06 00
7: Gemplus GemPC Twin 07 00
8: OmniKey CardMan 3121 08 00
9: OmniKey CardMan 3121 09 00
10: OmniKey CardMan 3121 0A 00
11: OmniKey CardMan 3121 0B 00
12: OmniKey CardMan 3121 0C 00
13: OmniKey CardMan 3121 0D 00
14: OmniKey CardMan 3121 0E 00
15: OmniKey CardMan 3121 0F 00
SCardGetStatusChange: Invalid parameter given.


---

