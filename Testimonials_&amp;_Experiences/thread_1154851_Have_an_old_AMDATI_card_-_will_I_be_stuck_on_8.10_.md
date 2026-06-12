---
title: "Have an old AMD/ATI card - will I be stuck on 8.10 forever?"
date: 2009-05-10
forum: Testimonials &amp; Experiences
---

### Post by timClicks on 2009-05-10
Hi all,

I have a year and a half old laptop that looks like it will stay running 8.10 for a while yet. What are people's thoughts that the open source world will be able to provide quality drivers for these "legacy" systems?

Also, should I upgrade to 9.04 anyway? Will it kill my system?

---

### Post by 3rdalbum on 2009-05-10
I think you misunderstand. ATI isn't going to be producing its proprietary 3D driver ("fglrx") for the "legacy" chipsets, but the open-source driver ("ati") will continue to support your chipset with 2D acceleration, and possibly 3D at some later date.

If all else fails, the unaccelerated "vesa" driver will continue to work.

So, if you upgrade to 9.04, your computer will still work, but the graphical display may feel a little sluggish compared to what you're used to. You might not be able to play 3D games on it anymore, or run Compiz. But you can still use Ubuntu.

On the up-side, you will probably suffer fewer freezes and fewer Xorg crashes with the open-source driver :-)

---

### Post by WSmart on 2009-05-10
I give Nvidia a ton of credit for their Linux driver support.  I have an older Nvidia GeForce2 32MB card and it works with the latest Linux just as it has since it was new.   Nvidia clearly get up early and come to work feeling fresh.  Good job Nvidia.

I installed 9.04 on a system with an AMD 9600 128MB card, and the desktop had the first stage of desktop affects enabled automatically.  AMD has released 3D documents to the community, and we'll likely see 3D support with those drivers going forward, and it will likely work well.

If you want 3D support and that laptop has the disk space or can take another hard drive, you might consider installing 8.10 and just booting that when you want 3D.  You could also install 9.04 fresh, before that, just to see what you think. 

Thanks for the post.  I've been wondering how to handle this too.

---

### Post by WSmart on 2009-05-10
Also, if your laptop has an R600 or newer GPU, that still has support.  You say 'older', but 18 months doesn't sound like R500.

Thanks.

---

### Post by Tamlynmac on 2009-05-10
> timClicks
I have a year and a half old laptop that looks like it will stay running 8.10 for a while

What is the issue with running 8.1? Some users are still running Hardy, why the hurry to upgrade? If you have a fully functional system that meets your expectations why the need to upgrade? If by upgrading you risk instability or incompatibility with legacy drivers then upgrading is illogical and unnecessary. Perhaps wait for the next LTS release and make an assessment at that time.

I've never understood the incessant need to upgrade. I still know some people who run older versions of Windows because of unsupported legacy drivers. Logic suggests that you use what works and not be compulsive regarding upgrading. Nowhere did you sign anything that mandates upgrading to the newest release of Ubuntu.

I'm hoping this isn't a let's bash Ubuntu thread, but rather one that is honestly questioning the logic of upgrading. If this turns into a lets bash Ubuntu thread - I will gladly pass on my "sympathies" and move on. For I will not provide a platform (by bumping) to those that feel the need to rant about that which no one in this forum can resolve. For those that wish to rant regarding new releases need to relize that the Devs don't live here.

---

### Post by 3rdalbum on 2009-05-11
> **Tamlynmac said:**
> What is the issue with running 8.1? Some users are still running Hardy, why the hurry to upgrade?

True, my home server will be running Intrepid until its EOL in 12 months time.

---

### Post by ukripper on 2009-05-11
> **3rdalbum said:**
> True, my home server will be running Intrepid until its EOL in 12 months time.

+1 and mine with 8.04 server till EOL another 4 years :-)

---

### Post by Niniel on 2009-05-11
If you want to get a useful reply to your question, you will need to tell what graphics chip you have. Unfortunately, just to call it "older" isn't very helpful.
E.g. I have 2 computers running 9.04. One has an ATI Radeon 9600 Mobility card, and it works very well with the open source driver. I didn't have to do any adjustments and I get smooth desktop effects.
My other box has an ATI X800 XT card, and it also works with the open source driver, although I had to edit xorg.conf a bit for desktop effects (which I have since disabled for performance reasons - which is kind of crazy since this is a newer, more powerful card, compared to the 9600).
Since your computer is relatively new at 18 months you probably have a newer card than I. But in your case new(er) might not be better for it seems that the open source driver works best with older chips, whereas the proprietary ATI driver works only with their latest offerings. The cards in-between appear to be having some problems, although most people seem to be concerned with 3D acceleration and compiz desktop effects, so if you can do without those you should be fine.

---

### Post by mdsmedia on 2009-05-11
To be fair to the OP, he did ask a question and didn't criticise anything.

I'm one who used 6.06 until a fair while after 8.04 was released, but am now using 9.04 on a Laptop (with Intel hardware) and a desktop with an nVidia card....oops, now have Debian on the desktop, but Jaunty was fine on it, and it IS a play/test machine.

But, unless you need the latest versions of software, no need to upgrade to Jaunty. In fact, few of the latest versions aren't already being used in Intrepid or Hardy. I upgraded to Jaunty simply because I wanted to freshly install my system and Jaunty had been released, and I'd run it on my desktop since Alpha, was happy with it, and decided to install it on my laptop. Give it a try. If it's not satisfactory, you can always reinstall Intrepid.

---

### Post by caravel on 2009-05-11
> **timClicks said:**
> Hi all,

I have a year and a half old laptop that looks like it will stay running 8.10 for a while yet. What are people's thoughts that the open source world will be able to provide quality drivers for these "legacy" systems?

Also, should I upgrade to 9.04 anyway? Will it kill my system?
You can probably upgrade, but completely uninstall fglrx first.  After upgrading you'll have no restricted drivers available but you can use the foss ATI/Radeon driver as the others have said.

---

