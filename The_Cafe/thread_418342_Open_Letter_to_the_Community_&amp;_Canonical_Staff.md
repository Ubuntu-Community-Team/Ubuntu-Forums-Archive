---
title: "Open Letter to the Community &amp; Canonical Staff"
date: 2007-04-22
forum: The Cafe
---

### Post by JReagan1990 on 2007-04-22
Hello, everyone.

As a member of the Georgia (US) LoCo, I recieve many different support requests, both here in the forums, and others through my external support links.  One of the most recurring support requests that I recieve involves networking.  In today's age, we are all connected to the internet, and for the most of us, our jobs depend on this connectivity.  I feel that too many of the wireless cards go unsupported by Ubuntu, and we need the drivers.

That's why I am asking that either the Ubuntu community, Canonical, or both, start an initiative to obtain these drivers.  These companies are not going to give away their drivers for free, as I have recently found out.  Cards like Broadcoms, Realteks, and others that are also in heavy use, need support.  As a person who provides support, I have some fear about what could happen to us as a community if someone installs Ubuntu on their only computer, and their wireless does not work.  Then, that unfortunate person would not know where to turn, because they can not get to the web to find HOWTO's and other helpful information.  We do not have much time before "average Joe's" start installing Ubuntu, so I really think this is a critical piece for us to achieve.

I also understand that many people will not like the idea of supporting these cards because of proprietary drivers.  As an example, I will use freespire, they have chosen to support these cards, which has made their distro much easier to use on the networking end.  I believe in World Domination 201 philosophy, which is that we should use proprietary drivers until free ones are made.  Thankfully, we will have a free version of Ubuntu with Gutsy Gibbon, so that these kinds of drivers can be placed in the default Ubuntu.  

I have never really faced this problem personally, until now, and now I fully comprehend how people really feel without internet connectivity..  My laptop has been a major pain to me just because of my wireless card.  As you might imagine, most of what I do involves me being able to get my work done with other members of my LoCo, over my internet.  Luckly, I have another backup computer with a different connection, allowing me to post this letter.  This letter is just a simple request, and thank you in advance.


Sincerely,

Jon Reagan

Ubuntu Georgia LoCo member

---

### Post by Tomosaur on 2007-04-22
Therein lies the rub. Propietary developers won't give us free drivers, refuse to co-operate with FOSS developers to create free drivers, yet the people the propietary devs are ignoring still buy the propietary product. They will not learn their lesson if you keep giving them money, and we will forever remain stuck in a world of dodgy drivers.

---

### Post by PartisanEntity on 2007-04-22
This is a sore point for me too. I use my laptop mainly, and connect to the internet using wifi only. I had quite a headache getting wireless to work in Dapper back then and have noticed with some disappointment that wireless remains the area where a lot of ground remains uncovered when it comes to Ubuntu releases.

Hopefully a solution acceptable to all can be found, such as giving a user the option of using open source or proprietary drivers where available. p.s. Including out of the box support for wpa-psk encryption.

---

### Post by srt4play on 2007-04-22
I admit I haven't done any research on the matter, but reading this post got me thinking.  Would it be illegal to include ndiswrapper and windows drivers by default for cards that need them to fully function 100% ( i.e. not just flaky 802.11b functionality)?

---

### Post by JReagan1990 on 2007-04-22
> **PartisanEntity said:**
> This is a sore point for me too. I use my laptop mainly, and connect to the internet using wifi only. I had quite a headache getting wireless to work in Dapper back then and have noticed with some disappointment that wireless remains the area where a lot of ground remains uncovered when it comes to Ubuntu releases.

Hopefully a solution acceptable to all can be found, such as giving a user the option of using open source or proprietary drivers where available. p.s. Including out of the box support for wpa-psk encryption.


well, I guess part of that problem would be solved.  With Gutsy Gibbon, there will be a super FLOSS edition, and then the regular Ubuntu.

---

### Post by phen on 2007-04-22
but are these drivers available for linux if you pay for them? so this click and run thing should help. and for the next hardware purchase the people will buy hardware from companies that provide them free and open. If I would by a new notebook i would stick to either lenovo hp or other companies with at least intel centrino. afaik these companies provide drivers for free. if enough people act like this the other companies will wake up some time...

---

### Post by Mathiasdm on 2007-04-22
> **JReagan1990 said:**
> ...
Nothing Ubuntu can do about.
The bcm43xx guys reverse-engineer the drivers and make sure they're in the kernel.
If Broadcom would allow Ubuntu to distribute the (proprietary) firmware on the CD, everything would work straight out of the box.

The thing is: they don't.

(Same for others)

---

### Post by JReagan1990 on 2007-04-22
That stinks... Freespire (and Linspire) paid for the drivers, and they now work out of the box.  I think that they are the only exception, since they are more like a company than a community driven project.  If we were able to reverse engineer the drivers, maybe that would be best?

---

### Post by Slackpacker on 2007-04-22
I'm still very new and ignorant.  The proprietary drivers snafu mystifies me, especially the wireless issue.  That said, I  did my homework and bought an Orinoco card on eBay that Just Works - for way less than the proprietary cards retail for.  I can't seem to find any good reason why things should be this way.  Hardware manufacturers should have the least to lose if people switch to FLOSS.  Surely they aren't making a profit on drivers?  Furthermore, if wifi is an industry standard and the hardware that runs the card is (mostly) standard, then why is the card itself a proprietary snarl?  How many ways can there be to skin the wireless cat?  I can see that companies don't want to support or warrantee open drivers - but they clearly don't have to (i.e. nvidia, right?).  Is it a problem of potential reverse-engineering/espionage?  Or institutional distrust of FLOSS?

