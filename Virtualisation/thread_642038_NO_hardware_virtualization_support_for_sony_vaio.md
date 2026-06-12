---
title: "NO hardware virtualization support for sony vaio"
date: 2007-12-16
forum: Virtualisation
---

### Post by Wingard on 2007-12-16
A couple weeks ago (beginning Novermber 2007), I bough a Sony Vaio business notebook (BX41VN). My intention was setting up a thin Linux server system, using KVM on top of it for hosting various virtual OS that I need for doing my job.

When configuring the system I discovered that Intel VT could not be enabled in the BIOS. Even after BIOS update, VT was still missing. After contacting the dealer, he asked the question directly to Sony and got the official answer that **Sony does definitively not support hardware virtualization on Vaio laptops**. The dealer told me that they did not give any further explanation, why.

For many years, I was really a Vaio fan, but now I'm disappointed. So I gave the notbook back and took a Toshiba Tecra S5 instead. This notebook supports VT, although the display is not as brilliant as Sony.

At least Toshiba is not a technology blocker.

---

### Post by can564 on 2008-04-01
I didn't dig to far to see if this applied to you're Sony.(I saw you had traded it back in) But I did spot this link for enabaling hardware virtualization on a Sony VGN-FZ280E that also did not offer a bios menu that could enable virtualization.

[http://www.neowin.net/forum/index.php?showtopic=619763](http://www.neowin.net/forum/index.php?showtopic=619763)

Thought it might help someone in the future when they stuble across the problem.

---

### Post by StOoZ on 2008-04-01
just a little question, no means to spam your thread :
does using vmware for virtualization , requires some sort of a hardware feature? 
If so, wow, I didnt know that, how come my old AthlonXP barton 2500 supports it..

---

### Post by fjgaude on 2008-04-01
> **StOoZ said:**
> just a little question, no means to spam your thread :
does using vmware for virtualization , requires some sort of a hardware feature? 
If so, wow, I didnt know that, how come my old AthlonXP barton 2500 supports it..

The CPU doesn't have to support VMs but it sure helps if it does. Likely adds 30% or more to the speed, quickness of the VM. At least this has been my experience going back three years.

---

