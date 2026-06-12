---
title: "Hardware question"
date: 2010-12-26
forum: The Cafe
---

### Post by 3Miro on 2010-12-26
My machine is acting funny and it is not a software issue, I need general advice on how to approach this, because it is very random.

Motherboard: GA-880GMA-UD2H Gigabyte (latest BIOS)
CPU: Phenom II X6 CPU
RAM: DDR3 Kingston KVR1333D3N9K2/4G
Video: ASUS Nvidia GTX 260

Using Gentoo (latest kernel) and Windows 7 (for testing to make sure it is the hardware and not some driver)

Bad symptoms: 
1. Random crashes, kernel panic, Xorg crashes, BSOD, sometimes I can play games for hours, sometimes it crashes in minutes. Windows 7 runs as if it were ME. Gentoo is mostly usable, crashing every other day.

2. Sometimes right after a crash, the machine will not post and it will give the error code for "bad memory". I will have to wait for 2 - 3 minutes before I can boot again (or clear the CMOS).

3. I tried memtest (from Xubuntu 10.10 liveCD). At 1333 memtest will consistently fail (although at always at a different spot). If I test the modules individually, memtest passes (I test it for 2 passes). With a single module the BIOS gives it as 1333 memtest gives it as 400 (i.e. 800). If I down-clock the RAM to 1066, memtest passes.

4. Here is the really strange one: sometimes after a crash, the LAN will fail. Both under Gentoo and Windows. To get the LAN back, I will have to clear the CMOS.

I can RMA the parts, but I have to know which one is causing the trouble. I don't want to RMA the wrong thing. Can anyone think of another test that I can make?

---

### Post by jerenept on 2010-12-26
Sounds like overheating..... are you overclocking, or the like? sometimes that would cause problems.

The memory as well, it may be overheating...

---

### Post by 3Miro on 2010-12-26
> **jerenept said:**
> Sounds like overheating..... are you overclocking, or the like? sometimes that would cause problems.

The memory as well, it may be overheating...

Thanks for the idea, it is worth considering.

I don't do Over-clocking.

Memory doesn't have heat sensor, so I don't know if it is bad. Unfortunately, RAM is also close to the CPU (due to the motherboard layout). 

Under Linux CPU idles in low 20C and goes to high 30C when under full load (according to lm_sensors). Windows reports similar values. Note that this is lower than my previous CPU that was in the same case (with different mobo and DDR2 RAM).

GPU under Windows goes to 58-60C (heavy gaming), I cannot check it under Gentoo (Gentoo has some issues Nvidia settings).

I guess I can try to see if I can get one of the case fans to blow air straight on the RAM and if this will improve the issue.

---

### Post by jerenept on 2010-12-26
Doesn't sound like overheating to me, if you're getting those kinds of temps. My system runs at 2x that, and is pretty stable.

If it works when one RAM chip is out, try exchanging the RAM modules, sometimes this works for me, I have no clue why ???.

Is this a DIY system? How old is it, have you always had these problems?

---

### Post by jerenept on 2010-12-26
Oh, and, the CMOS battery may be loose, or missing (or dead) you might want to check that out.

---

### Post by 3Miro on 2010-12-26
> **jerenept said:**
> Doesn't sound like overheating to me, if you're getting those kinds of temps. My system runs at 2x that, and is pretty stable.

If it works when one RAM chip is out, try exchanging the RAM modules, sometimes this works for me, I have no clue why ???.

Is this a DIY system? How old is it, have you always had these problems?

Thanks for the rely.

Except for the video, which I have had for a white, the system is DIY and only a week old. I have been doing my own machines since 2001 (about 10 machines), nothing has ever been as unstable as this one. The Video dies once in July and I had to RMA that one, but I have had no trouble since then, memtest also fails with another Video Card.

I did try changing the DIMM slots earlier. Did not help.

I tried feeling the temperature inside the box while it was working (very carefully). The area around the RAM is considerably hotter (even hotter than the CPU heat-sync).

---

### Post by 3Miro on 2010-12-26
> **jerenept said:**
> Oh, and, the CMOS battery may be loose, or missing (or dead) you might want to check that out.

BIOS has no trouble remembering the settings. I only have to clear the CMOS if the LAN dies.

---

### Post by jerenept on 2010-12-26
I honestly can't help you..... I think that the Hardware forum would be a good place to start..

---

### Post by 3Miro on 2010-12-26
> **jerenept said:**
> I honestly can't help you..... I think that the Hardware forum would be a good place to start..

Thanks for for posting, you are helpful. I know what the problem is, I have a defective piece of hardware. I think it is the RAM, but I am not feeling confident enough, so I was hoping someone can give me advice on what else I can test to make sure. I just opened the box and aimed couple of fans right at the RAM, needless to say, it failed at speed 1333. I do think it is the RAM, I will probably just order a new pair.

Hardware forum is for Linux related drivers and my problems have nothing to do with Linux or Ubuntu. That's why I placed the thread here (I have seen other people ask for hardware related advice here).

---

### Post by handy on 2010-12-26
I'd start at the RAM. Is it possible to swap in a piece from another machine, a friend's machine? Known good for possible bad is unfortunately the best kind of testing available to us.

Your CMOS battery is not dead, if it were you would have seen clues; depending on the BIOS, it may or may not find your drives, it would definitely have the wrong date/time & any other custom settings would all go back to the defaults on a cold boot.

As far as checking for cooling is concerned, if you have a household table fan, you can take the cover off & expose the electronics to the fan blowing air on it. I've known people who have run their machines like that for quite some time. It works, though if you have a heating problem it still doesn't resolve just exactly what is getting hot.

Full circle, I'd start at the RAM, heat/faulty?

---

### Post by 3Miro on 2010-12-26
> **handy said:**
> I'd start at the RAM. Is it possible to swap in a piece from another machine, a friend's machine? Known good for possible bad is unfortunately the best kind of testing available to us.

Your CMOS battery is not dead, if it were you would have seen clues; depending on the BIOS, it may or may not find your drives, it would definitely have the wrong date/time & any other custom settings would all go back to the defaults on a cold boot.

As far as checking for cooling is concerned, if you have a household table fan, you can take the cover off & expose the electronics to the fan blowing air on it. I've known people who have run their machines like that for quite some time. It works, though if you have a heating problem it still doesn't resolve just exactly what is getting hot.

Full circle, I'd start at the RAM, heat/faulty?

Thanks, I will feel better ordering new RAM. I have 3 desktops, but this one is the only one with DDR3 (and it was supposed to be the crown-jewel of my collection), so I can only get new RAM now. Lowering the RAM speed to 800 seems to have stabilized Windows, further indication about the RAM.

---

