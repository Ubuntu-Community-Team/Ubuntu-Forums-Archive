---
title: "Poor performance in VirtualBox when Intel-VT active"
date: 2009-10-18
forum: Virtualisation
---

### Post by mgol on 2009-10-18
I have Dell Latitude E6500 with P8600 CPU. When I run my Windows XP guest on VirtualBox OSE without virtualization VT-x option inactive it runs much faster than in the case I turn it on. It is really visible - with VT-x on I even see how screen flickers during the boot process.

I did Peacekeeper tests in Firefox and I got these results:
1) VT-x off, 3D support off - 1596
2) VT-x off, 3D support on - 1679
3) VT-x on, 3D support off - 900
4) VT-x on, 3D support on - 1314

Google Chrome behaves even more strange - with VT-x off it runs faster than Firefox while with VT-x on it runs *VERY* slow but looses no frames in graphic tests and it finally gets sth like 8800 points. :D

What could be wrong with my settings? I bought this machine to gain with using VT-x, not to decrease performace this way. ;/

I use 64-bit Karmic.

**EDIT:** I filed a bug report:
[https://bugs.launchpad.net/bugs/455112](https://bugs.launchpad.net/bugs/455112)

---

### Post by kaboyish on 2009-10-19
> **mgol said:**
> I have Dell Latitude E6500 with P8600 CPU. When I run my Windows XP guest on VirtualBox OSE without virtualization VT-x option inactive it runs much faster than in the case I turn it on. It is really visible - with VT-x on I even see how screen flickers during the boot process.

I did Peacekeeper tests in Firefox and I got these results:
1) VT-x off, 3D support off - 1596
2) VT-x off, 3D support on - 1679
3) VT-x on, 3D support off - 900
4) VT-x on, 3D support on - 1314

Google Chrome behaves even more strange - with VT-x off it runs faster than Firefox while with VT-x on it runs *VERY* slow but looses no frames in graphic tests and it finally gets sth like 8800 points. :D

What could be wrong with my settings? I bought this machine to gain with using VT-x, not to decrease performace this way. ;/

I use 64-bit Karmic.

**EDIT:** I filed a bug report:
[https://bugs.launchpad.net/bugs/455112](https://bugs.launchpad.net/bugs/455112)
my problems are quite similar to yours. and to make matters even worse, the sound sounds like an old record player skipping!! lets hope that someone will come to our rescue

---

### Post by mgol on 2009-10-19
> **kaboyish said:**
> my problems are quite similar to yours. and to make matters even worse, the sound sounds like an old record player skipping!! lets hope that someone will come to our rescue

For me sound is so bad not only when VT-x is enabled... Do You share my experiences? I filed a bug report about this:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/451688](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/451688)
You can subscribe and/or comment if You have a Launchpad account.

---

### Post by bodhi.zazen on 2009-10-19
Just a reminder, Karmic is still in Beta ;)

---

### Post by mgol on 2009-10-19
> **bodhi.zazen said:**
> Just a reminder, Karmic is still in Beta ;)
Yeah, I know, but in 2 days it will go RC, so it's getting hotter and hotter now. ;)

---

### Post by mgol on 2009-10-20
> **kaboyish said:**
> and to make matters even worse, the sound sounds like an old record player skipping!!
As for the sound issue (which is different from this one), see:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/451688/comments/2](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/451688/comments/2)

It seems very common, at least recently. A lot of apps have sound problems because they default to alsa instead of pulse...

---

### Post by garba on 2009-10-24
same here, running windows 7 on a karmic host, performance is horrible

---

### Post by Fale on 2009-10-26
I can confirm that I have same problem. Karmic 64-bit is host on my laptop and I run Windows XP 32bit as a guest on VirtualBoX 3.0.8.

Performance is **S L O W** with Intel-VT activated. Didn't had problems with 9.04.

---

### Post by mgol on 2009-10-26
> **Fale said:**
> 
Performance is **S L O W** with Intel-VT activated. Didn't had problems with 9.04.
Oh, that is interesting. Could You comment about that on the bug I mentioned at the beginning?

---

### Post by Fale on 2009-10-26
> **mgol said:**
> Oh, that is interesting. Could You comment about that on the bug I mentioned at the beginning?

I have not enough knowledge to comment that one... but clearly seems that many has performance issues when running VirtualBox under Karmic with Intel-VT enabled.

---

### Post by garba on 2009-10-26
I found out that enabling only one core helps quite a lot, by the way, disabling intel vt prevents windows 7 from booting (I get a progress bar at boot, like when you boot the win7 install cd... weird).

---

### Post by daffy_ on 2009-10-27
> **garba said:**
> same here, running windows 7 on a karmic host, performance is horrible

