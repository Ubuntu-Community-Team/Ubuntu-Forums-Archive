---
title: "Ok,.. I'll try one more time..."
date: 2010-06-19
forum: The Cafe
---

### Post by Zerocool Djx on 2010-06-19
SO, I was over at my friends house and where poking around with Linux... He, much, like a lot of people on here wondered why I don't do dual boot, because I took off Ubuntu... I told him that it was because a very weird quirky reason. When I get home from work and walk through the door the first thing I do is fire up the computer to check e-mails for my home business. Then I go take out the dog, get the mail etc... When I come back what do I see? Ubuntu.. which wouldn't be bad, but here is the thing. After checking my e-mails, most of them are tech support questions and things I got to change on peoples's sites.. There lays the problem.. I use Dreamweaver and refuse to use anything else. Please spare me the, well this works thing or try that program,.. NO! forget it,.. I won't switch programs,  need proficiency and not headaches. Anyway,.. so now what do I got to do? ARG! REBOOT and select Win from grub loader.. My friend proceeded to tell me that changing grub so that windows is the default boot ap is actually really easy... he showed me in like 2 min.. So he got into asking me about my ussage on Linux. While I cannot go into full details of that, what we did talk about was merging Something from a few Linux distro's we like all into one... By the end of the conversation, he got me hooked back into wanting to use Ubuntu again.. However, I will have windows as my primary till wine gets figured out. BUT,.. for those that like the usage of Linux in the network security world... mmmmmm,.. We got a new project in the works... Were starting it this weekend, today actually.. Don't know when we will be done, but should be something people are gonna want. Were going to work on it in Karmic Because it seems Lynx is still being worked on and people can always upgrade later if they want... So Yay! I'm coming back and bringing some friends...

---

### Post by ronnielsen1 on 2010-06-19
How about running Dreamweaver then? You don't say what version you have, but some of them will work in wine and ubuntu.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3482](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3482)

---

### Post by Zerocool Djx on 2010-06-19
I got the CS5 suite,.. but I'm not going to monkey with it,.. I just won't.. find someone that wants to play with it and let me know how it works out.

---

### Post by Swagman on 2010-06-19
DreamWeaver... Bah!

What's wrong with notepad ?

---

### Post by Zerocool Djx on 2010-06-19
things can be done in note pad,.. but it's just more efficant to use Dreamweaver. I mean you could argue a ton of programs, but comparing note pad to Dreamweaver is comparing using flint to a blow torch when starting a fire.

---

### Post by dragos240 on 2010-06-19
You actually can do quite a bit in gedit or a similar program. If you know html well, it can even be more efficient.

---

### Post by Penguin Guy on 2010-06-19
> **Zerocool Djx said:**
> things can be done in note pad,.. but it's just more efficant to use Dreamweaver. I mean you could argue a ton of programs, but comparing note pad to Dreamweaver is comparing using flint to a blow torch when starting a fire.
LOL  - That was me a year ago, but when I gave [gedit]("apt:gedit") a try I actually preferred it - I realized that although dragging and dropping items is easy, it doesn't make very good websites. A flint uses a lot less gas than a blow torch, yes?

If you want a solution to your problem then:
[LIST]
[*]Use a text editor like [GEdit]("apt:gedit")
[*]Use [Wine]("apt:wine1.2") - yes, you may have to 'monkey around' a bit
[*]Use [Virtual Box]("apt:virtualbox-ose") - install Windows *inside* Linux
[/LIST]
I doubt anyone here will 'monkey around' for you - if you want your problem solved, you have to put in *some* effort.

Good luck.

P.S. Some paragraphs would have been nice.

---

### Post by ronnielsen1 on 2010-06-19
> I got the CS5 suite,.. but I'm not going to monkey with it,.. I just  won't.. find someone that wants to play with it and let me know how it  works out.

I wasn't going to because you don't want to monkey with it but


> I copied the program files, common files, and user appdata from a vista installation. I also imported the registry keys for adobe in current user and local machine /software.

The program needs the c++ 2008 redistributable installed, but it must be downloaded and installed from microsoft. The one in winetricks does not work. odbc32.dll and odbcint.dll are required as well. gdiplus.dll must also be manually copied into the /system folder.


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20236](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20236)

