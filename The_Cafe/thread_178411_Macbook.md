---
title: "Macbook?"
date: 2006-05-17
forum: The Cafe
---

### Post by Cyfr on 2006-05-17
Hello, currently I have a Toshiba laptop, specs here: [http://www.ebuyer.com/customer/products/index.html?action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=79582&_LOC=UK](http://www.ebuyer.com/customer/products/index.html?action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=79582&_LOC=UK)

Due to one thing and another (though mainly the refusal of nvidia drivers on linux to work with this laptop) I have just XP and OSX86 installed on this laptop.

I really like OSX and have pretty much convinced myself that I *need* a mac :p

I've decided that i'll sell my current laptop and buy a macbook or macbook pro.

Now you guys come in, do I buy a macbook or macbook pro? I'll be planning to install dapper on it, i'll choose the 1gig version no matter which I get (unless you suggest 2gig?). The main difference between pro and normal is the 13" and 15" screens, but the pros also have their own graphics card, would I really need this? I don't really play games anymore so I can't see it being a serious issue, but I do like my desktop looking good.

If I just get a macbook with just onboard graphics, will I be able to use XGL etc? I can't think of anything else... except I don't have a huge budget (I expect £700'ish for my laptop, and I have a few hundred spare..)

Comments? ;)

---

### Post by mostwanted on 2006-05-17
ATI cards aren't well supported on Linux while the Intel cards have open source drivers made by the manufacturer. XGL is supported by both ATI, Nvidia and Intel cards.

All Mac laptops have Airport (a broadcom wifi chip) which have mediocre Linux support; it's a reverse-engineered driver made by the free software community.

All Mac laptops with Intel processors don't use BIOS like normal PCs, but rather EFI. I'm not hearing many people running Ubuntu on these things, only a few brave hackers. The Bootcamp BIOS emulator that Apple made is focused solely on dual-booting Windows, so there is no guarantee.

I'd advice you to look a little more into the subject... no actually, if you're planning to run Linux on it, I'd advice you to get something else.

---

### Post by tseliot on 2006-05-17
If you "need" a Mac it means that you also need Mac OSX (its operative system).

Why should you install Dapper if you said that it's not working for you?

---

### Post by Cyfr on 2006-05-17
[QUOTE=tseliot]If you "need" a Mac it means that you also need Mac OSX (its operative system).

Why should you install Dapper if you said that it's not working for you?[/QUOTE]


Well it's not working for me on my laptop because my laptop has a hissy fit about nvidia drivers (even in windows it needs drivers from the manufacturers website)

If I had a macbook perhaps dapper will work properly under it :)

(and yes i'd have osx too :p)

---

### Post by jdong on 2006-05-17
Would like to correct some factual inaccuracies in your post:

> **mostwanted]ATI cards aren't well supported on Linux while the Intel cards have open source drivers made by the manufacturer. XGL is supported by both ATI, Nvidia and Intel cards.
[/quote]
I would be cautious in making all three statements there. As far as ATI Linux support, that is the "popular opinion", but recently I bought a laptop with a Mobility Radeon X1400, and it's working under Linux perfectly fine, even with suspend/resume support and video performance on par with Windows XP.

Intel's open source drivers are created by various X subprojects (mainly DRI) said:**
> 
All Mac laptops have Airport (a broadcom wifi chip) which have mediocre Linux support; it's a reverse-engineered driver made by the free software community.

Actually, only true for the PowerPC macs. Intel macs use an Atheros chipset card, which has some of the BEST Linux drivers (next to Intel Pro/Wireless).

> 
All Mac laptops with Intel processors don't use BIOS like normal PCs, but rather EFI. I'm not hearing many people running Ubuntu on these things, only a few brave hackers. The Bootcamp BIOS emulator that Apple made is focused solely on dual-booting Windows, so there is no guarantee.

This is a true statement. I think mjg59 has an Intel mac, and there are a few articles out there about running Linux (and Ubuntu specifically) on Intel Macs, but most of those that I bothered to read involved quite a deal of unnatural hacking. So, please do your research carefully and do not assume that it's going to run Linux without a hitch.

> 
I'd advice you to look a little more into the subject... no actually, if you're planning to run Linux on it, I'd advice you to get something else.

If you are interested in looking at alternatives, take a look at the Lenovos and the Acers. I recently bought an Acer Aspire 5672 (Core Duo 1.66, 1GB RAM, Mobility Radeon X1400, DVD dual format + RAM drive, 100GB hd) for $1100 USD, and I'm very happy with my decision. My second choice were the Lenovo N100's, which were slightly higher priced for virtually the same base system.

