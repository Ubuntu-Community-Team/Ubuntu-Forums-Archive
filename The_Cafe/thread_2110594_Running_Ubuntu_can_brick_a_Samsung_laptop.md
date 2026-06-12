---
title: "Running Ubuntu can brick a Samsung laptop"
date: 2013-01-30
forum: The Cafe
---

### Post by szymon_g on 2013-01-30
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)

"(..)Booting Linux using UEFI just once on various Samsung laptops is enough to permanently stop them working. Several reports have been posted on the Ubuntu bug tracker, but the problem is likely to also be present in other Linux distributions, as it appears to be caused by a kernel driver for Samsung laptops. Kernel developers are currently discussing a change which would disable the driver when booting via UEFI. (..)"

So- when it will be the "year of Linux on destkop" ;)?

---

### Post by lz1dsb on 2013-01-30
What an irony... and when you think about it, Samsung is the corporation that sells the majority of Android phones these days. I'm not saying that Android is Linux, but still they're profiting from Linux in a way. And yet... they're laptops are... not supporting Linux. It's a strange world we're living in...:confused:

---

### Post by Linuxratty on 2013-01-30
Android runs atop the Linux kernel.

---

### Post by oldfred on 2013-01-30
This has been in release notes for a while.

       [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

     Some Samsungs do work:
       Samsung Ultrabook Windows 8 & Ubuntu & recovery boot
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

---

### Post by Lucradia on 2013-01-30
I am so glad that I would never buy a laptop from any retail store. Custom made ones like from Sager and Lenovo are the best bet for someone looking for power in one anyway =/

Also, Desktops aren't laptops, and vice versa. /didn'tGetJokeIfWasOne

---

### Post by szymon_g on 2013-01-30
> **Lucradia said:**
> I am so glad that I would never buy a laptop from any retail store. Custom made ones like from Sager and Lenovo are the best bet for someone looking for power in one anyway =/

yes. thats great if you know what you want. If you don't, you buy one from nearest pc store.

---

### Post by Lucradia on 2013-01-30
> **szymon_g said:**
> yes. thats great if you know what you want. If you don't, you buy one from nearest pc store.

If that were the case, best buy would sell a lot of ASUS ROG Laptops (G75VW-BHI7N07, the only in-store one) then, as they're more power per dollar than those =/ Though, they do weigh a lot. In terms of websites, Lenovo / Dell have the best price per dollar for mobile Intel (XM processor)

---

### Post by linuxcoffeelover on 2013-01-30
Wow that right there stops me from buying any Samsung laptop now the only thing I left on the list of things I will buy from samsung are the play stations and maybe a camera one day.

---

### Post by monkeybrain2012 on 2013-01-30
The point is not what I am going to buy, but say someone wants to try out some Linux distros on a Samsung laptop and gets his machine bricked. It is going to hurt Linux's reputation big time, and if you are the one who gave him the live usb you may have to pay for the laptop.

---

### Post by Lucradia on 2013-01-31
> **linuxcoffeelover said:**
> Wow that right there stops me from buying any Samsung laptop now the only thing I left on the list of things I will buy from samsung are the play stations and maybe a camera one day.

Samsung makes PlayStations? As I recall, the only thing Samsung made on a PlayStation was the memory of the PlayStation Portables. Isn't the PlayStation 3 / Vita / PSP software based on BSD?

---

### Post by santosh83 on 2013-01-31
> **monkeybrain2012 said:**
> The point is not what I am going to buy, but say someone wants to try out some Linux distros on a Samsung laptop and gets his machine bricked. It is going to hurt Linux's reputation big time, and if you are the one who gave him the live usb you may have to pay for the laptop.

It seems it was a bug in the firmware that was the actual culprit, so blaming Linux is wrong. It's Samsung that should write better code and work more closely with a major worldwide alternative to Windows. In any case no software should ever be able to *brick* hardware or firmware, at least in this day and age.

And anyway no one can stop ignorant people from trying out something without researching enough about it and jumping to wrong conclusions. In fact, even we too probably behave like that in other aspects of our life. :-)

UEFI Secure Boot was always going to be trouble for Linux IMHO cause it's security model doesn't suit the nature of open source software and diversity. In the Windows world the aim is to protect the user from the computer, just like with Smartphones, but in the Linux world the user wants control over *all* aspects of his computer, so pleasing both sides is going to take some cooperation in the coming days of increasing security lock-downs I guess.

The first step that should be done is provide the user fairly easy means to control all the keys via the BIOS, add and edit them, and disable Secure Boot if needed. The question is if all manufacturers will provide all this functionality, and inevitably Microsoft and Windows aren't going to play well.

It's ironic that after all the years of work by the FOSS communities we now need to get a key from Microsoft to *allow Linux to run on general purpose computers* side-by-side with Windows. Something is simply so wrong with this situation I don't know where to begin.

If UEFI Secure Boot is the future, then it should be something that is made an international standard and something tied only to the hardware and hardware manufacturers, not something that a software maker can so heavily influence.