If you google the app in question along with winehq, you usually can find out if someone has been successful at running it. Dreamweaver CS5 appears to be silver rated that is defined as Applications with minor issues that do not affect typical usage

---

### Post by koenn on 2010-06-19
> **Penguin Guy said:**
> P.S. Some paragraphs would have been nice.

If paragraphs were of any use, text editors would create them automatically.

:)

---

### Post by mickie.kext on 2010-06-19
> **Zerocool Djx said:**
> I got the CS5 suite,.. but I'm not going to monkey with it,.. I just won't.. find someone that wants to play with it and let me know how it works out.

Ok... so do you want me to buy DW and "monkey" for you, and do you want to come over to your house and make it work for you?:rolleyes:

Seriously, you don't want Wine, you don't want other programs, what do you want?

---

### Post by Zerocool Djx on 2010-06-20
> **mickie.kext said:**
> Ok... so do you want me to buy DW and "monkey" for you, and do you want to come over to your house and make it work for you?:rolleyes:

Seriously, you don't want Wine, you don't want other programs, what do you want?

Never said I didn't want wine,.. Just want my programs, the ones I bought, to work as they do on win platform. Till that day when someone can show me that it works flawlessly, I'll use them on win. Not trying to be stubborn about it and I did try a few times, but I'll leave it up to the experts to figure it out.

---

### Post by Zerocool Djx on 2010-06-20
Arg,.. now you guys got me thinkin' again... :P really,.. what's the word on wine and internet connectivity?

---

### Post by Zerocool Djx on 2010-06-20
Before this get put in reoccurring discussions, I'm taking it to wine... See you there.

[http://ubuntuforums.org/showthread.php?p=9486364#post9486364](http://ubuntuforums.org/showthread.php?p=9486364#post9486364)

---

### Post by koenn on 2010-06-20
I don't see what all the fuss is about.

You choose to use Dreamweaver
You know dreamweaver is supported on some versions of Windows, and some versions of Mac OS X
So you know you're going to be using one of those supported platforms.
If you have a problem with that, don't use Dreamweaver, or take it up with Adobe, it's their decision.

If you decide to ignore all that and try alternative solutions such as wine, dual booting, or virtualization, you (should) know that such things always always have trade-offs -- such as the burden of configuring the boot loader to match your preferred work flow in the case of dual boot, or configuring an emulator or a compatibility layer such as one to get the software to run on a platform it was not designed for. That's your decision. So what was this thread about, really ?

---

### Post by The Real Dave on 2010-06-21
For me, DreamWeaver 8 works perfectly in Wine (1.2-rc4). According to their [site]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14343"), quite a few people have had success with CS4 in Wine also.

I suggest that you get the latest version of Wine from their site, and try to install DreamWeaver. Don't assume that something won't work without trying it. Hell, I got most of Office 2007 to work by default.

[[img]http://linuxexpresso.files.wordpress.com/2010/06/dreamweaver8.png?w=200h=200[/img]]("http://linuxexpresso.files.wordpress.com/2010/06/dreamweaver8.png")

[[img]http://linuxexpresso.files.wordpress.com/2010/02/office_2007_28-feb-2010.png?w=200h=200[/img]]("http://linuxexpresso.files.wordpress.com/2010/02/office_2007_28-feb-2010.png")

---

### Post by Paqman on 2010-06-21
> **dragos240 said:**
> You actually can do quite a bit in gedit or a similar program. If you know html well, it can even be more efficient.

Ok, but this guy is not actually asking how he can *ditch* Dreamweaver, he's asking how he can *use* Dreamweaver.

Just because you use a certain app, doesn't mean others should too.

---

### Post by Johnsie on 2010-06-21
You're best just using Windows if you like dreamweaver. Wine runs Windows programs but it does it badly. 

Using virtualbox in seemless mode is probably the best way to run dreamweaver on top of Linux... But really it's best just to stick with Windows in this case. Fighting an uphill battle just to run a program is completely unnecessary when you can do it easily with Windows.

---

