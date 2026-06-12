---
title: "Sun Blade 100 and booting Edgy CD"
date: 2007-09-28
forum: Sun Sparc Users
---

### Post by pteri498 on 2007-09-28
I've been through the forums on this, and can't find a topic that matches me too well.

I've been given control over a Sun Blade 100 system in order to get it working. Solaris isn't behaving at all. 

I've been tasked with installing Ubuntu, so i've downloaded the 7.04 SPARC server install CD, but I can't get anywhere with the CD.

The system won't boot the CD automatically, and I can't see any bios options, since the screen refuses to switch on until Solaris starts itself.

The system throws out error after error during bootup, even after an attempt to reformat and reinstall, so we're running out of ideas.

Furthermore, I'm not sure about the IP address on this machine, since it's connected to a large cluster of computers, and I personally don't know how to dig the number out of the system.

Any tips on getting the Ubuntu CD to boot up on this system? Is it possible?

---

### Post by pteri498 on 2007-09-28
Update: Success!

I randomly stumbled across an instruction that helped me greatly.

press [stop]-a

type 'boot cdrom' without the quotes.

I am now booting the cd and I'll give updates if i have any more issues.

---

### Post by rampitec on 2007-09-28
Frankly, you'd better run Solaris on SPARC. It performs better, at least on SPARC. You have Blade, so probably you will have several of that machines in cluster. It scales better. Then it's more stable. You might also have a support for this along with the system, I don't know. If so, that's a great value.

Ubuntu, or any Linux in general is better choice for a desktop system. If you need a server Solaris works better. If you ask me, I have Solaris servers in my network, while my desktop system runs Ubuntu.

That's not an advertisement, that's just an experience. Take this as an opinion.

BTW, have you tried to press Esc while booting your blade? Mine Ultra gives a boot menu then.

P.S. Note, you may press Stop-A at any time **even** when OS is running. You will get into the BIOS code. System will be suspended. You can say 'continue' as far as I remember, or some other command. That has nothing to do with an OS. That is an unmasked system interrupt.

---

### Post by psychicist on 2007-09-29
Is Solaris really that much more stable, reliable and faster than Linux (at least on SPARC)? It's probably more mature and there are several technologies in Solaris 10 and in Nevada now that could make it more reliable (Predictive self-healing, ZFS). But it's really not faster than Linux because I have had current Slackware and Solaris installed on both x86 and Sparc and the former runs rings around the latter.

Ubuntu is generally slower than Slackware but is it also slower than Solaris Nevada? I don't know because I have never installed Ubuntu on SPARC. Of course for servers reliability is more important than for desktops and that could be a reason to still prefer Solaris.

---

