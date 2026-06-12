---
title: "Recommendations Windows-&gt;Linux"
date: 2008-07-13
forum: Ubuntu Studio
---

### Post by TomR55 on 2008-07-13
I'm a relative neophyte when it comes to recording and producing music in the Linux world. I'm currently running Hefty and recently installed the Unbuntu Studio suite.

First off: I'm pretty surprised with the number and types of tools available. I'm equally confident that some thought was devoted to ensuring that these tools inter-operate in a fairly seamless manner.

I haven't purchased a high quality soundcard for this box because I've used Windows in the past for all of my sound work. On that platform I'm using Cubase, Native Instruments, etc. I have several outboard mastering packages, and have been pretty happy with the quality of the products (as have other's).

The ONLY reason that I keep this Windoze box around is to continue composing and producing music.

Sorry about the longish introduction, but I thought it relevant to the following:

1) I see that RME (an excellent manufacturer) has Linux support. Is that the soundcard that most of you are using for quality work? (You should know that apart from the four and six string guitar work that I occasionally require, I've been using VSTi for most of the actual tracks.)

2) It appears that RME support is built-in to Jack or is that an illusion?

3) On Windows I've always used two disks: one holding libraries, etc., the other instrument patches ---the reason being that Kontact and similar tools seem to require fast, unimpeded disk access. Should I invest in a second disk for this box and assume similar i/o requirements?

4) I assume that WINE is another alternative? For reasons unknown, I would prefer not to add yet another layer ... but, if some of you who are more experienced tell me that WINE is the way to go ... hell, that is certainly feasible.

Again: I know that these questions are troublesome, and so I appreciate any kind souls' time and attention in at least providing opinion and preliminary feedback so that I might make better informed decisions.

Thanks,

TomR

---

### Post by Capoeira on 2008-07-13
well you will need wine at least to use your VSTi's with DSSI-VST in Linux since you wont find most of your instruments as DSSI-Variant.

---

### Post by thorgal on 2008-07-13
Hi Tom, I will try to answer as best as I can.

> **TomR55 said:**
> 
1) I see that RME (an excellent manufacturer) has Linux support. Is that the soundcard that most of you are using for quality work? 


I use an RME soundcard (the PCI Hammerfall DSP) linked to RME's Multiface II IO box. It's working great and gives me the sound quality I expect. COnsidering the price of this piece of h/w, that was the least :)


> **TomR55 said:**
> 
2) It appears that RME support is built-in to Jack or is that an illusion?

It's an illusion. Jack does not support ANY soundcard. Jack is handling audio flow between jack aware apps and lower level audio layer (ALSA, OSS, FFADO, CoreAudio, PortAudio, etc if any). So let's take ALSA, which is the layer that includes your soundcard's driver. If your card was not supported by ALSA (or any other low level audio layer that talks to the kernel and is supported by jack), jack would be useless. RME's HDSP is very well supported by ALSA. ALSA has a layer that abstracts the communication between the sound driver and audio applications. Jack has an ALSA backend that benefits from this abstraction, which results in that every ALSA supported h/w can be used by jack since this abstraction makes jack totally indifferent to the very h/w you have :)



> **TomR55 said:**
> 
3) On Windows I've always used two disks: one holding libraries, etc., the other instrument patches ---the reason being that Kontact and similar tools seem to require fast, unimpeded disk access. Should I invest in a second disk for this box and assume similar i/o requirements?

very very very much recommended! I have an HD for the OS and a couple of HDs for pure data. The OS processes (disk access) would slow down operations on your HD if you used it for writing/reading audio data as well. The best would be to have raid array composed of a few HDs for data. I never bothered going that road myself since I started with only one data disk (lazyness from my part, because a raid array can be expended).



> **TomR55 said:**
> 
4) I assume that WINE is another alternative? For reasons unknown, I would prefer not to add yet another layer ... but, if some of you who are more experienced tell me that WINE is the way to go ... hell, that is certainly feasible.


Wine would be an alternative for what exactly ? Wine allows you to run windows apps or plugins that do not have equivalents in linux or only poor ones. I use 2 VSTi's in my audio work : a drum sampler (Addictive Drums, very recommended!) and a linux sound generator called Pianoteq (very very realistic grand piano sounds GENERATED, not sample based). They don't have good equivalent in linux and wine makes them work so nicely that I forget that they are windows apps. Sure, Wine being an extra layer, it will introduce a tiny overhead but if you have enough power (RAM and CPU), it is peanuts. I don't even notice it (I have Core 2 Duo proc 2x2.4 GHz and 4G fast RAM). 

