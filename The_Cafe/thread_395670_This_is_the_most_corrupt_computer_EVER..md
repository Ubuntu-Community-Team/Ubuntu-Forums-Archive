---
title: "This is the most corrupt computer EVER."
date: 2007-03-28
forum: The Cafe
---

### Post by SZF2001 on 2007-03-28
So, for school, we have these really nice server computers - the thing is, they seem to be *too* nice, for server computers.

I asked my teacher if I could try out Ubuntu on the computer, since I was going to buy myself a nice model - lo and behold, it runs off the LiveCD like a dream, like as if it were actually on the hard drive. I'm hooked, I'm ready to start looking. Then I get this idea in my head:

"Is there a 'broken' computer?"

When I say "broken", people usually think that Windows has done something wrong and just won't boot - their definition of "broke". I can "fix" this if I just install a new OS, right?

Here comes all the fun crap. This computer REALLY DOES SEEM TO BE BROKEN.

I boot it uip, just to see exactly what they mean by "broken" - it takes me to this screen:

```
Windoes could not start because the following file is missing or corrupt:
\WINDOWS\SYSTEM32\CONFIG\SYSTEM

You can attempt to repair this file by starting Windows Setup using the origional Setup CD-ROM.
Select 'r' at the first screen to start repair.
```

Two things you should know - one, I don't have or own the origional Windows Setup CD-ROM anyway, so that isn't an option. Another thing you should know, if I do press 'r' from here the computer just restarts.

Alright, that's fine. I can just install Ubuntu, right?

WRONG.

This is what happens when I try to install Ubuntu, Kubuntu, Xubuntu, or any of the alternative CDs (Hell, I even tried Fluxbuntu):

```
[17179569.504000] Call Trace:
[17179569.504000] [<c014916a>] __kmalloc+0x7a/0X90

It just keeps showing that kind of stuff - the acpi things, they seemed to load up alright.

Then we get to this:

[17179569.504000] [<c0101385>] kernel_thread_helper+0x5/0x10
[17179569.504000] Code: 8b 51 14 8d b6 00 00 00 00 8b 03 8b 6c (it just continues a string of numbers that go on and on... Wish I didn't have to type it all in)
[17179569.504000] <0>Kernel panic - not syncing: Attempt to kill init!
```

Now, let me make this clear - I just tried Ubuntu on another computer **exactly the same as the one I am getting these errors on**. They are exactly the same.

The kernel panics. WTF.

So I am going to try and install a server from the 5.10 disc, and hopefully that works.

What else can I do? Is there a way to reformat the whole thing through the BIOS screen or something? This computer is basically screwed over, may as well start it out fresh and install Ubuntu...

Help help, please help. I am a lost cause. :mad:

EDIT: I also forgot to mention that I did a Memtest on this computer - everthing that revolves around being corrupt has to do with RAM. Could someone have stolen the RAM cards or something? Why wouldn't any sort of kernel, Linux or Windows, even be able to sync or work with this thing?

---

### Post by fenian on 2007-03-28
Download GParted and use it to reformat the drive to ext3.You should then be able to install Ubuntu
however Windows will be lost.If you need to keep Windows try defragging the drive before installing
Ubuntu.

---

### Post by use a name on 2007-03-28
If your ram is toast, then so are you. ;) No kernel can run on toasted ram.

---

### Post by SZF2001 on 2007-03-28
This JUST MIGHT WORK! Oh my GOD you are a hero.

I need to use it on my flash drive since I'm still in school right now and I can't get out of here with this computer unless I got Linux installed and stuff.

So... do I need to format my USB drive or anything? Yes, the BIOS will recodnize it, I've just never used a Flash stick before...

EDIT: Who knows, it might not be the ram... I'll just have to have hope though.

---

