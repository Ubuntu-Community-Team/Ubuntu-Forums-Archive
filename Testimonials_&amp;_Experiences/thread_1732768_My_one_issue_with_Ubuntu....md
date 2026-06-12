---
title: "My one issue with Ubuntu..."
date: 2011-04-18
forum: Testimonials &amp; Experiences
---

### Post by Mazate on 2011-04-18
I'm brand new to Ubuntu.  I've had it installed for several days and I really like it.  However, there is one issue that is, unfortunately, going to force me to  the gnewsense build of linux.  That is the issue of proprietary drivers & codecs, etc.  If I use Ubuntu, then I'm forced to have things installed that aren't 100% free or licensed.  I realize that probably no one cares, in the end, but for me its an ethical issue.  On a brand new install of Ubuntu, there are bad and ugly codecs installed for gstreamer by default.  I'm sure there are others.  Is there a way to get Ubuntu without infringing on some of this non-free software?  I'd hate to have to give up Ubuntu.

---

### Post by rg4w on 2011-04-18
Community software is written by the community.  Get GCC and get started. ;)

For myself, given the choice between using a proprietary driver or writing my own, I'm spending my time elsewhere and just using NVdia, grateful for their Linux support.

---

### Post by Mazate on 2011-04-18
> **rg4w said:**
> community software is written by the community.  Get gcc and get started. ;)

for myself, given the choice between using a proprietary driver or writing my own, i'm spending my time elsewhere and just using nvdia, grateful for their linux support.


xx

---

### Post by wolfen69 on 2011-04-18
Debian doesn't come with anything non-free, try that. Ubuntu is based on Debian btw.

Why do you assume ubuntu comes with non-free codecs? I have to install them manually every install I've done. (which is many)

---

### Post by 3Miro on 2011-04-18
There is an option in the installer about third party and non-free stuff. If you don't select that, then nothing non-free should be installed by default.

---

### Post by ikt on 2011-04-18
> **Mazate said:**
> Is there a way to get Ubuntu without infringing on some of this non-free software?

Nope.

The free software option will remove the non-free components of ubuntu from the install, but the kernel still has non-free blobs in it.

