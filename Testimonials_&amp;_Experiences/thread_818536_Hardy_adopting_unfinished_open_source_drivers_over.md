---
title: "Hardy adopting unfinished open source drivers over working proprietary ones"
date: 2008-06-04
forum: Testimonials &amp; Experiences
---

### Post by mostwanted on 2008-06-04
I've used Ubuntu since Warty and wireless has never been a real problem for me as the Intel chipsets are usually well supported in Linux.  The problem this time is a bug affecting some Intel wireless chipsets attempting to connect to hidden access points. They simply can't. The cause of the problem is Ubuntu's inclusion of new open source Intel drivers instead of the old semi-proprietary - but working - ones.

Why Canonical chooses to ordain their *long term support* release with unfinished drivers I cannot begin to grasp.

It's a good thing I'm a seasoned Linux user and know how to google and fix driver related issues, but any user with minimal Linux experience would be extremely frustrated - I suspect Internet connection problems are probably the most frustrating issues for new users since Ubuntu pretty much requires a working connection to be properly set up. This is particularly disheartening because Ubuntu prides itself in including a large variety of proprietary drivers for wifi cards so the user won't run in to this kind of problem.

Anyway, the verdict for Hardy has to be a thumbs down. It definitely does not seem very polished for an LTS release.

---

### Post by msrinath80 on 2008-06-04
Well, I do share your thoughts there. This is why I left Ubuntu for Fedora. Configuring things are not as easy as before, but least they work without problems.

---

### Post by stchman on 2008-06-04
> **mostwanted said:**
> I've used Ubuntu since Warty and wireless has never been a real problem for me as the Intel chipsets are usually well supported in Linux.  The problem this time is a bug affecting some Intel wireless chipsets attempting to connect to hidden access points. They simply can't. The cause of the problem is Ubuntu's inclusion of new open source Intel drivers instead of the old semi-proprietary - but working - ones.

Why Canonical chooses to ordain their *long term support* release with unfinished drivers I cannot begin to grasp.

It's a good thing I'm a seasoned Linux user and know how to google and fix driver related issues, but any user with minimal Linux experience would be extremely frustrated - I suspect Internet connection problems are probably the most frustrating issues for new users since Ubuntu pretty much requires a working connection to be properly set up. This is particularly disheartening because Ubuntu prides itself in including a large variety of proprietary drivers for wifi cards so the user won't run in to this kind of problem.

Anyway, the verdict for Hardy has to be a thumbs down. It definitely does not seem very polished for an LTS release.

I agree, the 3945 wireless card from what I understand was a big one going to the open source driver.

I wish there was a menu option that you could use the proprietary driver or the open source one.

---

### Post by karellen on 2008-06-04
agree with that, lucky for me as I have no wireless on my desktop rig. anyway, I'm a happy Mandriva user for more than a month, so it doesn't matter anymore how well or bad Hardy behaves

---

### Post by jrusso2 on 2008-06-04
Heh, I figured that was what was going on when drivers that used to work no longer work like Atheros and Intel.

---

### Post by hyper_ch on 2008-06-05
Why?
Have a look at the ubuntu page:
> Ubuntu CDs contain only free software applications; we encourage you to use free and open source software, improve it and pass it on.

---

### Post by karellen on 2008-06-05
I believe any Linux distro (especially one that's aiming at the masses) should adopt the **best working drivers**, no matter they're free or not. there are already enough distro who emphasize "absolute" freeom (gNewSense for example)

---

### Post by hyper_ch on 2008-06-05
> **karellen said:**
> I believe any Linux distro (especially one that's aiming at the masses) should adopt the **best working drivers**, no matter they're free or not. there are already enough distro who emphasize "absolute" freeom (gNewSense for example)

Well, Canonical wants to promote free software with Ubuntu. That's their aim. Other companies/distros have different stances.

The problem is, without a braod adaption of free and open source software the hardware manufacturer are not really inclined to provide free and open source drivers. By integrating proprietary drivers hardware manufacturers aren't inclined to provide free and open source drivers either.

---

### Post by klaasvanschelven on 2008-06-05
> **hyper_ch said:**
> Well, Canonical wants to promote free software with Ubuntu. That's their aim.

I'm not sure how one promotes free software by packaging non working free software. I surely know Ubuntu 8.04 has made me very very angry because of the above and a lot of other problems.

---

### Post by hyper_ch on 2008-06-05
it works all for me ;)

---

### Post by 23meg on 2008-06-05
> **mostwanted]The problem this time is a bug affecting some Intel wireless chipsets attempting to connect to hidden access points. They simply can't. The cause of the problem is Ubuntu's inclusion of new open source Intel drivers instead of the old semi-proprietary - but working - ones.[/QUOTE]

