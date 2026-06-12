---
title: "Why not use company drivers?"
date: 2009-03-30
forum: The Cafe
---

### Post by Benzaa on 2009-03-30
Hi,

Today, while I was installing xubuntu, I was wondering the reasons for not using drivers that are provided by the company.

For example, in my computer, xubuntu does not recognize the microphone. I have tried everything that I could find on google and none of those things have worked.

I understand that linux was built around the idea of being able to see what is under the hood, but, lets being honest, how many of you have been playing with the sound drivers (or any other driver) to make something work??

What is the reason for not going to the packard bell website (in my case), get the windows sound driver, and use it in xubuntu?

That could simplify a lot the development of it, couldnt it?


Well, just something that I wanted to ask to the community.

---

### Post by suitedaces on 2009-03-30
I think it's because the driver is built for windows, and will not work in linux.

---

### Post by Chemical Imbalance on 2009-03-30
Windows drivers aren't made with linux in mind--they are made for the Windows kernel.  Some drivers do work with a wrapper, but they were not intended for linux.

The fault is the hardware manafacturers for not opening up their specs.  If they opensourced their drivers, then they could be ported to various operating systems.

The linux community oftentimes has to reverse engineer the drivers just to be able to use them.

---

### Post by s.fox on 2009-03-30
I had a go using windows drivers using ndiswrapper.   Not something I would want to do again. In the end I gave up and used a linux driver instead. :)

---

### Post by SunnyRabbiera on 2009-03-30
Linux can only do so much without these companies supporting it.
Like said above the drivers are mainly written for windows, in order to make them work the developers create workarounds until they figure out how to reverse engineer.
I blame these companies too, linux is the most versatile OS out there yet completely ignored because of greed and ignorance.

---

### Post by joshdudeha on 2009-03-30
> **SunnyRabbiera said:**
> Linux can only do so much without these companies supporting it.
Like said above the drivers are mainly written for windows, in order to make them work the developers create workarounds until they figure out how to reverse engineer.
I blame these companies too, linux is the most versatile OS out there yet completely ignored because of greed and ignorance.

Wow. Imagine how more amazing Linux would be with the companies supporting it.
It really would be incredible I think.

But back to the question, that's a bit like asking for a windows program to work in Linux, it just wasn't built for the system.
Some day, it'll have just as good support, even though it has come EXTREMELY far today.

---

### Post by Benzaa on 2009-03-30
What about Dell?

They are selling computers with Ubuntu installed, right?

Are they developing their own drivers or just using the linux drivers?

---

### Post by forrestcupp on 2009-03-30
> **Benzaa said:**
> What about Dell?

They are selling computers with Ubuntu installed, right?

Are they developing their own drivers or just using the linux drivers?

They're using drivers already made for Linux, and their Ubuntu pre-installed computers only use hardware that works well with Linux.

But we *do* use company developed drivers when they're available.  A lot of people use nvidia's and ati's drivers rather than the open source ones.  It's just that there are a lot of hardware makers that don't support Linux.  Lexmark is horrible.

The main idea is that if you're setting up a system for Linux, check into what hardware works with Linux before you buy.  Then you'll have a painless experience.  The reason MacOS works so well is because it only runs on the hardware that is made for it.  If you tried installing unsupported hardware in a Mac, you'd have just as much trouble or more than doing it in Linux.

---

### Post by mips on 2009-03-30
> **Benzaa said:**
> What about Dell?

They are selling computers with Ubuntu installed, right?

Are they developing their own drivers or just using the linux drivers?

Linux drivers.

---

### Post by SunnyRabbiera on 2009-03-30
> **Benzaa said:**
> What about Dell?

They are selling computers with Ubuntu installed, right?

Are they developing their own drivers or just using the linux drivers?

Dell contributes drivers

---

### Post by Chemical Imbalance on 2009-03-30
Intel is an excellent contributor to the opensource community.

---

### Post by Benzaa on 2009-03-30
Well then, all I have to do is wait until packard bell starts developing drivers for their laptops.

Thanks for the answers

---

### Post by Chemical Imbalance on 2009-03-30
> **Benzaa said:**
> Well then, all I have to do is wait until packard bell starts developing drivers for their laptops.

