---
title: "Proprietary Software - Philosophy"
date: 2008-08-14
forum: The Cafe
---

### Post by MaindotC on 2008-08-14
There are some things Windoze can do that Linux-based o/s's cannot (such as Netflix or Silverlight broadcasts like nbcolympics.com) but I'm curious as to why the companies don't just release proprietary software that will run in Linux o/s's but won't have publicly available source code?

For example, the ATI driver is proprietary.  What is the philosophy behind keeping FREE proprietary software off of Linux o/s's?  Thanks!

---

### Post by decoherence on 2008-08-14
From the linux developer's perspective, proprietary, closed software is a pain in the rear because you can't debug it yourself or take it apart to see how it works. Thus, if there's a bug in ATI's driver that causes hard system lockups, it could only be through observation that you could identify the ATI driver as buggy, and then you wouldn't really be able to do anything about it.

From a commercial company's perspective, Linux is difficult to provide support for. You'll find there are some very high end tools that run on linux (particularly in the pro 3D market) but you often have to use the distribution and version that the company dictates.

This is issue is somewhat real and somewhat fabricated. The main thing they're worried about is that someone will try to run Softimage on Ubuntu, for example, and expect it to work just like a supported version. A company would need an amazing linux savvy tech support department in order to provide the same level of support for "linux" (all distros) that they do for windows or mac or a specific linux distro/version.

This is less of an issue in the open source world since the tech support department spans the globe, it's easy to figure out why something doesn't work and then disseminate that information to people without regard to whether they're competitors or partners or what.

---

### Post by ilrudie on 2008-08-14
You can totally watch Netflix on Linux.  Look into the Roku Netflix set top box.  Runs Linux.  Now when that will make it to main stream Linux Distros is another story. :)

[http://www.linux.com/feature/142729](http://www.linux.com/feature/142729)

---

### Post by MaindotC on 2008-08-14
I've see the roku thing and I don't really consider that a solution.  It's a separate box that streams to any o/s and directly to the TV, so it's more of a Netflix solution to anyone, not a Netflix solution for Linux users.

---

### Post by ilrudie on 2008-08-15
> **strAlan said:**
> I've see the roku thing and I don't really consider that a solution.  It's a separate box that streams to any o/s and directly to the TV, so it's more of a Netflix solution to anyone, not a Netflix solution for Linux users.

I'm aware.  It runs Linux though so you definitely can watch netflix on Linux.  Getting it into a distro like Ubuntu is the next step.

---

### Post by t0p on 2008-08-15
> **strAlan said:**
> 
For example, the ATI driver is proprietary.  What is the philosophy behind keeping FREE proprietary software off of Linux o/s's?  Thanks!

You're getting confused about the term "free".  The ATI driver is free as in free beer, but *not* free as in free speech.  In other words: the ATI driver doesn't cost anything, but it is not unencumbered - it comes with various conditions that prevent it being Free software.

Some other languages are better at conveying this - ie French has the terms *gratis* and *libre* for the 2 defferent senses of "free".  But if you speak English, you have to think about it a bit more.

---

### Post by MaindotC on 2008-08-15
It still seems confusing.  Perhaps I'm not educated enough in coding to see the complexities, but I would think if they have the source for a restricted feature, they could make packages that would install on other distributions.  I can see developers wanting to keep it off of systems and repositories, but I can't imagine that when the Windoze developers (for a company like ATI or Netflix or Epson) release a driver that they can't release a Linux package as well.  It could be there if you want it, and if you don't want it you don't have to use it.

I'm not mistaking the definition of free.  I understand it would be free to download just not free to modify and manipulate to serve your needs.  I still think they could offer a WMP for Linux that would incorporate DRM and is free for download, but not free to modify.

---

### Post by t0p on 2008-08-15
Some people might consider this to be a silver foil hat view of things: but I believe the reason some stuff like Silverlight have not been ported to Linux is because Microsoft don't want it on Linux.

If Silverlight becomes popular and supplants Flash, you can be sure someone will release a Linux plugin, in the same way you can get Flash plugins for Linux.  Maybe someone will produce a Free Silverlight plugin for Linux (just like Gnash was developed as a Free plugin for Flash).  But if Microsoft can stop this from happening, you can be sure they will.  **Microsoft hates Linux!**

---

### Post by paukku92 on 2008-08-15
> **t0p said:**
> You're getting confused about the term "free".  The ATI driver is free as in free beer, but *not* free as in free speech.  In other words: the ATI driver doesn't cost anything, but it is not unencumbered - it comes with various conditions that prevent it being Free software.

Some other languages are better at conveying this - ie French has the terms *gratis* and *libre* for the 2 defferent senses of "free".  But if you speak English, you have to think about it a bit more.

This is the reason why some people started using the term "Open source", it doesn't cause as much confusion as "Free software", but this is mainly a problem of the English language as you mentioned.

Of course the FSF guys keep the term "Free software" alive for philosophical reasons, but the word free especially in software has negative perceptions attached to it.

---

### Post by the_darkside_986 on 2008-08-15
GNU/Linux will have Moonlight, a free open-source Silverlight implementation that uses Mono. And non-free codecs from Microsoft will be provided, even though I personally would rather use GStreamer or something truly free. But it's not ready yet and no one has made a deb package out of it.

---

### Post by MaindotC on 2008-08-15
Yeah I've been following the thread about how the NBC Olympics won't play and a couple people have tried installing Moonlight but apparently it's not working yet :(  However, k_i_k did create a sweet python script to watch the video in VLC.

Thanks for all your replies.

---

### Post by Sporkman on 2008-08-15
> **strAlan said:**
> 
For example, the ATI driver is proprietary.  What is the philosophy behind keeping FREE proprietary software off of Linux o/s's?  Thanks!

Hardly anybody uses linux, and fewer computers are shipped with it. Furthermore, linux users don't pay for software, nor do they click on ads (in fact, many of them block ads).

Why should they bother?

---

### Post by MaindotC on 2008-08-15
Interesting viewpoint - advertisers like NBC "punish" users won't don't conform.

---

### Post by Sporkman on 2008-08-15
> **strAlan said:**
> Interesting viewpoint - advertisers like NBC "punish" users won't don't conform.

Non-paying customers tend to be a low priority for for-profit businesses. :)