There is already a pretty nice community growing around the Aspire 5672 on the forums, and a pretty detailed thread with our Linux experience on it (which has been quite smooth considering how new the hardware is)

---

### Post by imagine on 2006-05-17
The MacBook has a mirror as a display (Apple calls this "glossy") whereas the MacBook Pro has a normal display.
I'm not planning to buy an Apple notebook, but if I did, it would be a MacBook Pro.

---

### Post by tseliot on 2006-05-17
[QUOTE=Cyfr]Well it's not working for me on my laptop because my laptop has a hissy fit about nvidia drivers (even in windows it needs drivers from the manufacturers website)[/QUOTE]
Did you ask for help in the thread of my guide about the Nvidia driver or try my script?

---

### Post by cromestant on 2006-05-18
I have the same dilema... I own a macmini ppc, which was a gift from my stepfather, ( he loves mac) so that I get to know this OS. now i love it... just nos as much as linux ( gentoo user for 3 years, now ubuntu daper user( very happy BTW))

I am going to buy a laptop soon and I was very exited with the macbook, since I can run mac os, windows ( yes for work, no flame war please)... but the support for linux is really in beta testing.. EFI booting is quite diferent than BIOS, i know that gentoo is installable, since you can choose your boot loader ( in this case it would be ELILO) but I don;t know how well it would handle booting all 3 os..

Also the " mirror"  on the macbook has me really doubting...

I am looking at the lenovo 3000 n100, which has a slower dual core than the macbook ( 1.8ghz) but has some advantages :
1) under 1500 ( with 1gb ram, and 100gb sata drive)
2) no mirror
3) pci express nvidia geforce 7200 128mb ( nice..)
4) fingerprint reader, although I don;t know if this is suported in linux
some setbacks:
1) bigger than the macbook ( this is the primary reason that I want to change my inspiron 5150, almost 10 pounds and huuge to carry around)
2) heavier than the macbook ( not much)
3) no magsafe ( might be stupiud to some but i've seen many ac plugs broken with missuse.. so ..)

I am still waiting to see which one i'll grab..
I am split though.. I need to have linux... just love gnome.

BTW, nvidia has never been a problem for me on linux... just use the linux driver ( default " nv" )
or download the nvidia driver from nvidia.com, it easy to install although you need to have the kernel source... maybe aptitude has these on hand, have not tried it yet, since the default driver is working great on my geforce go fx 5200..

---

### Post by benplaut on 2006-05-18
if getting a macbook, go for the pro... i know from hands-on experience that the build quality is multitudes better.

If not, thinkpads have the best support of any linux laptop, from my experience.
Buy one with low ram, then upgrade yourself to save a few dozen $$$

---

### Post by HotshotEsquire on 2006-08-14
I have a macbook. I installed Dapper on it using these instructions:

[http://http://bin-false.org/?p=17]("http://http://bin-false.org/?p=17")

---

### Post by cromestant on 2006-08-14
Yeah I forgot to post back...I hace the blackbook, it is quite nice, dapper runs great on it, just two things bother me

No sleep on screen shut, and kernel upgrades are a pain in the arse... I now have refit showing 1 macos and 2 linux.. .and don't know how to fix this... its unerving...

---

### Post by leonedo on 2006-08-25
> I now have refit showing 1 macos and 2 linux.. .and don't know how to fix this... its unerving...

in the refit config file... under osx that is... there's an option, legacy first. just change it.

---

### Post by AllenJM on 2006-09-20
I have an iBook G4 and was using OSX for 10 months or so and it seemed great. Then three weeks ago it crashed and when I tried to boot up it, it stalled at the logon window. Turned out the HD was corrupted further more the install CD's that came with the machine wouldn't boot.

I 'discovered' Unbuntu DDrake and thought I would give it a go. Tried it first on my  test PC (old AMD wt 256M ram) although 'Live' wouldn't install the Alternative image did.

It turned out to be the same with the iBook (needed Alternative CD image), the drive was corrupted but manual partitioning sorted that out (well trial and error did :---) It's running fine (and fast) now, I got the Wireless working by following the HowTo posted on BroadComm 43XX. Mouseemu sorted the single button mouse issue but I'm still struggling with the keyboard mapping but i'm a linux newbie:) The sound, graphics, usb etc all worked right out of the 'box'.

Depends what apps you need in the end but I didn't have the option of dual booting. Open Office does all I need for on the go and it is easier programming Java on Ubuntu anyway!

---

### Post by slimdog360 on 2006-09-20
dapper works great under thinkpads too.

---

