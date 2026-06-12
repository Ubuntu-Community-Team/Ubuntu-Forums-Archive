---
title: "Ubuntu pro?!?!?!?!"
date: 2024-10-20
forum: Ubuntu, Linux and OS Chat
---

### Post by shadowtabby on 2024-10-20
Heyo,

I was watching a yt vid about what to do when you first get ubuntu, you know see if there is anything I like.  Then I hear about ubuntu pro, free for personal use.  My thoughts: "Eh what the heck, windows 10 and 11 pro 199+ ubuntu pro FREE for personal use and up to 5 devices." 

This was a nice suprise for me.

EVEN FOR 5 DEVICES!!!

---

### Post by deadflowr on 2024-10-20
*Thread moved to **Ubuntu, Linux, and OS Chat***

---

### Post by shadowtabby on 2024-10-20
Okies.

---

### Post by TheFu on 2024-10-20
Ubuntu Pro is mostly FUD.  There's nothing it adds that cannot be done without it.
It claims to provide support for selected Universe packages that otherwise wouldn't be supported.  I have doubts about that since if you use only LTS and supported desktop DEs, you'll upgrade every 2-3 yrs anyway.

FUD.  Feel free to read the marketing of Pro to learn more, if you like.  I've probably oversimplified the truth.

There's not such thing as a free lunch and don't expect that Pro is really free either.  Sure, you won't get billed, but there are other payments taken, you can be certain.
[https://www.howtogeek.com/902519/what-is-ubuntu-pro/](https://www.howtogeek.com/902519/what-is-ubuntu-pro/)  ... There are pros and cons.  Much of what Pro provides is is perceived value, which is great for Dilbert bosses.

On a 20.04 system that will lose standard support next June or July ....

```
$ pro status --all
SERVICE          AVAILABLE  DESCRIPTION
anbox-cloud      yes        Scalable Android in the cloud
cc-eal           no         Common Criteria EAL2 Provisioning Packages
esm-apps         yes        Expanded Security Maintenance for Applications
esm-infra        yes        Expanded Security Maintenance for Infrastructure
fips             yes        NIST-certified FIPS crypto packages
fips-preview     no         Preview of FIPS crypto packages undergoing certification with NIST
fips-updates     yes        FIPS compliant crypto packages with stable security updates
landscape        no         Management and administration tool for Ubuntu
livepatch        yes        Canonical Livepatch service
realtime-kernel  no         Ubuntu kernel with PREEMPT_RT patches integrated
ros              yes        Security Updates for the Robot Operating System
ros-updates      no         All Updates for the Robot Operating System
usg              yes        Security compliance and audit tools

This machine is **not attached** to an Ubuntu Pro subscription.
```

And 
```
$ ubuntu-security-status 
This command has been replaced with 'pro security-status'.
1805 packages installed:
     1315 packages from Ubuntu Main/Restricted repository
     438 packages from Ubuntu Universe/Multiverse repository
     43 packages from third parties
     9 packages no longer available for download

This machine is receiving security patching for Ubuntu Main/Restricted
repository until 2025.
This machine is NOT attached to an Ubuntu Pro subscription.
...
Universe/Multiverse packages until 2030. There are 28 pending security updates.

```
So, for a non-business user, which of those is actually useful? To me, looks like only the esm-apps and esm-infra stuff, maybe, but what does that actually mean?
438 packages might be getting patched that aren't.  That sounds scary.  But that isn't really true.  According to the next command, "There are 28 pending security updates".  That isn't nearly as scary, is it?  I tried to get a list of the packages that could be updated under PRO, but wasn't able to find the answer in 10 seconds.  Nothing has changed concerning what is and isn't already supported for 5 yrs for non-Pro connected systems.

_Liabilities in running an OS too long_
If you run an LTS longer than the standard support period which can be 3 or 5 yrs, depends on the DE involved, then Pro CAN make sense.  But delaying an OS upgrade bring s other liabilities regardless of support.  Everyone needs to choose for themselves whether some hassle every 3-4.5 yrs is worth it, or a big hassle every 8-9.5 yrs is better.  What I've seen is that delaying OS upgrades makes the changes huge and people lose skills by delaying to the point that they become fearful of any change at all.  In a business, where professionals have a mix of systems to manage, delaying upgrades won't impact skills usually. There will be new systems going in with each new LTS release, so that knowledge will be captured.  However, migrating a 16.04 LTS+Pro system to 26.04 when it comes out in a few years will be a much harder task because of all the changes.  In fact, for enterprise software, applications usually take at least a year before they become available, so the upgrade won't be to 26.04, but the 24.04 and it will likely be a *wipe and install*  process, not an upgrade.  There are a few people who claim to "upgrade" lts-to-lts-to-lts-to-lts-to-lts.  I have doubts.  I've never had that work more than 2 times myself.  When it fails, the solution is a clean wipe and fresh OS load, then reinstall all the applications that were there previously.  Perhaps I'm just unlucky or stupid. Hard to know which.

In a business, it isn't a hard choice.  Pro makes good sense.  Your boss would expect it and expect to pay.

Anyway, those are the realities.  There are articles with the few negatives that Pro requires, like individual system tracking.  Is that a negative for you?  Hard to say.

---

### Post by ian-weisser on 2024-10-20
Withdrawn.

Mooted by prior edit.

---

### Post by grahammechanical on 2024-10-20
I would like to offer a use case for a home user to subscribe to Ubuntu Pro.

I purchased a OEM laptop with Ubuntu 20.04 LTS pre-installed. All the hardware was fully functional. The keyboard had a backlight and the colour could be changed. There were other functions that the keyboard could do.

What would happen when I upgrade to Ubuntu 22.04 LTS? I decided to find out by dual booting with Ubuntu 22.04 LTS. The extended functions of the keyboard did not work. Linux did not have the supplier provided keyboard driver. I subscribed to Ubuntu Pro for the 20.04 LTS install and got peace of mind whilst I worked out how to get that driver installed.

Since then I have worked out a method for installing the keyboard driver on 22.04 LTS and 24.04 LTS. The driver will not compile with the kernel in 24.10. What will happen when I need to upgrade to Ubuntu 26.04 LTS. Who knows! So, I might just subscribe to Ubuntu Pro for 24.04 LTS. I am 76 years old and with Ubuntu Pro 24.04 LTS might still be in support when my life support has ended. Who knows?

So, even for home users being on a supported release is not always as simple as upgrading from LTS to LTS.

Regards

---

### Post by TheFu on 2024-10-20
> **grahammechanical said:**
> So, even for home users being on a supported release is not always as simple as upgrading from LTS to LTS.

Excellent points for consideration.

---

### Post by pantazi on 2024-10-22
This is my quandary.  I am running a rock solid Ubuntu 20.04 on my laptop and similarly on my non-techie wife's. Perfect for our requirements.

I have been testing 22.4 in a VM but can't see any advantage for us.  I see what The Fu is getting at regarding delaying upgrades, I too am 76 so would just adding Pro be sufficient, or  upgrade to 22.04 plus Pro for longer life?   24.04 with Wayland seem unnecessary for my situation (average user, but not averse to experimenting a little).

---

### Post by grahammechanical on 2024-10-22
I think that I understand what The Fu was getting at. I thought that he was saying that Ubuntu Pro was not necessary because we can upgrade from one LTS release to the next and in that way be using a supported version of Ubuntu. I agree with that point of view.

I was the one saying that there could be a special use case that might make Ubuntu Pro useful for the home user. I was speaking from my own experience.

As regards the situation that your wife and yourself are in. It is for you to make the decision. It is not for us to tell you what decision to make. Subscribing to Ubuntu pro will extend support for Ubuntu 20.04 beyond April 2025 to April 2030. You get to continue using the user interface that you are both familiar with. 

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

That might be just what you and your wife want. What happens beyond April 2030? Who can say? Except to say that unless there are serious changes we can expect Ubuntu 30.04 to be an LTS release. The future is unknown because it has not yet happened.

Regards

Edit: Mis-typed 2030 as 2020. OOPS!

---

### Post by pantazi on 2024-10-22
Thank you for your view grahammechanical.   Sure, I don't want anyone to make a decision for me and I think I have made up my mind in any case.

Regards.

---

### Post by TheFu on 2024-10-22
I thought of another consideration.  Older GPUs often lose support (thanks nvidia!), so newer kernels aren't compatible with drivers created for the older kernels.  By going with a PRO entitlement on that specific system, 5 more years of a working GPU could be possible.  Obviously, for a gamer, this is blasphemy, but for all the rest of us who just want an image displayed at our preferred resolution, having a GPU that works fine keep working 5 more years is a good thing.

Sadly, when I had a GPU lose support, the idea of ESM was just beginning, so I had to quickly buy a new GPU to re-gain support under newer OSes.  No way was I going to live with 1024x768 resolution when booting with the exact same GPU on a prior LTS supported 1920x1200 resolution without any difficulty.

Would I sign up for ESM/PRO to save $130?  Probably.  I wouldn't do it to save $30, however.  If my privacy is for sale, I want more perceived value.  Each of us has a price take for this trade off.  If you use Google Docs or Gmail, your price is much lower than mine.

---

### Post by davetheoldcoder on 2024-10-23
> **TheFu said:**
> There's not such thing as a free lunch and don't expect that Pro is really free either.  Sure, you won't get billed, but there are other payments taken, you can be certain.

What are these other payments?

---

