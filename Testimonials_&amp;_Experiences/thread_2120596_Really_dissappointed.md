---
title: "Really dissappointed"
date: 2013-02-26
forum: Testimonials &amp; Experiences
---

### Post by oxman on 2013-02-26
My 12.04 software updates are more and more difficult to perform. I've used ubuntu from the beginning and red hat before that starting in 96. I have enjoyed years of ubuntu usage with great gratitude. But more and more lately it is getting bloaty. Software updates should be a piece of cake and they never are. It doesn't matter if I'm using the update manager, synaptic or cli. It really should be as simple as apt-get update and apt-get upgrade. You're loosing me. 

Good luck. I hope you find your path again.

---

### Post by carl4926 on 2013-02-27
I don't understand....

What exactly is the problem? You merely eluded to to an issue, but gave not explanation.

```
sudo apt-get update && upgrade
```

Not so difficult?

---

### Post by Topsiho on 2013-02-27
I just updated my 12.04, and it was the usual piece of cake :)
If it isn't for you anymore, then something must have happened.
One thing is that maybe your hard disk is getting full, with all the downloaded update files.
Those are easily got rid of with

sudo apt-get clean

Also some other hardware related possibilities come to my mind, as a failing hard disk, failing or not sufficient RAM, and possibly other issues.

For me Ubuntu still rocks, ever since I discovered the hedgehog :), and after I got used to Unity, which really is great.

Topsiho

---

### Post by Armann on 2013-02-27
Works fine for me, can you tell us what the problem is ?

---

### Post by fdrake on 2013-02-27
> **carl4926 said:**
> I don't understand....

What exactly is the problem? You merely eluded to to an issue, but gave not explanation.

```
sudo apt-get update && upgrade
```

Not so difficult?
I think that is what he means. What he is saying, if I am not wrong, he is saying that the othe managers , like theGUI update managers are kinda of confusing .

In part I agree with that , that is why I do not use other package managers like synaptics ot the new ubuntu softare center..
also Ubuntu soft. center is soo slow to load all the content.

---

### Post by Topsiho on 2013-02-27
I think the original poster has lots of experience using Linux generally, and Ubuntu specifically.
If he runs now into trouble I don't think that that is because he is new or so: something else must have happened, so that he now can't perform the usual updates, which he must have done for year after year.
As for me the updates are as easy as ever, using the same Ubuntu version, I think the problem is hardware related.

Topsiho

---

### Post by oxman on 2013-02-27
Hey, thanks for the replies.

Topsiho, you are correct. I have been using linux either cli or ubuntu gui for the better part of two decades. I have NOT run any windows systems for the same amount of time. I run strictly FOSS software on linux.

I am not confused at all by any method of updating or upgrading. All of my equipment is either custom for linux specifically  or commercial for linux only. This is the third time in a row that I have had to jump through long hours of hoops dealing with so called "unauthorized repositories PPA issues" or when they're the ubuntu precise main and still will not upgrade, or how about this one: No internet connection. Good grief. You just updated my package list. I am connected just fine of course. It's just one thing after another. Very frustrating and I don't have the time for it. It seems like an unholy mess. I'm thinking of reverting to mint. I hate doing it because I have been a loyal ubuntu fan for years.

---

### Post by dino99 on 2013-02-27
you does not say if you are doing rolling dist-upgrade all the way long, or follow  a more strict route.
i mean, the different releases has the bad ideas to left behind them some config files and borked settings that are able to disturb/confuse/break new system installation.
thats why doing fresh installation from time to time avoid bad adventures.
there are also some config folders that can be auto regenarated on boot (but with the default settings, so take care of your own tweaks or mails storing for example: .gconf, .local, .config, .gnome2

):P

---

### Post by varunendra on 2013-02-27
*Thread moved to **Ubuntu Testimonials & Experiences**.*

---

### Post by MadmanRB on 2013-02-27
Hmm, well truth be told I have had issues with updates in the ubuntu 12 series.
I fixed it with help from a fresh install.

---

### Post by Topsiho on 2013-02-27
First: I have to add that I nearly always do a fresh reinstall, with /home sitting in it's own partition, which I preserve during the install.

I have no extra PPA's installed. They sit in other servers, not Ubuntu ones, so a bad experience with them is not Ubuntu's fault.

I use the (a (?)) Dutch mirror for the repositories, and it is always fast and OK, even my new very fast internet connection cannot outrun it. You might try other mirrors than the standard one for your region.

