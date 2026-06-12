---
title: "RHEL6 is out."
date: 2010-11-11
forum: The Cafe
---

### Post by kaldor on 2010-11-11
RedHat Enterprise Linux 6 was released yesterday.

Great news, I say; the last stable RHEL system was based on Fedora Core **6**. That's quite old now and was using Linux Kernel 2.6.18.

Can't wait until CentOS 6 follows.

Any RHEL/CentOS users here?

---

### Post by CharlesA on 2010-11-11
*raises hand*

I've messed with CentOS off and on, and it's not really all that different from other distros. I prefer Ubuntu tho. :P

---

### Post by Spice Weasel on 2010-11-11
Yay!

Well, I'll be getting a copy for my Mum (who likes Fedora but wants a more stable system), either in the form of CentOS or a cheap copy on Ebay. Whichever comes first. :)

I wish there was an Xfce version of CentOS/Scientific/RHEL, that's a major downside for me. I mean, Scientific Linux includes IceWM. I'm sure more people use Xfce.

---

### Post by snowpine on 2010-11-11
I use CentOS 5.5 on my work computer. I've never found its software to be particularly old/outdated for my needs. So long as OpenOffice and Firefox are recent versions, I'm OK. 

Xfce and CentOS are a great combination! (Not sure why you think they wouldn't be.) I have this combo up and running on a spare Pentium 3 laptop and it is very nice. (I use Gnome with Compiz on my more powerful work desktop.) CentOS 5.x has been excellent for me on older hardware, for example Youtube videos play smoother than on most other distros. I have a hunch 6.x will not be quite as "lightweight," but that is to be expected.

I have no experience with paid/registered RHEL, only CentOS.

---

### Post by Dragonbite on 2010-11-11
I'm tossing up between using Fedora or CentOS as my next server.  If I go with CentOS I'll probably go with 6 when its released.

---

### Post by Spice Weasel on 2010-11-11
> **snowpine said:**
> 
Xfce and CentOS are a great combination! (Not sure why you think they wouldn't be.) I have this combo up and running on a spare Pentium 3 laptop and it is very nice. (I use Gnome with Compiz on my more powerful work desktop.) CentOS 5.x has been excellent for me on older hardware, for example Youtube videos play smoother than on most other distros. I have a hunch 6.x will not be quite as "lightweight," but that is to be expected.

I was saying that I wanted an official Xfce version.. At the moment they only provide KDE and GNOME (and in the case of Scientific, IceWM). :(

---

### Post by snowpine on 2010-11-11
> **Dragonbite said:**
> I'm tossing up between using Fedora or CentOS as my next server.  If I go with CentOS I'll probably go with 6 when its released.

Fedora's a bad choice for a server, in my opinion. Each release is supported for only 13 months, so you will be doing a lot of upgrading.

---

### Post by kaldor on 2010-11-11
> **snowpine said:**
> Fedora's a bad choice for a server, in my opinion. Each release is supported for only 13 months, so you will be doing a lot of upgrading.

Agreed.

---

### Post by snowpine on 2010-11-11
> **Spice Weasel said:**
> I was saying that I wanted an official Xfce version.. At the moment they only provide KDE and GNOME (and in the case of Scientific, IceWM). :(

There is no official CentOS Xfce Live CD, true. However when you actually get around to installing (I recommend using the netinstall CD, not the Live CD), the Anaconda installer lets you choose exactly which package groups you want to install. You do **not** have to install KDE or Gnome if you prefer Xfce. I have done it before, and it's incredibly easy. :)

---

### Post by Dragonbite on 2010-11-11
> **snowpine said:**
> Fedora's a bad choice for a server, in my opinion. Each release is supported for only 13 months, so you will be doing a lot of upgrading.

I understand that, but it would be at home where it isn't under a heavy load, nor is connected to the outside world. So if it isn't touched until 2015 that wouldn't (shouldn't) be a big deal.  By then I should be more experienced with server admin and networking (one would hope).

But with Fedora I would get a more up-to-date version now.. to last me those 5 years. Or I could go with CentOS and have a more stable and secure system to last those 5 years, but with more conservitive package versions.

That's just my thinking.

---

### Post by kaldor on 2010-11-11
On this topic, I'm considering switching to CentOS 6 when it comes out because I want a stable OS with minimal issues for a while.

Will drivers (such as nvidia) be supported and easily installable on RHEL 6? I couldn't use CentOS 5.x at *all* on my laptop do to numerous issues due to outdatedness. Fedora 12 ran great apart from the nvidia drivers being extremely buggy. Has this been fixed up for RHEL?

---

### Post by snowpine on 2010-11-11
> **Dragonbite said:**
> I understand that, but it would be at home where it isn't under a heavy load, nor is connected to the outside world. So if it isn't touched until 2015 that wouldn't (shouldn't) be a big deal.  By then I should be more experienced with server admin and networking (one would hope).

But with Fedora I would get a more up-to-date version now.. to last me those 5 years. Or I could go with CentOS and have a more stable and secure system to last those 5 years, but with more conservitive package versions.

That's just my thinking.

If you are serious about studying server admin and networking, then it is never too early to learn "best practices." Running an "end-of-life" Fedora release is not going to teach you much (except headaches).

Is there a reason why you don't just use Ubuntu Server? 10.04 will be supported until April 2015.

---

### Post by Spice Weasel on 2010-11-11
Enable the RPMFusion repository for RHEL, then install the kmod-nvidia package.

---

### Post by CharlesA on 2010-11-11
> **snowpine said:**
> If you are serious about studying server admin and networking, then it is never too early to learn "best practices." Running an "end-of-life" Fedora release is not going to teach you much (except headaches).

Agreed. I might switch over, but for the moment, Ubuntu works fine, so there's no real reason for me to switch.

Does RHEL6 have ext4 support?

---

### Post by snowpine on 2010-11-11
> **kaldor said:**
> On this topic, I'm considering switching to CentOS 6 when it comes out because I want a stable OS with minimal issues for a while.

Will drivers (such as nvidia) be supported and easily installable on RHEL 6? I couldn't use CentOS 5.x at *all* on my laptop do to numerous issues due to outdatedness. Fedora 12 ran great apart from the nvidia drivers being extremely buggy. Has this been fixed up for RHEL?

You can test drive RHEL 6 today with a 30-day trial, if you are curious how it will perform on your hardware. RHEL/CentOS is not generally regarded as a "non-free hardware works perfectly out-of-the-box" type of distro (like Ubuntu) but I'm sure you are not the only person in the world with this question. I'm afraid I don't have any Nvidia hardware myself, so I can't be of assistance with your query.

---

### Post by snowpine on 2010-11-11
> **CharlesA said:**
> Does RHEL6 have ext4 support?

5.5 does, so I would be surprised if they dropped this important feature from 6.x. :)

---

### Post by Cuddles McKitten on 2010-11-11
> **CharlesA said:**
> Does RHEL6 have ext4 support?

According to the one article I read, yes it does.

EDIT: Beaten by mere seconds!

---

### Post by Dragonbite on 2010-11-11
> **snowpine said:**
> If you are serious about studying server admin and networking, then it is never too early to learn "best practices." Running an "end-of-life" Fedora release is not going to teach you much (except headaches).

Is there a reason why you don't just use Ubuntu Server? 10.04 will be supported until April 2015.

I currently have Ubuntu 8.04 LTS still working, but looking for setting up another server.

I've just been turning to Fedora lately because it works better on my system (my laptop) than Ubuntu 10.04 or 10.10, largely because of the Intel 855 video issue.

> **CharlesA said:**
> Agreed. I might switch over, but for the moment, Ubuntu works fine, so there's no real reason for me to switch.

Does RHEL6 have ext4 support?

I seem to remember hearing that this version (6) is supposed to.

---

### Post by CharlesA on 2010-11-11
> **snowpine said:**
> 5.5 does, so I would be surprised if they dropped this important feature from 6.x. :)

