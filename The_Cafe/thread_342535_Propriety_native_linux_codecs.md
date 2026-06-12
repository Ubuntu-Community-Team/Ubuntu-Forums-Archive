---
title: "Propriety native linux codecs?"
date: 2007-01-20
forum: The Cafe
---

### Post by Sunnz on 2007-01-20
[http://www.fluendo.com/press/releases/PR-2007-01.html](http://www.fluendo.com/press/releases/PR-2007-01.html)

Seems like they are making native codecs for Linux. Though propriety, should be better than the damn dlls we are using now!!!

---

### Post by PurplePenguin on 2007-01-20
> **Sunnz said:**
> [http://www.fluendo.com/press/releases/PR-2007-01.html](http://www.fluendo.com/press/releases/PR-2007-01.html)

Seems like they are making native codecs for Linux. Though propriety, should be better than the damn dlls we are using now!!!

Here's a bit from the article on DesktopLinux.com: 

> Fluendo's codecs for Linux and Solaris are available now, direct from the company's online store. Most are priced at 7 Euros; the mp3 decoder, is free, however, and the complete bundle costs 28 Euros (approx. $36).

This seems good, though, because now commercially available linux distros can legally offer these kinds of multimedia playback.  I'll stick with downloading lame, flash, win32codecs, etc. to get multimedia codecs on my system, though.

---

### Post by tikal26 on 2007-01-20
Well, 
I understand that some people find no use for this, but in some countries it is illegal to do this and I just don't want to expose myself to this. I mean its the law so if I am able to keep myself safe for $36 why not. I don;t use ubuntu because I am cheap, but because I like linux and feel that Ubuntu is a solid distribution. Another thing that is good is that you can buy all of this for 86_64
architrecture also which win32codecs are not. Also, I like to be able to support the comapny fluendo since they are doing things like gstreamer and Elisa if I can get something usefull while bringing them business even better. I believe that if we want wider adoption of Linux we need to support commercial companies that use linux , this is the reason I get Nokia phones and I am buying the fleundo codec pack.

---

### Post by zerhacke on 2007-01-20
I think the idea of proprietary Linux software is against the very spirit of Linux.  I won't be buying.

---

### Post by Sunnz on 2007-01-20
Please correct me if I am wrong, but I think codecs are userland library, codes that runs on top of the OS... so I think it is alright, just because the OS is free it should not limit the kind of software people can run on it, in fact I think it is more good than harmful to have all kinds of software that runs on Linux.

Kernel side of things are little different though, the core (linux) of the system is free and should be kept free... but again, considering lots of people with nVidia cards has the propriety closed-source drivers installed...

---

### Post by maniacmusician on 2007-01-20
even the nvidia drivers don't run in kernel space; they can't, because they're closed source. They use a binary interface to communicate with the kernel. In Linux, this binary interface is not very stable or popular (since open source drivers are preferred everywhere), which is why its harder for people to develop proprietary drivers for Linux.

Windows has a really good binary interface, because they promote the existence of prorpietary drivers.

But I understand what you mean.

---

### Post by chele on 2007-01-21
> **Sunnz said:**
> Please correct me if I am wrong, but I think codecs are userland library, codes that runs on top of the OS... so I think it is alright, just because the OS is free it should not limit the kind of software people can run on it, in fact I think it is more good than harmful to have all kinds of software that runs on Linux.

Kernel side of things are little different though, the core (linux) of the system is free and should be kept free... but again, considering lots of people with nVidia cards has the propriety closed-source drivers installed... I think that Ubuntu has taken the opposite approach. No proprietary applications, including codecs. 

See this article: [http://www.markshuttleworth.com/archives/84](http://www.markshuttleworth.com/archives/84) for Mark Shuttleworth's take on this subject.

Ubuntu has always included some proprietary kernel modules, with the idea that those would be removed once Ubuntu has enough critical mass (10% of the PC market or more) By the way, nVidia only has 20% of the PC market, the most popular graphics chips are from Intel, and they have full support using libre drivers.

The proprietary Fluendo codecs are at least legal in most places, the w32codecs project has lifted proprietary dll's right out of MS windows applications. There is no way that any of the owners of those dll's have given anyone permission to do that.

Other codecs package are libre as far as I understand. The authors have figured out how play the secret formats through clever hacks.

---

### Post by lyceum on 2007-01-21
The sad fact is that not everyone is a computer geek. When my dad and I went to Linuxfest last year, the key words used over and over were "just works". Then I got him to switch and all of his hardware DID "just work" but when he couldn't play a DVD he was not happy. His exact words were "just works my ***". I had to explain the legal side of things to him (he is a lawyer, that went over REALLY well). By the end of the conversation he wanted to know who to call to pay for the right to watch his DVDs. If Linux or GNU or any FOSS project is gong work there has to be something for the non-geeks to get set up easily and legally.

---

### Post by chele on 2007-01-21
> **lyceum said:**
> The sad fact is that not everyone is a computer geek. When my dad and I went to Linuxfest last year, the key words used over and over were "just works". Then I got him to switch and all of his hardware DID "just work" but when he couldn't play a DVD he was not happy. His exact words were "just works my ***". I had to explain the legal side of things to him (he is a lawyer, that went over REALLY well). By the end of the conversation he wanted to know who to call to pay for the right to watch his DVDs. If Linux or GNU or any FOSS project is gong work there has to be something for the non-geeks to get set up easily and legally.

The owners of the DVD format are called DVD FLLC [http://www.dvdfllc.co.jp/faq.html](http://www.dvdfllc.co.jp/faq.html) While your dad may own the plastic of the DVDs, the format is owned by DVD FLLC and the content by the companies that distribute the films.

---

### Post by chele on 2007-01-21
> when he couldn't play a DVD he was not happy. His exact words were "just works my ***".

DVD playback does not work out of the box on a generic MS Windows system either. If you perform a simple, generic install of MS Windows (just windows, no driver or additional application disks) on a typical PC, many things do not work, including DVD playback.

---

### Post by Sunnz on 2007-01-21
Umm but if you buy a computer with Windows pre-installed, the DVD will 'just work', right?

So what's missing if you install Windows/Linux yourself? The driver or decoder or what not? Which one has legal issues? (The DVD driver would be supported by the Linux kernel, right?)

---

### Post by lyceum on 2007-01-21
> **chele said:**
> The owners of the DVD format are called DVD FLLC [http://www.dvdfllc.co.jp/faq.html](http://www.dvdfllc.co.jp/faq.html) While your dad may own the plastic of the DVDs, the format is owned by DVD FLLC and the content by the companies that distribute the films.

Right, that's what ticked him off. Why are they (Sony, Fox, etc...) hiding the movie from him, he paid for it. 

Thanks for the link.

---

### Post by lyceum on 2007-01-21
> **Sunnz said:**
> Umm but if you buy a computer with Windows pre-installed, the DVD will 'just work', right?

So what's missing if you install Windows/Linux yourself? The driver or decoder or what not? Which one has legal issues? (The DVD driver would be supported by the Linux kernel, right?)

If you use a disrto that doesn't care about the US legal system and sets it up to work out of the box, it works. Ubuntu does not pay for the rights, as it is not for sale. So, you have to use Easy Ubuntu or Automatix to get it working if you do not know how to do it yourself. The whole thing is to stop movie pirating, but instead it just hurts those legally buying the movies.

Does the MS box work? If you buy one with the right programs it does. Mediaplayer 11 seems to play DVD's out of the box, but that is the way it downloaded. That maybe because I already bought the lisence when I bought the PC.

---

### Post by chele on 2007-01-21
> **Sunnz said:**
> Umm but if you buy a computer with Windows pre-installed, the DVD will 'just work', right?

So what's missing if you install Windows/Linux yourself? The driver or decoder or what not? Which one has legal issues? (The DVD driver would be supported by the Linux kernel, right?) The decoder is missing. The drive itself is supported by the Linux kernel, as you say. 

When you buy a computer with MS windows already installed, usually the PC manufacturer or the DVD drive maker  or the store will have licensed and pre-loaded the codecs to play DVDs, assuming the computer comes with DVD drive.

If you buy a DVD drive and install it into a computer you generally will need to load the DVD software that comes with the DVD drive. In that case, the DVD drive manufacturer has purchased a license from DVD FLLC.

Linux users have the option of using libdvdcss which is software libre. It is not, however, licensed from DVD FLLC, so is not legal in many parts of the world. I use it myself, but have not found out if it is legal here in Canada.

Does the Fluendo package of codecs include DVD playback? If so, that would be a legal option.

---

### Post by PurplePenguin on 2007-01-22
> **lyceum said:**
> Right, that's what ticked him off. Why are they (Sony, Fox, etc...) hiding the movie from him, he paid for it. 

According to the movie studios, you can't "buy a DVD", you can "pay $20 for a license to watch a movie on a DVD, as long as you do it under their terms". :D

---

### Post by ssam on 2007-01-22
has anyone tried the fluendo codecs?

how do they compare to w32codecs? they ought to be faster and more stable if they are designed for linux.

---

### Post by lyceum on 2007-01-22
> **PurplePenguin said:**
> According to the movie studios, you can't "buy a DVD", you can "pay $20 for a license to watch a movie on a DVD, as long as you do it under their terms". :D

Which is why I do not buy movies. If I am going to rent movies, I do not want to store them at my house. If I buy something, I want to own it, which means doing what I want with it, including editing, making copies for myself, etc. I am still ticked of about that store I read about that edited movies for Christians that wanted to see the movie but not with an "R" rating. The studios got their money for the DVDs but still sued the company for messing with their "art". That company lost and had to give all the movies they had back to the studios, not money back and pay fines. That is nonsense!

---

### Post by Sunnz on 2007-01-24
> **chele said:**
> The decoder is missing. The drive itself is supported by the Linux kernel, as you say. 

When you buy a computer with MS windows already installed, usually the PC manufacturer or the DVD drive maker  or the store will have licensed and pre-loaded the codecs to play DVDs, assuming the computer comes with DVD drive.

If you buy a DVD drive and install it into a computer you generally will need to load the DVD software that comes with the DVD drive. In that case, the DVD drive manufacturer has purchased a license from DVD FLLC.

Linux users have the option of using libdvdcss which is software libre. It is not, however, licensed from DVD FLLC, so is not legal in many parts of the world. I use it myself, but have not found out if it is legal here in Canada.

Does the Fluendo package of codecs include DVD playback? If so, that would be a legal option.
I see... so does `DVD FLLC` specify how one can (legally) watch movies from their DVD drive on a computer???

---

### Post by awakatanka on 2007-01-24
Question to the people that life in a land where its illegal, must you buy for every OS/pc you got a license of dvd decoder? 

Maybe soon car manufactors going to put licenses on there car to, you got a license to use it, but other persons can't drive it and you must put in fuel from there gasstations, and if the car breaks you only can use there garage. Hmm put a license of use on everything and nobody owns anything and manufactors control us all.

---

### Post by Sunnz on 2007-01-24
Then you end up with communism?

Well when you buy a DVD-Drive, it should come with a license, right?

---

### Post by lyceum on 2007-01-24
> **awakatanka said:**
> Question to the people that life in a land where its illegal, must you buy for every OS/pc you got a license of dvd decoder? 

Maybe soon car manufactors going to put licenses on there car to, you got a license to use it, but other persons can't drive it and you must put in fuel from there gasstations, and if the car breaks you only can use there garage. Hmm put a license of use on everything and nobody owns anything and manufactors control us all.

That's what it feels like. <sigh> and considering that they are putting OS's into cars soon there will be a microsoft tax when you buy the car. :mad: Personally, I can't wait to get one and put linux on it. :)

---

### Post by chele on 2007-01-24
In the news, there is another commercial service due online in a few months, they say they will provide proprietary native codecs for most multimedia on Linux, including DVD playback.

[http://www.cnr.com/faq.html](http://www.cnr.com/faq.html)

> Will proprietary codecs and drivers be available at CNR.com?
           Yes. Using CNR.com, you will now be able to safely and legally add support to your Linux desktop for things such as mp3, Windows Media, Quick Time, Java, Flash, ATI drivers, nVidia drivers, and so on.


Appears to be the result of this: [http://www.catb.org/~esr/writings/world-domination/world-domination-201.html#id288946]("http://www.catb.org/%7Eesr/writings/world-domination/world-domination-201.html#id288946")

So, that addresses the legal side of the question. What about the ethics of running non-free software on your computer and participating in their proprietary games?

---

### Post by tikal26 on 2007-01-25
I feel that there are two people taht object CNR and I admire the ones that don't want it becasue they believe passionately on open source and stand by them. I have immense amount of respect for all of you because without you Linux would not get where it is today. So I guess that even if I don't agree with you I have total respect for you and your opposition of CNR in Ubuntu.

---

### Post by Sunnz on 2007-01-25
> **lyceum said:**
> That's what it feels like. <sigh> and considering that they are putting OS's into cars soon there will be a microsoft tax when you buy the car. :mad: Personally, I can't wait to get one and put linux on it. :)
Definitely ask for a discount/refund to have a car to come with no Windows...

We don't want cars to be end up like the PC world where Windows always comes pre-installed is the norm.

---

### Post by steven8 on 2007-01-26
> Definitely ask for a discount/refund to have a car to come with no Windows...

That's gonna sound neat when you ask a dealer for a car with no windows. :-)

---