I mean, ARM devices can already not boot anything other than Windows, and PCs can't disable Secure Boot without losing their 'Made for Windows' stickers and subsidies, and Linux now needs a certificate from Microsoft to run side-by-side with Windows. What next? Soon consumer PCs will not be able to dual boot if Microsoft have their way. We'll be forced into a *"either you're with us or against us"* decision. Or purchase server grade hardware?

I know all this hasn't come to pass yet, and I hope I'm totally wrong with all my speculations above, but given that the commercial software industry and free software are so ideologically at odds, I've a bad feeling about this. :-(

---

### Post by lancest on 2013-01-31
I've never trusted Samsung laptops anyway.
ASUS/MSI run great for me.

---

### Post by Gremlinzzz on 2013-01-31
:popcorn:Good to know,i would never buy a picky computer.
plus i can now warn other users to stay away from Samsung computers and if they have one,not to install Linux on it.

---

### Post by kurt18947 on 2013-01-31
> **szymon_g said:**
> yes. thats great if you know what you want. If you don't, you buy one from nearest pc store.

If you don't have a clue what you want, you probably have no idea what Linux is.  For Linux to become an appliance is going to require having installation and support from the manufacturer.  As long as Microsoft has the Windows bludgeon to wield over OEMs, it's going to be an uphill battle.  

If manufacturers devoted the same resources to making sure their hardware was supported by Linux as they devote to making sure their hardware supports Windows, it'd likely be a different story.  But how many are going to risk angering the God in Redmond to offer linux preinstalled?  There is talk of Microsoft putting $3 billion into a pot to take Dell private.  I wonder what will happen to Dell's linux offerings in that event?  On the other hand, it'd be nice to see *some* standardization in the linux hardware interface world.

---

### Post by sdowney717 on 2013-01-31
> Samsung repaired the laptop, which was under warranty, by **replacing the motherboard**

Think this due to the bios chip being soldered into the board?
What a waste, electronic e-waste philosophy in play versus a design that allows for a recovery even by the end user.

---

### Post by santosh83 on 2013-01-31
> **kurt18947 said:**
> If you don't have a blue what you want, you probably have no idea what Linux is.  For Linux to become an appliance is going to require having installation and support from the manufacturer.  As long as Microsoft has the Windows bludgeon to wield over OEMs, it's going to be an uphill battle.  

If manufacturers devoted the same resources to making sure their hardware was supported by Linux as they devote to making sure their hardware supports Windows, it'd likely be a different story.  But how many are going to risk angering the God in Redmond to offer linux preinstalled?  There is talk of Microsoft putting $3 billion into a pot to take Dell private.  I wonder what will happen to Dell's linux offerings in that event?  On the other hand, it'd be nice to see *some* standardization in the linux hardware interface world.

It seems we encounter the 'chicken-and-egg' conundrum with most human problems!