---

### Post by MaindotC on 2008-08-15
Well they certainly are low priority but as I stated above I just don't see it as a huge inconvenience.  They're writing the source code to make it work Windowsz platforms, why not just take a minute and re-compile the source for other platforms?  Perhaps it's more involved than that.

---

### Post by Sporkman on 2008-08-15
> **strAlan said:**
> why not just take a minute and re-compile the source for other platforms?  Perhaps it's more involved than that.

Very likely, I believe that any app that is UI or media oriented involves a non-trivial effort to port between OSs...

---

### Post by MaindotC on 2008-08-15
sorry...wasn't thinking :(

---

### Post by MaindotC on 2008-08-15
But you know what - take Flash for example.  That has been developed for several platforms.  Adobe didn't have to do it.

---

### Post by Sporkman on 2008-08-15
> **strAlan said:**
> But you know what - take Flash for example.  That has been developed for several platforms.  Adobe didn't have to do it.

Well, here's my personal experience: at my previous job, I worked on a proprietary CAD-type engineering app, which was chiefly supported in Windows & Solaris. Porting the UI from Windows to Solaris was not straightforward, they (the UI guys, I'm not into UI work) had to use a completely different API for the UI, using a package called "openwin" or something. They were frequently having issues with this...

---

### Post by MaindotC on 2008-08-16
Were they having issues because the platform conversion, or were they having issues because of the lack of education of the staff?  Or better yet, were they purposefully having issues to scrub the project?  That's what I'd like to know.

---

### Post by Swarms on 2008-08-16
> **strAlan said:**
> Were they having issues because the platform conversion, or were they having issues because of the lack of education of the staff?  Or better yet, were they purposefully having issues to scrub the project?  That's what I'd like to know.

