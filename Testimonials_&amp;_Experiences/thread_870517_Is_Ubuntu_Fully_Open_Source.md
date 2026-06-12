---
title: "Is Ubuntu Fully Open Source?"
date: 2008-07-25
forum: Testimonials &amp; Experiences
---

### Post by soumen08 on 2008-07-25
Hi ive been using ubuntu for a while now and i love it. In my college however most people who use linux use fedora. We are having trouble deciding which OS to give out in the upcoming LUG meet. While Ubuntu is definitely more fun and ease of use, criticism has been directed towards it that

1) They patch the kernel to an extent that if we custom compile a kernel and install it everything comes crashing down and that they dont make open the patches they do to the kernels
2)That Launchpad is not open source
And some others. while i have found out that launchpad isnt open source but is going to be in the next 12 months, i would like info on the kernels matter as in how different is the ubuntu kernel from the linux kernel and how open are the changes (if any)
Hope you take my questions in the correct spirit,
Soumen

---

### Post by steveneddy on 2008-07-25
Ubuntu is a good distro to give out, but if you want customer compiled kernels and total customization, then you may want to try Gentoo.

---

### Post by Keyper7 on 2008-07-26
It's definitely **not true** that if you compile a custom kernel and install it everything comes crashing down.

Last year, when I still had my crappy HP laptop, I needed the 2.6.22 kernel to hibernate properly and use a decent framebuffer console, so I replaced the 2.6.20 default Feisty kernel with a vanilla 2.6.22 kernel directly downloaded from kernel.org and everything worked flawlessly.

Furthemore, doesn't a simple apt-get source linux give you access to the full source of the patched kernel and the patches themselves?

I'm not sure what you're talking about but sounds like a "someone heard that someone heard that..." FUD.

Did you do some basic initial research, like downloading the Ubuntu kernel sources from launchpad?

I agree about Launchpad, though... It's taking forever for Canonical to open it. I'm confident they will, but it already feels like a long wait.

> **steveneddy said:**
> Ubuntu is a good distro to give out, but if you want customer compiled kernels and total customization, then you may want to try Gentoo.

Um, that has nothing to do with his questions...

---

### Post by mbsullivan on 2008-07-26
> Furthemore, doesn't a simple apt-get source linux give you access to the full source of the patched kernel and the patches themselves?

Yes, this is true. To get Linux source with Ubuntu patches:

```
sudo aptitude install linux-source
cd /src/
tar -xjf [source .tar.bz file]
```

> if you want customer compiled kernels and total customization, then you may want to try Gentoo. 

That's what I thought originally, too. Portage is definitely nice if you like to hack source code.

However, I agree that Ubuntu should be fine for your purposes (as Fedora would be). There is no clear winner... Fedora will tend to have slightly more experimental packages and Ubuntu's apt system IMHO is nicer than yum.

Mike

---

### Post by hyper_ch on 2008-07-26
Launchpad and Ubuntu are two different things. So what does it matter?

And as already said, the ubuntu source can be easily obtained by apt-get source.

---

### Post by soumen08 on 2008-07-26
hi thanks for your answers. i think i confused a lot of important things,meanwhile i'll try to compile a kernel and try it out.

Soumen

---

### Post by Keyper7 on 2008-07-26
> **hyper_ch said:**
> Launchpad and Ubuntu are two different things. So what does it matter?

Matters a lot, because Launchpad is also developed by Canonical and Ubuntu is entirely developed inside it instead of an well-known open-source bug tracking system like bugzilla.

A huge part of Ubuntu's marketing consists in promoting free software and stating how great freedom is, so it's very hard for the closeness of Launchpad not to come off as hypocritical. This understandably raises concerns about how commited to freedom Canonical really is and if the lack of freedom on Launchpad's side could someday be extended to Ubuntu.

I'm not saying I have those concerns, but can I understand those who do.

---

### Post by hyper_ch on 2008-07-26
does canonical offer launchpad for general usage (download) or is it rather to be considered as internal tracking program for the development?

In the end Ubuntu is totally open source ;)

---

