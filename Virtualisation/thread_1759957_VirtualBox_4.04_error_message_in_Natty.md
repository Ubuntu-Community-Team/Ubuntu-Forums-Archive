---
title: "VirtualBox 4.04 error message in Natty"
date: 2011-05-16
forum: Virtualisation
---

### Post by rewyllys on 2011-05-16
While I was running VirtualBox 4.04 under Maverick, I tried to upgrade to 4.06, but the result was that VBox crashed completely.  (I reported that problem here, but ultimately decided to wait and hope that it would be cured by installing Natty.)

Yesterday, I did a clean install of Natty on my laptop, and re-installed VBox 4.04 via the Synaptic Package Manager.  Now VBox opens okay, and shows that it has picked up my previous Windows XP installation.  

But when I click on what I named "LaptopVirtualXP", I get only a momentary glimpse of the XP desktop.  It closes almost immediately, and then the following error message appears:

>                                   

 **VirtualBox - Error ** 
 Failed to open a session for the virtual machine **LaptopVirtualXP2 ** 
 
 Unsupported version 13 of data unit **'pgm'** (instance #1, pass  
 0xffffffff) (VERR_SSM_UNSUPPORTED_DATA_UNIT_VERSION)  
 
 Result Code:     NS_ERROR_FAILURE (0x80004005)  
 Component:     Console  
 Interface:     IConsole {515e8e8d-f932-4d8e-9f32-79a52aead882}Any and all suggestions as to what I should do to solve this problem will be much appreciated.

---

### Post by rewyllys on 2011-05-17
bump

Help, please.

---

### Post by brian70809 on 2011-05-17
I have gotten these errors before...  

I think I had to make a new instance of a VM.... double check all the hardware and check marks for ACPI, etc...

copy the saved instance into that new VM folder and see if you can launch it from there.

---

### Post by rewyllys on 2011-05-18
Thanks, Brian.  I'd pretty much come to the conclusion that I might as well start a new virtual XP installation, so your reply prompted me to go ahead and try it.

The new virtual Windows XP installation is going smoothly, although slowly (downloading and installing SP3 to XP alone took over an hour!).

I guess that my attempt to ugrade to VirtualBox 4.06 damaged the original virtual XP installation when that attempt crashed VBox completely.  Oh well, it's not the worst misfortune of my life--just an annoying one.:(

---

### Post by Bazon on 2012-04-18
I had the same problem *(only with newer vb versions)*, for me the following helped:
rightclick on virtual machine in virtualbox, select "Verwerfen" (STRG+J) *[I suppose "discard" (CTRL+J) or something like that in english].*
Next time, the virtual machine booted from bios and everything went fine. :-)

---

