---
title: "Daily iso's are uploaded"
date: 2019-10-20
forum: Ubuntu Development Version
---

### Post by wildmanne39 on 2019-10-20
Just to let everyone know that have been waiting for the daily iso's they are now uploaded and the links to the official Ubuntu flavors are in the sticky.

---

### Post by Frogs Hair on 2019-10-20
Thanks ! I just received first Budgie updates.

---

### Post by mrfelker on 2019-10-21
I'm downloading an iso with the codename focal.   is  focal <animal>  offical

---

### Post by wildmanne39 on 2019-10-21
Focal Fossa is the official name.

---

### Post by mrfelker on 2019-10-21
Cool.  From wikipedia

The fossa is the largest mammalian carnivore on the island of Madagascar and has been compared to a small cougar. Adults have a head-body length of 70&#8211;80 cm (28&#8211;31 in) and weigh between 5.5 and 8.6 kg (12 and 19 lb), with the males larger than the females. It has semi-retractable claws (meaning it can extend but not retract its claws fully) and flexible ankles that allow it to climb up and down trees head-first, and also support jumping from tree to tree. The fossa is unique within its family for the shape of its genitalia, which share traits with those of cats and hyenas.

---

### Post by guiverc on 2019-10-21
The idea of QA-testing 20.04 is still scary....  for me anyway

Still too soon after eoan, as my usual first chore is testing all [my] bugs of eoan-cycle to confirm they were fixed (if not closed/released/etc), and adding 'focal' to .... nah I still need a few more days before I start that merry-go-round...
(esp. given touching the bug reports means I should also chase up-stream... way too early!)

(head goes back in the sand!)

---

### Post by Irihapeti on 2019-10-21
I'm also still catching my breath after the Eoan final testing.

Plus, real life has thrown some distractions in my way. As I'm getting paid for one of them, I'm not complaining. :)

As for scary, though, I think that VMs have made a huge difference. Trashing a VM seems much more comfortable that discovering you've screwed up your main machine and can't boot (or something). 8-[

---

### Post by #&amp;thj^% on 2019-10-21
> **Irihapeti said:**
> As for scary, though, I think that VMs have made a huge difference. Trashing a VM seems much more comfortable that discovering you've screwed up your main machine and can't boot (or something). 8-[

Sheesh Where's your sense of adventure? ):P

---

### Post by ajgreeny on 2019-10-21
Just downloaded and installed Xubuntu Focal as a VM in Virtualbox version 6.0.14.

Seems to be OK so far except that every boot gives me a notification of a system problem but with no detail of what the problem is.  So far I have not had time to search any logs to see what is happening, and the system appears to overcome whatever the problem is and continues to run well.

It's a pity that chromium is available only as a snap; I forgot that and used synaptic to install it which froze the system almost completely, so I ran commands ```
snap remove chromium && snap install chromium
``` which appeared to clean things up and happened much quicker than synaptic.

---

### Post by Irihapeti on 2019-10-21
> **mrfelker said:**
> Cool.  From wikipedia

The fossa is the largest mammalian carnivore on the island of Madagascar and has been compared to a small cougar. Adults have a head-body length of 70–80 cm (28–31 in) and weigh between 5.5 and 8.6 kg (12 and 19 lb), with the males larger than the females. It has semi-retractable claws (meaning it can extend but not retract its claws fully) and flexible ankles that allow it to climb up and down trees head-first, and also support jumping from tree to tree. The fossa is unique within its family for the shape of its genitalia, which share traits with those of cats and hyenas.

Sounds like the fossa isn't quite as big as I'd imagined, so maybe not quite as scary as I thought. I once had a rather large cat who weighed 6.5 kg and I wasn't scared of him. But I think the local rabbits were... :)

---

### Post by PaulW2U on 2019-10-21
> **ajgreeny said:**
> I forgot that and used synaptic to install it which froze the system almost completely, so I ran commands ```
snap remove chromium && snap install chromium
``` which appeared to clean things up and happened much quicker than synaptic.
Installing Chromium using synaptic installs a transitional .deb which then installs snapd (if not already installed), the chromium snap and any other snaps that the Chromium snap needs in order to function such as gtk-common-themes. This can be a lengthy process on Kubuntu, Lubuntu and Xubuntu compared to Ubuntu, Ubuntu MATE and Ubuntu Budgie which will have some of what Chromium needs preseeded as other snap applications are installed by default.

Removing the Chromium snap and re-installing it would of course be much quicker than the initial installation as removing the snap wouldn't undo a lot of what had already been done.

---

### Post by ajgreeny on 2019-10-22
> **PaulW2U said:**
> Installing Chromium using synaptic installs a transitional .deb which then installs snapd (if not already installed), the chromium snap and any other snaps that the Chromium snap needs in order to function such as gtk-common-themes. This can be a lengthy process on Kubuntu, Lubuntu and Xubuntu compared to Ubuntu, Ubuntu MATE and Ubuntu Budgie which will have some of what Chromium needs preseeded as other snap applications are installed by default.

Removing the Chromium snap and re-installing it would of course be much quicker than the initial installation as removing the snap wouldn't undo a lot of what had already been done.
Thanks for that info Paul; this is the first snap I have ever installed and so far I have not had a chance to look at it very much, nor see how well chromium runs as a snap compared to a .deb installation.

Lots to investigate and so little time to do it all these days!

---

### Post by Bashing-om on 2019-10-22
Hey Guys :)

Media attention:
Ubuntu 20.04 LTS (Focal Fossa) Daily Build ISOs Are Now Available to Download
[https://news.softpedia.com/news/ubuntu-20-04-lts-focal-fossa-daily-build-isos-are-now-available-to-download-527935.shtml](https://news.softpedia.com/news/ubuntu-20-04-lts-focal-fossa-daily-build-isos-are-now-available-to-download-527935.shtml)

with links to the flavor builds.

[INDENT]moving right on along
[/INDENT]

---

### Post by VMC on 2019-10-23
> **Bashing-om said:**
> Hey Guys :)

Media attention:
Ubuntu 20.04 LTS (Focal Fossa) Daily Build ISOs Are Now Available to Download
[https://news.softpedia.com/news/ubuntu-20-04-lts-focal-fossa-daily-build-isos-are-now-available-to-download-527935.shtml](https://news.softpedia.com/news/ubuntu-20-04-lts-focal-fossa-daily-build-isos-are-now-available-to-download-527935.shtml)

with links to the flavor builds.
[INDENT]moving right on along
[/INDENT]

Let the fun begin again! Thanks for the link.

---

