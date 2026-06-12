---
title: "Windows in VirtualBox for gaming"
date: 2010-11-26
forum: The Cafe
---

### Post by Oxwivi on 2010-11-26
Is such a solution a considerable? Forget  the having to buy Windows part - would games work in virtual Windows?

---

### Post by snowpine on 2010-11-26
Virtual Windows = Windows

The games should run fine, so long as the virtual machine meets the game's hardware requirements (for example you may not be able to play games that require a specific graphics card).

---

### Post by Oxwivi on 2010-11-26
The reason I've posted this thread is because, AFAIK, VirtualBox emulates the hardware. But according to what you say, if I have a latest GPU, I can play the latest games without a hitch, am I right?

---

### Post by Oxwivi on 2010-11-26
And what of the strain of running two OSes at once?

---

### Post by Red_Steve on 2010-11-26
Actually you are wasting ressources by having a virtual windows. 
Als don't expect your emulated hardware to be as snappy as it would be under ubuntu.

If you are planning to play games made for windows, I' recommend installing wine and playonlinux and do some (by some I mean at least have a look at the wine appDB) research as this WILL be much better for your system load.

---

### Post by snowpine on 2010-11-26
> **Oxwivi said:**
> The reason I've posted this thread is because, AFAIK, VirtualBox emulates the hardware. But according to what you say, if I have a latest GPU, I can play the latest games without a hitch, am I right?

Your physical hardware is irrelevant. The **virtual machine **needs to meet the game's hardware requirements.

Curious if you have read the VirtualBox manual yet? You may find this section particularly relevant: [http://www.virtualbox.org/manual/ch03.html#id458608](http://www.virtualbox.org/manual/ch03.html#id458608)

---

### Post by Oxwivi on 2010-11-26
I wonder if I can port Windows' actual DLLs into WINE.

---

### Post by Red_Steve on 2010-11-26
> **Oxwivi said:**
> I wonder if I can port Windows' actual DLLs into WINE.

What for? Most games already check for needed DLLs and would install them if missing.

But it will work as long as the DLLs and your windows version used by wine are the same.

---

### Post by snowpine on 2010-11-26
I wonder if you've considered a "dual boot" setup? This would allow you to choose between Windows and Ubuntu each time you turn on the computer, so you can run Windows apps natively in Windows (and Linux apps natively in Ubuntu).

---

### Post by joepie91 on 2010-11-26
In my experience running games in a virtual machine is absolutely horrible. The virtual machine I have has permission to use pretty much all hardware in my machine yet it's terribly laggy, responds slow, often freezes for a few seconds, etc.

I'd recommend using PlayOnLinux, Cedega (does that still exist?), or something similar.. or just set up a dualboot.

Myself, I just got a new PC and I now just have a dual PC setup. My Linux machine is always running, the Windows machine only when I want to do gaming or website testing under IE. I just have a KVM switch to switch between computers and the audio is looped from the Windows Line-out to the Linux machine Line-in... and then handled by PulseAudio. My main monitor is switched between the two PC's through the KVM switch, while my secondary monitor is always connected to my Linux machine so I can keep an eye on incoming messages on Pidgin, downloads, etc. That's the best way for me, but it does require two machines.

---

### Post by Oxwivi on 2010-11-26
> **Red_Steve said:**
> What for? Most games already check for needed DLLs and would install them if missing.

But it will work as long as the DLLs and your windows version used by wine are the same.
Well, most of the problems of running under WINE lies with DLLs, since the one in Windows and in WINE are not exactly the same, and may possibly be incomplete or behave dissimilarly. Using native Windows DLLs will eliminate the problem.

Thanks, joepie91, I was also looking for someone with hands-on experience.

And actually, I'm gathering info for a friend of mine (I'm stuck with a Pebtium IV and 10 GB HDD and amazingly still run Windows XP in VB); but the problem lies with games. He already tried Ubuntu, but doesn't want to dual boot. I doubt he'd bother messing with WINE either.

---

### Post by joepie91 on 2010-11-26
> **Oxwivi said:**
> Well, most of the problems of running under WINE lies with DLLs, since the one in Windows and in WINE are not exactly the same, and may possibly be incomplete or behave dissimilarly. Using native Windows DLLs will eliminate the problem.

Thanks, joepie91, I was also looking for someone with hands-on experience.

And actually, I'm gathering info for a friend of mine (I'm stuck with a Pebtium IV and 10 GB HDD and amazingly still run Windows XP in VB); but the problem lies with games. He already tried Ubuntu, but doesn't want to dual boot. I doubt he'd bother messing with WINE either.

I think the problem with using native DLLs is that you can't use them if you don't have a legal Windows license, however if you have a legal Windows license you accepted the EULA which, if I recall correctly, states you cannot use any system files and libraries outside of a Windows environment. Which makes implementing an 'import native DLLs' feature, an encouragement to breaking the EULA, which, I think, the developers can be held responsible for. I may be wrong, but this is as far as I know how the EULA for Windows works :P

And it's a lot easier to just install PlayOnLinux. It will take care of the needed WINE versions and configurations automatically.

---

### Post by Oxwivi on 2010-11-26
Oh yeah, the EULA... Dashes my dreams... :'(

LOL

---

### Post by Ric_NYC on 2010-11-26
Optimize the virtual machine by changing the Display settings:


Settings>Display>Video Memory

[IMG]http://img822.imageshack.us/img822/2596/11454464.png[/IMG]

---

### Post by forrestcupp on 2010-11-26
Virtual machines are not made for gaming.  They're made for keeping businesses and offices working.  Like someone else said, your hardware doesn't matter; it's the VM's virtualized hardware that matters.  Unfortunately, the virtual video card is crappy and support for 3D is extremely lacking.  After a lot of tweaking and headaches to get it to be the best possible, it still sucks.  That's because VMs are not made for gaming at all.

> **Oxwivi said:**
> He already tried Ubuntu, but doesn't want to dual boot. I doubt he'd bother messing with WINE either.

Then he's out of luck.  I want to be in the Bahamas right now, but I don't want to walk, swim, drive, fly, or take a boat there. ;)

---

### Post by CharlesA on 2010-11-26
> **forrestcupp said:**
> Virtual machines are not made for gaming.  They're made for keeping businesses and offices working.  Like someone else said, your hardware doesn't matter; it's the VM's virtualized hardware that matters.  Unfortunately, the virtual video card is crappy and support for 3D is extremely lacking.  After a lot of tweaking and headaches to get it to be the best possible, it still sucks.  That's because VMs are not made for gaming at all.

+1.

I've tried it before and the only thing I was able to get to run "decently" (5fps) was D2 and that was with the direct draw driver.

---

### Post by Paqman on 2010-11-26
> **Oxwivi said:**
> if I have a latest GPU, I can play the latest games without a hitch, am I right?

No. 3D graphics emulation is in it's infancy in Virtualbox. Recent versions do enable you to at least do some 3D graphics, which you couldn't before, but you won't be running anything recent, and even older games don't work 100%.

---

### Post by Oxwivi on 2010-11-26
> **forrestcupp said:**
> i want to be in the bahamas right now, but i don't want to walk, swim, drive, fly, or take a boat there. ;)
+++ :)

---

### Post by Ric_NYC on 2010-11-26
**Virtualbox 2.1 OpenGL 3D Accelerated Gaming Demo**

[http://www.youtube.com/watch?v=XiZyigv_aRc](http://www.youtube.com/watch?v=XiZyigv_aRc)

---

### Post by cariboo on 2010-11-26
We're up to Vbox 3.2.10, and 3d graphics are still the pits. The new version of Unity still won't run.

---