Thanks for the answers

I wouldn't sit around waiting if I were you :)

May take a while...a long while, if ever.  They might tomorrow, or never.

---

### Post by forrestcupp on 2009-03-30
I didn't even know that Packard Bell is still around.

Packard Bell will never develop drivers for Linux.  But you may be in luck with the makers of the individual pieces of hardware in the Packard Bell laptop.  Packard Bell probably doesn't make much hardware; they just take hardware from other companies, like Intel, and throw them together to make their own computers.  You need to know the brands of the different things like the wireless device, sound card, graphics card, etc.  Then you will be able to know how compatible they are.

Have you even tried Linux on it yet?  If not, boot up a LiveCD and you'll be able to tell what works and what doesn't.  You don't have to install Ubuntu to run it off the Live CD.

If you've tried it, and you're having problems, there are plenty of people in the support sections of this forum who are there just to help you with the specific problems you're having.

---

### Post by Benzaa on 2009-03-30
Thanks for the suggestion of using a live CD, but too late, I've been working with linux for over a year :D

I've tried several distributions (Fedora, PClinux, Ubuntu and Xubuntu, arch). None were able to make my microphone work. 

I removed Alsa and install OSS. No luck at all. Tried so many things. Maybe I am missing something really simple.

That is the only reason why I still have a partition with windows Xp. I need to use Skype to call home, otherwise, my computer would be windows free :p. 

Yesterday I did a fresh install of Windows. It was kind of slow. I think it was a virus (i dont have anti-virus or firewall on windows). During the installation I was wondering, how come the linux developers dont create a wrapper for the known drivers. 

But know I understand the reasons.

---

### Post by Vince4Amy on 2009-03-30
> Yesterday I did a fresh install of Windows. It was kind of slow.

If you used the Packard Bell reinstall program you would get a lot of OEM Bloat with it. Packard Bell are one of the worst for adding that rubbish to a Windows install.

---

### Post by Lunx on 2009-03-30
> **Vince4Amy said:**
> Packard Bell are one of the worst for adding that rubbish to a Windows install.

They'd still have to go hard to catch Sony...

Sony machine running Windows with Norton AV installed, ahh, now there's a true thing of beauty :lolflag:

---

### Post by forrestcupp on 2009-03-31
> **Benzaa said:**
> None were able to make my microphone work. 

I removed Alsa and install OSS. No luck at all. Tried so many things. Maybe I am missing something really simple.


When I first started with Linux, I couldn't figure out how to get my audio inputs working.  It ended up that I just had to run **amixer** in the command line to get to the CLI alsa mixer, and turn up the volume sliders that apply to the inputs.  I forget which one it is, but one of the F buttons switches your sliders to the inputs.

Maybe it's actually working, but the slider is just down all the way.  For some reason it's like that by default sometimes.

---

### Post by ReddogOne on 2009-03-31
> **SunnyRabbiera said:**
> I blame these companies too, Linux is the most versatile OS out there yet completely ignored because of greed and ignorance.

I get people like to have a good old moan but it doubt its got anything to do with greed or ignorance. 

Lots of these companies are quite small or don't have particularly wide profit margins. So why should they spend money on a 'handful' of customers meaning they may spend 50% of their investment fund on 5% of their customers. Makes no business sense. 

Going open source is probably not an option as well as many of the suppliers have unique selling points which are made possible to because of the software. Going open source would loose them their advantage. 

If the Linux community wants to change this I think they would have to do something like come up with some open standard so that drivers could be moved to any OS that supported the standard. Whether this is possible or not... I would not have a clue.

---

### Post by forrestcupp on 2009-03-31
> **ReddogOne said:**
> 
Going open source is probably not an option as well as many of the suppliers have unique selling points which are made possible to because of the software. Going open source would loose them their advantage. That's something that a lot of Free Software advocates just can't seem to understand.

> **ReddogOne said:**
> If the Linux community wants to change this I think they would have to do something like come up with some open standard so that drivers could be moved to any OS that supported the standard. Whether this is possible or not... I would not have a clue.I'm sure that would be possible, and it's a great idea.  Unfortunately, most hardware makers don't care enough that they would change their format and use it even if the open standard were developed for them.

---

