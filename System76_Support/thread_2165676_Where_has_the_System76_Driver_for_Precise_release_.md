---
title: "Where has the System76 Driver for Precise release gone?"
date: 2013-08-05
forum: System76 Support
---

### Post by NathanZal on 2013-08-05
The System76 driver ppa for the Precise Pangolin release--and all the other releases other than Raring-- as of this posting are gone from

[http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists](http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists)

The Raring driver won't install on Pangolin (the current LTS release, might I add). Synaptic reports it as "broken" when I try to install it. I've recently re-installed a fresh copy of 12.04 on my Pangolin Performance Version 6. Will I be forced to upgrade to Raring or will the Precise version reappear?

EDIT: I found version 3.2.7 here:

[http://planet76.com/repositories/](http://planet76.com/repositories/)

and installed the Debian archive that I found there. Note that the driver change log only goes up to 3.2.1. That should take care of my fingerprint reader, but following the instructions [here]("http://knowledge76.com/index.php/Restoring_Your_System") tries to add the non-existent Precise driver and needs to be fixed.

---

### Post by isantop on 2013-08-06
We don't officially support Precise. We only recommend running the latest version of Ubuntu.

---

### Post by NathanZal on 2013-08-06
> **isantop said:**
> We don't officially support Precise. We only recommend running the latest version of Ubuntu.

Really? Are you kidding me? You're kicking all the 12.04 **LTR** users to the curb and breaking their ability to re-install. Terrific. 

You're telling me that you DO NOT support *the current LTR* (which is what Precise is) once it's no longer the latest? That's an anti-customer decision. Surely maintaining a ppa channel of previous "unsupported" releases isn't that resource intensive. You've gone to the trouble of removing them, after all. 

You can at least update your Wiki to reflect this, so people will know.  

It looks like it's time for me to put Windows 7 on my panp6 and run Ubuntu in a VM. At least I'll be able to run the latest Nvidia drivers.

---

### Post by isantop on 2013-08-06
Because we use brand-new cutting edge hardware, we've found that the latest release will tend to be more stable and faster than older releases. I should point out that LTS releases aren't significantly more or less stable than normal releases. They're intended for businesses with large numbers of machines, and who can't update all of them every six months, and thus update them every two years instead, which is much more manageable.

The new PPA architechture is new for 13.04, and will be the new system going forward. Previous releases should use the drivers from planet76.com.

---

### Post by houstonbofh on 2013-08-08
Wow!  I am still somewhat surprised from the reaction to my laptop in the other thread and now this?

For the record, I am just now starting to migrate from 10.04 to 12.04 as there were stability problems up to now. (With gnome-panel)  And there are some major issues going forward with the step versions.  And you will have to support 12.04 for the server hardware, or you will see a big hit in sales.

Lastly, this does not seem like the company I dealt with a couple of years ago when I bought several laptops and servers.  At that time the support was beyond fantastic.  It was one of the reasons I have recommended you so highly to this point. (In one case to a client who wanted a Windows server, and yours was still the best value for the money)  Please tell me I am over reacting!

---

### Post by NathanZal on 2013-08-08
What System76 didn't tell you is that they no longer imbed any drivers in system76-driver. It's a dummy package that pulls in a bunch of stuff--not including the fingerprint reader, mind you--as packages distributed elsewhere. There are instructions about where to get the fingerprint reader buried in the wiki. There's also support for a system76-nvidia-driver package that pulls in the latest supported version of the Nvidia universal driver, if that's something you need. It's not the latest by a long shot, but it's about the best you can so. But that's all in 13.04. There is a Debian package on planet76.com (there's a link in my post) where you can find the old system76 driver and install it by hand. I did that and was able to get the fingerprint reader working again, although not as consistently as it did in the past.

I did the "migration" from 10.04 to 12.04 by saving the home directory on an external drive and then doing a clean install. If there's an upgrade path I wasn't able to find it. And going step-by-step through all the releases sounds like asking for trouble, frankly.

I found their terse unhelpfulness and their justification for brushing LTS users off the way they did as, frankly, ample evidence as far as I am concerned that they no longer want my business. Well, the feeling is mutual.

> **houstonbofh said:**
> Wow!  I am still somewhat surprised from the reaction to my laptop in the other thread and now this?

For the record, I am just now starting to migrate from 10.04 to 12.04 as there were stability problems up to now. (With gnome-panel)  And there are some major issues going forward with the step versions.  And you will have to support 12.04 for the server hardware, or you will see a big hit in sales.

Lastly, this does not seem like the company I dealt with a couple of years ago when I bought several laptops and servers.  At that time the support was beyond fantastic.  It was one of the reasons I have recommended you so highly to this point. (In one case to a client who wanted a Windows server, and yours was still the best value for the money)  Please tell me I am over reacting!

---

