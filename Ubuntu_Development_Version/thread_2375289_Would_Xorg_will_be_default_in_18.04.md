---
title: "Would Xorg will be default in 18.04?"
date: 2017-10-23
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-10-23
It was a bit adventurous in 17.10 give double systems, Wayland and Xorg, but 18.04 would be 5 year LTS, so Wayland cannot be default. Users, enterprise and otherwise, who opt for LTS, won't be happy with some system that might not allow known apps to work. I think, Canonical would release Ubuntu 18.04 with Xorg as default. Wayland maybe available for those, who want to experiment.

---

### Post by dino99 on 2017-10-23
Plan is to make wayland working everywhere, like Fedora have done.

---

### Post by Chanath on 2017-10-23
> **dino99 said:**
> Plan is to make wayland working everywhere, like Fedora have done.

The paying customers would want a stable LTS for 5 years. They won't want workarounds as we do here, playing with fire in one or two partitions. Many crucial apps won't work with Wayland, and you just can't tell those users not to use Nvidia.

---

### Post by cariboo on 2017-10-23
Paying customers don't upgrade when an LTS version is released, they usually wait until the first point release, if they upgrade at all. Keep in mind that 16.04 is supported until April 2021.

---

### Post by ventrical on 2017-10-23
Yes... last I heard xorg wil be default for 18.04. It was to be wayland but now xorg and wayland as option..

---

### Post by jbicha on 2017-10-23
> **Chanath said:**
> The paying customers would want a stable LTS for 5 years. They won't want workarounds as we do here, playing with fire in one or two partitions. Many crucial apps won't work with Wayland, and you just can't tell those users not to use Nvidia.

Paying customers use Ubuntu Advantage. Ubuntu Advantage only [supports packages]("https://www.ubuntu.com/legal/ubuntu-advantage/service-description#support-scope-packages") from 'main'.

> **Chanath said:**
> 18.04 would be 5 year LTS, so Wayland  cannot be default.

Why not? 

Canonical doesn't support Synaptic or running apps like gedit and nautilus as root (use the gvfs admin backend!)

Enterprise customers are expected to read the Release Notes. I believe the [Release Notes]("https://wiki.ubuntu.com/ArtfulAardvark/ReleaseNotes/#Desktop") are pretty clear that some apps don't work with Wayland and give a brief mention of how to work around that by logging into *Ubuntu on Xorg*. *Ubuntu on Xorg* will still be there in Ubuntu 18.04 LTS.

---

### Post by ventrical on 2017-10-23
Well consider the source..

[http://www.omgubuntu.co.uk/2017/10/ubuntu-18-04-name-speculation](http://www.omgubuntu.co.uk/2017/10/ubuntu-18-04-name-speculation)

> 
The nature of LTS releases mean we can expect minor and conservative  changes to what’s on offer in Ubuntu 17.10, rather than bold new  features. But 18.04 is likely to include a new GTK theme, and revert to  using Xorg as default (though Wayland will, we hear, still be installed  as an option).


---

### Post by jbicha on 2017-10-23
As far as I know, the mention of Wayland in that quote is speculation at this point.

---

### Post by Chanath on 2017-10-23
> **jbicha said:**
> 

Why not? 



You just can't demand the paying customers not to use Nvidia, can you?

---

### Post by jbicha on 2017-10-23
Please be more specific.

Honestly, I expect most Ubuntu Advantage customers would just be using ordinary integrated Intel graphics cards which work great in Ubuntu's default Wayland session.

---

### Post by Chanath on 2017-10-23
> **jbicha said:**
> Please be more specific.

Honestly, I expect most Ubuntu Advantage customers would just be using ordinary integrated Intel graphics cards which work great in Ubuntu's default Wayland session.

No self respecting business organisation would keep its files and folders in a cloud, in other words, in someone else's servers. 
If all companies buy only Intel, then Nvidia would go bankrupt. That's not the way business work.

---

### Post by jbicha on 2017-10-23
I don't know what you're talking about.

Anyway, enterprises have system administrators. It is a one line change to a gdm3 configuration file to disable Wayland if the system administrator doesn't feel like supporting Wayland. That means this is literally **no big deal**.

By the way, that one line change is exactly what System76 did with Pop!_OS 17.10. It's a bit unexpected for their users to [figure out]("https://www.reddit.com/r/pop_os/comments/75wn18/how_do_i_start_wayland_session/") how to re-enable Wayland but it's not really that hard either.

---

### Post by Chanath on 2017-10-23
> **jbicha said:**
> I don't know what you're talking about.

Anyway, enterprises have system administrators. It is a one line change to a gdm3 configuration file to disable Wayland if the system administrator doesn't feel like supporting Wayland. That means this is literally **no big deal**.

By the way, that one line change is exactly what System76 did with Pop!_OS 17.10. It's a bit unexpected for their users to [figure out]("https://www.reddit.com/r/pop_os/comments/75wn18/how_do_i_start_wayland_session/") how to re-enable Wayland but it's not really that hard either.

I was just thinking about, whether or not Wayland would be default on 18.04. That's why I asked the question. There are more reasons not to use Wayland than to use it. Your post tells the same--System76 disabled Wayland, for its a business. Btw, system administrators don't really want to hack around. They might suggest to the management to look for some other distro. They wouldn't want dozens of people complaining everyday. 

Thanks for the link. Would try Pop! OS again.

---

### Post by jbicha on 2017-10-23
System76 is a very particular kind of business that does not represent the typical Ubuntu Advantage customer. Anyway, Ubuntu enabling Wayland by default was not a problem at all for them.

I think it's far-fetched to imagine that any system administrator would rather switch to a totally different distro than remove literally one character (a # comment) from one file. And what distro would they switch to? I don't think it's a stretch at all to believe that the reason Red Hat is making Wayland a [technical preview]("https://www.phoronix.com/scan.php?page=news_item&px=RHEL-7.5-Wayland-Tech-Preview") soon is so that it can be enabled by default in RHEL 8. Debian 10 "Buster" will also default to Wayland.

---

### Post by amano on 2017-10-23
Other questions arise: How well will X be supported in 5 years? The reason that Wayland exists was that X was so hard to keep secure. Who will pay for maintaining it?  Red Hat/Fedora seems to make the switch early, more and more resources will be shifted from X to Wayland with every new party making the switch.

---

### Post by QIII on 2017-10-23
We're devolving into a mildly contentious philosophical/opinion disagreement here.  Although the title appears straight forward enough, the actual question in the OP is not straight forward enough to be a passable subject for this sub forum.

Closed.

---

