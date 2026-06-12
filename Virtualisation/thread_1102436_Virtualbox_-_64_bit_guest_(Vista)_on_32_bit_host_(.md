---
title: "Virtualbox - 64 bit guest (Vista) on 32 bit host (Ubuntu)"
date: 2009-03-21
forum: Virtualisation
---

### Post by Adamantus on 2009-03-21
Hey,

I downloaded Virtualbox OSE to run 64 bit Vista inside of 32 bit Ubuntu. I have a HP dv5 with an AMD Turion X2 64 bit processor that initially ran 64 bit Vista. I installed 32 bit Ubuntu because too many 64 bit program didn't work. 

Now, when I try to install Vista through Virtualbox, I get the message:

[I]Windows failed to start. A recent hardware or software change might be the cause. To fix this problem:

1. Insert your Windows installation disk and restart your computer
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not haev this disc, contact your system administrator or compute rmanufacturer for assistance.

File: \windows\system32\boot\windload.exe
Status: 0xc000035a
Info: Attempting to load a 64 bit application, however this CPU is not compatible with 64 bit mode.[/I]

I'm sure my CPU is 64 bit compatible since it ran Vista 64 bit. I've looked through Google and there is a lot of stuff for Intel CPUs where you have to change some boot options to allow 64 bit virtualization, but I can't find too much info on AMD processors. What exactly can I do to run Vista 64 bit in Ubuntu? Would VMWare work better?

---

### Post by inobe on 2009-03-21
if vt is enabled in the bios it should work regardless of the host.

your cpu must also support vt technology.


i have only tested this with vmware

here is a simple example [http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1237674853485+28353475&threadId=1120296](http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1237674853485+28353475&threadId=1120296)

i don't think virtualbox ose supports a 64bit guest

goodluck

---