If you really miss windows apps, you can as well run some of these audio multitrack + MIDI sequencers you are used to through wine thanks to WineAsio which will give these apps an emulated Asio device to work with. WineAsio is quite efficient and can be used at low latency. Of course, not all apps are fully supported by Wine and you may face some weirdness here and there (GUI issues, whatever). But with my two VSTi's everything works perfectly, so it's a non issue in my workflow.

Some ppl have different experiences and it all depends on your h/w. If you want to build a dedicated linux DAW, read A LOT about linux support before buying anything ;)

Hope this helped :)

---

### Post by pcjunkie on 2008-07-13
If audio is your thing I would recommend Ubuntu studio. It has extra kernel features that enable a wine app for eg to have dedicated CPU time. This means other applications won't hog or steal the CPU from the app you need. Also Ubuntu Studio come loaded and pre-configured with ALSA and JACK, ASIO etc. no need to set up or install anything. There are other options available though I don't know how "friendly" the user interface is as compared to Ubuntu. Studio 64 is one of the best Multimedia platforms and is sponsored by the EU. From what I hear it is well crafted though the forums are not as busy as they are here. In any case Ubuntu Studio should be your first port of call. Its has a beautiful UI and is exceptionally nimble. Once you become familiar with Linux and its goings on you might want to migrate to studio 64 but I would think Ubuntu Studio is plenty happening.

---

### Post by TomR55 on 2008-07-13
First off: Thank you for your quick and knowledgable reply. I'm thinking that the RME card is the way to go. As far as re-acquiring libraries, I see several options here---not all of them too bad. Like most things that I've experienced with Ubuntu, it's been a pleasant surprise, and a learning experience, so far.

I guess that the next order of business is groveling through the support forums to figure out exactly what's real and what isn't.

I like the idea of a RAID but don't know if I have the time and cash to learn how to really do it the "right" way.

Wine is not exactly what I'd thought from some postings a while back ... I had a quick look at the site and see that Wine does suppose some of the VSTi's that I own ... now, what happens to licensing issues (half joking here ... thinking about how compulsive NI is regarding all of this stuff).

I'll have a gander at the support forums. I'll also investigate how difficult it would be to just add another high performance hard-drive.

Thanks again ... I'll re-post after doing some homework.

TomR

---

### Post by aclex on 2008-08-30
Hello.
I have to to host Win for music software, too, so I decided to write a petition to Steinberg asking them to release a Linux version of Cubase. If you agree with it, please, sign it here: [http://www.petitiononline.com/stc4linx/petition.html](http://www.petitiononline.com/stc4linx/petition.html) Well, I don't think it's quick, but I hope sometime it will be released.

---

### Post by thorgal on 2008-08-30
aclex, you have to ask yourself if the possible customer linux base would be big enough for Steinberg to invest the time and effort into this project. If Steinberg derives most of its revenues from the MS and Apple communities of professionals, these will have the highest priorities when Steinberg has to plan for the year's work activity plan (feature requests, customer support, bug fixes, etc).

So let's say that Steinberg and competitors in the audio software business sniff that more and more people are tired of using MS  or Apples products because of the licence cost, virus plagues, piracy, etc, which makes them switch to linux, a free and powerful OS that provides for most daily use (internet, communication, office work, entertainment) - there's also freeBSD by the way - . So these companies would invest in porting their products to linux. However, linux is much more dynamic and versatile than the other OSes (cf. the kernel development). The open-source community is no centralized entity, etc. How would these companies agree on something with the OS community ? which kernel version to support ? which patched kernel ? debian's ? fedora's ? suse's ? can the realtime kernel be supported ? is it safe enough ? etc, etc. That's only the technical side of things. Then comes the deal they have with prior OSes, the old customer base, etc. Which features for whom ? should all product ports be aligned feature-wise, etc, for each new release ? what if a bug crawls up in the linux port but a fix can only be scheduled 6 months after ? and what if the customer changed its kernel because of an improvement in ALSA for his audio interface, but thereby broke the say Steinberg software product's functionality ? etc, etc.

I can perfectly understand why these companies are shy when it comes to this. Softwares like Cubase or other depends too much on other parts of the OS (like the ASIO driver for the h/w in windows). For Cubase to work under linux, every audio h/w is required to work as one can reasonably expect with ALSA or FFADO, etc. Cubase would be useless otherwise. A very bad compromise would be for these companies to provide their own h/w driver ... you can see why this is a bad idea ;)

