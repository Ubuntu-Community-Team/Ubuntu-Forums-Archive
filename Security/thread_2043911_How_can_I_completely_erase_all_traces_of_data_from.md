---
title: "How can I completely erase all traces of data from a hard drive?"
date: 2012-08-17
forum: Security
---

### Post by LustyCrow on 2012-08-17
Hi,
I've been given an old hard drive from a mate at work but it had some very sensitive information on it. 
I'm trying to find a way to completely remove all traces of data from it. 
So far I've used a live CD and ran the 3 follow commands:
1. sudo dd if=/dev/zero of=/dev/sda bs=1
2. sudo dd if=/dev/urandom of=/dev/sda bs=1
3. sudo dd if=/dev/zero of=/dev/sda bs=1
Will that have removed everything or is there anything else I can do to clear the hard drive?
Thanks in advance for any help you can offer.
:)

---

### Post by unevenflow on 2012-08-17
Hey, you can also use DBAN
[http://www.dban.org/](http://www.dban.org/)

---

### Post by LustyCrow on 2012-08-17
Cool, thanks I'll give that a try. :)

---

### Post by QIII on 2012-08-17
Be careful with DBAN.  It works very well.

I'd unplug all other drives but the one you want to nuke so you don't take a chance on a regrettable mistake.

---

### Post by ajgreeny on 2012-08-17
Having carried out three passes of the dd command I can not see much point in now using DBAN.

Unless you have something incredibly valuable on that hard drive which someone is willing to pay vast amounts of money to recover, the three passes of dd will have made it all but non-recoverable, and as I understand it, it would only be by using very careful and intricate (and costly) forensics that anyone could recover anything.

---

### Post by QIII on 2012-08-17
> **ajgreeny said:**
> Having carried out three passes of the dd command I can not see much point in now using DBAN.

Quite right.

But it is fun to put on shades, a fedora and a trenchcoat, have your cloak and dagger close at hand ...

---

### Post by bodhi.zazen on 2012-08-17
> **ajgreeny said:**
> Having carried out three passes of the dd command I can not see much point in now using DBAN.

Unless you have something incredibly valuable on that hard drive which someone is willing to pay vast amounts of money to recover, the three passes of dd will have made it all but non-recoverable, and as I understand it, it would only be by using very careful and intricate (and costly) forensics that anyone could recover anything.

I think one pass of dd is sufficient.

You can also use scrub

[http://linux.die.net/man/1/scrub](http://linux.die.net/man/1/scrub)

scrub is faster then dd ;)

---

### Post by wacky_sung on 2012-08-20
I will suggest you to crush and hammer it to destruction a hard disk if you are not going to sell or keep it. Inregardless of how many rounds of erase of traces and it is still retrievable.

---

### Post by Ms. Daisy on 2012-08-20
> **wacky_sung said:**
> I will suggest you to crush and hammer it to destruction a hard disk if you are not going to sell or keep it. Inregardless of how many rounds of erase of traces and it is still retrievable.
No. If you live inside a spy novel, then you may want to do 3 passes with dd. 

In reality one pass of dd will get it done.

If you can actually retrieve anything of any use from a machine that has had one dd pass, please post your methods. The forensics world would be extremely interested, I'm sure.

---

### Post by ottosykora on 2012-08-20
>If you can actually retrieve anything of any use from a machine that has had one dd pass, please post your methods. The forensics world would be extremely interested, I'm sure.<

yes, as all those reports about possible remanent magnetism and possible recovery of data after number of overwrites are just part of those famous urban legends and there has been so far not a single real evidence that someone in the world managed to recover something after it has been overwritten.

---

### Post by bodhi.zazen on 2012-08-20
> **wacky_sung said:**
> I will suggest you to crush and hammer it to destruction a hard disk if you are not going to sell or keep it. Inregardless of how many rounds of erase of traces and it is still retrievable.

That theory has been debunked years ago, someone like you should not be spreading FUD.

Technical paper here:

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

---

### Post by Hungry Man on 2012-08-20
There really isn't any question. It's never been proven that you can retrieve data from a disk and the methods to do so involve really intense forensics. I would do two wipes personally only to ensure that, if there were errors during the first wipe, they'll be taken care of during the second.

At this point it's really just not feasible.

If you're holding the location of a dozen nuclear warheads the NSA might try to use an electron microscope to see the data. It probably wouldn't work.

---

### Post by wacky_sung on 2012-08-20
> **bodhi.zazen said:**
> That theory has been debunked years ago, someone like you should not be spreading FUD.

Technical paper here:

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

What you have saw is only based on paper and one side of your story. It may be tough but it does not mean it is impossible.

---

### Post by kurtymckurt on 2012-08-20
DBAN is pretty sweet and works well.  For something just as good, look into "shred -fuz"

---

### Post by bodhi.zazen on 2012-08-20
> **wacky_sung said:**
> What you have saw is only based on paper and one side of your story. It may be tough but it does not mean it is impossible.

Paranoia is healthy, but must be tempered with reality.

The reality is there is not a published example of successful data recovery after data that has been overwritten. Any paper you could cite is theoretical only, and the paper I cited is accepted (within the computer science field) as debunking the theory.

I do not have to prove something that does not exist, rather the burden is on you to prove it can be done.

---

### Post by Hungry Man on 2012-08-20
> **wacky_sung said:**
> What you have saw is only based on paper and one side of your story. It may be tough but it does not mean it is impossible.

It's actually the techniques that would be used to get the data that are only on paper.

It has never been shown possible, even theoretically it's unlikely, and even if it were possible it would be incredibly difficult and time consuming to do it. The general consensus is that it's not practical, potentially not even possible.

---

