---
title: "virtualization for photoshop issues"
date: 2012-10-30
forum: Virtualisation
---

### Post by acfreema on 2012-10-30
Long-story short, I use Gentoo or Debian-based Linux for my non-gaming needs and I've convinced my lady-friend that Mac is overpriced for the hardware, which has lead to the situation I have now: In order for her to leave Mac, I need to find a way to run Photoshop and a couple of other Adobe products, but there are security concerns with Windows, and Adobe hates Linux.

Essentially, what I need to find is a way to get true virtualization support for Windows 7 64bit in a Linux environment (mainly because CS6 supports using the GPU for assistance). Since this is my first foray into hardware-supported virtualization, I thought it would make sense to ask around. 

After some reading, I learned that Xen is likely the swiftest option available. I tried Xen in Ubuntu 12.10 64bit, but I'm unsure about the hypervisor issue (and broke grub trying to get around it), so I'm back at the drawing board. If someone could suggest a reliable means to make Xen work, I would like to try that.

I read that QubesOS might be worth a try, and I have heard great things about Cent or Redhat, but I'd rather not stray far from what I know when building something for someone else. Any help would be appreciated.

---

### Post by Lars Noodén on 2012-10-30
You won't be able to run OS X apps on Ubuntu AFAIK.  Nor can you easily run OS X in virtualization if it can be done at all.  

Instead you can run the Windows version of [photoshop in WINE](http://wiki.winehq.org/AdobePhotoshop).     It seems that [CS 5](http://appdb.winehq.org/appview.php?appId=17) runs best.  WINE is a bug-for-bug reimplementation of the Windows API and many versions of many Windows packages work well under it.  It's definitely worth a look.

Myself, I moved over to GIMP because it met my needs better and I found it easier to do what I wanted.  However, it is different enough that not everyone is going to find it to their liking.

---

### Post by acfreema on 2012-10-30
> **acfreema said:**
> Essentially, what I need to find is a way to get true virtualization support for Windows 7 64bit in a Linux environment

That's why it makes the most sense to virtualize a 64bit Windows 7. The only reason for the change to a different machine is because she keeps complaining about her Mac being too slow. Using CS5 is not acceptable.

I suppose I should have prefaced by saying that she's a professional photographer who has found Photoshop and Lightroom to be tools as much as her Pentax and good lighting.

---

### Post by Lars Noodén on 2012-10-30
I would try Virtualbox first.  It might also be good to work from snapshots.

Also, if only out of curiosity, I would try CS6 in WINE just to see what the silver rating is about.

---

### Post by acfreema on 2012-11-02
After some tinkering, it seems I've got an even uglier problem than I initially thought: GPU drivers.  It looks like this laptop has one of the newer Nvidia "optimus" adapters that won't respond to the normal driver, and doesn't like bumblebee either.

---

### Post by nwalkey on 2012-11-12
Which nvidia card does it have?

---

