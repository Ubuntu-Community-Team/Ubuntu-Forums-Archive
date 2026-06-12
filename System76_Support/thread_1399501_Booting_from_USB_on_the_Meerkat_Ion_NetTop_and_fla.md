---
title: "Booting from USB on the Meerkat Ion NetTop and flash the BIOS"
date: 2010-02-05
forum: System76 Support
---

### Post by pureblood on 2010-02-05
I have finally found out how to start up the system from the BIOS in the Meerkat Ion NetTop. When you plug a USB stick, most BIOS will just recognize it as an additional booting device and let you choose if you want to boot from the hard drive or from the stick. The BIOS in the Zotac motherboard treats the USB stick as a second hard drive and to be able to boot from it, you have to change the order of the two hard drives from the Boot section of BIOS, and not by pressing F11 during startup. A bit counterintuitive but it works.

I wanted to use the boot from USB to start a DOS environment to flash the BIOS. Something is buggy about the BIOS shipped with the system. In the Advanced tab there is a section about fan speed control. You can apparently change the speed of the fan from that section but nothing really happens to the fan speed if you do so. On the Zotac website:
[http://www.zotac.com/index.php?option=com_docman&task=doc_details&gid=309&Itemid=100032&lang=nd](http://www.zotac.com/index.php?option=com_docman&task=doc_details&gid=309&Itemid=100032&lang=nd)
there is a BIOS update which apparently adds "Smart Fan Control". I am not sure what that means. I was wondering if the BIOS update would fix that. Has anybody tried that and had success?

Edit: In the end I managed to update the BIOS. It was incredibly easy. I used unetbootin to install FreeDOS on a USB stick. Then I downloaded from the Zotac website mentioned above the BIOS update, that is, a file named pa123.zip. I unpacked this on the USB stick and I rebooted the system. After changing the hard drive order to boot the USB, this are the commands I executed to flash the BIOS:
> c:
cd PA123\AFUDOS
AFUDOS ..\PA123\N1012WZT.ROM /B /P /N /X /C
It took a few seconds to erase the previous BIOS and install the new one. Make sure the power does not go away in the meanwhile.

Now I have a newer BIOS which display the Zotac brand when the computer starts and supports the Smart Fan Control, which is a dynamic control of the fan speed. Alas, what I did not know was that the fan shipped with the Meerkat Ion does not support PWM, and therefore the motherboard cannot control its speed. That's why changing the settings in the BIOS achieves nothing. I checked online and it seems that no 60mm fans support PWM. Fans with PWM have an extra pin which connects to the control pin on the CPU fan connector of the motherboard allowing the motherboard to slow down their speed. I am not sure why there are no 60mm fans with PWM on sale. Maybe there is no market for them? I am finally resigned to buying a quieter fan. I will let you know the results.

Edit2: I have noticed that after the BIOS upgrade, the computer now sees 3459MB out of the 4GB installed. Before it was more something like 3.2-3.3GB, I can't remember exactly. But this is definitely an improvement for those who bought 4GB like I did.

---

### Post by thomasaaron on 2010-02-08
If you're running 32-bit Ubuntu on the system, it won't see the whole 4GB. If you move to 64-bit, it will.

There is also a 32-bit pae kernel that is capable of seeing the whole 4GB. We've not really tested with it, but it should work fine.

---

### Post by pureblood on 2010-02-08
I do use a 64 bit kernel. Still, the BIOS has some limitations. I see exactly 3459MB of memory now. I think the right amount should be 4096-256=3840MB, since 256MB are shared with the graphic unit. I am not sure where the rest is gone. I don't remember exactly what it was before the BIOS update but I think it was a bit less than that. If you have a system with 4GB you can check from the BIOS. Overall, I am missing 3840-3459=381MB of memory.

---

### Post by thomasaaron on 2010-02-09
I'm using the previous BIOS, and I'm seeing 3328MB...
and System Monitor shows 3.2GB.

I'll bring this to R&D and see what they think.

---

### Post by thomasaaron on 2010-02-09
With only 2GB installed, the BIOS detects 1792 MB, and System Monitor detects 1.7GB.

2048 - 256 (graphics) = 1792.

I'll let you know what R&D says.

---

### Post by thomasaaron on 2010-02-09
OK, so here are some specs on the IONITX-F-E...
[http://www.pugetsystems.com/part_info.php?part=6570](http://www.pugetsystems.com/part_info.php?part=6570)
...which show that the GPU can share up to 512MB of RAM.

In the BIOS (Chipset > SouthBridge) the iGPU framebuffer size is set to 256MB.

So, as best I can tell, since you have 4GB installed, 512MB + 256MB (= 796MB ) is being reserved.

So, 4096 - 768 = 3300, which is in line with what the BIOS and System Monitor are detecting in my 4GB example above.

---

### Post by pureblood on 2010-02-09
So I remembered correctly, before the update it was 3328MB, and after the update it is now 3459MB. Not that much more but still appreciated. Maybe it is just a different BIOS configuration rather than be due to the BIOS update.

---

### Post by thomasaaron on 2010-02-09
Yeah, you might check Chipset > Southbridge > iGPU Framebuffering. Yours might be set to 128 instead of 256.

---

### Post by pureblood on 2010-02-13
Thomas, you were right. For some reasons after the BIOS upgrade the automatic iGPU FrameBuffer detection was disabled and only 64MB were dedicated to that. I wonder what the negative consequences of that could be. Users that update the BIOS should be aware of it. I changed it back to 256MB (is there any point of sharing 512MB?). Now the BIOS sees again 3520MB and the operating system sees 3271MB. My understanding is that half GB is gone to begin with because of a limitation in the BIOS. Not too bad anyway. Thanks for your help. The System76 support is the best.

---

### Post by thomasaaron on 2010-02-15
> My understanding is that half GB is gone to begin with because of a limitation in the BIOS.

Hi, Pureblood. I don't think that's the case. See post #6 above. The 256MB from the iGPU framebuffer and the 512 shared memory taken by the memory card are... automatically deducted from the 4096 MB total. That's why the BIOS only reports 3.something GB.

To see how that works, if you remove one of your memory cards, the BIOS will only deduct 256MB for the memory card + the 256MB from the iGPU frame buffer. (That's because the graphics card can reserve either 256MB or 512MB, depending on how much RAM is installed).

I've not really seen a BIOS tally RAM like that before. Typically, they would show 4GB installed... period. But this one seems to pre-calculate everything.

---

