---
title: "audio user question re 16.04 to 16.10 upgrade"
date: 2017-01-25
forum: Ubuntu Studio
---

### Post by braintree12 on 2017-01-25
Some questions re: upgrading from Ubuntu Studio 16.04 to 16.10. I've got Ardour 5.5 and JACK working nicely on 16.04, with a2jmidid set up to run midi clock out to my sound card (RME pci) to drive a modular synth, and various plugins (including LXVST) working. How disruptive is the upgrade? I'm guessing it reinstalls Ardour -- it says version "5" -- but how much havoc does it cause with the other files/folders? I'm a relative newcomer to Linux and Ardour so, sorry, if this is an un-technical noob question. How essential is upgrading?

---

### Post by howefield on 2017-01-25
> **braintree12 said:**
> Some questions re: upgrading from Ubuntu Studio 16.04 to 16.10. I've got Ardour 5.5 and JACK working nicely on 16.04, with a2jmidid set up to run midi clock out to my sound card (RME pci) to drive a modular synth, and various plugins (including LXVST) working.

You've answered your own question.. "*working nicely on 16.04*" ;)

> How disruptive is the upgrade? I'm guessing it reinstalls Ardour -- it says version "5" -- but how much havoc does it cause with the other files/folders? I'm a relative newcomer to Linux and Ardour so, sorry, if this is an un-technical noob question. How essential is upgrading?

Upgrading to 16.10 with its 9 month support life cycle is very disruptive in as much as you are really committing to upgrading again to 17.04, 17.10 before you get to the next Long Term Support release of 18.04. 

I enjoy the incremental improvements of each release but on machines that are expected to just keep on working I'd suggest sticking to Long Term Support releases.

---

### Post by braintree12 on 2017-01-25
Thanks, much appreciated!

---

### Post by Bucky Ball on 2017-01-25
> **howefield said:**
> You've answered your own question.. "*working nicely on 16.04*" ;)

Upgrading to 16.10 with its 9 month support life cycle is very disruptive in as much as you are really committing to upgrading again to 17.04, 17.10 before you get to the next Long Term Support release of 18.04. 


Couldn't agree more. If you're running an audio production box, stick to LTS. If everything is working, leave as is. You are supported until 2021. With the interim releases, you may need to do that unexpected OS upgrade halfway through mixing down your next million selling album!

Seriously, you're right where you should be for audio production. Spend time audio producing rather than faffing about with upgrades every six months I reckon. 

Good luck with it. Sounds like you have your audio setup just nice (something I'll be aiming for, finally on Linux, on my own machine when I finally get time in a month or two). :)

---

### Post by howefield on 2017-01-25
> **Bucky Ball said:**
> You are supported until 2021.

2019 with Ubuntu Studio 16.04

---

### Post by braintree12 on 2017-01-25
Thanks. I set the software updater for "long term releases only." I have been doing the kernel changes, and other smaller updates, as they come in. Performance seems to have improved, if anything. I assume there's no risk in that.

---

### Post by howefield on 2017-01-25
> **braintree12 said:**
>  I have been doing the kernel changes, and other smaller updates, as they come in. Performance seems to have improved, if anything. I assume there's no risk in that.

I'd say low risk rather than no risk :)

If you get bitten with a kernel issue (which although unlikely is not completely unknown) generally all you'd do is boot with the last know good one.

---

### Post by braintree12 on 2017-01-25
I'd rather not have to deal with a bad kernel, since it might take me a while to identify the problem. I'm OK with skipping those regular, smaller updates until 4/19 if I'm not bringing some other kind of doom down on my head. I don't use the PC for websurfing, except as related to linux/software issues. I'd be curious to get your opinion on this, or if you could point me to a thread on "updating pros and cons," that would be great, too.

---

### Post by Bucky Ball on 2017-01-25
> **howefield said:**
> 2019 with Ubuntu Studio 16.04

Got ya. That's right; UStudio is based on Xubuntu?

Anyhow, for the record, I'm using Xubuntu-core, also based on Xubuntu, tweaked for audio and video production so very similar and, *_to this point_*, have had no kernel issues running 16.04 LTS. (I don't need everything that comes with UStudio. I'll never use some of it. :))

A bad kernel means rebooting and dropping to the last working one (the majority of the time), as howefield mentioned. I'd rather that than upgrading every five minutes and running the LTS is far from bringing doom down on your head. You're using one now. Any issues so far? ;)

---

### Post by howefield on 2017-01-26
> **braintree12 said:**
> ... I'd be curious to get your opinion on this, or if you could point me to a thread on "updating pros and cons," that would be great, too.

Well I wouldn't countenance not updating regularly (albeit I switch off automatic updates so I can do them on my own timetable). The vast majority of updates to a release, in this case 16.04 are security updates, so in my view they are not nice to have(s) but must haves.

Bearing in mind that each update goes through testing and quality before it gets to the -proposed repositories and even then the software updater will phase the updates in stages so a bad update can be caught before everyone gets it means that the risk is really, really low.

You used the term "no risk" above, there is no such thing, but I am concerned that I have inadvertently made you think the risk is greater than it is.

---

### Post by braintree12 on 2017-01-26
Thanks. I've been installing all the updates since 16.04 and haven't had a problem. I expect I'll keep doing it until 18.04 arrives. I appreciate the feedback about the interim "decimal point" releases, it's really helpful.

---

