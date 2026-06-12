---
title: "I just built my first kernel!!"
date: 2008-04-17
forum: The Cafe
---

### Post by myusername on 2008-04-17
I just built my first kernel and I optimized it for a pentium 4!! :) right now its compiling

---

### Post by Triggerhapp on 2008-04-17
Congrats!! But why XD

---

### Post by myusername on 2008-04-17
because I am trying to see how fast I can make my system

---

### Post by Triggerhapp on 2008-04-17
Fair deal! I manage to break most things in my machine, so I shall refrain from squeezing most performance out and be happy with my setup asis for now :P

---

### Post by fedex1993 on 2008-04-17
did you build your own kernel on ubuntu i would like to today that for my laptop to speed it up a bunch :)

---

### Post by Whiffle on 2008-04-17
Congrats :)  Post again when it boots :D 

Kernel compiling really isn't all that bad, is it? :)

---

### Post by Joeb454 on 2008-04-17
I've compiled a kernel before :) Admittedly it was in a VM so I couldn't care less if it didn't boot ;)

---

### Post by aktiwers on 2008-04-17
KernelCheck does a great job too..  I both used that and done it manually..  damn it takes a long time to compile :D

---

### Post by bobdob20 on 2008-04-17
Ive compiled a kernel before and it booted, but my wireless didn't work so i just went back to the normal kernel.

---

### Post by aktiwers on 2008-04-17
You need to install drivers for that again

---

### Post by bobdob20 on 2008-04-17
Which drivers would that be? cos it worked out of the box with the other kernel.

---

### Post by swoll1980 on 2008-04-17
> **bobdob20 said:**
> Which drivers would that be? cos it worked out of the box with the other kernel.

the driver was already a part of the first kernel

---

### Post by andrewabc on 2008-04-17
Can you post links on what you used to learn how to custom compile the kernel?
I have no idea what to do, but think it would be nice to do for old computers.

---

### Post by original_jamingrit on 2008-04-17
Don't forget to edit Grub so that it's able to boot both your new and old kernel.  An annoying mistake to make, whether or not your new one works properly :-P

---

### Post by aktiwers on 2008-04-17
> **andrewabc said:**
> Can you post links on what you used to learn how to custom compile the kernel?
I have no idea what to do, but think it would be nice to do for old computers.

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by odiseo77 on 2008-04-17
I've compiled the kernel for different reasons (mainly to add some hardware and for experimenting and learning), but I haven't noticed any performance improvement. Maybe I didn't get very well the difference between monolithic kernel and modular kernel (I have a general idea, though) and included lots of stuff and drivers I didn't need (but anyway, it's a good learning experience, besides being fun).

---

### Post by myusername on 2008-04-18
it boots up WAY faster than the stock xubuntu kernel....but my wireless card didn't seem to work even with ndiswrapper so i am on a live cd and ill try it when hardy comes out...and btw here is how i learned to do it
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
[http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile](http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile)
definitions of everything you need to turn off:
[http://ubuntuforums.org/showpost.php?p=1174954&postcount=507](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507)

---

### Post by Eclipse. on 2008-04-18
KernelCheck is a nice program that will build and install custom kernels for you aswell as leaving a .deb incase you need to reinstall.

I have always had to reinstall my nvidia drivers with new kernels but apart from that using custom kernels is alot better.

Theres a few guides (google is your friend) that give some tips for when configuting which really speed things up alot.

---

### Post by Whiffle on 2008-04-18
> **odiseo77 said:**
> I've compiled the kernel for different reasons (mainly to add some hardware and for experimenting and learning), but I haven't noticed any performance improvement. Maybe I didn't get very well the difference between monolithic kernel and modular kernel (I have a general idea, though) and included lots of stuff and drivers I didn't need (but anyway, it's a good learning experience, besides being fun).

Yeah I have too, never got much of a performance boost out of it.  I don't even bother on my desktop anymore, sometimes I might on my laptop to get patches for HDAPS or some other such thing.

---

### Post by myusername on 2008-04-18
i didn't really notice a preformance boost but i did notice that my boot up time was about five-ten seconds faster and its a great learning experience

---

### Post by kinematic on 2008-04-18
Kernel compiling is nice and easy once it has become a routine. Right now I'm on 2.6.25-kinematic_17 (the last number being the number of custom kernels I've rolled). I always strip out everything I don't need and compile the file system/disk driver into the kernel so I also don't need and initrd. Small and lean kernels are the way to go for speeding things up.

---

### Post by andrewabc on 2008-04-18
So how do yuo know what to say y/n/m/? to when compiling?
Also once you get to the make xconfig and got all those options how do you know what to keep or lose?
Is there a way for it to know what hardware your computer uses and only use options for it?

I've got one compiling now, but I pressed whatever was the first for all the y/n/m questions and left most of make xconfig the same. Does this mean my custom kernel will be similar to the one already installed?

---

### Post by fwojciec on 2008-04-18
> **andrewabc said:**
> So how do yuo know what to say y/n/m/? to when compiling?
Also once you get to the make xconfig and got all those options how do you know what to keep or lose?
Is there a way for it to know what hardware your computer uses and only use options for it?

Basically the answer to your questions is: you have to know what you're doing.  Most distributions provide a one-size-fits-all modular kernel these days that works pretty much as well as a highly customized kernels since, in either case, only the modules that are needed on a particular system are going to be loaded during boot.

Having said that, it's fun and educational to learn how to optimize a kernel for a given set of hardware components, but there isn't an easy solution/guide that will walk you through it.  To learn how to do it requires a lot of patience, googling a lot, learning about the hardware your computer uses and how the kernel deals with it, as well as a lot of systematic trial and error with different configuration options.

In general I'd recommend sticking to the default kernel -- unless you're willing to spend a lot of time to overcome a somewhat steep learning curve at first.  The performance benefits of having a custom compiled kernel, in most cases, are going to be in the "placebo" range, i.e. negligible.

> **andrewabc said:**
> I've got one compiling now, but I pressed whatever was the first for all the y/n/m questions and left most of make xconfig the same. Does this mean my custom kernel will be similar to the one already installed?

If you actually get it to work at all it'll probably be, essentially, the same as the default kernel.

---

### Post by andrewabc on 2008-04-18
It took an hour to compile my kernel. I had no idea what I was doing.
I booted into it and it got past the ubuntu loading bar, then went to a black screen and did nothing.

My custom kernel image is 510 mb compared to ubuntus 62mb image.

Looks like I'll be sticking with ubuntus kernel for a long time :P

---

### Post by aimran on 2008-04-18
Is it monolithic or is it micro?

---

### Post by andrewabc on 2008-04-18
> **aimran said:**
> Is it monolithic or is it micro?

If you are asking me I have no idea. And I deleted the custom kernel already so I won't know.

---

### Post by Whiffle on 2008-04-18
If you're using the ncurses interface to configure your kernel you can press ? and it will provide some help.  Knowing what hardware your computer has is often as simple as looking through the output of lspci and dmidecode.

---

