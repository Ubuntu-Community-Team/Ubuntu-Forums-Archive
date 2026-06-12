---
title: "Curiosity About Linux and Phones"
date: 2012-08-04
forum: The Cafe
---

### Post by Dylan1473 on 2012-08-04
I'm not sure exactly where to put this. I don't want to put it in any of the support categories because I'm pretty sure I already know the answer to the bits that even somewhat pertain to immediate instructions. And fair warning: this is going to be long.

So, lately I've been wondering a bit about Linux and its role in phones. It kind of started I guess when I was looking into solutions to sync phones with Linux ([I]("http://wammu.eu/") [found]("http://sourceforge.net/projects/nokuntu/develop/") [them]("http://series60-remote.sourceforge.net/"). Sort of). I don't just mean smart phones. That to, but I'm also curious about communicating through phones. Calling and texting and such. While certainly not nonexistent, there is a disappointing lack of the sort of information I'm looking for. I'm aware of projects like [Openmoko]("http://wiki.openmoko.org"), and I realize that Android is technically Linux based. I've also come across [GNU Telephony]("http://www.gnutelephony.org") which, while interesting, is not what I'm looking for. Well, let me get into some specific questions so I'm more clear:

My primary question: is it possible to use a laptop as a phone? I mean both "has it been done and is it a thing I could do?" and "is it hypothetically possible?". I know that some laptops include a slot for SIM cards. I also know that these are generally used with data plans, not for calling and texting. Which leads to my next question...

Is that a hardware or software restriction? Could Linux be adapted to use that sort of hardware for this purpose? Would I be able to, say, plug a USB SIM card reader into my computer and then effectively use it as a phone? Does software exist for this purpose/could it be developed?

Now another, related curiosity - is it possible to build one's own Linux based, handheld cellphone? I've found a few references to such (dead) projects and the Openmoko project, which doesn't really seem to be the same thing (it is a group of smarter people than me working on it, and you still have to get the parts from them). I've found discouraging answers in the past to the effect that the small, integrated parts used in cellphones would need to be specially developed and produced on a large scale and that no parts purchasable by enterprising individuals exist. Is this true?

I doubt that this is within my capabilities but I'm very interested in whether it is theoretically possible.

EDIT: To clarify, I'm referring to building Linux phones or using Linux computers as phones that can use existing cell phone networks, not common VoIP services like Skype. Whether the cell phone providers would allow it is a separate issue, as well.

---

### Post by newbie2 on 2012-08-05
Your looking for something like this ? -> [http://www.itechpost.com/articles/3780/20120804/android-ubuntu-looks-kill-motorola-atrix-2.htm](http://www.itechpost.com/articles/3780/20120804/android-ubuntu-looks-kill-motorola-atrix-2.htm)
:)

---

