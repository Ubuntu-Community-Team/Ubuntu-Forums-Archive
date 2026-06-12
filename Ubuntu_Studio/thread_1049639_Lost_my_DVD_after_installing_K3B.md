---
title: "Lost my DVD after installing K3B"
date: 2009-01-24
forum: Ubuntu Studio
---

### Post by marcgh on 2009-01-24
Hi,

My intention is to encode and burn my DVDs with Ubuntu. Till now I always did it with Nero in XP.

I encoded the DVD to a ISO file with DeVeDe ant no problem from that side.
When I fire K3B I have a warning that there is no CD-DVD writer detected.

When I boot again in XP it (the DVD writer)is there and working.

I downloaded both ( DeVeDe and K3B ) via add/remove programs.
Is there anything else I should do before I can burn my DVD.

I went to the K3B website ([http://k3b.plainblack.com/faq](http://k3b.plainblack.com/faq)) but got only more confused about enabling the <CDRDAO> driver for SCSI or ATAPI. I really don't have the slightest idea where to begin.

Thanks in advance for your precious help, as I really need this DVD's ready for Monday morning and want to prove to myself that I no longer need XP to do the job.

Marc

---

### Post by Stochastic on 2009-01-25
Can you get it to work with any other burning software?  GnomeBaker, Brasero, etc...

That might help narrow the problem down.

---

### Post by HavocXphere on 2009-01-25
I don't think <CDRDAO> applies to DVD writing. Its for CDs only afaik. The DOA part defines what method is used to write the CD. DOA is not support by all devices afaik.

k3b worked out of the box for me. The default values should work just fine.:popcorn:

Also, make sure the ISO size fits onto a dvd. A standard single layer DVD has about 4.5gb space...while many of the commercial DVDs are dual-layer disks (8gb or so). If you try to write a 8gb iso onto a 4.5gb DVD then the stuff is going to hit the fan.;)

btw, why are you messing around with special drivers for this? Does it not detect your DVD writer without them?

---

### Post by marcgh on 2009-01-25
Thanks to Stochastic and HavocXphere for your advice.

I decided to remove k3b and try a reinstall. 
Don't know what went wrong the first time but now K3B is working perfectly.
I am currently burning a Vide DVD (ISO file made with DeVeDe) and at 73% all looks well.

Once agains, thanks.

Somebody knows how to mark this treath as SOLVED?

---