[https://lists.ubuntu.com/archives/gobuntu-devel/2008-April/000653.html](https://lists.ubuntu.com/archives/gobuntu-devel/2008-April/000653.html)

It's why gNewSense exists in the first place.

> If I use Ubuntu, then I'm forced to have things installed that aren't 100% free or licensed. I realize that probably no one cares, in the end, but for me its an ethical issue. 

Can I ask why it's such a huge ethical issue for you?

---

### Post by marl30 on 2011-04-18
Op, you would fit in fairly well with Richard Stallman. Maybe you would love the distro he uses that use only free stuff. ***[B][I]***[/I][/B]

---

### Post by Graham-W on 2011-04-18
Like a lot of people mentioned even if you do remove the "non-free" stuff it'll mess up other things. Just don't even try to mess with it.

---

### Post by Simian Man on 2011-04-18
> **Mazate said:**
> I realize that probably no one cares...

I sure as hell don't.

---

### Post by Timmer1240 on 2011-04-18
having non free parts in there has no effect on me if it works then Im for em!

---

### Post by mastablasta on 2011-04-19
try FreeBSD
 
Linux core is not totally free anyway. It uses some patents i believe.

---

### Post by 3rdalbum on 2011-04-19
Canonical is aware of this, but there's not really a very good way around it. Ubuntu includes the minimum non-free stuff it needs to actually work on people's computers. gNewSense includes no non-free stuff, but few people would use it because it simply won't run very much essential hardware like wifi cards.

The best thing to do is to write free replacements for non-free blobs, but there aren't enough people doing this, and it's not a priority for Ubuntu as far as I can tell; I can understand their viewpoint too.

---

### Post by Arthur_D on 2011-04-19
Why are most people in this thread trying to belittle his view that he doesn't want anything unfree on his computer?

To the OP: I use Debian, which by version 6 doesn't include non-free drivers in its kernel by default. I had to install one for my wireless and one for proper 3D support, but then I do not share the view that everything must be Free. If the alternatives were avaliable and just as good, I'd certainly use the Free ones instead.

---

### Post by rg4w on 2011-04-19
> **Arthur_D said:**
> Why are most people in this thread trying to belittle his view that he doesn't want anything unfree on his computer?

To the OP: I use Debian, which by version 6 doesn't include non-free drivers in its kernel by default. I had to install one for my wireless and one for proper 3D support, but then I do not share the view that everything must be Free. If the alternatives were avaliable and just as good, I'd certainly use the Free ones instead.
I can't speak for others, but when I suggested that he consider writing the driver himself I was only half-joking.

It's a lot of work to write drivers, esp. if you don't work for the company that makes the hardware, so it's a lot to ask of the community that all drivers be entirely free.

We as a community must either limit our hardware selection, be willing to invest the time and/or capital to create free drivers, or accept the occasional non-free component from the hardware vendor, as NVidia offers.

Until code grows on trees, I don't see a fourth option available.

---

### Post by wolfen69 on 2011-04-19
> **Arthur_D said:**
> Why are most people in this thread trying to belittle his view that he doesn't want anything unfree on his computer?


I just re-read the whole thread and didn't see anyone trying to belittle his point of view. 

But anyway, good luck (they're going to need it) to anyone that is going to try and go 100% "free".  Being the media junkie I am, there is no way I could go without non-free software. I'm not *pro* or *for* anything, I just use what works for me to do what I have to do. Without non-free stuff, I couldn't use my wireless, couldn't watch DVD's or TV, couldn't play mp3's, couldn't play 3D games and so on. I like to have fun on my computer, and that would be too much for me to give up. But I respect someone's decision *not* to use them. Once again, good luck with that.

---

### Post by kaldor on 2011-04-20
gNewsense is a lost cause project, in my opinion. They've been at a standstill for too long. The version of Ubuntu they're based on is Hardy, which is going to be unsupported as of June.

Use Debian 6. It's as free as you can get.

---

### Post by pony-tail on 2011-04-22
Whilst I agree in principal with the OP . And in an ideal world would do the same . I live in this world of greedy companies and patent trolls and industrial espionage that makes companies nervous of releasing hardware specs to the Linux community . So I put up with the non-free components just so that my system works .
My thanks to AMD for their release of Video card data to the OSS community but I wish more companies ( Yes you Nvidia and various wireless companies too ) would release their specs too . It does not happen because they fear that another company will steal their IP .
Then there are the multi media codices they are all proprietary and yet have become sudo-standards . Unfortunately that is the state of the real world .
That said , Debian can be setup to a functioning system  with all free software , If that is how you wanted to go .
More power to you for following that which you believe in .
Good luck OP

---

### Post by armandh on 2011-04-22
I suspect that a lot of hardware mfg don't wish to expose their driver code for its lack of provenance.

with any chip 
its instruction will by necessity be similar and in some spots exactly like some one else's instructions.

an opportunity to respond to complaints

---

### Post by jdrodrig on 2011-04-22
I think the issue the OP is getting is whether ubuntu using non-free stuff is violating anybody's licenses; I am no expert, but I will be surprised Canonical would set itself up for future lawsuits.

OP, did I get it? or even if it is perfectly legal to use it, you would still object to it because some higher standard you impose on providers (eg. Fair Trade coffee)?

---

### Post by julianb on 2011-04-22
> Then there are the multi media codices they are all proprietary and yet have become sudo-standards.

I'm glad there are people hard at work on things like webM and webP and html5 so that we can watch movies using free codecs.

---

### Post by wolfen69 on 2011-04-22
> **julianb said:**
> I'm glad there are people hard at work on things like webM and webP and html5 so that we can watch movies using free codecs.

Yeah, I can't wait until flash dies.

---

### Post by Derxst on 2011-04-22
I am interested to know what the ethical problem is, though. I have no problems installing a WiFi driver or a codec that is proprietary if it works. Proprietary does not mean it costs money; it just means they aren't willing to share the source. If it is obtained and used legally, no problem ethically.

---

### Post by jdrodrig on 2011-04-23
> **Derxst said:**
> I am interested to know what the ethical problem is, though. I have no problems installing a WiFi driver or a codec that is proprietary if it works. Proprietary does not mean it costs money; it just means they aren't willing to share the source. If it is obtained and used legally, no problem ethically.

I think the OP is talking something analog to Fair Trade Coffee or Cosmetics not tested on animals type of ethical issues.

---

### Post by Tamlynmac on 2011-04-23
> Derxst
I am interested to know what the ethical problem is, though.

I seriously doubt you will find out, as the OP hasn't responded for five days. ;)

---

### Post by wolfen69 on 2011-04-24
> **Tamlynmac said:**
> I seriously doubt you will find out, as the OP hasn't responded for five days. ;)

True, yet this thread lives on........ 

Aren't they supposed to have closed it by now? <solved>

---

### Post by MarcusW on 2011-04-24
+1 on trying Debian. It doesn't include any non-free parts (as long as you don't manually add non-free and contrib that is), not even blobs in the kernel. :)

---