### Post by octathlon on 2013-08-11
I am shocked to read this.  As a previous purchaser from System76 I was always very happy with their support, but that was a few years ago.  I always stick with LTS releases, and I would expect support on them for at least the 2 years until the next LTS is released.  That goes double now that intermediate releases have only a nine-month lifespan instead of 18 months. I never dist upgrade right when the new LTS release comes out, either-- I wait 2-3 months for the kinks to be worked out. I assume that most business customers value stability and would take a similar approach, so a policy of not supporting customers using the LTS six months after it came out is something that any potential customer should consider carefully before purchasing!

---

### Post by isantop on 2013-08-13
I apologize for the miscommunication. I see where I misspoke.

By "support" I don't mean technical support, I mean active driver development. By the time new releases come out, the LTS release has had all bugs fixed, and in general will no longer require additional patches. 

Running an LTS will not void your technical support policy.

---

### Post by houstonbofh on 2013-08-13
However, trying to install 12.04 on a new Lemur Ultra Thin, and your on your own?  Really?  Then why not just buy it from Clevo, if I have to find the drivers myself?  If this sounds a little cold and callus, than you are hearing it right.  You are hearing what I heard from your end about folks wanting to stay on an LTS.  It is far from the service I got from Janella Bonner back in 2010.  Of from Carl Richell in 2009.  This is very sad...

---

### Post by hawkmage on 2013-08-13
Ubuntu 12.04 is 16 months old, this would be like Dell or Lenovo not supplying drivers for Windows 7 or a better example HP still providing drivers for Red Hat Enterprise 4 on their servers.

I can understand dropping unsupported versions of Ubuntu but there should be an install package for each supported version of the OS available through it own update channel.

---

### Post by octathlon on 2013-08-17
To clarify, are all hardware features of System76 models at time of sale guaranteed to work with the current LTS version or not? even if one or more non-LTS versions had been released when the model went on sale?

---

### Post by isantop on 2013-08-20
No, models are only compatible with the current and future versions at the time of their release. That doesn't mean you can't try and install them, however we can't provide drivers for them and we can't offer technical support for hardware problems that arise. It won't void your hardware warranty, and we'll continue to provide technical support for future installations of supported versions.

---

### Post by houstonbofh on 2013-08-23
> **isantop said:**
> No, models are only compatible with the current and future versions at the time of their release.
12.04 is a current version.  So is 10.04 for a bit longer, but I can forgive that.  But not supporting the latest LTS is a joke.

And, others can.  I guess the replacement for my Lemur Ultra 2 when it dies will be an UltraLap.  [http://zareason.com/shop/UltraLap-430.html](http://zareason.com/shop/UltraLap-430.html)
It can come installed with;
Ubuntu 13.04
Ubuntu 12.04
Kubuntu 13.04
Edubuntu 13.04
Debian 7
Linux Mint 15
Fedora 19

I am willing to pay more for Linux support.

It is really disappointing, because I really liked your hardware and used to really like your support.  This is for several Eland Pro servers, and a few laptops.  But apparently, you do not want my business.

---

### Post by Welly Wu on 2013-08-25
I re-installed Ubuntu 12.04.3 LTS 64 bit and I used the Planet76 repository to install the System76 device driver. It installed the Barossa device driver for my SDXC card slot just fine. I think that's all I need right now. I still have faith in System76.

---

### Post by houstonbofh on 2014-01-11
Just to add insult to injury...  (And yes, I found it quite insulting...)
[http://carlrichell.com/post/44549453930/lts-should-die](http://carlrichell.com/post/44549453930/lts-should-die)

---

### Post by Jason_Gibson on 2014-01-15
[http://carlrichell.com/post/44549453930/lts-should-die](http://carlrichell.com/post/44549453930/lts-should-die)

I think its great. Where is the problem with moving to a rolling release. LTS is the old way of doing things and it shows. I would rather have features as they become available instead of held up until they have a big package of them. Trickle them out slow so they can be worked on as they go instead of one big release that usually causes a mess of problems because its a big blob that wasn't tested properly. You would honestly prefer to be on a LTS schedule and whine about new releases instead of always being updated with the newest stuff?

Servers I agree, but for servers you really should be using Debian / CentOS / Redhat. Anyone using Ubuntu, whether LTS or not is asking for trouble to begin with as far as servers are concerned. That is just my experience with it though. Bring on the rolling release desktop. Much easier for almost every other customer except the few because then they will always be updated as they normally do it, not having to go through a potential nightmare of a dist-upgrade.

*EDIT* In the end it isn't hard to backup your /var/cache/apt/archives/system76-driver????.deb file and run it manually. Anyone who understands enough about LTS and release cycles should be able to do this without issue.

---

### Post by joe4ska on 2014-01-18
By now 12.04.3 technically speaking is the current version and supports the backlight and card reader in my Lemur Ultra rev 4. But if you need it you can always download the latest and previous drivers at[ via their wiki]("http://knowledge76.com/index.php/System76_Driver").

---

