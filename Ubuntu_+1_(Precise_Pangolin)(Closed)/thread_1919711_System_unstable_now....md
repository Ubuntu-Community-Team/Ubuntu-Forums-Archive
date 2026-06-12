---
title: "System unstable now..."
date: 2012-02-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by exploder on 2012-02-03
I just installed today's updates (2/3) on my Ubuntu 12.04 x64 install in Virtualbox and the system is unstable now. The desktop turns black, applications do not render right, launcher does not respond, etc.

The alpha 2 release was pretty stable. Is anyone else seeing this with a Virtualbox install?

---

### Post by Sworddragon on 2012-02-03
I have some major problems which I hope that they will get solved:

- With the new X-Server I'm seeing bad fonts and graphics.
- lxdm-binary is using 100% cpu time of one core.
- Wine is crashing with the new X-Server.

---

### Post by exploder on 2012-02-03
Just tried Unity 2D and it works fine in Virtualbox.

---

### Post by exploder on 2012-02-04
I did a wubi install on my HP laptop today and the problems I was seeing in VirtualBox are not showing up on the installed system.

---

### Post by kevpan815 on 2012-02-04
> **exploder said:**
> I just installed today's updates (2/3) on my Ubuntu 12.04 x64 install in Virtualbox and the system is unstable now. The desktop turns black, applications do not render right, launcher does not respond, etc.

The alpha 2 release was pretty stable. Is anyone else seeing this with a Virtualbox install?

I did have some small minor issues with yesterdays updates (Compiz Crashed for one thing) and a few other things like you described as well, however it all straightened itself out after the 20 updates that were being held back using sudo apt-get update and sudo apt-get upgrade finally installed just fine using the update-manager instead of the terminal to get the remaining updates. Keep in mind however that I am directly running this on the Dell PC itself and not a Virtual Machine due to the fact that I only have 1 GB of RAM on this Net Book Computer.

---

### Post by exploder on 2012-02-04
The wubi install seems to work very well for an alpha release. I am glad I gave it a try because it works so much better than in VirtualBox.

---

### Post by jbicha on 2012-02-04
Like kevpan said, I believe this has all straightened out now. Unity update day is a bad time to upgrade until all of the pieces are built, published to the archives, and installed. After that you need to at least log out and maybe restart.

Also, it's probably not obvious but the day of a milestone Alpha release is a bad day to upgrade. Any time there is a freeze (there was a soft freeze this week of anything on the CDs to minimize introducing new problems), there's a lot of stuff that piles up to get released as soon as the freeze goes away.

Last cycle the worst day was Feature Freeze day as new features were pushed into Ubuntu, still broken, but at least they beat the freeze. It shouldn't be as bad this time but expect things to not be 100% then either as developers try to get a bunch of things in before the deadline. Feature Freeze is in just under 2 weeks.

---

### Post by shuttleworthwannabe on 2012-02-05
yup, for me too--too many hangings--decided to lay off a bit on the alpha. rebooted into 11.10 for now.

---

### Post by VMC on 2012-02-05
I don't know about virtual box installs or updates, but for the past week or so, the current iso installs works perfect on my system - hardware does makes a difference.

---

### Post by exploder on 2012-02-05
I am removing Windows 7 from the laptop now and installing the 12.04 beta. I don't care much for Windows 7 and all my hardware is working fine in the x64 12.04 alpha. I can still test updates for breakage in VirtualBox before applying them to the laptop. 

I was on the laptop all last night using the wubi install, it makes things so much more appealing than the factory installed OS.

---

### Post by mustangkr500 on 2012-02-05
I have no problems with Alpha 1 or 2 in virtual box, runs fine.

---

### Post by ranch hand on 2012-02-05
> **mustangkr500 said:**
> I have no problems with Alpha 1 or 2 in virtual box, runs fine.
Sorry to hear that.

I am disgusted too.  My Xubuntu 12.04-testing install just keeps ticking right along.

Have some problems for some reason with cups related things installing right in chroot but they straighten right out when I boot in and sic dpkg on them.

This is supposed to be an A2 release.  Where is the breakage?

{For all you old testers out there}  This just makes Ubuntu look bad.  Is this the best that it can do?

About time for some of those threads to show up and without better breakage than this we are going to miss them.

---

### Post by rburkartjo on 2012-02-05
yes and a2 runs great on my computer i have it installed on a separate partition. what impresses me is that i actually updated 11.10 to 12.04 a1 by the command line and then updated to a2 and have had very few problems,never could have done that when testing 11.10 when it was in alpha dev

---