### Post by coldraven on 2012-08-05
Have a play with gammu, 
[http://wammu.eu/gammu/](http://wammu.eu/gammu/)

if you read this man page you can see the sort of capabilities it has.
[http://linux.die.net/man/1/gammu](http://linux.die.net/man/1/gammu)

gammu is in the repos, it is a CLI program.
I use it to back up my contacts in my Nokia

---

### Post by Dylan1473 on 2012-08-05
Unfortunately, neither of those is quite what I had in mind. I'm already aware it's possible to run Linux OSes on Smartphones and I know that wammu/gammu can be used to *interact* with phones. What I'm curious about is 

a) Using a laptop as a phone and removing the phone from the equation, perhaps by using a USB SIM card reader or similar hardware and Linux-based phone software (which I'm sure must exist in some form due to projects like Openmoko) as well as

b) Physically assembling a phone (in much the way one might construct a desktop or a laptop, albeit with greatly increased difficulty I'd expect) and then installing a Linux OS as well as software that would allow it to act on a phone on conventional networks using a SIM card

---

### Post by thatguruguy on 2012-08-05
I'm still not entirely sure what you're looking for. However, have you taken a look at [this]("http://www.ubuntu.com/devices/android")?

---

### Post by Dylan1473 on 2012-08-05
Yes, I have. That's cool and the sort of thing I want to see, but not specifically what I'm asking about. I have a very general curiosity about Linux and phones, but what I want to know about specifically is using Linux *as a phone*.

What I want to know is this: is it possible to make a Linux laptop (or presumably any computer device that can handle Linux and has the necessary equipment) that works as a cellphone. Like, interact *directly* with cell phone networks by sending messages and making phone calls. I know that some computers come equipped to use cellular networks for data transfer. I also know that the SIM card slots and adapters inside are intended for that purpose and that purpose only - but I want to know if that's a hardware restriction or if Linux plus the correct software would mean you could use it as a phone. Alternatively, is it possible to acquire equipment that  can be used with a computer in that way.

[I]It cannot be attached to a cellphone, as this kind of defeats the point.

[/I]Look, [here is the Openmoko project]("http://wiki.openmoko.org/wiki/Main_Page"). An open-source phone running on Linux. Think this, but with a laptop.

EDIT: To clarify, I mean like...using a computer as a phone on 3G/"4G" type networks to send and receive text messages and calls *exactly as a cellphone would*. No VoIP.

---

### Post by thatguruguy on 2012-08-06
> **Dylan1473 said:**
> Yes, I have. That's cool and the sort of thing I want to see, but not specifically what I'm asking about. I have a very general curiosity about Linux and phones, but what I want to know about specifically is using Linux *as a phone*.

What I want to know is this: is it possible to make a Linux laptop (or presumably any computer device that can handle Linux and has the necessary equipment) that works as a cellphone. Like, interact *directly* with cell phone networks by sending messages and making phone calls. I know that some computers come equipped to use cellular networks for data transfer. I also know that the SIM card slots and adapters inside are intended for that purpose and that purpose only - but I want to know if that's a hardware restriction or if Linux plus the correct software would mean you could use it as a phone. Alternatively, is it possible to acquire equipment that  can be used with a computer in that way.

[I]It cannot be attached to a cellphone, as this kind of defeats the point.

[/I]Look, [here is the Openmoko project]("http://wiki.openmoko.org/wiki/Main_Page"). An open-source phone running on Linux. Think this, but with a laptop.

EDIT: To clarify, I mean like...using a computer as a phone on 3G/"4G" type networks to send and receive text messages and calls *exactly as a cellphone would*. No VoIP.

I think it would be awkward to hold a laptop up to your ear.

The reason I provided the link I did was because you had also written the following:
> **Dylan1473 said:**
> 
b) Physically assembling a phone (in much the way one might construct a  desktop or a laptop, albeit with greatly increased difficulty I'd  expect) and then installing a Linux OS as well as software that would  allow it to act on a phone on conventional networks using a SIM  card

The Ubuntu phone project is meant for a device acts as a phone when you're using it as a phone (using conventional networks and using a sim card), and acts like a regular Ubuntu desktop when hooked up to a keyboard and monitor.

---

### Post by Grenage on 2012-08-06
I'm not sure why it *wouldn't* be possible, but I've not seen any software for handling phone calls through a sim card.

---

### Post by Dylan1473 on 2012-08-06
> I think it would be awkward to hold a laptop up to your ear.Indeed it would, though one could use a headset without much trouble. I wouldn't use a laptop as my main phone (wouldn't really be practical to carry around and use it for that purpose), I was just wondering if it was possible. The thing is, if it's possible on a laptop with Linux it's presumably possible on many computer devices due to the extreme flexibility of Linux, just as long as you can somehow integrate the hardware. Plus, I like texting people on my keyboard. Regarding the Ubuntu phone, that's neat and *close*, but it looks like it's just integrating Ubuntu with the already existing Android phone - Ubuntu itself isn't handling the actual texting and calling, just providing a nice interface for it along with lots of other handy features.

Anyway, I think I may have found an answer of sorts to one question - the software certainly exists to use Linux as a phone in a way without relying on a previously existing solution such as Android. I actually found it looking through the Openmoko projects trunk where I found a text file declaring some code to no longer be under development there and to look here - [freesmartphone.org]("http://www.freesmartphone.org/"). I'm still not entirely clear on how to use it or what equipment you'd need, but there's definitely software intended to make use of various phone features (such as texting and calling over GSM networks, GPS etc.). I don't know how heavily developed this one is either, but there have been a few changes within the last week and the IRC channel they've listed on their site is loaded with people.

So, other major question: does anyone know of a place to purchase cellphone parts? I very much doubt I could afford it right now but I'm interested in taking a look. I've previously heard it's basically impossible for an individual as the only parts that can realistically be used for that purpose tend to be mass manufactured specifically for use by cellphone companies. They also can't really be switched around and used with different parts.

EDIT: [Well how about that]("http://www.nowsms.com/faq/what-is-a-gsm-modem"). GSM modems can be used to send/receive text messages and looks like a mobile phone to your cell provider. [Now this is exactly what I am talking about.]("http://www.ebay.ca/itm/ZTE-MF180-Mobile-Broadband-HSPA-USB-GSM-3G-Modem-3-6-Mbps-Support-Voice-Calls-/221083688496?pt=LH_DefaultDomain_0&hash=item33799d5e30")

---