You may try Mint of course, don't know why you shouldn't. I did too, but reverted back to Ubuntu. You could try Fedora, OpenSuse, and what not. I did and went back to Ubuntu.

So far a very happy Ubuntu user, especially after having tried other distro's, and having accustomed myself to the new Unity interface, which IS great ...

Real thing is you will be happy again using Linux ...

:)

Topsiho

---

### Post by stalkingwolf on 2013-02-27
Im having the same type issue with a sony vaio desktop.  everything is fine until the updates.  after restart wired internet is gone, shows disabled.  The last time i unplugged it removed the battery and the next morning was fine both times.

---

### Post by MutantJohn on 2013-02-27
Oh my God, I have had the worst internet connectivity issues with Ubuntu. That is definitely not one thing they've done well. Or at least, don't ever, ever try to use a USB plug-in wireless network adapter. That was so awful.

But other than that, Ubuntu was pretty sweet to me. I think I've also had errors or issues with PPAs before but never quite like the OP...

---

### Post by LestISleep on 2013-02-28
So far I am loving the 12 series.

:)

---

### Post by RoosterHam on 2013-02-28
I have experienced similar problems to OP. My problems came from repositories I had added for particular software I wanted (sometimes needed) and pointing to au sources that were quicker but simply lacked some repos. Since I committed to only installing LTS releases from 12.04 onward there has been enough progress in Gnu, general Linux and Ubuntu development that I no longer need to add repositories, I can get everything done with a 'standard' install. This may not be the case for others. I also just point to the global Ubuntu servers and get no problems.

I've also had problems with breaking connectivity (both generally and software sources) after an 'apt-get update && apt-get upgrade.' Now I have the following cycle. When an LTS is released, I plan backups of data and configs, including inventory of what I've installed. When the new LTS reaches 3 or 4 months old, I format and do a fresh install. 

Not saying it will work for everyone, just that it works for me. So far no breakages from the LTSes.

Just on a random note, I hate the Software Center. Slow and IMO only half of what it could be. apt-get is my friend.

---

### Post by stalkingwolf on 2013-03-01
the only usb wireless adapter i have found to work is so outdated as to be almost useless.

---

### Post by Hellfirept on 2013-03-04
True. I had some issues too with the updater. Only solved them with a fresh install.
Noob problem-solving strategy! :P

---

### Post by Topsiho on 2013-03-04
> **MutantJohn said:**
> Oh my God, I have had the worst internet connectivity issues with Ubuntu. That is definitely not one thing they've done well. Or at least, don't ever, ever try to use a USB plug-in wireless network adapter. That was so awful.

I use these for some years now, and they work fine. I now use an 150N adapter, and it's great.

So you can not generalise your negative experiences.

This particular adapter did not work at all initially, but after Ubuntu 10.04, or was it 11.04, it worked great. The trouble was that the chipset used was very new, and not yet supported, but now it is. And so it happens generally: very new hardware has to wait until it is properly supported in a new kernel.

And this may apply not only to USB adapters, but to any device, external or internal. USB has nothing to do with this.

Topsiho

---

### Post by kurt18947 on 2013-03-04
> **Topsiho said:**
> I use these for some years now, and they work fine. I now use an 150N adapter, and it's great.

So you can not generalise your negative experiences.

This particular adapter did not work at all initially, but after Ubuntu 10.04, or was it 11.04, it worked great. The trouble was that the chipset used was very new, and not yet supported, but now it is. And so it happens generally: very new hardware has to wait until it is properly supported in a new kernel.

And this may apply not only to USB adapters, but to any device, external or internal. USB has nothing to do with this.

Topsiho

Exactly.  With WiFi (or a lot of hardware) I like recent but not brand new.  Judicious selection of wifi devices makes for a stress free ride.  Pick the wrong adapter and oh boy.  The upside to this is that once a device is supported, it seems to remain supported for a good long time.

---

### Post by oxman on 2013-03-05
Well case in point. I purchased a new printer today. HP officejet 4620. Can't get the drivers installed because of dependencies. The dependencies are not in the repose. That's rediculas. Why should a person spend all day trying to meet depencies that should be in the repositories. Like cups-devel and a libusb that will work with the printer. That's blah. I mean its not like its an off brand for crying out loud.

---

### Post by mastablasta on 2013-03-05
i think the drivers are in repositories.

---

### Post by carl4926 on 2013-03-05
[http://hplipopensource.com/hplip-web/models/officejet/officejet_4620_series.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_4620_series.html)

HPLIP should install as easy as plug and play from the repos

---

### Post by Elfy on 2013-03-05
Closed.

---

