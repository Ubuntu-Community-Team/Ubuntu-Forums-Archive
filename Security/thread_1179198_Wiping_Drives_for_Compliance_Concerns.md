---
title: "Wiping Drives for Compliance Concerns"
date: 2009-06-05
forum: Security
---

### Post by DnDer on 2009-06-05
Our company wants to wipe some hard drives and sell them back to our employees. So I e-mailed the head IT guy who is in charge of compliance and picked his brain about DBAN. Here's his reply.

> DD-Linux or another similar robust tool that ensures hard drives are formatted down to the block and sectore levels. I'm not familiar with the tool described below. Also, a degauzer as a secondary tool to ensure all data on the hard drive has been destroyed.

I know the dd command erases drives in Linux, but these are old Windows machines. I suppose that leaves me with the following questions:

(1) Can dd be run from a live distro (say, 9.04) successfully?
(2a) What would the exact line be to scrub stuff at the block and sector levels? 
(2b) I know the option exists, so: scrub with 0s or random at the block and sector level?
(3) Is DBAN a tool that can do this automatically? I don't really understand *how* it works, just that it zero-fills with however many passes a particular method dictates.
(4) Where does a person get a reasonably-priced degausser?

---

### Post by rookcifer on 2009-06-05
> **DnDer said:**
> Our company wants to wipe some hard drives and sell them back to our employees. So I e-mailed the head IT guy who is in charge of compliance and picked his brain about DBAN. Here's his reply.



I know the dd command erases drives in Linux, but these are old Windows machines. I suppose that leaves me with the following questions:

(1) Can dd be run from a live distro (say, 9.04) successfully?

Yes.

> (2a) What would the exact line be to scrub stuff at the block and sector levels? 

```
dd if=/dev/zero of=/dev/hda
```

or

```
dd if=/dev/urandom of=/dev/hda
```

where /dev/hda is the name of the device you wish to scrub.

The first option writes zeroes.  The second option writes random data.  Both methods, even with one pass, will render to data unrecoverable.  The second method will probably take longer.

Or, if you prefer you could use "shred" which does the same thing:

```
shred -vfz -n 1 /dev/hda
```

The above command will result in one pass of zeroes.  You can specify (-n x) for as many passes as you want, i.e shred -n 20 /dev/hda.

> (2b) I know the option exists, so: scrub with 0s or random at the block and sector level?

Unless you have NSA after your data, one write with zeroes is enough.  I have never seen any documentation that a drive wiped one time with zeroes can be recovered.

> (3) Is DBAN a tool that can do this automatically? I don't really understand *how* it works, just that it zero-fills with however many passes a particular method dictates.

Yes, DBAN does essentially what the above does.

> (4) Where does a person get a reasonably-priced degausser?

No idea on this one.

*EDIT*

If you want to look at a very low level, close to the metal method of wiping, look [into this.]("http://blogs.zdnet.com/storage/?p=129")

---

### Post by bodhi.zazen on 2009-06-05
There was a theory that people could recover data from hard drives after multiple writes, thus a number of tools such as dban and shread and secure delete programs.

In practice, to my knowledge, it has never been done and this theory has been "debunked"

[16 Systems The Great Zero Challenge]("http://16systems.com/zero.php") 

[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html") 

[Overwriting Hard Drive Data « SANS Computer Forensics, Investigation, and Response]("http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/") 

Corporate policies, military policies, and general paranoia will take some time (amnd may never) revise these defunct policies.

---

### Post by rookcifer on 2009-06-05
> **bodhi.zazen said:**
> There was a theory that people could recover data from hard drives after multiple writes, thus a number of tools such as dban and shread and secure delete programs.

In practice, to my knowledge, it has never been done and this theory has been "debunked"

[16 Systems The Great Zero Challenge]("http://16systems.com/zero.php") 

[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html") 

[Overwriting Hard Drive Data « SANS Computer Forensics, Investigation, and Response]("http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/") 

Corporate policies, military policies, and general paranoia will take some time (amnd may never) revise these defunct policies.

All very good links.  It's like the guy at the "Great Zero Challenge" website said, this notion of needing to wipe with 35 passes or degauss, incinerate, etc. has perpetuated itself without any evidence (other than Peter Gutmann's now outdated paper which does not apply to modern hard drives).  Essentially, the multiple pass theory is an old wives tale and that research paper you posted seems to be proof.

---

### Post by DnDer on 2009-06-05
These posts have reached epic levels of both awesome and interesting, in equal parts. How do I become one of the guys who knows this stuff? (Seriously. Security, forensics and data recovery seems like a fascinating field to me.)

That being said, I'll submit the Secure Erase information to my CIO for review. Even if they're "old wives' tales," just about every business has to meet regulation and compliance standards with those tales. For now.

Thanks for the enlightenment, even if I'm not 100% sure I grok it all yet. ^_^

---

### Post by HermanAB on 2009-06-05
All disk drives have an erase function built into the drive controller.  All you need to do is activate it:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

You can either use the abovemention Windows utility or use Linux hdparm to activate the erase routine.

For some inexplicable reason, very few people know this.

---

### Post by The Cog on 2009-06-05
For really securely erasing drives I think thermite is probably an extremely satisfying solution, although it has a negative impact on the resale value.

---

### Post by rookcifer on 2009-06-05
> **HermanAB said:**
> All disk drives have an erase function built into the drive controller.  All you need to do is activate it:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

You can either use the abovemention Windows utility or use Linux hdparm to activate the erase routine.

For some inexplicable reason, very few people know this.

Yeah, I mentioned that in my above post.  The last line.  I've never used it, though.

---