---

### Post by aclex on 2008-08-31
Thorgal, thank you for a very detailed answer.
I considered such kind of things you describe when I was preparing the text of the petition. But I think that these problems will be fixed 'by design' if a version for Linux is released. I think, stability and standards appear when the are needed. For example, programmers have stable API for much things because it's important for them and their progress depends on it. The same for proprietary video drivers. No one will change X API tomorrow without discussion with AMD, NVidia and all the open source drivers developers. In fact, they make great influence on how it will look like. So I think, when the first proaudio program will be ported to Linux (and I think it's inevitable), all the necessary standards will appear. It's good for everyone: musicians make commercial music using Linux and they are interested in stability of software and software companies are interested in increasing of number of users, so they will tend to make more stable software.
As for technical problems, I think, on Linux they are much reduced. We already have JACK, we have LADSPA, we have Qt and Gtk+ etc. which are all in userspace, so there's no need to afraid of kernel development. And all these existing ones make the development even easier because no workarounds like ASIO etc. are needed.
Of course, some tweaks to the development model could be necessary, but I don't think it's a big problem.
Also, they could sell Linux version without support, for example, or at increased price. I think, there's no problem to pay more for a better environment, a lot of producers pay for Mac much more and there's no problem.

To be honest, I didn't expect that there would be so few signs, maybe it's too early for this petition. But I'm sure that Linux version is a question of time, especially taking into account Ubuntu progress.

---

### Post by TomR55 on 2008-08-31
> **thorgal said:**
> aclex, you have to ask yourself if the possible customer linux base would be big enough for Steinberg to invest the time and effort into this project. If Steinberg derives most of its revenues from the MS and Apple communities of professionals, these will have the highest priorities when Steinberg has to plan for the year's work activity plan (feature requests, customer support, bug fixes, etc).

This is an excellent point! You know, I wear two hats. One, is a professional computer scientist who now (in retirement) teaches. The other is a long-term, working composer/producer--also still working. Now, I bring this up to underscore a point that the author, I believe, is making: the two don't meet. I really have neither the time nor the patience to navigate the subtleties of any operating system at 2 o'clock in the morning. I want to finish the master or whatever it is I'm doing and get some sleep. In some ways, the old 2-inch tape had it's problems, but my workflow was dependable.

So let's say that Steinberg and competitors in the audio software business sniff that more and more people are tired of using MS  or Apples products because of the licence cost, virus plagues, piracy, etc, which makes them switch to linux, a free and powerful OS that provides for most daily use (internet, communication, office work, entertainment) - there's also freeBSD by the way - . So these companies would invest in porting their products to linux. However, linux is much more dynamic and versatile than the other OSes (cf. the kernel development). The open-source community is no centralized entity, etc. How would these companies agree on something with the OS community ? which kernel version to support ? which patched kernel ? debian's ? fedora's ? suse's ? can the realtime kernel be supported ? is it safe enough ? etc, etc. That's only the technical side of things. Then comes the deal they have with prior OSes, the old customer base, etc. Which features for whom ? should all product ports be aligned feature-wise, etc, for each new release ? what if a bug crawls up in the linux port but a fix can only be scheduled 6 months after ? and what if the customer changed its kernel because of an improvement in ALSA for his audio interface, but thereby broke the say Steinberg software product's functionality ? etc, etc.

Yeah ... true enough, but I can also understand the "dream" ---getting away from the profit-driven, albeit talented engineers, that have made Cubase, ProTools, etc. possible. When I think of the Linux platform, which I use for everything else, I think of the "ideal." When I work on the Windoze box, I think of the tyranny of the practical. I'm thinking that I'd use any working studio on the Linux side to make truly experimental music ---think algorithmic composition here.

I can perfectly understand why these companies are shy when it comes to this. Softwares like Cubase or other depends too much on other parts of the OS (like the ASIO driver for the h/w in windows). For Cubase to work under linux, every audio h/w is required to work as one can reasonably expect with ALSA or FFADO, etc. Cubase would be useless otherwise. A very bad compromise would be for these companies to provide their own h/w driver ... you can see why this is a bad idea ;)

Again ... the tyranny of the practical; these softwares work because they do attend to the niggling (and often proprietary, and there's the rub) details.

Thanks for your insights ... food for thought.

TomR

---