Personally I do mildly advocate Linux to my friends, but distressingly, the few who do use it now, started to do so from work-related compulsion and still fiddle with Windows for their personal purposes. :-(

In fact India is about as ideal a place as I can imagine where Linux could really take off in a big way. The population is huge (especially the younger segment) and even today, Windows would be unaffordable to 90% of the populace if it weren't for the damned fact of near-universal piracy.

That's why I inwardly cheer every time Microsoft institutes ever more difficult anti-piracy measures. I wish they'd go after a few people like the MPIA/RIAA folks do in the West. People would probably switch over to Linux by the hordes.

Instead I find in nearly all places that Windows is either pirated and used unethically or significant sums of money are wasted in legally using it when a superior (or equivalent) alternative is so readily available. An alternative that fosters tinkering, DIY, sharing, altruism and community building as well, which makes it superior in my eyes to the Miscrosoft ecosystem. But there's hope though. Apparently a whole state (Kerala) has adopted Linux and I do encounter more and more of the educated younger generation who're dual-booting.

But as in all cases, once momentum is gained in a direction, change is very slow. And Microsoft's immense organisational and tactical reach is no mean thing.

---

### Post by santosh83 on 2013-01-31
> **sdowney717 said:**
> Think this due to the bios chip being soldered into the board?
What a waste, electronic e-waste philosophy in play versus a design that allows for a recovery even by the end user.

Indeed. Thats why I insisted on getting my motherboard repaired twice when the prevailing trend (advocated to me by all the repair shops and technicians) is to "throw" it away and get a new system. It makes me sick. What's worse is the shops willing to do minor repairs are ever reducing. And not to mention no systems in place to reclaim broken parts and recycle them. Everything goes to the landfills apparently. :mad:

Anyway I've resolved to keep using any component until it's totally dead and beyond recall or cost to repair approaches the purchase price, even if that means I don't have the latest and greatest or am 'legacy.' So be it! :-)

---

### Post by Linuxisfast on 2013-01-31
> **lancest said:**
> I've never trusted Samsung laptops anyway.
ASUS/MSI run great for me.

My pick has been ASUS and I have several of them including heavily used EeePC, Transformer and two well used and traveled laptops, they all have been flawless. Also SONY and Toshiba laptops are other good ones to consider. I don't bother with the rest of them, Dell offers lots of tempting stuff as does HP here in India but I am well aware of their life here.

---

### Post by Hishighness on 2013-01-31
Man, that's scary. Thank God I had a dell.

I hope the same thing doesn't happen to tablets.

---

### Post by monkeybrain2012 on 2013-01-31
> **santosh83 said:**
> It seems it was a bug in the firmware that was the actual culprit, so blaming Linux is wrong. It's Samsung that should write better code and work more closely with a major worldwide alternative to Windows. In any case no software should ever be able to *brick* hardware or firmware, at least in this day and age.



I know that it is not Linux's fault. But if someone tries a live usb and bricks his computer guess who will be blamed?

---

### Post by doorknob60 on 2013-01-31
Dang, that's serious. I have a Samsung laptop, but it's pre UEFI (came with Windows 7, bought it in August last year). It's a well built machine for what I paid for it, and it runs flawlessly with Linux. Hope they get this problem fixed ASAP, because if I had bought this computer a couple months later, after Windows 8 came out, I could have accidentally discovered this myself :O

---

### Post by newbie2 on 2013-01-31
> **monkeybrain2012 said:**
> ... guess who will be blamed? ...
[QUOTE="Brid-Aine Parnell at theregister :"]Motherboard DEATH alert. Suddenly Windows 8 doesn't look so bad[/QUOTE]
[http://www.theregister.co.uk/2013/01/31/ubuntu_uefi_bricking_samsung_laptops/](http://www.theregister.co.uk/2013/01/31/ubuntu_uefi_bricking_samsung_laptops/)
:P

---

### Post by monkeybrain2012 on 2013-01-31
Canonical (and whoever managing other distros' too) should put a warning on the download page until Samsung fixes this.

---

### Post by oldfred on 2013-01-31
See post #4
It is in the release notes (which few read). I noticed it a month ago, while helping some Samsung users actually boot Linux and have it work. 

So not all models have the problem.

---

### Post by kurt18947 on 2013-01-31
> **santosh83 said:**
> 
............
 I do encounter more and more of the educated younger generation who're dual-booting.

But as in all cases, once momentum is gained in a direction, change is very slow. And Microsoft's immense organisational and tactical reach is no mean thing.

The generational thing might be a benefit.  Young people are not intimidated by technology.  People who have a somewhat tenuous understanding of what something really is and how it works are not as likely to "color outside the lines".  "If an 'expert' tells me to do A then B then C, I'm not going to deviate one iota.  If I do, the whole thing may blow up and I have no bloody clue how to fix it." Young people don't have the same inhibitions, or they just don't know any better:D.  And there's the "If Mom and Dad do THIS, I'm going to do THAT."

---

### Post by C.S.Cameron on 2013-01-31
From PC World:

[http://www.pcworld.com/article/2026807/booting-linux-via-uefi-can-brick-some-samsung-laptops.html](http://www.pcworld.com/article/2026807/booting-linux-via-uefi-can-brick-some-samsung-laptops.html)

---

### Post by varunendra on 2013-02-01
Similar topics merged.

---

### Post by prodigy_ on 2013-02-01
Serves people right for buying Samsung.

---

### Post by C.S.Cameron on 2013-02-01
Problem solved says The Register:

[http://www.theregister.co.uk/2013/02/01/linux_samsung_laptop_fix_advice/](http://www.theregister.co.uk/2013/02/01/linux_samsung_laptop_fix_advice/)

---

### Post by varunendra on 2013-02-02
> **C.S.Cameron said:**
> Problem solved says The Register:

[http://www.theregister.co.uk/2013/02/01/linux_samsung_laptop_fix_advice/](http://www.theregister.co.uk/2013/02/01/linux_samsung_laptop_fix_advice/)
Well.. I wouldn't call it 'Solved' unless the correction is made by samsung in its firmware itself rather than any fix in the kernel. Until then, it would always be dangerous to use the CD/DVDs, that have already been released, on these laptops.

---

### Post by unbreach on 2013-03-31
Im new to ubuntu, and in the seaarch for recording input devices troubleshooting run across this. im not too sure what the uefi stuff means. guess im super lucky i didnt brick this samsung. 

Ive installed 12.10 twice on this laptop. once in mid february and once in mid march. both using ubuntu from the main site, and using their universal usb installer. 

I am on a Samsung NP-SF410 A02 US

I dont have too many problems that I can see. Using 64bit Ubuntu managed the 64bit flash and got java in there somewhere. 

IDK if this will help anyone, or if anyone can give me any advice when 13.04 comes out for upgrading, if i should or shouldn't

Thanks for your time

JOsh

---

### Post by mr john on 2013-04-01
I agree that there should be a warning message put on the installer. And when you click "click here for more info" you should get a list of devices affected by this issue. This is a Samsung problem, but it it's going to negatively affect people who install Linux then we have to do what we can to make sure people know what they are getting into.



> **prodigy_ said:**
> Serves people right for buying Samsung.


Nonsense

---

