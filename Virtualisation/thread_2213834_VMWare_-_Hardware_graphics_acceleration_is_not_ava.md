---
title: "VMWare - Hardware graphics acceleration is not available"
date: 2014-03-28
forum: Virtualisation
---

### Post by curtranhome on 2014-03-28
Hey everyone,

Information about my build, to try and help with your guy's diagnostics:

I've advanced from windows 7 to linux cause I refuse to go to 8, so please pardon me if I ask some low-level questions. Any who, I have a weird setup that needs some attention from professionals. I have 2 totally different graphics cards in my machine, one is a cheap-o MSI ($30 give or take) and the other is an ASUS GTX650-E-2GD5 GeForce GTX 650 with 2 gb of RAM (~$140). I've got the two of them in there because each card has one HDMI port and I needed HDMI for my new monitors and windows did not like the fact I was running 2 monitors off of 2 different cards (which is another reason why I switched over). I also am in school for network administration and getting my MCSE (Microsoft Certified Solutions Expert) cert for windows server 2012 and they require me, as a student, to be able to run virtuals. Well, I CAN run them but the graphics in the interface suck and I also would like to run gaming inside of a windows virtual. I'm currently sitting on 32 gb of RAM, so there is no issue with that (no joke), and have a 1 tb HDD and a 100 gb SSD (my OS drive), thanks to ubuntu I actually have some breathing space on my SSD.

Specifics:

When I start up VMWare 10 and get a virtual running, I get an error (as mentioned in the title) on top of a second error: "No 3D support is available from the host." When I open the message log and click on the first error (the one in the title), I get the following description:
        "As a result, this virtual machine may experience very low graphics performance. Follow the instructions provided by your graphics card vendor or Linux distribution in order to update your computer's OpenGL drivers."

The 3D error is just saying it will be disabled.


Any ideas on these messages?

---

### Post by richardsdma on 2014-04-24
the same problem here. 
i have vmware player installed on a ubuntu 14.04 host and, while i start windows XP (as guest) i get the warning that the hardware acceleration is not available on the host. 
a have a laptop with an 2008 ati x1270, radeon OSS driver. 
is there any chance to enable hardware acceleration for this configuration? 
thenx.

---

### Post by hoc3010 on 2014-07-23
I got this problem, too.

I am using Dell Vostro 3550 with Intel HD 3000. I installed driver by Intel-Linux-Graphic-Installer.

---