### Post by ice60 on 2007-03-28
maybe the answer is somewhere here -
[http://www.kellys-korner-xp.com/xp_sys32.htm](http://www.kellys-korner-xp.com/xp_sys32.htm)

you might be able to copy over, or restore, some registry keys, or whatever part of the registry is needed.

---

### Post by kevinf311 on 2007-03-28
mmm... toast.

It might be a DIMM slot problem too. I was having a fun round of Kernel Panicks a while back after I bought some more RAM. I thought the new stick I had purchased was bad, but it turns out that only my first DIMM slot functions correctly. Luckily the stick I had just received was a 1GB stick so I can run on just that.

I figured this out by running memtest for a day or two through every permutation I could think of between 4 sticks of RAM and increasing numbers of DIMM slots. I noticed a problem and could predict a failure when the memtest that my computer does after the POST spit back a number that was less than the sum of the RAM plugged in.

I just can't figure out why everything was working fine with the 3 sticks of 256 in slots 1, 2, and 3 :confused: 

Oh well, hope you get everything worked out.

---

### Post by IYY on 2007-03-28
If even the liveCD doesn't boot up, re-formatting won't help. It must be some broken hardware: not the hard disk, probably the memory or motherboard. Try doing a memtest (can be done from the LiveCD without booting into the OS).

---

### Post by Dual Cortex on 2007-03-28
Not much of help but just wanted to comment that yeah.... PC's at school through a liveCD run faster than my PC.
Oh well... still waiting for the day I can buy*myself* a good PC.

---

### Post by SZF2001 on 2007-03-29
Here's an update on the whole issue...

So, pretty much, the hard drive is corrupt. Some Windows files can't be found, so it never mounts, so that's why the kernels can't sync - neither Windows or Linux.

So here's the thing - I was rummaging through the Kubuntu LiveCD, and realised it has a partitioner (and I remember burning GParted, as well). I got an idea in my head - maybe I could take the hard drive from the corrupt computer over to a working one and partition it, basically clean the whole thing?

I've tried the GParted CD by itself - it can't find any partitions, and when it does it just bring it back to the Windows press 'r' screen I mentioned before.

But I can't just take apart this computer at school, let alone two. I don't have the techie kid status for some reason. Go figure.

If I just took a network cable - one that people plug in from their computer to a DSL/Cable box - could Ubuntu recodnize the other connected computer and I could partition it from there like that? But how can I even do that if there is no kernel to be found in the first place?

Maybe I really should go looking for this Windows XP disc...

---

### Post by use a name on 2007-03-29
In your firt post you mention trying to get it installed and running a memtest that reports errors. I assume you've only tried to boot a live/install cd, but that one already crashes. If that's the case, then the hd has not been touched yet. As for windows, the install can be broken (may happen when your ram is toast) or it's just a plain ram error again.

If my assumption was right, then focus on the ram first. Try with one module on different slots first, to see if that module is broken or if slots are broken.

It still can be something else of course, but don't blame the hd yet. Eliminate the ram problem first.

---

### Post by Tomosaur on 2007-03-29
> **SZF2001 said:**
> Here's an update on the whole issue...

So, pretty much, the hard drive is corrupt. Some Windows files can't be found, so it never mounts, so that's why the kernels can't sync - neither Windows or Linux.

What? That makes no sense. Linux doesn't look for Windows files at all, you're just way off base here. A broken hard drive? Maybe. Corrupt Windows files? No. Linux does not need Windows files. It is possible the Windows files ARE corrupt, but it's certainly not the cause of your kernel panic.

> 
So here's the thing - I was rummaging through the Kubuntu LiveCD, and realised it has a partitioner (and I remember burning GParted, as well). I got an idea in my head - maybe I could take the hard drive from the corrupt computer over to a working one and partition it, basically clean the whole thing?

I've tried the GParted CD by itself - it can't find any partitions, and when it does it just bring it back to the Windows press 'r' screen I mentioned before.

But I can't just take apart this computer at school, let alone two. I don't have the techie kid status for some reason. Go figure.

If I just took a network cable - one that people plug in from their computer to a DSL/Cable box - could Ubuntu recodnize the other connected computer and I could partition it from there like that? But how can I even do that if there is no kernel to be found in the first place?

Maybe I really should go looking for this Windows XP disc...

You're really barking up the wrong tree here, I'm afraid. Let's look at what you've found so far:

1) The LiveCD works.
2) Anything on the hard drive doesn't.
3) The same problem happens when you try to use a different computer with the same hardware.

