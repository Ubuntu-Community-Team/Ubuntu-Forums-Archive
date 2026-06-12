---
title: "fatal errors in installing ubuntu server on virtual box"
date: 2018-04-08
forum: Virtualisation
---

### Post by leon123411 on 2018-04-08
I had no issues when I installed ubuntu desktop.
But, the fatal error I got installing server version is too frustrating...
I copied the bottom part of vbox.log.
Hope it would help to find the solution...


00:00:21.433953 VGA Graphics Controller (3CF): GR index 3CE:05
00:00:21.433953  GR00:00 GR01:00 GR02:00 GR03:00 GR04:00 GR05:50 GR06:05 GR07:0F GR08:FF
00:00:21.433956 !!
00:00:21.433956 !! {vgapl}
00:00:21.433957 !!
00:00:21.433957 read mode     : 0     write mode: 0
00:00:21.433958 set/reset data: 00    S/R enable: 00
00:00:21.433958 color compare : 00    read map  : 0
00:00:21.433959 rotate        : 0     function  : 0
00:00:21.433960 don't care    : 0F    bit mask  : FF
00:00:21.433960 seq plane mask: 0F    chain-4   : on
00:00:21.433961 !!
00:00:21.433961 !! {vgasr}
00:00:21.433962 !!
00:00:21.433962 VGA Sequencer (3C5): SR index 3C4:04
00:00:21.433963  SR00:03 SR01:00 SR02:0F SR03:00 SR04:0A
00:00:21.433964 !!
00:00:21.433965 !! {vgatext}
00:00:21.433965 !!
00:00:21.433965 Not in text mode!
00:00:21.433966 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
00:00:21.433981 emR3Debug: rc=VINF_EM_TRIPLE_FAULT
00:00:22.433827 Changing the VM state from 'RUNNING' to 'GURU_MEDITATION'.

---

### Post by wildmanne39 on 2018-04-08
*Thread moved to **Virtualisation, a more appropriate forum**.*

---

### Post by leon123411 on 2018-04-08
one thing more....
I succeeded in installing desktop version on virtual box.

And, then I installed asterisknow on the virtual machine that I installed desktop version.
Then, I tried to install server version on the another virtual machine, and I got the error which still keeps haunting me.
I tried to install desktop version because installing asterisknow seemed to delete the desktop version.
What happened is....I got the same issue even with desktop one which I never had problem with....

I thought I did something wrong and deleted all the virtual machines(even the asterisknow) and tried to install desktop and server version on separate machines.
Still, I got the same error when installing server version, but it looks fine installing desktop one..until now...

I hope this additional information will help you guys come up with better solution.

---

### Post by SeijiSensei on 2018-04-08
Did you install the extension pack as well as VirtualBox itself?  The extension pack has a proprietary video driver that might work better.  I'm dubious about this since we're talking vanilla VGA here, but it's worth a shot.

I've installed Server 16.04 on a couple of different machines with both Windows and Linux hosts without incident.

Are you using the version of VirtualBox from the Oracle repositories?  If not, try that: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by sp40140 on 2018-04-08
What are the specs for the Host machine?
What resources have you allocated to the server VM?
At what stage of the install you get the error?
What (if any) notable options you have selected during the install?
What is the version of the Host OS?
What is the version of the VBox?

---

### Post by leon123411 on 2018-04-13
Thanks for reply. I was so frustrated and didn't try to solve this issue for last five days..sorry for late reply
I installed the extension anyway. 
And I am trying to use the version from the link you recommended.
Maybe,, I am gonna try ubuntu bionice version.
Honestly...I almost gave up until now...and considering using different programme rather than virtual box or just using desktop linux...

---

### Post by leon123411 on 2018-04-13
I got sick of this issues...and didn't want to even have a look at it...
What made me feel worse is it is just a installation issue. 
I have so many other issues I have to commit myself to solving and this is just one of them...and maybe not that crucial one...
I decided to focus on more important matter. Maybe i will be able to solve this issue later with more knowledge or new computer... 
Anyway, thank you guys for trying to help me.

---

