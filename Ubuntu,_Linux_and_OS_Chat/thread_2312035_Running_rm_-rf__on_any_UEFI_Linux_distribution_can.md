---
title: "Running rm -rf / on any UEFI Linux distribution can potentially perma-brick your syst"
date: 2016-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by SuperFreak on 2016-02-01
Not sure where to post this

[http://www.phoronix.com/scan.php?page=news_item&px=UEFI-rm-root-directory](http://www.phoronix.com/scan.php?page=news_item&px=UEFI-rm-root-directory)

---

### Post by SeijiSensei on 2016-02-01
I've used Linux for two decades and have never issued an "rm -rf /" command.  If I want to trash an installation, I'll just repartition and reformat.

---

### Post by SuperFreak on 2016-02-01
I am under the impression this effects more than the hard drive but also the firmware. But your right it is a dangerous command to use

---

### Post by Nuno_Abreu on 2016-02-01
If you run it with the sudo, of course.

Actually, if you run this on your Home folder, it is rather complicated too. I unfortunately have done that accidentally and I tried my luck with recovery software.

---

### Post by slickymaster on 2016-02-01
> **SuperFreak said:**
> Not sure where to post this

[http://www.phoronix.com/scan.php?page=news_item&px=UEFI-rm-root-directory](http://www.phoronix.com/scan.php?page=news_item&px=UEFI-rm-root-directory)

You nailed it. It's on the correct sub-forum ;)

---

### Post by ian-weisser on 2016-02-01
Typical Phoronix hyperbole to attract eyeballs (The-sky-is-falling! Lennart-doesnt-care! Oh-the-humanity! Wont-somebody-think-of-the-children!)
I don't consider Phoronix a useful news site because too many of their postings are like that.

Running that command will effectively brick *any* system for most users, regardless of BIOS vs UEFI, and has for decades.
Installing a new OS is not a task most non-Linux users are up for....else they would be Linux users.

We have shouted for years that root is dangerous. So many ways to irrecoverably destroy your system.
And this has always been one of them.

Erasing UEFI merely makes the next OS much harder to install
...and demonstrates that admin probably shouldn't be trusted with root.

---

### Post by matt_symes on 2016-02-01
> **ian-weisser said:**
> Typical Phoronix hyperbole to attract eyeballs (The-sky-is-falling! Lennart-doesnt-care! Oh-the-humanity! Wont-somebody-think-of-the-children!)
I don't consider Phoronix a useful news site because too many of their postings are like that.

Lol.

> I am under the impression this effects more than the hard drive but also the firmware. 

That's the impression i initially had from reading the article.

What i don't understand about that article is why unlinking (deleting) files should destroy the firmware. Writing to those files maybe; but unlinking ?

It's almost like two different ideas are being conflated.

Then again, I don't know much about UEFI implementation details in the Linux kernel, so maybe it's just my ignorance on the matter.

---

### Post by howefield on 2016-02-01
> **ian-weisser said:**
> Running that command will effectively brick *any* system...

Not exactly.

You'd have to try a little harder than running that command to brick an Ubuntu installation, at least on a BIOS machine, don't have an UEFI machine to try but I'd expect it to be the same.

---

### Post by yoshii on 2016-02-01
I didn't read the article yet... I'm about to.  I don't understand why deleting a filesystem would "brick" a computer.  Can't you just swap out the hard drive and put in a new one and then reinstall an operating system?  Bricking implies that it can't be fixed again--a permanent loss.  But surely, you can just use gParted from a LiveCD and create a new MBR or GPT filesystem again thought right?  And BIOS/UEFI settings can be reverted to factory defaults and then edited again.  I don't see the problem unless you improperly flash the eproms of the BIOS.  What am I missing?

---

### Post by oldfred on 2016-02-01
I did not think so either, but at least one implementation of UEFI copies NVRAM data to drive & copies it back. It is the copy back of zeros that is the issue.

I would think a dd to zero a drive that a user wanted to erase may do the same thing.

It really is the UEFI implementation.

---

### Post by matt_symes on 2016-02-01
> **oldfred said:**
> I did not think so either, but at least one implementation of UEFI copies NVRAM data to drive & copies it back. It is the copy back of zeros that is the issue.

I would think a dd to zero a drive that a user wanted to erase may do the same thing.

It really is the UEFI implementation.

I'm still confused by this oldfred. 

If the filling system is deleted then would there be anything to copy back ?

Is it copying or moving from NVRAM ? Moving would explain it if there's nothing to move back.

Is it mounting NVRAM directly in some way so that the contents of /sys/firmware/uefi are actually the contents of NVRAM itself ? 

Just I'm just having difficulty understanding the mechanism by which deleting files would trash UEFI.

Like i said though, it may just be due to my ignorance about UEFI and how the kernel handles it.

Another thought along those lines. If deleting the file system could trash UEFI, would having a catastrophic hard drive failure while running Linux also trash UEFI ?

---

### Post by oldfred on 2016-02-01
I would think all those would be an issue.
But I get that it was just one vendor's UEFI, but they have not checked others.
And they showed it can be done from Windows, as often the first thing they like to blame is Linux.

I thought you needed tools like efibootmgr to write data into UEFI. 
And UEFI like BIOS writes detailed hardware info into hard drive for system to use.
But there is some sync of NVRAM and harddrive.

---

### Post by kansasnoob on 2016-02-01
> If deleting the file system could trash UEFI, would having a catastrophic hard drive failure while running Linux also trash UEFI ? 

I would think not, or maybe I've just been lucky. I have a somewhat new-ish (one year old?) AsRock mobo:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157514](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157514)

And I have a spare SATA hard drive that I swap in for testing, and before beginning my iso-tests I always use Gparted to create a fresh GPT partition table. So far no problems and I've done that probably half a dozen times. When I put the working "production" hard drive back in it just works with no fanfare.

I wonder if MSI did something just totally ignorant? Regardless I'd never run such a reckless command!

---

### Post by matt_symes on 2016-02-01
> **oldfred said:**
> I would think all those would be an issue.
But I get that it was just one vendor's UEFI, but they have not checked others.
And they showed it can be done from Windows, as often the first thing they like to blame is Linux.

I thought you needed tools like efibootmgr to write data into UEFI. 
And UEFI like BIOS writes detailed hardware info into hard drive for system to use.
But there is some sync of NVRAM and harddrive.

Very interesting. I'll have to do some reading up on the syncing at some point when i get the time.

If i understand the syncing correctly, I would have thought the greater risk would be dropping laptops and breaking the hard drive than running *rm -fr* on the root file system. A failed hard drive can't sync.

Anecdotally, I've dropped a laptop and that did kill the drive (along with the screen). That was a BIOS laptop though. I've never run (that i can remember) rm -rf on the root filing system though.

---

### Post by matt_symes on 2016-02-01
> **kansasnoob said:**
> I would think not, or maybe I've just been lucky. I have a somewhat new-ish (one year old?) AsRock mobo:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157514](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157514)

And I have a spare SATA hard drive that I swap in for testing, and before beginning my iso-tests I always use Gparted to create a fresh GPT partition table. So far no problems and I've done that probably half a dozen times. When I put the working "production" hard drive back in it just works with no fanfare.

I wonder if MSI did something just totally ignorant? Regardless I'd never run such a reckless command!

Maybe it depends on the board manufacturer ? I don't know.

---