Lol, I guess that shows how often I used 5.5. :P

I know that Debian Lenny doesn't support ext4 out of the box, but wasn't sure about CentOS, since it uses ext3 for the root partition.

---

### Post by kaldor on 2010-11-11
RHEL 6 uses Ext4 by default according to their website.

---

### Post by snowpine on 2010-11-11
RHEL 6 is roughly equivalent to Fedora 12, Debian Squeeze (not Lenny!), or Ubuntu 10.04 in the "freshness" of its packages:

[http://distrowatch.com/table.php?distribution=redhat](http://distrowatch.com/table.php?distribution=redhat)

---

### Post by CharlesA on 2010-11-11
> **snowpine said:**
> RHEL 6 is roughly equivalent to Fedora 12, Debian Squeeze (not Lenny!), or Ubuntu 10.04 in the "freshness" of its packages:

[http://distrowatch.com/table.php?distribution=redhat](http://distrowatch.com/table.php?distribution=redhat)

Awesome. I will look forward to trying out CentOS 6 when it comes out.

---

### Post by Khakilang on 2010-11-12
Fedora is ver 14 now. Why RHEL is only ver 6?

---

### Post by I'mGeorge on 2010-11-12
Hmmm RHEL or Fedora....what should it be ?! I think I'll flip the coin if it's tails it's RHEL if it's head I'll go with Fedora. Brrring, would you look at that it's tails he he, I never would had hoped for it on my two sided tails coin. :-)

---

### Post by nlsthzn on 2010-11-12
After the nightmare I had with CentOS 5 I will rather pass... *buntu all the way for me :D

---

### Post by CharlesA on 2010-11-12
> **Khakilang said:**
> Fedora is ver 14 now. Why RHEL is only ver 6?

Does the version number really matter?

RHEL 5 was released in 2007. 5.5 was released 8 months ago. 6 was released yesterday.

[https://access.redhat.com/support/policy/updates/errata/](https://access.redhat.com/support/policy/updates/errata/)

---

### Post by szymon_g on 2010-11-12
> **Khakilang said:**
> Fedora is ver 14 now. Why RHEL is only ver 6?

RHEL is based on Fedora; but Fedora is released approx. every 6-7 months, the last stable release of RHEL /excluding this one/ is more than 3 years old.

from Wiki:

* Red Hat Linux 6.2 &#8594; Red Hat Linux 6.2E
* Red Hat Linux 7.2 &#8594; Red Hat Enterprise Linux 2.1
* Red Hat Linux 9 &#8594; Red Hat Enterprise Linux 3
* Fedora Core 3 &#8594; Red Hat Enterprise Linux 4
* Fedora Core 6 &#8594; Red Hat Enterprise Linux 5
* Fedora 12 / 13 Mix &#8594; Red Hat Enterprise Linux 6

remember: producing good distro takes a time- there is alot of bug-hunting to do :) (i think devs of ubuntu should remember that)

---

### Post by kaldor on 2010-11-12
> **Khakilang said:**
> Fedora is ver 14 now. Why RHEL is only ver 6?

Fedora is progressive. It's cutting/bleeding edge and often has a lot of issues. They needed a place to work with and continue on.

Fedora 12 came out last year and Fedora 13 had some good additions. The base of RHEL 6 is Fedora 12 and some things from 13. RHEL is an enterprise-quality OS and cannot afford any issues or bugs. If they used Fedora 14 as a base it would be a mess.

RHEL's repositories are a little bit different than the others. One thing I notice is that Firefox 3.6.12 is the default browser in 5.5 which is based on Fedora Core 6. It keeps certain things up to date.

---

### Post by Dragonbite on 2010-11-12
> **Khakilang said:**
> Fedora is ver 14 now. Why RHEL is only ver 6?

Because they are different distributions their version numbers increment at a different pace.

It would be similar if Ubuntu LTS was released as a seperate distribution, then it would be *Ubuntu 10.10* and *Ubuntu LTS 3.1* (I think 6.06 would be 1, 8.04 would be 2 and 10.04 would be 3 so we would be at 3.1 since 10.04.1 is the current version).  You get the idea.

While technology flows from Fedora into RHEL, they are not 100% compatbile with each other. They are similar (like Ubuntu to Debian?), but there are differences that keeps them from being 100%.

---

### Post by Dragonbite on 2010-11-12
> **Khakilang said:**
> Is there a reason why you don't just use Ubuntu Server? 10.04 will be supported until April 2015.

I pulled out my Ubuntu LTS Administration book last nigth and now I'm flip-flopping between them (I do this all the time.. annoys the heck out of me ;) ).  It will probably end up with whatever I have available in front of me at the time.

I think the other hesitation I have going is I am uncertain about Ubuntu's future on the desktop with the proposed changes (and other things I've noticed, not just the Unity/Wayland issue) so I am not sure whether to put Ubuntu on the back-end if my front-end is possibly going to change, or not.  At least I know I'll have this Ubuntu on the front end for my desktop until 2012, and then decide to go LTS to LTS or not.

---