Therefore, your issue is hardware.

If the LiveCD will allow you to install Ubuntu correctly, but Ubuntu won't actually boot from the hard drive, then it certainly does look like a faulty hard drive. The LiveCD runs from RAM, so obviously the RAM hasn't been stolen. It is possible it is faulty RAM, but you would expect the LiveCD to fail if that were true.

I'm going with dodgy hard drive. It is not simply a matter off corrupt files. It is possible there ARE in fact corrupt files, but since Ubuntu fails to boot, it is more likely that the real problem is a fault in the hardware.

---

### Post by Albi on 2007-03-29
Why don't you run memtest86 overnight to make sure it's **not** the ram?
[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)

---

### Post by nihilocrat on 2007-03-29
Beyond reiterating that you should make sure your RAM is okay, I would also like to point out that I've had problems with hardware compatibility on installed Ubuntu systems (namely, server installs from the Dapper 'alternative' CD). Ubuntu didn't like my RAID controller (a Compaq SMART array on a Proliant of some sort) because it didn't load the proper kernel drivers for it. Because I was booting off of a drive on the array, I couldn't just put 'cpqarray' in my /etc/modules file, I had to make my own initrd image. I don't distinctly remember if the kernel panicked or if it kindly remarked that it had no root partition to boot off of.

---

### Post by SZF2001 on 2007-03-29
Wow, I'm not sure what the hell I was tripping on when I wrote that last giant post...

I basically told the tech center (school tech people, basically) that their hard drive is corrupt and ram is fried. And also, there is only one fan out of two working on said computer (who'd a thunk it?). Maybe they will get around to fixing it, or just give it to me for me to fix (this'll be some work, I think).

I know that Linux doesn't depend on Windows and vice versa. I was able to make a complete successful install on another computer like it, so I knew that Ubuntu could work on these ThinkCentre computers. In fact, I installed it on another ThinkCentre just to make sure - yup, everything was good.

I did leave the tests going all night, over night, at school - I got permission to leave it going for the sake of a grade, or something. I dunno. We'll have to deal that out later...

Thanks for the help, guys. I tried, honestly. If I could open it up and see whats up, I would - too bad it's the schools.

---

### Post by Feenix3k on 2007-03-29
When the live disk is booting push f6 instead of load/install.

At the end of the Boot:  line add acpi=off or noacpi

this sound like my desktop when I tred to put Ubuntu in. I had to use 6.10 on my desk because it was too new for 6.06

---

### Post by SZF2001 on 2007-03-30
Meh, that didn't work on either Breezy, Dapper, or Edgy. Harddrive is screwed.

---

### Post by daynah on 2007-03-30
Pleease take the computer apart. Get alone in the room, just start taking stuff apart. Bring extra cords from home. Cords that don't even belong, like as many tv cords as you can find in your basement, ya? And when someone walks in just hold up some of the guts of the computer, cords trailing out to the floor, and look real pitiful like you just turned back into Dr. Jekyl...

"I... I just don't know what happened..."

And get someone in a closet to video tape it all so I can see their face. :)

---

### Post by SZF2001 on 2007-03-30
If I even try to take this baby home (which God, I wish I could, my computer is so crap - 128 RAM alone is enough of a reason for a new computer), they will call the cops on me if it leaves school grounds. They'll know it's the kid who's been screwing around on it and doing memory tests and trying to partition it.

---

