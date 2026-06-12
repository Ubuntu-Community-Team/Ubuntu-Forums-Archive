---
title: "ubuntu-release-upgrader should purge PPA's"
date: 2016-07-11
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2016-07-11
I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1602052](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1602052)

I didn't know how to properly mark it as a "wish list" bug :redface:

Anyway, if you agree, please adorn with the appropriate bells and whistles  :)

Maybe if someone here is a member of the paper cuts team they could nominate it for addition to the most wanted 100 culprits.

---

### Post by ian-weisser on 2016-07-11
I think you should bring it up in the ubuntu-devel mailing list.
That will quickly generate more heat and interest.

---

### Post by mc4man on 2016-07-12
> **kansasnoob said:**
> I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1602052](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1602052)

I didn't know how to properly mark it as a "wish list" bug :redface:


Only those with proper permissions can alter the Importance of a report so nothing you could do there. You could tag if desired.

Auto purging or setting (purging all ppa's) as a requirement is not practicable,   at best a warning would be good though Ubuntu seems reticent about using/extending  them (warnings

---

### Post by ventrical on 2016-07-12
It already disables them on upgrade. So what would be the point in purging them?

---

### Post by kansasnoob on 2016-07-12
> **ventrical said:**
> It already disables them on upgrade. So what would be the point in purging them?

There is a huge difference between disabling them and purging them. If you use a PPA to install and/or upgrade certain packages and then disable the PPA those changes remain. You just won't get any updates the PPA owner might provide.

A good (and simple) example would be nautilus in the gnome3 PPA. It upgrades nautilus and a few deps to 3.18 but Ubuntu's bog standard is 3.14*. If not actually purged the version of nautilus provided by that PPA is newer than the version currently available in Yakkety I believe so a Xenial -> Yakkety release upgrade may very well fail mid-stream.

---

### Post by mc4man on 2016-07-12
> **ventrical said:**
> It already disables them on upgrade. So what would be the point in purging them?

If one has packages that are a higher version then the upgrade process will leave them. In some cases this could be either ok or not that big of a deal. In some other instances it will be a bigger issue, for instance if one had higher but now incompatible mesa libs. So purging is the only way to reyurn to current package versions that will be upgraded.

Generally when a ppa has such packages it explicitly notes on the page that it must be purged before upgrading releases. (or should
 Some users never read, some forget, many others never ever go to the ppa page. The later is due to them being give a command to install vs. being directed to the page. This is quite common on blogs/sites where the writer/runner thinks more about benefit to their page than the user 
(omg ubuntu is prime example of one

---

### Post by ventrical on 2016-07-12
so it is major bug then I think. Nvidia driver also breaks when upgrading from wily ubuntu desktop to xenial. Plymouth give me the four dots plus two exclamations marks !! and a small square with an X through it. I cant file bug just yet .. forums are real slow to post again.

---

### Post by mc4man on 2016-07-12
> **ventrical said:**
> so it is major bug then I think. Nvidia driver also breaks when upgrading from wily ubuntu desktop to xenial. Plymouth give me the four dots plus two exclamations marks !! and a small square with an X through it. I cant file bug just yet .. forums are real slow to post again.
Don't see that, more of an informational deficiency at best. 
As far as nvidia drivers it's likely best to remove them before doing a release upgrade.

---

### Post by ventrical on 2016-07-12
> **mc4man said:**
> Don't see that, more of an informational deficiency at best. 
As far as nvidia drivers it's likely best to remove them before doing a release upgrade.

yeah .. for us the testers it's a slice .. What about the noobs and new converts .. when they go to use the automated upgrader and it breaks their install?

regards..

---

### Post by zika on 2016-07-13
> **ventrical said:**
> yeah .. for us the testers it's a slice .. What about the **noobs and new converts** .. when they go to use the automated upgrader and it breaks their install?
regards..They use such PPA's? That is oximoron... ;)
If they do then they are to be blamed. Do not use stuff that You do not understand fully... But, still, I think that they do not ...

---

### Post by mikodo on 2016-07-13
> **zika said:**
> They use such PPA's? That is oximoron... ;)
If they do then they are to be blamed. Do not use stuff that You do not understand fully... But, still, I think that they do not ...

That seems an un-charitable stance to take. 

I am sure there are many casual users who use PPA's for any number of reasons, who do not know of these consequences in a full release upgrade. Many people casually allow updates && upgrades and have no understanding to what is happening behind the scenes and probably those who are new and casual users of Ubuntu most likely are a larger percentage of people that fit in that category. It is the way they do things often in this stage of learning how to administrate their Linux install.

 I agree that something should be done, to not allow them to make these unknowing mistakes. Where is the harm in helping these people out?

---

### Post by ventrical on 2016-07-13
@Mikodo

The fact that they are ticked off in software as per my previous post [http://ubuntuforums.org/showthread.php?t=2330465&p=13516491#post13516491](http://ubuntuforums.org/showthread.php?t=2330465&p=13516491#post13516491)  is a good starting point. But to ask new users not to try anything in the form of ppas or be scolded for not knowing their linux basics is not the way to bridge this gap. We then might all have static forensic installs .

Regards..

---

### Post by ventrical on 2016-07-13
> **zika said:**
> They use such PPA's? That is oximoron... ;)
If they do then they are to be blamed. Do not use stuff that You do not understand fully... But, still, I think that they do not ...

Installing the proprietary nVidia driver is not from a ppa. Now , after a release-upgrade from Wily to Xenial I get the nVidia logo (unbelievable) just after plymouth which now has relics:)

regards..

---

### Post by mikodo on 2016-07-13
> **ventrical said:**
> @Mikodo

The fact that they are ticked off in software as per my previous post [http://ubuntuforums.org/showthread.php?t=2330465&p=13516491#post13516491](http://ubuntuforums.org/showthread.php?t=2330465&p=13516491#post13516491)  is a good starting point. But to ask new users not to try anything in the form of ppas or be scolded for not knowing their linux basics is not the way to bridge this gap. We then might all have static forensic installs .

Regards..
huh?

---

### Post by zika on 2016-07-13
> **mikodo said:**
> That seems an un-charitable stance to take. 
I am sure there are many casual users who use PPA's for any number of reasons, who do not know of these consequences in a full release upgrade. Many people casually allow updates && upgrades and have no understanding to what is happening behind the scenes and probably those who are new and casual users of Ubuntu most likely are a larger percentage of people that fit in that category. It is the way they do things often in this stage of learning how to administrate their Linux install.
I agree that something should be done, to not allow them to make these unknowing mistakes. **Where is the harm in helping these people out?**Not a good way of making conversation is to put untold words in someone's mouth... Where did I say not to help them? I just said:> **zika said:**
> They use [SIZE=4]**such**[/SIZE] PPA's? That is oximoron... ;)
If they do then they are to be blamed. Do not use stuff that You do not understand fully... But, still, I think that they do not ...

---

### Post by zika on 2016-07-13
> **ventrical said:**
> Installing the proprietary nVidia driver is **not from a ppa**. Now , after a release-upgrade from Wily to Xenial I get the nVidia logo (unbelievable) just after plymouth which now has relics:)
regards..So that case is off-topic here? Topic name is: **ubuntu-release-upgrader should purge PPA's **or am I wrong...?

---

### Post by zika on 2016-07-13
> **kansasnoob said:**
> I filed a bug report:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1602052](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1602052)
I didn't know how to properly mark it as a "wish list" bug :redface:
Anyway, if you agree, please adorn with the appropriate bells and whistles  :)
Maybe if someone here is a member of the paper cuts team they could nominate it for addition to the most wanted 100 culprits.I would (and did) support the idea to stop/pause and give user opportunity to do purge himself because some PPA's are not friendly when purge is in order and only those are essentially topic here as far as I can see... Anything more and we are back to square one as we have already been several times this same topic occured here...

---

### Post by ventrical on 2016-07-13
> **zika said:**
> So that case is off-topic here? Topic name is: **ubuntu-release-upgrader should purge PPA's **or am I wrong...?

My bad..

 I was speaking in the larger scope..

regards..

---

### Post by grahammechanical on 2016-07-13
Would the purge command actually do a batch purge of PPAs? Does APT work with wild cards? It might be possible to create a batch script for Launchpad PPAs but how would something like the Google Chrome PPA be handled. Non standard PPA URLs.

And there is something else that we have never tested. Upgrading with snap packages installed. That test is yet to come. In theory the snap app should not be affected by upgrading to a newer version of Ubuntu. As I understand things, snaps will make PPAs unnecessary.

This bug report might just be another one of those bugs that never get fixed because Time, Linux & Ubuntu have marched on.

Regards.

---

### Post by kansasnoob on 2016-07-14
> **zika said:**
> I would (and did) support the idea to stop/pause and give user opportunity to do purge himself because some PPA's are not friendly when purge is in order and only those are essentially topic here as far as I can see... Anything more and we are back to square one as we have already been several times this same topic occured here...

I think that may be the wisest approach. We already notify that the PPA's will be disabled, so if we simply added a prominent warning that it may be best to actually purge any and all PPA's currently or previously used then we could at least say, "we told you so".

I realize that's not ideal but I've been tossing this around in my head and there are numerous obstacles, like; (1) a reboot is often needed following a ppa-purge, so if multiple PPA's are purged the upgrader would have to call for a reboot after each purge, (2) as previously mentioned it may be necessary to also purge previously used PPA's whether they've been disabled or purged, etc, etc.

If we did include a warning then we'd need a wiki page with some detailed info. I'll have to put my thinking cap on there :-k

---

### Post by kansasnoob on 2016-07-14
> **mc4man said:**
> If one has packages that are a higher version then the upgrade process will leave them. In some cases this could be either ok or not that big of a deal. In some other instances it will be a bigger issue, for instance if one had higher but now incompatible mesa libs. So purging is the only way to reyurn to current package versions that will be upgraded.

Generally when a ppa has such packages it explicitly notes on the page that it must be purged before upgrading releases. (or should
 Some users never read, some forget, many others never ever go to the ppa page. The later is due to them being give a command to install vs. being directed to the page. This is quite common on blogs/sites where the writer/runner thinks more about benefit to their page than the user 
(omg ubuntu is prime example of one

You nailed it! People see a nifty headline "how to run the latest GNOME DE in Ubuntu GNOME version#whatever" and they just jump on it. Then two years later they give it no thought.

I play with a lot of PPA's in the process of testing, but the 50+ individual PC's I actually maintain for others get very few packages form PPA's. Only stuff like 'hal' or the 'caffeine' screensaver inhibitor.

A good off-topic comparison would be seeing how many people have installed adobe-flash properly. I find that the vast majority have installed using a method that results in them not getting the latest version from the repos. Luckily more & more sites block flash playback if the player is not up to date.

---

### Post by zika on 2016-07-14
> **grahammechanical said:**
> In theory the snap app should not be affected by upgrading to a newer version of Ubuntu. As I understand things, snaps will make PPAs unnecessary.[img]http://ubuntuforums.org/customavatars/avatar690937_24.gif[/img]

---

