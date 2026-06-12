---
title: "Motherboard question"
date: 2010-02-22
forum: The Cafe
---

### Post by rmccutchan on 2010-02-22
Hi.

This is not necessarily related to Ubuntu, but I have spent several hours trying to find an answer to a question.

I just built a computer and put a ECS Elitegroup motherboard in it with dual channel ram with 4 slots.

The manual says for _optimal_ performance for 1 module, use the DIMM 3 slot.  For 2 modules, use slots 3 and 4.  (I currently have 1 and have ordered another)

That would simple enough, but no where in the manual, on the motherboard, ECS website, or the internet does it specify which slot is 1,2,3,or 4, or which channel is 0 or 1.

I'm not a computer tech, but my guess is that there is an industry standard as to the numbering of ram slots.  For example:  "slot #1 is always the one closest to the processor, slot 2 is next, and so on.....", or something like that.

I guess it is not a HUGE deal, but it is just something that has been puzzling me.

Thanks in advance for any insight.

---

### Post by Mike'sHardLinux on 2010-02-22
What is the model of your board?

---

### Post by rmccutchan on 2010-02-22
A785GM-M Version 1.0

---

### Post by LowSky on 2010-02-22
might sound dumb but its most likely the yellow slots... and check your manual, they will be listed, look in the memory section.

Odd they would tell you 3+4 usually they like 1+2 filled first. Especially AMD boards...

And when in doubt just pick a slot and then go into BIOS to check... it will tell you which DIMM sllot there too

Edit: just found your manual, [http://www.ecs.com.tw/ECSWebSite/Downloads/DownloadFile.aspx?catid=1&driverid=4646&areaid=2&LanID=9](http://www.ecs.com.tw/ECSWebSite/Downloads/DownloadFile.aspx?catid=1&driverid=4646&areaid=2&LanID=9)


And your right it doesn't, and by the way that is the worst manual I have seen in a long time.

go with yellow, and check the BIOS it will tell you the right DIMM, even if you have to pick blind at first

---

### Post by rmccutchan on 2010-02-22
Thanks.

Nothing sounds dumb to me anymore.:)  Kids, grandkids, computers.....need I say more?

I looked in the manual and nothing says which color is which channel or slot, and the bios doesn't tell me which one is being used.  Unless I am not understanding.  It just gives me options for "Enable Auto Detect" or "Disable Auto Detct", etc, but it doesn't say what it has detected.  Can Ubuntu tell?

Just checked the manual and it says:  *"For best performance and compatibility, we recommend that users install DIMMs in the sequence of DIMM3, DIMM4, DIMM1, and DIMM2."*

I'm so confused :confused:

---

### Post by Mike'sHardLinux on 2010-02-22
The manual isn't very clear on this, but it implies that the first yellow DIMM slot (The 3rd slot from the CPU), starting from the CPU, is slot 3. It says if you have 1 DIMM to install in slot 3, and the picture shows where the single DIMM is installed.

---

### Post by paydaydaddy on 2010-02-22
If the computer will boot into ubuntu you can open a terminal and enter the following code:

```
sudo dmidecode --type 5,6,16,17
```

The output will tell you which dimm slot is occupied.

---

### Post by rmccutchan on 2010-02-22
Excellent!

The book says 1,2,3,4.  But when I run the command, it says 0,1,2,3.

I am going to assume that since ubuntu tells me that #1 is occupied, it is #2 according to the book.

Also, it says the speed is 667 mhz.  Does that sound correct for DDR3 1333 Kingston ram?

Thanks for the command!!  I am new and still learning.

---

### Post by paydaydaddy on 2010-02-22
667 MHz is the correct I/O bus clock for ddr3-1333 SDRAM.

---

### Post by rmccutchan on 2010-02-22
Cool.  Thank you very much for you expertise!  I really do appreciate the people here.

---

### Post by 3rdalbum on 2010-02-22
I thought 667MHz was a DDR2 speed. And not a fast one at that.

I believe Memtest (which can be accessed from the GRUB menu) will tell you what RAM slots are occupied with what RAM.

---

### Post by Pinoy915 on 2010-02-23
> **3rdalbum said:**
> I thought 667MHz was a DDR2 speed. And not a fast one at that.

I believe Memtest (which can be accessed from the GRUB menu) will tell you what RAM slots are occupied with what RAM.

DDR= double data rate. 667x2=~1333Mhz.

---

### Post by rmccutchan on 2010-02-23
Just got this reply from ECS:

*[FONT=Tahoma]**"T****he DIMM SLOT that is closest to the CPU socket is DIMM SLOT #1. And it goes up in number as you move further away from the CPU socket. "**[/FONT]*

Just in case somebody else has the same question in the future.

Thanks for the replies.

---

