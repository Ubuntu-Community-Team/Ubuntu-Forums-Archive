---
title: "Any hope for jmicron users and Linux?"
date: 2006-12-09
forum: The Cafe
---

### Post by v8YKxgHe on 2006-12-09
This Jmicron IDE/SATA controller issue is annoying the hell out of me, and probably others.

I have tried installing Ubuntu Edgy about 10 times now all with different methods I've seen posted around with other users having the same problem, yet Ubuntu still refuses to boot. 

I've tried FC6 but the installer never appears, just a black screen and a bit of hard drive activity, few mins later no hard drive activity.

Arch Linux also does the same as Ubuntu, it will install but refuse to boot. 

I've seen others who are using the 2.6.20 kernel reporting similar problems with the jmicron ide/sata controller, and this is the latest kernel! Is there _any_ hope for jmicron users that this severe issue will get fixed any time soon? I am forced to use Windows because of this. :confused: 

Specs:
Intel Core 2 Duo E6600
Abit AB9
2x SATA 2 hard drives ( 1 for Windows, 1 was going to be for Ubuntu )
1x IDE 80 GB Hard drive
1x IDE DVD RW, Slave to the IDE hard drive
ATI X800XT

](*,)

---

### Post by pmj on 2006-12-09
I have an ASUS P5B motherboard and Ubuntu could be installed but not boot. In the end, I had to buy a controller card to be able to use my computer.

Honestly, I don't have any hope of this being fixed in time for Feisty. I mean, it should be simple enough, and it should be top priority, but it's constantly claimed in the bug report comments that everything is long fixed, while it's clearly not. And I hear it's still not fully fixed in the current version of Feisty.

---

### Post by v8YKxgHe on 2006-12-09
Pmj, glad you got your install working, I'm not exactly sure what a controller card is though - is it a PCI SATA controller?

Developers of Ubuntu have know since as early as August that this severe issue exists yet 4 months down the line it is _still_ not fixed. I know this issue may not be directly linked to Ubuntu it's self, more of a Kernel Issue AFAIK - but a 4 month bug severe as this not getting fixed is stupid.

---

### Post by pmj on 2006-12-09
It's just a PCI card with two extra IDE slots. Booting from it works flawlessly, unlike when the system drive was connected to the motherboard.

---

### Post by v8YKxgHe on 2006-12-09
ahhh I see, do you have any SATA hard drives at all?

---

### Post by pmj on 2006-12-09
I have one SATA drive and it works. I don't know if I could boot from it or not, I just use it for extra storage.

---

### Post by pelle.k on 2006-12-09
jmicron is crappy even under windows. Some 965 mainboards have the intel ich8 sata controller, as well as a jmicron controller.
I am one of those lucky bastards with 2 jmicron slots, and 4 intel slots. I run all my drives except for my dvdrw (i think the ide is on the jmicron controller) on the intel ones. Everything works great. It's a Gigabyte GA-965-S2 by the way.

---

### Post by vayu on 2006-12-09
> **AlexC_ said:**
> I am forced to use Windows because of this.

If it were me, I'd say I was forced to buy another controller.

---

### Post by v8YKxgHe on 2006-12-10
> If it were me, I'd say I was forced to buy another controller.

What type of controller do I need? an IDE or SATA Controller?

Edit: I emailed Jmicron before and they said everything was fine and there was no problem installing Linux. Yet I've seen people have the same problem with 2.6.20!

> Thanks for choice JMicron product ,

        Kernel 2.6.18.2 already built-in driver full support JMicron product,
        There is no problem to install any distro which base kernel 2.6.18.2. ......

---

### Post by mips on 2006-12-10
> **AlexC_ said:**
> What type of controller do I need? an IDE or SATA Controller?


Well that depends. Is the problems with both PATA(normal ide) & SATA or just with SATA ?

I like Adaptec products, good quality but I do not think they make any PATA stuff anymore, just SATA. I actually have a SATAConnect 1205SA card lying around here somewhere.

Maybe check newegg or the likes, just ensure the chipset is supported by linux & known to work.

---

### Post by v8YKxgHe on 2006-12-10
Hum I have no idea what problem it is - I've just ordered a Adaptec SATA controller, so I'll see if that will work.

---

### Post by kuja on 2006-12-10
Depends if you want to use an IDE or SATA drive. Get a controller for whichever one you use, or both if neccessary.

---

### Post by mips on 2006-12-10
Has anyone tried installing Debian with 2.6.18-3 or higher ?

[http://www.linuxquestions.org/questions/showthread.php?t=492030](http://www.linuxquestions.org/questions/showthread.php?t=492030)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502)
[http://www.ubuntuforums.org/showthread.php?t=234706](http://www.ubuntuforums.org/showthread.php?t=234706)

Alternatively maybe try [http://kanotix.com/](http://kanotix.com/) as it is based on Debian Sid.

---

### Post by mips on 2006-12-10
> **AlexC_ said:**
> Hum I have no idea what problem it is - I've just ordered a Adaptec SATA controller, so I'll see if that will work.

Not so fast, maybe have a look at Debian or Kanotix first. See my post above in this regard.

How are you going to boot from CD-Rom with a SATA controller seeing it is PATA according to your first post.

---

### Post by pmj on 2006-12-10
I can boot from the Edgy CD just fine, with the drive connected to the PATA jmicron controller. I can also install Ubuntu just fine. It's after that I can't boot my new Ubuntu installation. From what I've read, this problem is pretty common.

So the bugs do appear to be fixed at some level, just not all the way, because if I try the Dapper CD I can't boot from it at all.

---

### Post by v8YKxgHe on 2006-12-10
I think the time it's gonna take to get a working Linux distro on this jmicron infested PC is not worth it. I'm just gonna sell my AB9 and get a new motherboard without jmicron.

Anyone know if the Abit AW9D Intel 975X works?

Edit: going to give Gentoo one more try, if it doesn't work then new mobo for me :P

---

### Post by daou on 2006-12-10
I put together a comp for a friend with an MSI P965 Neo motherboard. It has one JMicron SATA slot and four Intel ICH8 ones.

The newest Edgy has support for JMicron but Grub does not. So the solution was to install on JMicron and boot with ICH8. Somehow installing on ICH8 did not work.

---

### Post by mips on 2006-12-10
Just get a gigabyte or Intel board depending on your cpu offcourse.

---

### Post by v8YKxgHe on 2006-12-10
Well I checked out on the Core2Duo support wiki page and there is no mention of Abit AW9D Intel 975X and I found this review: [http://www.phoronix.com/scan.php?page=article&item=583&num=1](http://www.phoronix.com/scan.php?page=article&item=583&num=1) which they test it with FC6.

I also got another email back from Jmicron saying 

> We do have a complete test to install ubuntu before.
        And all problem already solved by ubuntu kernel team  by ubuntu 6.10.

        JMicron keep in touch with all kerenl developer to get linux working,


They seem on insisting that it works, when it clearly doesn't.

---

### Post by mips on 2006-12-10
> **AlexC_ said:**
> 
They seem on insisting that it works, when it clearly doesn't.

Well maybe be firm with them and give them links to back up your case.

---

### Post by v8YKxgHe on 2006-12-10
I have already given them links to the 26 page thread about it, and the Core2Duo wiki page.

---

### Post by mips on 2006-12-10
In that case maybe sell your MB and get something else.

---

### Post by v8YKxgHe on 2006-12-10
Yep, I ordered the Abit AW9D earlier today, should be here Tuesday, finally I'll be able to get off Windows :mrgreen:

---

