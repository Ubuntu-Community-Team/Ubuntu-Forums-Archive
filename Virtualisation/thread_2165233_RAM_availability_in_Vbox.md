---
title: "RAM availability in Vbox"
date: 2013-08-04
forum: Virtualisation
---

### Post by achu91 on 2013-08-04
Initally  i had ubuntu 32  bitas host  and used virtual box 4.2 for linux  and i had 4.2 GB(as per free -m command and as per bios ) of ram ;then i installed XP 32 bit  in virtual box 4.2 ; The virtual box system tab reported 3.5 GB of ram and and upto 1.92 GB in green color;Then i i reliaed that XP and all 32 bit use/reconinises max of 3.2 GB. now to utilize th3 4GB i installed  12.04 LTS 64Bit as host  ;i installed orcale virtual box 4.2 for linux amd 64  ;Now in the systemof VB  it showed 4.2 GB of RAM .but again upto 1.98 GB in green colour;

why is it so:initially when Vbox system as 3.5GB of ram it showed 1.92 as free and now after intalling 64bit it still shows 1.92 gb free insite of increase in base RAm to 4.2 GB.please help;

---

### Post by TheFu on 2013-08-04
I don't understand where you are seeing these things, but if your PC has 4G of RAM, then some of that RAM is used by the hostOS just to run.  Depending on your video card, some of that RAM will be used as video memory - this happens with cheaper GPUs, especially on laptops.  In general, the hostOS needs about 1G of RAM to run well.  Then the guest OSes share the remaining RAM - so 2.5G would be the max I'd expect available for a single guestOS, if no other guests were running.  WinXP runs very well for most uses in 1.5G of RAM.

Let me see if google can find an answer to the green vbox memory question ... nope. Nothing jumped out.
I've written and presented in a few countries on optimizing VirtualBox setups. Hopefully this [http://www.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://www.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) will help.

---

### Post by achu91 on 2013-08-05
i attaching the screen shot which shows my problem;rather i cannot sat its a problem ,its one observation i made; ;The obervation in a nut shull; even after installing ubunt64bit the available free memory is only 2GB(out of 4GB)  when compared to 32bit ubuntu 2G(out of 3.5GB).

Please any can tell me the reason for this

---

### Post by TheFu on 2013-08-05
I've never noticed it - are you sure the green isn't just a recommended RAM amount?  On a netbook now, so I can't check it on the machine that runs vbox.
The vbox manual doesn't help: [http://www.virtualbox.org/manual/ch03.html#settings-motherboard](http://www.virtualbox.org/manual/ch03.html#settings-motherboard)
The New VM wizard has a little more [http://www.virtualbox.org/manual/ch01.html#gui-createvm](http://www.virtualbox.org/manual/ch01.html#gui-createvm)

Lacking any more information, the colors appear to be something a developer put in without any specific meaning.

I'll say this again - WinXP runs very well in 1.5G of RAM.  Is there a specific reason you WANT more?

---

### Post by achu91 on 2013-08-05
Thanks for the information that 1.5GB is only required for XP.Just out of inquisitiveness i wanted to use more memory for  XP as i thought  it makes system faster for cad application like draftsight;blender etc  .More over if i increase the RAM above the green mark an  message/warning apperas that "**non optimal settings detected**".I had gone through the manual and there is noting is mentioned regarding green color

Thanks a lot for giving the links ,replies and kindly excuse me  poor english;

---

### Post by TheFu on 2013-08-05
> **achu91 said:**
> Thanks for the information that 1.5GB is only required for XP.Just out of inquisitiveness i wanted to use more memory for  XP as i thought  it makes system faster for cad application like draftsight;blender etc  .More over if i increase the RAM above the green mark an  message/warning apperas that "**non optimal settings detected**".I had gone through the manual and there is noting is mentioned regarding green color

Thanks a lot for giving the links ,replies and kindly excuse me  poor english;

More memory can be needed for huge applications in Windows.  Very few people use Blender or CAD applications inside a VM on a limited machine.  As you see in those links - it is counter productive to give a guestOS too much of the RAM on the system. Also, the guestOS needs extra RAM for the virtual video card. For a desktop guestOS - 128MB is the recommended amount of video RAM - that means the guestOS needs
* base RAM +
* video RAM +
* whatever RAM the hostOS needs to emulate virtual hardware for the guest - probably 100-200MB of RAM, but I don't know.

WinXP will run in 384MB of RAM - that doesn't mean you can run CAD applications.
WinXP runs well on 1G of RAM for normal desktop use.  

BTW, isn't Blender a Linux app - so you want as much RAM available for it on the Linux side, not inside WinXP.

I'm positive that your English is better than my command of **any** other language - even after years of trying to learn Spanish, German, Japanese .... I can barely understand anything and might speak 200 words, not sentences. ;)

---

### Post by achu91 on 2013-08-06
thanks for the replyl, I installed ubuntu version of belnder as well as draftsight;and its working fine;Thanks for the help.

---

### Post by TheFu on 2013-08-06
So, just for clarification - you found native Linux applications that will meet your needs, instead of running WinXP inside a VM and running MS-Windows applications?  I hope that works well.

---

### Post by achu91 on 2013-08-07
Yes i have found out similar software on linux and its meeting my needs

---

