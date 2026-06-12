---
title: "VirtualBox Networking and HDD help"
date: 2008-09-01
forum: Virtualisation
---

### Post by Jungle-Cat on 2008-09-01
Hello,
I have 2 main problems with VirtualBox. So far I love it, simple UI, easy to install and use... mostly self explanatory as well - love it. So I have XP installed in a virtual machine, but I have 2 problems. Because the OSE of VirtualBox which I have doesn't support shared folders (they're website says this is to help make money by making people use the closed source version, which has several added features such as this. I don't understand their logic at all, but hey, I have to live with it) so in order to get my windows post-install files to my virtual system I want to manually (in Dolphin or whatever - a file manager in Kubuntu) copy the files from my drive to the virtual drives real directory oh the host PC. So, where is the virtual drive stored?

My second problem is the networking... it doesn't work! In the networking settings, by default, it is set to NAT. I do not know what that means... the next setting I have is Host Interface which sounds right, but it requires extra settings which I do not know what to configure with. I have 2 network cards in my sytem - the onboard which I use, and an unused PCI card. I just have a normal setup where the the cable enters the onboard, into my switch, which then goes to the router, then the adsl2 modem. How do I set this up?

I think I've said everything that is of use... if I can get this all going well, and games going with Cedega/wine, I can use Virtualbox for all other windows things and I'll never have to use windows again!

Thanks

---

### Post by Bakon Jarser on 2008-09-01
Do you have guest additions installed?  Devices > Install Guest Additions
That might fix your networking problem.

---

