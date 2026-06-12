---
title: "Graphics problem with new llvm / Unity"
date: 2012-10-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by emk2203 on 2012-10-04
I have two really old (> 10 years) Dell Latitude C840 laptops which are still capable of running a modern OS - I am running a dual-boot installation, and until now, both OSes (Windows and Ubuntu) ran everything without a problem. Every single hardware, including the dock with SCSI, is supported (the graphics driver needed some tweaking under Windows), but even Windows 8 runs without problems with this tweaked graphics driver - including transparency effects (Aero Design)!

They have Nvidia GForce4 440 Go graphics (NV17M, DirectX 7.0-capable), 1 GB RAM and the latest IDE harddisks with 320 G, so they are quite capable (with nice 1600x1200 screens).

With the advent of Quantal and Unity 2D gone, the machines are unusable with Ubuntu - termninals under X not even coming up, menus taking literally a minute to appear etc. etc.

I am **really** pissed that even MS Windows 8 runs with everything supported, while Ubuntu drops support for aging machines.

Is there anything to have them at least functional under Ubuntu without losing too much functionality? For example, last time I checked, comfortable network browsing with Xubuntu was gone, compared to standard Ubuntu (2 years ago?).

So, I am up for suggestions.

---

### Post by JRV on 2012-10-04
If I were you I would try Lubuntu.

---

### Post by grahammechanical on 2012-10-04
You are moaning about a version of Ubuntu that is still under development.

I started using 12.10 before Alpha 1 was released and it worked fine. Then things began to go wrong. First, it was with the Nvidia drivers. So, I stopped using them and switched to Nouveau. Which worked fine. Even gave me 3D until they started causing me problems.

The removal of Unity 2D, which in my opinion should not have happened without my approval, but it did happen, seems to have coincided with problems due to Xserver, Nvidia, Nouveau, Compiz. I could not install 12.10 Beta 2 without using the nomodeset option. I had 2 x 12.10 installs that I could not log into without first going through Recovery mode>resume.

Things have been so bad over the last few weeks that I have had to revert to using my 12.04 install in order to get any work done.

Are you sure that your problems are down to llvm/unity? And not to one of these other areas that have been discussed again and again in this section of the forum?

Wait for the final release. And install an alternative desktop if you need to. Or, stick to 12.04.

Oh, one final thing. A few days ago 12.10 was updated from Grub 1.99 to Grub 2.0. It has been causing some of us problems. So, watch out.

Regards.

---

### Post by Stinger on 2012-10-04
You could also try [Ubuntu Gnome Remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/") if you like Gnome / Gnome-Shell.
The Remix does not use compiz as Unity does :)

---

### Post by kansasnoob on 2012-10-04
Well, first, Ubuntu 12.04 is supported until April 2017 so you can keep using Precise and wait to see how things shape up in 13.04 or beyond. But I share your pain. 

I maintain about 23 desktops with 5 to 7 year old VIA P4M800 graphics and they would run either Unity-2D or [Gnome classic (no effects)]("http://ubuntuforums.org/showthread.php?t=1966370") previously, but they're a total no-go with Comiz + llvmpipe :(

I'm sure you already know about Lubuntu and Xubuntu but I've also been testing this:

[http://ubuntuforums.org/showthread.php?t=2064293](http://ubuntuforums.org/showthread.php?t=2064293)

And I wrote a brief review here:

[http://ubuntuforums.org/showpost.php?p=12272939&postcount=18](http://ubuntuforums.org/showpost.php?p=12272939&postcount=18)

Hope that might help a bit :)

---

### Post by emk2203 on 2012-10-05
@*JRV*: Yes, Lubuntu might be a solution, but as I said in the first post - what do I sacrifice? Has at least the access to network drives gotten better?

@*grahammechanical*: I know that Quantal is still under development. However, I am with Linux since kernel 2.0, and with Ubuntu since Warty. I have tested the development versions since Natty, and of all these, Quantal gave me the least problems - except for the aforementioned issues. I am surprised to hear that I was lucky.

I am not moaning about the issue, but about the design decision. I was always proud of Ubuntu when all hardware came up supported, everything everywhere worked out of the box. I could use the live cds for every pc for troubleshooting - if it didn't work under Ubuntu, hardware failure was the most likely explanation.

Maybe you are right, and I am barking up the wrong tree. Could be another issue, fixed in the final. But we are in beta2 stage now. I don't expect major changes until final. And the issues I am seeing look like this llvm setup simply overtaxes the CPU.

To offload tasks from the GPU to the CPU in scenarios where the CPU is as ancient or slow as the GPU is a bad decision. What were they thinking? That it ran OK on the developer's machine with a i7-3990K?

I just would love to have my standard, current Ubuntu support the broad range of hardware as it did all these years.

@*Stinger*: Ubuntu Gnome Remix sounds promising. Is it possible to install it from the standard Ubuntu install via apt-get (or a ppa)?

@*kansasnoob*: Yeah, that's my point exactly. Thanks for the links. Gnome Remix seems to be the thing now... :p 

With Gnome, you probably don't loose to much comfort. That was the dealbreaker with the last test of XFCE / Xubuntu. The fact that you couldn't mount network drives comfortably or browse Windows networks out of the box killed it for me.

---