Same with me. Running Win7 64 bit (and 32bit) guests on an AMD Phenom(tm) II X3 710 Processor with 8GB of DDR3 RAM. On Ubuntu 9.04 it was really snappy and fast, while on 9.10 it is really really slow.

I'm running VirtualBox 3.0.8. (I did run 3.0.3 or something like that on ubuntu 9.04 with good performance)

---

### Post by garba on 2009-10-27
tried disabling nested paging, it helps some

---

### Post by mgol on 2009-10-28
> **garba said:**
> tried disabling nested paging, it helps some
Really? Not for me. BTW, nested paging is not present in all but Core i7 Intel CPUs (it is present in most AMD ones, though). VirtualBox knows that and it doesn't enable this feature if not present. It would be really weird if disabling something that VBox disables itself worked.

Maybe it just seemed to work a bit faster one time? It can happen but it still means nothing.

---

### Post by joewski on 2009-10-29
I had the same problem with performance on Vista and W7. 

I found the solution to the problem increasing the VM memory to 960mb respectively. That drastically improved stability and usability for me. However I suspect that as more applications are installed in the vm it will need even more memory on these systems.

---

### Post by mgol on 2009-10-29
> **joewski said:**
> I found the solution to the problem increasing the VM memory to 960mb respectively.
I gave it 1024 MB at the beginning and efficiency sucks.

---

### Post by HotShotDJ on 2009-10-30
> **joewski said:**
> I found the solution to the problem increasing the VM memory to 960mb respectively.

> **mgol said:**
> I gave it 1024 MB at the beginning and efficiency sucks.I've given my VM (WinXP) 1792 MB -- I have 4G on my system -- and I still have issues when defining 2 CPU's.  With VT-x enabled and only 1 CPU defined, performance is fine.  Just as with Fale, I did not have this problem with Jaunty.

---

### Post by HotShotDJ on 2009-10-30
> **bodhi.zazen said:**
> Just a reminder, Karmic is still in Beta ;)The problem persists in the final release and with VirtualBox 3.0.10 (PUEL) :(

---

### Post by bodhi.zazen on 2009-10-30
I hope you find a solution and fast =)

Two general comments :

1. Keep in mind , VBox is a third party application, try teh VirtualBox forums and the PUEL will lag a bit behind the Karmic release.

2. Personally I have been using KVM for the last few months. I understand it to has limitations, but it does what I need and with less problems then VBox or VMWare.

I run KVM from the command line =)

---

### Post by sevketcaba on 2009-10-31
Similar problem for me:

Host Info : 
OS  : Windows XP SP3 x86, 
PRO : AMD64 4200+ X2
RAM : 2 GB DDR2 800
GRA : Radeon HD2600 PRO 512 MB

Virtual Machines :
APP : VirtualBox 2.2.4
OS : Kubuntu 9.04 (Upgraded from 8.04 and changed to Gnome)
3D : Enabled
PRO : 1
RAM : 1024
RESULT : Everything went well, i could activate compiz  at least

APP : VMWare 6.5
OS : Pardus 2008.2
3D : Enabled
PRO : 2
RAM : 1024
RESULT : Works Fine

Virtual Machines :
APP : VirtualBox 3.0.8 (Also upgraded to 3.0.10 but nothing changed)
OS : Ubuntu 9.10 (Clean install)
3D : Enabled
PRO : 1
RAM : 1024
RESULT : Performance is really poor, disabled compiz but every login i have to reload metacity, still apps lags and when activate compiz, for example when dropdown a menu, it has a yellowish color, mouseover fixes the color issue. When click to an item, menu does not disappear, stays there with app. %40 alpha. When click on screen, then it disappears. 


Note : I tried to use Vmware with ubuntu 9.10, enabled 3D but could not activate desktop effects, so deleted.

Sorry for poor English...

---

### Post by mgol on 2009-10-31
> **HotShotDJ said:**
> With VT-x enabled and only 1 CPU defined, performance is fine.
The real question is not if performance is fine (I could say that it's fine even with VT-x off...) but whether it's better or worse with VT-x enabled. For me it's worse and that worries me because I thought virtualization is an improvement, not a step back.

---

### Post by sevketcaba on 2009-10-31
I think i found out the problem. 

First of all, i misunderstand the issue in my before post. The problem is not the performance, the problem is just about the keyboard and the mouse. When click, roll over or press a key, it lags, but the 3D performance is quite well.

The problem is i think, the host machine has a 32Bit OS, but the guest is 64Bit. I learned that my processor does not support AMD-V, but 64Bit guests require the feature, so you can not disable the AMD-V support. There starts the problem. Now i'm downloading the 32Bit Ubuntu 9.10 and will try. I will share the results here.

---

### Post by mgol on 2009-10-31
@sevketcaba
This is certainly **not** my problem. I run 32-bit guest on 64-bit host.

---