It doesn't matter for the first two, if its tougher than it seems, then it will be costly for the company and they have to compare the expenses to the potential earnings.

---

### Post by Sporkman on 2008-08-16
> **strAlan said:**
> Were they having issues because the platform conversion, or were they having issues because of the lack of education of the staff?  Or better yet, were they purposefully having issues to scrub the project?  That's what I'd like to know.

IIRC, the issues were related to the different API not behaving consistently with the MS API. There may have been other issues as well. I don't think there was any deliberate sabotaging as you suggest, it was to our advantage to provide the software on both platforms (the software was of the EDA variety, used to program the company's chips, which is the main product).

---

### Post by Daveski on 2008-08-16
> **Sporkman said:**
> Porting the UI from Windows to Solaris was not straightforward, they (the UI guys, I'm not into UI work) had to use a completely different API for the UI, using a package called "openwin" or something. They were frequently having issues with this...

I guess this is one of the things the WINE project will help with. I know we all think of WINE as a way to run apps compiled for Windows, but as I understand it, if you have the Windows source you can compile against the WINE libraries with almost no effort to get a working Linux 'native' app.

---

### Post by phrostbyte on 2008-08-16
> **strAlan said:**
> There are some things Windoze can do that Linux-based o/s's cannot (such as Netflix or Silverlight broadcasts like nbcolympics.com) but I'm curious as to why the companies don't just release proprietary software that will run in Linux o/s's but won't have publicly available source code?

For example, the ATI driver is proprietary.  What is the philosophy behind keeping FREE proprietary software off of Linux o/s's?  Thanks!

Some people are completely against proprietary software. Other people are against certain proprietary software, but might actually encourage others. 

Linus for example, is completely against proprietary drivers, but supports proprietary development ontop of Linux. He is against proprietary drivers (like the ATI driver) because it makes life harder for kernel developers to support these drivers without the source code. Proprietary drivers might even be illegal, since they run in kernel mode and link directly to the kernel, and the kernel is GPL. Usermode stuff that runs on top of the kernel is most certainly not illegal, however, because they link via libc, and the kernel has a special libc linking permission.

Mostly the reason is Linux's small market share and the difficulty of developing proprietary software that works universally.

---

### Post by mister_pink on 2008-08-16
Writing software that is cross platform can be extremely complicated, depending on what sort of software you're talking about. The gui, for a start, is written with a totally different toolkit (although you can get cross platform ones) and anything that needs to interact with hardware needs to be totally different. In short then, the answer is: because its more effort than its worth. For the repeated references to flash: I believe that as a browser plug in it would be less effort to port, and more importantly, adobe wanted to conquer the world with flash, by making the effort to support all platforms they ensured they could do that.

---

### Post by Giant Speck on 2008-08-16
> **mister_pink said:**
> Writing software that is cross platform can be extremely complicated, depending on what sort of software you're talking about. The gui, for a start, is written with a totally different toolkit (although you can get cross platform ones) and anything that needs to interact with hardware needs to be totally different. In short then, the answer is: because its more effort than its worth. For the repeated references to flash: I believe that as a browser plug in it would be less effort to port, and more importantly, adobe wanted to conquer the world with flash, by making the effort to support all platforms they ensured they could do that.

In addition to what you have said, it's even more difficult to try to make a program for Linux because of all the different distributions.  Each one handles the program differently, and you need to write the code to fit the distribution.

It think that's one of the main reasons we don't see too many proprietary programs for Linux.  Because they'd have to not just worry about writing their product for Windows, OS X, and Linux, but they'd have to worry about writing for Windows, OS X, Ubuntu, Fedora, openSuSE, ArchLinux, Gentoo, etc.

What could be probably more feasible would be a proprietary software company making software that could work flawlessly with Wine.

---

### Post by Daveski on 2008-08-16
> **Giant Speck said:**
> In addition to what you have said, it's even more difficult to try to make a program for Linux because of all the different distributions.  Each one handles the program differently, and you need to write the code to fit the distribution.

Is there really that much of an issue between different distros? I thought that on the whole the libraries and toolkits are distro-agnostic. The details of configuration scripts have various flavours, but again I thought there was 2 maybe 3 varieties.

---

### Post by Sporkman on 2008-08-16
> **Daveski said:**
> I guess this is one of the things the WINE project will help with. I know we all think of WINE as a way to run apps compiled for Windows, but as I understand it, if you have the Windows source you can compile against the WINE libraries with almost no effort to get a working Linux 'native' app.

True, however in this case the main "other" OS was Solaris. When I left (3 years ago) they were still in the early stages of porting to Linux & HP unix.

---

### Post by MaindotC on 2008-08-17
> **Daveski said:**
> Is there really that much of an issue between different distros?

Giant Speck, I considered this also because different distros use different kernels (by default - I know you can use whichever kernel you please), but when you download something for Linux, it's usually a already-compiled package (such as a .deb) or source code labeled "Linux Download" (or something to that effect) and you compile and install it to your desire, assuming you have the correct dependencies.

Some examples that come to mind are Sopcast, the ATI driver (a .sh that builds whichever package), and Wine (available in source if you choose not to use the repo).

---

### Post by salsafyren on 2008-08-17
Reasons for not porting to Linux:

* no platform as such exists, it is just a bunch of libraries put together

* Linux users generally prefer free software, that is both gratis and libre. Adobe has realised this and won't port Photoshop

* Various areas in Linux are bad: audio is a big mess, the libraries are constantly upgraded so you don't have a baseline to test against

* binary compatibility doesn't exist. The philosphy in the linux world: give us the source and we will package it. That philosphy is hurting linux pretty badly

Generally, proprietary software works best on proprietary platforms and I don't see Linux growing to more than max 2% usage in 2015. It has less market share than Windows 2000, which says a lot.

---

### Post by Dremora on 2008-08-17
> **strAlan said:**
> There are some things Windoze can do that Linux-based o/s's cannot (such as Netflix or Silverlight broadcasts like nbcolympics.com) but I'm curious as to why the companies don't just release proprietary software that will run in Linux o/s's but won't have publicly available source code?

For example, the ATI driver is proprietary.  What is the philosophy behind keeping FREE proprietary software off of Linux o/s's?  Thanks!

I never understood keeping display drivers, webcam drivers, and a lot of other things out of a distribution, as long as it's redistributable, it should be in the distribution.

All distros like Gnewsense serve to do is show how horribly broken and useless a Linux distribution is without all the binary drivers and stuff.

Richard Stallman even had a writeup about the OLPC, and said he can't endorse it because it has like 100 kilobytes of firmware for the wireless, and he deleted that on his OLPC.

It's people like that, which make me twitchy.

---

### Post by MaindotC on 2008-08-17
Wow, a lot of these points help me understand this a lot better.  Salsa - I like your last two points :)

Dremora - I agree with you.  If it can be done, I don't see why it shouldn't be done.

---

### Post by Dremora on 2008-08-17
> **salsafyren said:**
> Reasons for not porting to Linux:

* no platform as such exists, it is just a bunch of libraries put together

* Linux users generally prefer free software, that is both gratis and libre. Adobe has realised this and won't port Photoshop

* Various areas in Linux are bad: audio is a big mess, the libraries are constantly upgraded so you don't have a baseline to test against

* binary compatibility doesn't exist. The philosphy in the linux world: give us the source and we will package it. That philosphy is hurting linux pretty badly

Generally, proprietary software works best on proprietary platforms and I don't see Linux growing to more than max 2% usage in 2015. It has less market share than Windows 2000, which says a lot.

Thats not really accurate, proprietary and binary only software generally works just fine between different distributions, like everything id Software makes? The Flash plugin?

Some people, I call them Stallmanites, insist so harshly on using "free" software, that they scare all the fish away and make sure no company making professional products takes Linux seriously.

---

### Post by saulgoode on 2008-08-17
> **Dremora said:**
> Some people, I call them Stallmanites, insist so harshly on using "free" software, that they scare all the fish away and make sure no company making professional products takes Linux seriously.

And the situation is excellent.

---