---

### Post by H.E. Pennypacker on 2007-04-22
Slackpacker hits the nail on the head.  There is no real reason for hardware manufacturers to not open source their drivers.  The main argument they use is that they fear their competitors will know how their drivers work, but this has to be rubbish.  I can't think of any evidence that supports their fear, and even if their competitors knew what the drivers did, I don't see how that would affect the manufacturing of wirless cards.

It seems to be that they are making excuses.  I will promise myself right now that I will not by a single product by Broadcom, and I will pay extra to find a company that is Linux friendly (e.g. Intel).  

You have seen that their refusal to make drivers open source actually affects their customer base.  Time and time again, people decide to stay away from companies such as Broadcom, and compared to competitors seeing the driver code, where is the real loss?   The loss is in keeping the drivers closed source.

The solution to Reagan's (the original poster of this thread) problem is to create a buzz regarding open source drivers.  The intention is to gain awareness and win over driver developers.  This would work like the open source NVidia driver project (it is called Nuveou or something).

---

### Post by Slackpacker on 2007-04-22
It also occurs to me that if Dell actually started selling pre-installed Linux machines, then they would most likely have supported wireless cards as an option, providing a very strong force for change.

And come to think of it, how did ethernet cards escape this problem?  I think it's safe to say that without them Linux would be stuck in the dark ages!

---

### Post by Daveski on 2007-04-22
> **H.E. Pennypacker said:**
> Slackpacker hits the nail on the head.  There is no real reason for hardware manufacturers to not open source their drivers.  The main argument they use is that they fear their competitors will know how their drivers work, but this has to be rubbish.  I can't think of any evidence that supports their fear, and even if their competitors knew what the drivers did, I don't see how that would affect the manufacturing of wirless cards.

I agree entirely, and recently tried to get someone to counter the exact same argument for Open Source 3D graphics drivers. I could not see how driver code would give competitors any advantage, but one of the answers I got was that nVidia uses some licenced third-part code / IP that could not be disclosed.

Surely the really clever stuff these days is done in firmware / microcode on the hardware itself? A driver is just a translator layer between the virtualized device and the real thing... or am I misunderstanding the whole process?

---

### Post by JReagan1990 on 2007-05-29
Alright.... after reading my original post from a way back, I feel somewhat stupid.  I will clarify: I don't want proprietary drivers.  I always prefer open source over proprietary.  How we get the drivers, I am still not sure.  It is almost like a war you can't win, but not all at once.  On one hand, if you pay for the drivers, they (the wireless drive builders) will never learn, as one of the previous poster's said. On the other hand, if you only try to backward-program the drivers, you can get incompatibility, and it takes much more effort.  So far, things are looking rather good for Linux, and lobbying seems to be working rather well.  Hopefully with Dell behind us, we can get some things done. 

I was only concerned for new users who install Ubuntu on their system, completely deleting Windows, and not having internet, which they would need to get help on how to get internet working on their computer.

At the same time, I bring some good news.  Dell is going to be working on getting multimedia codecs for Linux.  Sweet. :D

Anyways, hopefully this deal with Dell will help bring much better support to Ubuntu and Linux in general.

---

### Post by starcraft.man on 2007-05-29
I agree with everything thats been said. I do wish the companies supported open source more. Just like ATI, there really isn't any reason not to, it only alienated a small (but growing) market for them to sell their product to. Maybe we should start a petition directed at the companies holding onto proprietary drivers and refusing to support FLOSS. Petition can't hurt, and unlike the "sue me first list" we aren't asking to be sued :p.

---

### Post by Hex_Mandos on 2007-05-29
I agree that "just working" should be a priority. However, new users SHOULDN'T install Ubuntu before trying out their hardware using the LiveCD.

---

### Post by jrusso2 on 2007-05-29
Save your breath.  What Ubuntu and others do is a philosophical choice and it makes no sense in any other view.

Certainly people like Freespire and Linux Mint have the right idea here so I would suggest using one of these distros to any new user.

Save you breath on trying to get these Freedom riders to understand what regular users need.

---

### Post by starcraft.man on 2007-05-29
> **jrusso2 said:**
> Save your breath.  What Ubuntu and others do is a philosophical choice and it makes no sense in any other view.

Certainly people like Freespire and Linux Mint have the right idea here so I would suggest using one of these distros to any new user.

Save you breath on trying to get these Freedom riders to understand what regular users need.

Uh..... there are distributions for 'regular" (by regular, I assume you mean people who want no hassles) users. They are called Windows and Mac, and they don't need any config, they work out of the box and their programs install in one click >.>. There is even freespire like you mentioned. I don't particularly like your tone either... don't be so insulting to us Ubuntu users.

And how do you define "regular" users? I mean I know a lot of windows users, and IMO they are very under informed about their computers. For instance they don't know about partitions, that isn't a very difficult concept, I think its important and applies to all OS's. Does that mean they are regular? Maybe if I picked another 30 friends they would all know about partitions? That is of course just a single piece of information, the thought experiment works for anything else. Or does that mean that because OEM's have preinstalled OS's that they have never learned about this, and are actually ignorant of an important section of knowledge of computers? You make very broad and generalized statements, and such are usually flawed and easily refuted.

And I might add, there is nothing that "forces" you to be here if you find the philosophy of Ubuntu to be so (insert your negative word of choice), you are free to go use another distro (of Linux Windows or Mac).

---