### Post by Joeb454 on 2008-07-26
> **soumen08 said:**
> Hi ive been using ubuntu for a while now and i love it. In my college however most people who use linux use fedora. We are having trouble deciding which OS to give out in the upcoming LUG meet.

Why not just give both out?

---

### Post by Keyper7 on 2008-07-26
> **hyper_ch said:**
> In the end Ubuntu is totally open source ;)

Eh, no.

Ubuntu installs closed-source firmware by default and has optional closed-source drivers in the official repositories.

Debian does not install closed-source firmware by default, but has them in the official repositories.

So far, the only totally open-source distros I know are the [free distros recognized by the Free Software Foundation.](http://www.gnu.org/links/links.html)

(Disclaimer: I'm aware that free and open-source are not the same thing, but in the examples above I'm pratically only talking about binary blobs, which are both non-free and closed-source at the same time.)

---

### Post by hyper_ch on 2008-07-27
what closed firmware is installed by default?

(I don't think ubuntu installs any firmware at all ;))

---

### Post by Keyper7 on 2008-07-27
From [http://www.ubuntu.com/community/ubuntustory/components:](http://www.ubuntu.com/community/ubuntustory/components:)

> The licences for software applications in main must be free, **but main may also may contain binary firmware**

If you check the contents of the package [linux-ubuntu-modules-2.6.24-16-386](http://packages.ubuntu.com/hardy/i386/linux-ubuntu-modules-2.6.24-16-386/), which is **installed by default**, you will find for example the firmware for intel wireless chipsets:

```
/lib/firmware/2.6.24-16-386/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-16-386/iwlwifi-3945.ucode
/lib/firmware/2.6.24-16-386/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-16-386/iwlwifi-4965.ucode
```

Take a look at [contents of the package](http://packages.ubuntu.com/hardy/i386/linux-ubuntu-modules-2.6.24-16-386/filelist) and the [contents of the firmware-iwlwifi package in Debian](http://packages.debian.org/lenny/firmware-iwlwifi). Debian does not ship this firmware by default and puts it on the non-free repository. Take a look at your own installation: they are probably there.

The [Intel wireless page itself](http://intellinuxwireless.org/?n=FAQ&s=license) admits that the binaries are free as in beer but not free as in freedom:

> You can redistribute the binaries without cost (free as in beer). **There are restrictions against modification or redistribution of modified binaries**, but you can definitely redistribute the originals.

If you're not convinced yet, then hear [Mark Shuttleworth himself](http://www.markshuttleworth.com/archives/84):

> **Ubuntu has included firmware, and used proprietary drivers since its inception**. That’s always been a slightly uncomfortable proposition, as Mako observed, but **it’s been true since the Warty Warthog**. Even Debian goes some way along that road with its inclusion of **firmware and other non-free bits**

---

### Post by karellen on 2008-07-27
just a little off topic, does it matters if it's not (100+1)% open source? what do you want? an OS that works or an OS that's ideally free and crippled?

---

### Post by Keyper7 on 2008-07-27
> **karellen said:**
> just a little off topic, does it matters if it's not (100+1)% open source? what do you want? an OS that works or an OS that's ideally free and crippled?

And who said that working and being free are mutually exclusive features? What if the person has an Intel video card and an [Atheros wireless card](http://mobile.slashdot.org/mobile/08/07/26/2138228.shtml)?

Really, this kind of overly general "open-source things are crippled" statements is exactly what gives Linux a bad image.

---

### Post by Bachstelze on 2008-07-27
> **soumen08 said:**
> 1) They patch the kernel to an extent that if we custom compile a kernel and install it everything comes crashing down and that they dont make open the patches they do to the kernels

1) Running a custom kernel aways Worked For Me&#8482; in Ubuntu, just like in any other distro.

2) The kernel patches are available on the mirrors, and directly accessible from [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

You really shouldn't believe what people tell you, especially when someone using a distro tells you bad things about another. It might have been good-faith ignorance or plain lies, but the person who told you that was definitely wrong.

---

### Post by Bachstelze on 2008-07-27
> **Keyper7 said:**
> Really, this kind of overly general "open-source things are crippled" statements is exactly what gives Linux a bad image.

You, sir, are really funny trying to play the Great Knight of Freedom when you speak of "open-source" instead of "Free Software". Let's hope the Great God Richard M. Stallman doesn't read this forums, or you shall be hanged for you betrayal ;)

---

### Post by Keyper7 on 2008-07-27
> **HymnToLife said:**
> You, sir, are really funny trying to play the Great Knight of Freedom when you speak of "open-source" instead of "Free Software". Let's hope the Great God Richard M. Stallman doesn't read this forums, or you shall be hanged for you betrayal ;)

Hey, hey, HEY! I put a disclaimer for that on one of my previous posts:

> (Disclaimer: I'm aware that free and open-source are not the same thing, but in the examples above I'm pratically only talking about binary blobs, which are both non-free and closed-source at the same time.)

Now seriously, I wanted only to use the word "free", but then I noticed the OP used "open-source", karellen did too and then I got all confused trying to come across all that. :)

And I'm not trying to be the knight of anything, I'm a "working before free" supporter myself (I use nvidia binary blobs and intel wireless firmware). I just don't like seeing statements like "F/OSS = crippled".

And for the record, I don't like [harassment for freedom](http://mobile.slashdot.org/mobile/08/07/26/1827208.shtml) either and I disagree with a great deal of what RMS says. If he tries to hang me I'll just kick his ***.

---

### Post by karellen on 2008-07-27
> **Keyper7 said:**
> And who said that working and being free are mutually exclusive features? What if the person has an Intel video card and an [Atheros wireless card](http://mobile.slashdot.org/mobile/08/07/26/2138228.shtml)?

Really, this kind of overly general "open-source things are crippled" statements is exactly what gives Linux a bad image.

I didn't say that open source software is crippled by default. you are aware of the fact that your hardware, in order to work properly, must use closed source drivers (video card especially) most of the time

---

### Post by Mr. Picklesworth on 2008-07-27
I think it's entirely fair that Canonical is taking their time opening up Launchpad. It is an incredible piece of techology, and maybe Canonical's chance of getting established as a solid contender in this space (eg: Sustainable business model). Besides that, Launchpad isn't really *done* yet. While the release early release often philosophy can definitely be applied, I think it would be best if Launchpad could work as a distributed system of web sites before it gets an open source release. After all, the power here is that Launchpad can seamlessly connect the free software ecosystem. That won't work if we have 50 Launchpads.

---

### Post by Keyper7 on 2008-07-27
> **karellen said:**
> I didn't say that open source software is crippled by default. you are aware of the fact that your hardware, in order to work properly, must use closed source drivers (video card especially) most of the time

See, that's exactly the kind of "overly general statements" I'm talking about. What is "working properly"? If the guy has an Intel card, he has fully-functional 3D capabilities with a open-source driver. If the guy has a very low-end nvidia card and is not interested in 3D rendering, he just needs the nv driver. If the guy has a high-end card but only uses it for games for which he needs to boot Windows anyway, nv is fine for linux.

What is "working properly"? Answer: depends on your needs. So why ask

> what do you want? an OS that works **or** an OS that's ideally free and crippled?

when the option "ideally free and that works" might be available?

But yeah, I'm just being overly picky and annoying here. I think I'll shut up now, I wrote too much already.

---

### Post by karellen on 2008-07-27
> **Keyper7 said:**
> See, that's exactly the kind of "overly general statements" I'm talking about. What is "working properly"? If the guy has an Intel card, he has fully-functional 3D capabilities with a open-source driver. If the guy has a very low-end nvidia card and is not interested in 3D rendering, he just needs the nv driver. If the guy has a high-end card but only uses it for games for which he needs to boot Windows anyway, nv is fine for linux.

What is "working properly"? Answer: depends on your needs. So why ask



when the option "ideally free and that works" is available?

I agree with the last part, I reduced everything to only 2 situations, for emphasize :). obviously, if the open source driver does it job and the performance is approximately the same, one should stick to it

---

### Post by ukripper on 2008-07-27
I've compiled custom kernel on gutsy 2 months ago and i see no problem working with my dell vostro and gutsy to date.

---

