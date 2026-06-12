---
title: "LTSP or puppy"
date: 2015-12-03
forum: Ubuntu, Linux and OS Chat
---

### Post by drazenprado on 2015-12-03
1. Introduction.


Best regards:


Well, I have the intention to open a cyber cafe, wanted to do long ago. However, I do not have much capital investment. That is why we have sought interesting ways to "save". What I have found is the LTSP, and distributions of linux very small and light. Even approaches "gamer" by multiseat unfortunately in windows.


So unfortunately also, Windows is snowballea himself, leaving his bugueado unusable hardware and ugly system. And even worse that many game companies focus on this bad platform, instead of giving if linux distribution, but not directly gain from the sale of the game but "online shopping (LoL, WoW, Hon, hos, Dota2-even the latter has its "native client").


2 Workstations.


Is what I'm going to start, simple workstations for Internet and office automation functions. It follows that also for playing music and video. The hardware used for this is 9 pcs. Pentium II and Pentium Pro (I'm not so sure how many are which). These have to 96-128MB RAM, 233 mhz 2GBy as processing.


For "central PC" I focus on AMD FX 8XXX. (Compared to Intel, the price is lower, and has an excellent performance, but the motherboard is a bit more expensive).


Ubuntu LTSP 2.1.


The first thought that occurred to me was riding in the "central computer" an LTSP server, once I read it, but I've never been able to prove.


The theory is great, but in practice I've found many mistakes


2.1.1 Process.


• My first attempt was starting these pc in LTSP-live with an Ethernet hub network by booting the BIOS. It did not work at all, I'm not sure I could have failed, at least not now. I can attribute the error to the fact that the hub and using the PXE boot network cards are not optimal.


• Then I installed the system and try to boot from the network on a computer core i3. It worked perfectly, although the first boot with unity was slow, then was normalized gnome, unity, tried many combinations, with straight cable, crossover cable with a switch tp-link. Any combination worked.


• With that in mind, I'm working Pentium II. PXE booting is not working. neither live nor ltsp the installed version. First try using ipxe but no idea how to do it, then try to gpxe and run the boot network, it is interesting that different shows "images boot" one that I run the i3 325 mb and then displays another 512 mb. I'm not sure what this means.


• After that, it displays "Edubuntu 14.04 LTS" right after "saned disabled /opt/ltsp.../ edit a file that has settings" saned "then edit it poniendole" true ".


• The main problem is that just after that, only a black screen, nothing more, I can not even enter the terminal mode ctlr alt f1.


• I made many attempts to fix it, but nothing worked.


• I have read that many people have similar problem, after some 10.04, but it works fine in 8.04. It will download and try, but do not have a good Internet connection now. Or attempts to fedora, Open Suse, Gentoo Linux or any distribution that allows for this


Puppy Linux 2.2 and Legacy OS.


I have something quickly, very soon I will open the internet and do not see fit to Windows 2000 or Windows XP that come with computers. I really want to use the LTSP, but I need time to make it work.


Therefore, I have seen this pair of systems, and I gather that will put any of them so soon, or even DSL Damn Small Linux. until a functional LTSP.


3 Final Questions


I need to ask, which recommended for pcs I said?


Puppy linux


DSL


Legacy OS 4 Mini


Legacy OS 2


Also would appreciate being told why does not the ltsp ie the black screen. At the end I changed many files, I think "ruin" my LTSP.

---

### Post by Bucky Ball on 2015-12-03
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Welcome The majority of your post is not a support request but a recounting of your experiences with various operating systems. If you want support with the few questions you've dotted throughout the post, best to break them up into separate threads and post them as concisely and clearly as you can in the appropriate forum areas.

Be aware that Puppy, DSL, and the usupported Ubuntus you mention (8.04, 10.04) are not supported on the main forum areas here. (I strongly advise you forget about 8.04 and 10.04 and move on: they reached end-of-life some time ago, for 8.04, four years.) You may be better served posting on forums that are dedicated to the OS you are wanting to know about. Just to be clear, the main forum areas here provide support for: 

Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu and Ubuntu Mate.

Thanks and good luck. ;)

* I will have a go at giving an opinion on one of your questions, and opinions is what you will get to many of them as they can't be answered definitively, and that is that none of the official flavours of Ubuntu are going to run well or at all on anything with less than 512Mb of RAM. So, you are on the right track. Puppy or DSL should be fine. As in, they will run. Can they do what you want? No idea.

---

### Post by Mike_Walsh on 2015-12-03
If you want some answers to your questions vis-a-vis Puppy, the best place to try would be the Puppy Forums:-

[http://www.murga-linux.com/puppy/index.php](http://www.murga-linux.com/puppy/index.php)

We'd be more than happy to see you!


Regards,

Mike. ;)

---

### Post by ramesh24 on 2016-03-05
If you have several older machines. Then you should go for LTSP Fat Clients. If you do not want older ugly CRT monitors. You can consider latest monitors. Try to install Ubuntu LTSP using the following help page.
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

---

