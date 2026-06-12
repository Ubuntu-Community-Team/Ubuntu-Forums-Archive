---
title: "Problems With 14.04 Install"
date: 2013-10-24
forum: Ubuntu Development Version
---

### Post by NM5TF on 2013-10-24
I have Ubu 14.04 on a bootable USB stick for testing...:!:

It boots fine, but has some display driver issues....using a Nvidia graphics card
that exhibits the same problems I had coming from Ubu 10.04 to 12.04....zig-zag
lines, hung screens, etc....#-o

question: would it be beneficial going to 13.04 from 12.04 before going to 14.04 :-s

or is there some other sequence I should do 1st ??? 12.04 to 12.10 to 13.04 to 14.04 maybe :confused:

TIA...Tommy

---

### Post by NM5TF on 2013-10-24
I have Ubu 14.04 on a bootable USB stick for testing...

It boots fine, but has some display driver issues....using a Nvidia graphics card
that exhibits the same problems I had coming from Ubu 10.04 to 12.04....zig-zag
lines, hung screens, etc....

question: would it be beneficial going to 13.04 from 12.04 before going to 14.04 

or is there some other sequence I should do 1st ??? 12.04 to 12.10 to 13.04 to 14.04 maybe 

TIA...Tommy

---

### Post by VMC on 2013-10-24
There's a problem with *nouveau* for sure. I have a bug report on the System-Settings freeze. The "zig-zag" lines I only had on Kubuntu. I solved that by first boot using *nomodeset* and then from second boot on *nouveau* worked fine.

---

### Post by NM5TF on 2013-10-24
> **VMC said:**
> There's a problem with *nouveau* for sure. I have a bug report on the System-Settings freeze. The "zig-zag" lines I only had on Kubuntu. I solved that by first boot using *nomodeset* and then from second boot on *nouveau* worked fine.

@VMC.....thanx for quick reply...

for clarity I have NOT installed 14.04 yet....using a "live" session to be certain
14.04 works with my HW 1st....

can I get to the boot screen to use nomodeset from a "live" session ??

if so, how ??

I see no grub menu to edit the boot file....

Tommy

---

### Post by VMC on 2013-10-24
I think its 'F6' and then go to the end of the line , type a space then *nomodeset, *thenreturn. I use loop-back and haven't used the cd/dvd install in a while.

---

### Post by NM5TF on 2013-10-24
> **VMC said:**
> I think its 'F6' and then go to the end of the line , type a space then *nomodeset, *thenreturn. I use loop-back and haven't used the cd/dvd install in a while.

thanx...will try that....

BTW...you have exactly same HW as mine...AMD Athlon K8-64 Dual Core + NvidiaGEforce 6150se graphics
so it must be possible to make it work

Tommy

---

### Post by NM5TF on 2013-10-24
OK nomodeset worked for the display problem...

now if I can just get my wifi working reliably I'll be happy

have already tried blacklisting the native realTek drivers
and running RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip
but it crashed...maybe it's for an older kernel ???

will check the forums for wireless problems under 14.04

---

### Post by oldfred on 2013-10-24
Moved to Ubuntu +1.

You do know that 14.04 will not be released until 2014, in month o4? 
Only testers that want to look for bugs should be attempting to use it. Plus the daily just opened so it is mostly just 13.10, but may change and break daily.

---

### Post by cariboo on 2013-10-24
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by VMC on 2013-10-24
> **NM5TF said:**
> thanx...will try that....

BTW...you have exactly same HW as mine...AMD Athlon K8-64 Dual Core + NvidiaGEforce 6150se graphics
so it must be possible to make it work

Tommy
Since we have the same nvidia graphics, please go to my bug report on this problem and click that "[This bug effects you]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1242767")", thanks.

---

### Post by NM5TF on 2013-10-24
> **VMC said:**
> Since we have the same nvidia graphics, please go to my bug report on this problem and click that "[This bug effects you]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1242767")", thanks.

done...

---

### Post by NM5TF on 2013-11-02
marking this thread SOLVED now

got rid of nouveau video driver & installed nvidia-current...display freezing/smearing
now solved....

wifi now working with 3.11 kernel by following directions in this thread:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

Tommy

---