Could you specify the exact chipset you have, the "semi-proprietary" driver that you think should have been shipped, and the free driver that doesn't work? There may be issues other than licensing and the specific feature that's broken for you that may have affected the decision.

[QUOTE=hyper_ch said:**
> Why?
Have a look at the ubuntu page:

It deliberately says "free software **applications**", so as to exclude the non-free firmware, drivers and fonts.

> **hyper_ch said:**
> Well, Canonical wants to promote free software with Ubuntu. That's their aim. Other companies/distros have different stances.

The problem is, without a braod adaption of free and open source software the hardware manufacturer are not really inclined to provide free and open source drivers. By integrating proprietary drivers hardware manufacturers aren't inclined to provide free and open source drivers either.

Your case being this, and your example being Ubuntu, they don't match. Ubuntu's stance leans more towards providing the available non-free firmware and drivers that are distributable and practical to ship, if they are absolutely necessary for the functioning of the hardware, so that the user can actually use the free software stack that goes on top of those.

---

### Post by hyper_ch on 2008-06-05
I just wanted to keep it very short but if you insist:
> 
Our work is driven by a philosophy on software freedom that aims to spread and bring the benefits of software to all parts of the world. At the core of the Ubuntu Philosophy are these core philosophical ideals:

   1. Every computer user should have the freedom to download, run, copy, distribute, study, share, change and improve their software for any purpose, without paying licensing fees.
   2. Every computer user should be able to use their software in the language of their choice.
   3. Every computer user should be given every opportunity to use software, even if they work under a disability.

Our philosophy is reflected in the software we produce and included in our distribution. As a result, the licensing terms of the software we distribute are measured against our philosophy, using the Ubuntu License Policy.

When you install Ubuntu almost all of the software installed already meets these ideals, and we are working to ensure that every single piece of software you need is available under a license that gives you those freedoms.

**Currently, we make a specific exception for some "drivers" which are only available in binary form, without which many computers will not complete the Ubuntu installation.** We place these in a restricted section of your system which makes them easy to remove if you do not need them. 

---

### Post by ukripper on 2008-06-05
Particular case of 3945 which doesn't like hidden ssids and /etc/network/interfaces fails to configure using WPA/WPA2 using wext (for some reason wext is not recognised by interfaces for this chipset, also fails to see iwl3945 when I replace wext with iwl3945) so i can't really configure interfaces file to work with WPA. Only way I connect to hidden essids is through network manager and each time I have to manually enter the key on reboot. i can live with it but I don't understand why interfaces file fails to pick up wext or iwl3945.

ipw3945 had its own issues on gutsy but I replaced that with iwl

---

### Post by Flimm on 2008-06-05
> **msrinath80 said:**
> Well, I do share your thoughts there. This is why I left Ubuntu for Fedora. Configuring things are not as easy as before, but least they work without problems.
I thought Fedora didn't ship any proprietary drivers whatsoever.

---

### Post by stchman on 2008-06-05
> **ukripper said:**
> Particular case of 3945 which doesn't like hidden ssids and /etc/network/interfaces fails to configure using WPA/WPA2 using wext (for some reason wext is not recognised by interfaces for this chipset, also fails to see iwl3945 when I replace wext with iwl3945) so i can't really configure interfaces file to work with WPA. Only way I connect to hidden essids is through network manager and each time I have to manually enter the key on reboot. i can live with it but I don't understand why interfaces file fails to pick up wext or iwl3945.

ipw3945 had its own issues on gutsy but I replaced that with iwl

Hidden SSIDs are a complete waste of time and offer no security benefits at all.  MAC filtering is also up there for useless security measures.  Enable your SSID and you will have an easier time.

You are already running WPA 1/2 so you you don't need anything else.

---

### Post by ukripper on 2008-06-05
> **stchman said:**
> Hidden SSIDs are a complete waste of time and offer no security benefits at all.  MAC filtering is also up there for useless security measures.  Enable your SSID and you will have an easier time.

You are already running WPA 1/2 so you you don't need anything else.

I am pretty much aware of that. At home I have disabled hidden SSID but at work due to company's policy we can't disable hidden SSIDs on our routers. MAC filtering is also in place and so is WPA2. MAC filtering does help to keep amateur crackers away, WPA2 does the most with AES encryption.  

Our IT Directors are hard to convince in terms of hidden SSID provides not much benefit. As they run mostly windows XP so not a problem for them.

---

### Post by AdamWill on 2008-06-05
There is no difference in freedom between ipw* and iwl* drivers. For both, the code of the driver is free software, but they require non-free firmware.

The difference between them is simply that ipw* drivers use the old softmac infrastructure for wireless drivers, while the iwl* drivers use the new mac80211 infrastructure. iwl* is just a port of ipw* to mac80211.

---

### Post by ukripper on 2008-06-05
From my experience ipw3945 was really unreliable when it came to connection as it kept dropping until I switched to iwl3945 which is highly stable and doesn't drop. I don't really care whether it is free or not all I care is it works with my wireless card on ubuntu.

---

### Post by Keyper7 on 2008-06-05
I'm getting tired of saying what should be obvious: **stop giving statements about what Ubuntu should do or not do based on specific experiences**. iwl3945 connects fine to my hidden WEP network while ipw3945 caused hard freezes and kernel panics on my laptop.

Furthermore,

> **karellen said:**
> I believe any Linux distro (especially one that's aiming at the masses) should adopt the **best working drivers**, no matter they're free or not. there are already enough distro who emphasize "absolute" freeom (gNewSense for example)

there's no such thing as "something any Linux distro should do", otherwise what would be the point of having different distros at all? 

Ubuntu's philosophy is not, never was and probably never will be being for the masses **at all costs**. It's trying to be for the masses while promoting free software and still giving the user the option ot easily use proprietary stuff. ipw3945 is an exception because it directly involves decisions from the kernel team.

If you don't agree with that philosophy, that's what distros like Linux Mint are for (to give an example where you don't even have to leave the Ubuntu world).

---

### Post by stchman on 2008-06-05
> **ukripper said:**
> I am pretty much aware of that. At home I have disabled hidden SSID but at work due to company's policy we can't disable hidden SSIDs on our routers. MAC filtering is also in place and so is WPA2. MAC filtering does help to keep amateur crackers away, WPA2 does the most with AES encryption.  

Our IT Directors are hard to convince in terms of hidden SSID provides not much benefit. As they run mostly windows XP so not a problem for them.

If you are running WPA2 with a strong passphrase then MAC filtering is COMPLETELY unnecessary.  You IT directors need to do a little catching up on the wireless stuff.

You can use Wicd as it works far better on hidden SSIDs.

Here is a little reading for your IT people.  Those XP laptops spew out the SSID constantly when they are connected to a hidden SSID.
[http://blogs.zdnet.com/Ou/?p=454](http://blogs.zdnet.com/Ou/?p=454)

It amazes me that still to this day people think that hidden SSID and MAC filtering do anything for security.  Router manufacturers are to blame as well.

---

### Post by ImpressMe on 2008-06-05
Believe it or not, but end users tend to value "freedom from IT related problems" more than terms like "open source" and "community".

With a less than insignificant market share for desktop operating systems Canonical and the 1000+ other distros should think about delivering flawless working products with great usability rather than releasing flawed and complex products marketed with empty rhetorics.

---

### Post by Keyper7 on 2008-06-05
> **ImpressMe said:**
> Believe it or not, but end users tend to value "freedom from IT related problems" more than terms like "open source" and "community".

With a less than insignificant market share for desktop operating systems Canonical and the 1000+ other distros should think about delivering flawless working products with great usability rather than releasing flawed and complex products marketed with empty rhetorics.

Sigh... Here I go, repeating myself once again...

Okay, let's try this again. Pay attention. Seriously.

**There ARE distros that don't mind shipping proprietary drivers by default. Linux Mint is an example. Just choose whatever suits you better and use it. Nobody is pointing a gun to your head and forcing you to use anything.**

But don't call Ubuntu's principles "empty rhetorics" just because you don't agree with them. That's arrogance. In fact your "proprietary drivers = less IT problems" logic is much more close of "empty rethorics" than anything Canonical has ever said. Do a quick search for "ipw3945 freeze" in Google and you'll understand how flawed this argument is.

Never, EVER, underestimate the bad side of proprietary drivers. A lot of ATI users know that very well.

---

### Post by ukripper on 2008-06-06
> **stchman said:**
> If you are running WPA2 with a strong passphrase then MAC filtering is COMPLETELY unnecessary.  You IT directors need to do a little catching up on the wireless stuff.

You can use Wicd as it works far better on hidden SSIDs.

Here is a little reading for your IT people.  Those XP laptops spew out the SSID constantly when they are connected to a hidden SSID.
[http://blogs.zdnet.com/Ou/?p=454](http://blogs.zdnet.com/Ou/?p=454)

It amazes me that still to this day people think that hidden SSID and MAC filtering do anything for security.  Router manufacturers are to blame as well.

Especially, hidden ssid should be scrapped. Mac filtering still is first point of counter measure so i would still have it as my initial blacklist filter.  WPA2 takes care of the rest.

Wicd is not an option for me as i just do things using configuration files through command line mostly. That is why i am going to remove network manager as soon as i get iwl3945 working in my interfaces file. My only purpose of using network manager is to have connection to my wireless. i hope hardy sorts it out for me when I upgrade.


i agree on IT literacy of some IT directors is pretty limited but still they think they know it all. Working under them is not easy though.

---

