---
title: "ubuntu kernel module update notifications?"
date: 2014-10-02
forum: Ubuntu Development Version
---

### Post by redrumrogue on 2014-10-02
Hi folks,

I previously posted this thread under "Hardware" and nobody responded ... maybe the wrong section!  

A couple of months ago I bought a new soundcard, ASUS Xonar Essence STX  II.  I discovered that it was not supported by the ubuntu kernel modules  at the time I installed it.  I eventually had to compile kernel 3.16.2  to get the card to work.  So this is the only reason why I'm currently  running an un-supported kernel in ubuntu.  I would prefer to just run  the ubuntu kernel so I can receive all the updates in the normal way.  I  know that the ubuntu kernel team update the ubuntu kernel with patches  from time to time and I'm wondering how I would find out if / when an  ubuntu kernel supports my sound card.  The kernel module needed for my  card is called snd_virtuoso.  Is there an ubuntu kernel changelog that I  could search for updates to this module?  Or perhaps a mailing list I can add myself to to be notified of changes in a specific module?

Thanks!

---

### Post by Doug S on 2014-10-02
I think, but am not sure, your card should be supported by default in kernel 3.17. As far as I can determine, the related module has always been included in the Ubuntu kernel and the specific driver was added recently:```
f42bb22 ALSA: virtuoso: add Xonar Essence STX II support
```That commit was between 3.16 and 3.17RC1.
I would suggest to try 3.17RC7 and see if your card works. You might also try the most recent default kernel for whatever release you are using, as maybe it has been backported already.

Edit: I realize I did not actually answer your questions with my reply.

Edit 2: see also: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17-rc1-utopic/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17-rc1-utopic/CHANGES)

---

### Post by redrumrogue on 2014-10-02
Hi there!  Thanks for the reply.  I was already aware that my card would be supported from 3.17, as it is stated on the ALSA project website here [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus)
I learned that a few months ago and decided that I would learn how to compile and install the latest linux kernel in the hopes that when 3.17 is eventually released I could install it and have a working card.  So i did eventually compile / install 3.16 (.1 maybe?) and when 3.16.2 stable was released I installed that and hey presto, I had a working card!  So it seams the snd_virtuoso module was updated to support my card from 3.16.2 - great.

However, although I've enjoyed learning how to configure, compile and install linux kernels, and I like having that control ... i don't really want to have to update the kernel manually everytime an update is released.  I would prefer to go back to the standard ubuntu kernel and recieve all the updates via the usual software update process.  This would mean going back to 3.13.... which doesn't support my sound card.

So what I really want to know is - when will the updated snd_virtuoso module, which DOES support my card, be included in the ubuntu kernel?  Will the ubuntu kernel dev team eventually take the snd_virtuoso module from 3.16.2+ and put it in the ubuntu kernel before the ubuntu kernel gets up to 3.16.2 version?  Is that even possible?  If they will do that then how would I find out when the ubuntu kernel eventually has this updated module?  Is there a mailing list I can subscribe to for ubuntu kernel updates?

I think this would be useful in general really, for any piece of hardware I may buy. I'd like a way to find out if the hardware is currently supported or to find out when the ubuntu kernel eventually does support it.

Thanks!

---

### Post by Doug S on 2014-10-02
> **redrumrogue said:**
> ...  This would mean going back to 3.13.... which doesn't support my sound card.[Check this out]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.11.7-trusty/CHANGES"). It should be in the next kernel update.> **redrumrogue said:**
> So what I really want to know is - when will the updated snd_virtuoso module, which DOES support my card, be included in the ubuntu kernel?Soon, see above link.  > **redrumrogue said:**
> Will the ubuntu kernel dev team eventually take the snd_virtuoso module from 3.16.2+ and put it in the ubuntu kernel before the ubuntu kernel gets up to 3.16.2 version?  Is that even possible?Yes it is possible, and backporting is ongoing all the time. > **redrumrogue said:**
> If they will do that then how would I find out when the ubuntu kernel eventually has this updated module?  Is there a mailing list I can subscribe to for ubuntu kernel updates?I don't know.

Edit: You might find what you want via the [kernel team mailing list]("https://lists.ubuntu.com/mailman/listinfo/kernel-team"). [This thread]("https://lists.ubuntu.com/archives/kernel-team/2014-September/048469.html"), for example

---

### Post by redrumrogue on 2014-10-03
Thanks a lot for this - good to see my sound card will be supported soon!

---

### Post by grahammechanical on 2014-10-03
The kernel team hold regular meetings and the Ubuntu Weekly Newsletter always provides a link to the minutes of those meetings and they also appear on planet.ubuntu.com. For example:

[http://voices.canonical.com/kernelteam/2014/09/30/kernel-team-meeting-minutes-september-30-2014/](http://voices.canonical.com/kernelteam/2014/09/30/kernel-team-meeting-minutes-september-30-2014/)

Kernel freeze for 14.10 is less than a week away and we are still on 3.16. So, I would not expect Ubuntu 14.10 to have the Linux 3.17 kernel. 

Regards.

---

