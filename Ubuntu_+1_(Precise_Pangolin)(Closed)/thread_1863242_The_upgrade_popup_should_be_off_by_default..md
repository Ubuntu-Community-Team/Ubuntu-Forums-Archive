---
title: "The upgrade popup should be off by default."
date: 2011-10-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by madjr on 2011-10-17
trying to grab devs attention about the **risks of upgrading** (seems most are un aware...).

A better proposal to keep **bad/problematic upgrades** down to a minimum (specially in pp cycle) for new users who have no fall backs and only 1 OS on their computers:

**proposal/bug report: Upgrading Ubuntu is risky**
[https://bugs.launchpad.net/bugs/876146](https://bugs.launchpad.net/bugs/876146)

anyone interested please add themselves to the bug report.


reference: thread for failed upgrades
[http://ubuntuforums.org/showthread.php?t=1858475](http://ubuntuforums.org/showthread.php?t=1858475)


ps. please review bug report prior commenting, thanks.

---

### Post by Atamisk on 2011-10-17
I think one user's suggestion to focus on installation/upgrade bugs is an appropriate one. Instead of hiding the button, just make it *work*. However, i like the idea of warning that upgrading is *always* risky business and that one should only attempt to upgrade if they've got the time to work out a breakage.

---

### Post by madjr on 2011-10-17
> **Atamisk said:**
> I think one user's suggestion to focus on installation/upgrade bugs is an appropriate one. Instead of hiding the button, just make it *work*. However, i like the idea of warning that upgrading is *always* risky business and that one should only attempt to upgrade if they've got the time to work out a breakage.

"Make it work" would be ideal, but is not really possible in the short term.

Specially, when you have **no automated tool to send feedback** of how many upgrades go bad and why...

**Fall-backs** is the only warranty to keep **at least 1 usable OS** on the machine: backups, system restore, install to new partition and keep old one, etc.

---

### Post by Gyokuro on 2011-10-17
Upgrades are always risky and should be never done without proper backups. The warning is an good idea but want help in case the whole update/upgrade procedure is not bullet proof tested. Search in the forums where users have lost all their emails due to the change - evolution to thunderbird. That is kind of work which must have a high priority and I think the time for such tests is too few in a 6 month release cycle.

---

### Post by madjr on 2011-10-17
> **Gyokuro said:**
> Upgrades are always risky and should be never done without proper backups. The warning is an good idea but want help in case the whole update/upgrade procedure is not bullet proof tested. Search in the forums where users have lost all their emails due to the change - evolution to thunderbird. That is kind of work which must have a high priority and I think the time for such tests is too few in a 6 month release cycle.

yes, we have a thread with a huge list of bad upgrades (link in the op).

the sooner the devs notice the issue the better, if we want "precise" pangolin to really be precise.

---

### Post by screaminj3sus on 2011-10-17
Users should be encouraged to do a clean install instead of upgrading. Upgrading isnt stable enough currently for it to pop up for everyone like that.

---

### Post by Atamisk on 2011-10-17
> **madjr said:**
> "Make it work" would be ideal, but is not really possible in the short term.

Specially, when you have **no automated tool to send feedback** of how many upgrades go bad and why...

**Fall-backs** is the only warranty to keep **at least 1 usable OS** on the machine: backups, system restore, install to new partition and keep old one, etc.

I agree fully. What i was trying to say was that 'hiding the button' is only a symptomatic fix. Eventually, you have make fixing the root cause a priority. I'm just a little worried that if it's hidden by default, nobody will ever be bothered to fix it. I understand that it might be a good idea short-term though. 

You bring up a good point about an automated tool. X and a full linux session is in RAM during an upgrade, so would this be terribly hard to implement?

---

### Post by ventrical on 2011-10-17
Well.. I am about to *upgrade* from (natty) to Oneiric under Edubuntu. The updater looks very confident. If it fails I will just reinstall Edubuntu 11.04.

I'll be back, either weeping or laughing :)

---

### Post by madjr on 2011-10-17
> **Atamisk said:**
> I agree fully. What i was trying to say was that 'hiding the button' is only a symptomatic fix. Eventually, you have make fixing the root cause a priority. I'm just a little worried that if it's hidden by default, nobody will ever be bothered to fix it. I understand that it might be a good idea short-term though. 

You bring up a good point about an automated tool. X and a full linux session is in RAM during an upgrade, so would this be terribly hard to implement?

There is a comment from developer Matthew (MPT) in the bug report. He agrees with an auto-feedback tool.

Still this topic will need to grab more attention, feedback and planning for a while.

anyone interested , please add themselves to the bug report, thanks.

---

### Post by ventrical on 2011-10-17
I'll get back when this upgrade is done installing. Even file a bug report if it fails.

---

### Post by ronacc on 2011-10-17
while I habitually upgrade as soon as the next cycles repos open and have yet to have one go so bad I could not recover I am not a newbe and I have had several go enough astray they left me only terminal access . I think atleast a warning and some advice for emergencies would be a very good thing .

---

### Post by ventrical on 2011-10-17
Yes , I agree with your experience. Back several months ago  somebody suggested I was just lucky. :) I dunno .. if I don't try it I don't know how to fix it if it is broken then, no?

---

### Post by beew on 2011-10-17
> **screaminj3sus said:**
> Users should be encouraged to do a clean install instead of upgrading. Upgrading isnt stable enough currently for it to pop up for everyone like that.

+1, and they definitely shouldn't be prompting users at the very day when a new rerelease comes out whatever one's view on upgrading. It takes at least a few weeks (and usually longer) for major bugs to get fixed for every new release, something like graphic drivers, for example, are almost always problematic at release.

---

### Post by ventrical on 2011-10-17
There were a lot of bell and whistles (all video taped) but it ended up a seamless install. Most of the pop-ups were f/ps. I don't understand it. Also if you are upgrading using wireless (broadcom) after the upgrade files are downloaded and the installer starts, it will kill the wireless. So near the end of the install it will start to pop up (broadcom erro , Adobe flash error.. etc.. just close those. stick in your eth0, sudo apt-get update - sudo apt-get bcmwl-kernel-source and it all updates. All settings are the same as with natty, firefox, compi etc.

 I'll post some vids tommorow .. but definetly some f/p bugs for sure .

---

### Post by cariboo on 2011-10-17
It seems some of us want things both ways, the independence to setup and use our install the way we want, and also to restrict users from updating to a new version, isn't that a bit contradictory?

We see users with problems with their version upgrades every release, why should things be different this time?

I haven't run an upgrade since the last LTS release, isn't there a link to the release notes, before you click the upgrade button? If there is, I think it should be more strongly worded for example:

***Before upgrading please read the release notes, as this may make your system unusable.***

---

### Post by PaulInBHC on 2011-10-17
I've been away from ubuntu for a couple of releases. I was pleasantly surprised when beta 1 installed without a hitch on my AMD/ATI box. I haven't really changed anything just updated as we went along.

I was surprised by the outcry over unity and the dash. I've been around since DOS and Apple II but I prefer a GUI. And I'm getting too old to remember commands.

My first reaction is to agree with the OP. On the other hand, I wonder how many people upgraded without a problem, or a minor problem, they do like unity, and do not post a thing? Maybe the silent majority is happily using OO and we only see the rants?

---

### Post by cariboo on 2011-10-17
@PaulInBHC, you hit the nail on the head, the happy users almost never post anything if they are satisfied with their new install, it's just the people with problems that post anything, and many of them are overly demanding, and once their problem is solved we usually never even get a thank you for the help.

---

### Post by madjr on 2011-10-18
> **cariboo907 said:**
> It **seems some of us want things both ways, the independence to setup and use our install the way we want, and also to restrict users from updating to a new version, isn't that a bit contradictory?**

We see users with problems with their version upgrades every release, why should things be different this time?

I haven't run an upgrade since the last LTS release, isn't there a link to the release notes, before you click the upgrade button? If there is, I think it should be more strongly worded for example:

***Before upgrading please read the release notes, as this may make your system unusable.***

@cariboo

not sure if you read the bug report, but it is not about "restricting users from updating".

Is actually about providing **more options, alternatives and more info**, instead of letting **non-technical** users upgrade on 1 click, without even reading anything or knowing how to at least get to a terminal(if they even know what it is) or even post a bug report.

**They are the ones that complain when things go downhill.**

So as Mark said, "precise" is about reducing the amount of problems/bugs people encounter... and this certainly includes breaking the primary or only OS of an un-savvy individual.

On the other hand, Technical users should have no problems trying to upgrade, as the options will remain there, but hidden for users who dont have necessary **skill, time, patience** to fix anything in case of a problem (which unfortunately is the majority in a distro like ubuntu).

In the bug report it was also suggested (by MPT himself) an auto feedback tool for both good and bad upgrades.

If you have suggestions (or anyone else), i advise you leave us some on the bug report, thanks.

---

### Post by cariboo on 2011-10-18
@madjr, I haven't read the bug report yet, and probably won't until I get back from work tomorrow, but the title of your thread suggest restricting users.

---

### Post by madjr on 2011-10-18
> **cariboo907 said:**
> @madjr, I haven't read the bug report yet, and probably won't until I get back from work tomorrow, but the title of your thread suggest restricting users.

oh no i wouldnt am not that ebil ! ;D

i think there is some confusion.

the "**popup**" am referring is this huge one that appears for everyone on day 1 (looks friendly and inviting but it has a dark secret!):


[IMG]http://www.thegeekstuff.com/wp-content/uploads/2008/12/1-upgrade.png[/IMG]


If you feel a better title might be needed, please go ahead.

---

### Post by cariboo on 2011-10-18
Maybe they should make the cancel button the default, then it would be up to the user. :)

---

### Post by ranch hand on 2011-10-18
> **cariboo907 said:**
> It seems some of us want things both ways, the independence to setup and use our install the way we want, and also to restrict users from updating to a new version, isn't that a bit contradictory?

We see users with problems with their version upgrades every release, why should things be different this time?

I haven't run an upgrade since the last LTS release, isn't there a link to the release notes, before you click the upgrade button? If there is, I think it should be more strongly worded for example:

***Before upgrading please read the release notes, as this may make your system unusable.***
I agree completely.  Restricting folks is not the way to go.

A warning is a good idea.

The 8.04 to 10.04 upgrade was well tested for a long time before the release of 10.04.  This maybe should become the norm for regular releases.

I am all in favor of letting folks ruin their own install.  That is their choice and their right to make that choice.  Giving them some information on which to make that choice is just plain being neighborly.

---

### Post by ranch hand on 2011-10-18
> **cariboo907 said:**
> Maybe they should make the cancel button the default, then it would be up to the user. :)
And a warning like;
"NOOBs this may seriously ruin your day"

above the OK button.

---

### Post by beew on 2011-10-18
> **cariboo907 said:**
> It seems some of us want things both ways, the independence to setup and use our install the way we want, and also to restrict users from updating to a new version, isn't that a bit contradictory?


How is it restricting while you can still upgrade by entering a simple command? No one should upgrade based on impulse because they are prompted by a popup, period (you need testing and backup to say the least) And I remember there are threads of guys hosting their systems because they had a bad day and clicked "ok" by mistake (there is no way to reverse it, "cancel" doesn't work once the process starts)

---

### Post by ventrical on 2011-10-18
Thanks you guys for all your input. Ok .. I go up this :am, started my Dell with the *new* Oneiric *upgrade* and .. just like Natty Narwhal testing - NO NETWORK! Last night the networked (wireless.eth0) were working fine.

  I took some vids of it. Very interesting .I'm sure all of you are familiar with those pop-ups.. I think I will make some addendums to the bug reports in question. There seems to be a lot of problems with the *upgrader*. 

One thing for sure is that it does not set out to jockey for current Network settings (especially with Broadcom ) and there is even a popup for this. It erroneously tells to  that adobe-flash cannot be installed, then tells you to file a bug report - and then installs it right out of the blue.

 For the most part it starts out  very clean and tailored - but when it gets to that Broadcom driver .. BOOM !! all E'll breaks loose - or so it seems.

 But for the most part the original install of Edubuntu Natty - was seamless.

---

### Post by ventrical on 2011-10-18
This is a vid of the last part of an upgrade from natty to oneiric. At the end I can be heard saying "seamless install" which it was not. (me, have high hopes!) :) Looks like the Broadcom drivers seem to persist to be an issue here - at least on some of my machines.

Please forgive the bad video quality . I'm really busy , up to my elbows so to speak.

thanks

it' s a 6 min video. I capped some other stuff - may use that in a bug report.

[http://www.youtube.com/watch?v=F0zIb8Ij9fY](http://www.youtube.com/watch?v=F0zIb8Ij9fY)

---

### Post by ronacc on 2011-10-18
My realtek 8185 wireless worked on the livecd but after reboot to oneiric I had to add a wireless connection with networking to get it up , it hadn't carried through to the install and it don't require an extra driver .

---

### Post by ventrical on 2011-10-18
Here is the start up process of the same said machine.

My apologies for being so boring.

[http://www.youtube.com/watch?v=m-IC70bql5o](http://www.youtube.com/watch?v=m-IC70bql5o)

---

### Post by ventrical on 2011-10-18
> **ronacc said:**
> My realtek 8185 wireless worked on the livecd but after reboot to oneiric I had to add a wireless connection with networking to get it up , it hadn't carried through to the install and it don't require an extra driver .

Thats exactly it. The *upgrader* tool does not seem to remember (or retain) the previous network settings (or drivers). I can't understand why it kept all the apps I downloaded on the previous version but did not select to recall the wireless drivers.

---

### Post by dino99 on 2011-10-18
What the past dist-upgrading have teach me:

- at first glance, dist-upgrading seems to be the easiest/fastest way
- but lot of old settings/configs/symlinks are left behind and make the system not working as it might (agree that such things might not exist)
- so now, before dist-upgrading, i prepare the new installation with unetbootin + mini-iso
- and finally boot with the usb stick to get a clean install: does not take more time and then i dont have to fight with false positive bugs

Thats what the "popup" should explain, instead of the magic click & break

---

### Post by 23dornot23d on 2011-10-18
I would prefer to see something similar to this .....

[IMG]http://img171.imageshack.us/img171/4637/buttons1upgrade.jpg[/IMG]



This way you should never end up with a system that does not work .......

Install 11.10 in the clean partition ...... if this works ..... ( We have a clean install on the disk that works )

If the install in the clean partition.should fail ......     ( We still have our main system untouched )

If we choose to upgrade after the clean install and it should fail ( We still have the first clean install that works )


[COLOR=Red][B]
Should we choose to upgrade without taking note of the warnings and it  fails ( Then its our own fault - as we have no options but to re-install  )



Which is the way it is now and many of these users below ...... have fewer options or a long process trying to recover things
[/B][/COLOR]

---

### Post by dino99 on 2011-10-18
> **23dornot23d said:**
> I would prefer to see something similar to this .....

[IMG]http://img171.imageshack.us/img171/4637/buttons1upgrade.jpg[/IMG]

You'll never be a Canonical marketer (be aware that can fail: wow you are saying ubuntu=crap, are you aware ?)

---

### Post by 23dornot23d on 2011-10-18
> 
wow you are saying ubuntu=crap, are you aware ?



I am saying nothing of the sort and do not put words into my mouth ...... 

( I am sure your marketing people can word it much better )



I am giving reasonable options ......... the list of failed upgrades is a record of what is happening now .......



Do nothing and you are guaranteeing the same in your next release ........

As the list below shows ..... this is what is happening now ..... ignoring it does not make it go away .......

---

### Post by ronacc on 2011-10-18
> **23dornot23d said:**
> I would prefer to see something similar to this .....

[IMG]http://img171.imageshack.us/img171/4637/buttons1upgrade.jpg[/IMG]



This way you should never end up with a system that does not work .......

Install 11.10 in the clean partition ...... if this works ..... ( We have a clean install on the disk that works )

If the install in the clean partition.should fail ......     ( We still have our main system untouched )

If we choose to upgrade after the clean install and it should fail ( We still have the first clean install that works )


[COLOR=Red][B]
Should we choose to upgrade without taking note of the warnings and it  fails ( Then its our own fault - as we have no options but to re-install  )



Which is the way it is now and many of these users below ...... have fewer options or a long process trying to recover things
[/B][/COLOR]

you wouldn't say that if you had been there when fiesty ate my dapper (main) install + everything on the other 3 drives in my box , thats why I test on a separate dedicated test box now . and when I update my "work" box to a new LTS I back up my data twice on 2 separate external drives which are not connected during install and wipe the internal drive and start fresh .

---

### Post by wgarcia on 2011-10-18
Having succeeded in all upgrades since 6.10 in 4 or 5 different machines, only 2 or 3 times I had to help the upgrade by some manual commands but I always succeeded in getting the upgrade finish, I must say that in any case I agree 100% with this thread as I know people who are completely lost and how easy it is to click "New version is available...". New users don't even know why this is different from other non-distribuion updates offered.

Here is my proposal for the wording:

This is a distribution upgrade to version 11.10.

Make a backup of your important data  before starting the upgrade.

Be sure to read the Release Notes before upgrading your system to see if there is any issue related to your system.

Choose an upgrade option:

-  Fresh install: this option creates a new, separate partition for the new version, and will allow you to try the new version without affecting your old installation. To finish upgrading, you can either transfer your data to your new installation or upgrade your existing installation.


- Upgrade your existing installation: this option will upgrade your existing installation. The process is thoroughly tested but be aware that the upgrade may fail and you may need technical support to access your old installation.

---

### Post by 23dornot23d on 2011-10-18
@ronacc

Your dead right ..... why change anything

I did exactly the same thing when I was younger .... countless OS's lost

and its still happening  for the newcomers ......

___________________________________

I Wonder why ..... 

If things don't change they will stay as they are ...... ;)

___________________________________

@wgarcia ( as your post  just cane in as I was typing )

I totally agree at least the wording needs to be changed .... to let new users know what they are letting themselves in for.
we all started by learning ..... its the ones that do not know 

It does not even state clearly this will overwrite your existing system and you can not recover back to it

Lots are asking for a Roll back .... whatever that might be .....

---

### Post by ventrical on 2011-10-18
I think effenberg had proposed somthing very similar.

---

### Post by PaulInBHC on 2011-10-18
I think some of the roll back requests are from those that don't like unity and don't understand that there are options.

---

### Post by 23dornot23d on 2011-10-18
Do you want to go onto the list and let them know the options then ....

There are still a lot unanswered ...... I am sure they would be glad of any advice to get there systems back ......

They are writing to let people know how many options they think they have

[]("http://ubuntuforums.org/showthread.php?t=1862287")

---

### Post by ventrical on 2011-10-18
> **PaulInBHC said:**
> I think some of the roll back requests are from those that don't like unity and don't understand that there are options.

 I like Unity. I think it's great - better than during my last beta test. But the upgrader has some probs. Who knows .. maby it's a conspiracy theory of sorts.  A broken upgrader will discourage a lot of noobs. I think thats the point . I think it's about bringing noobs into the fold.  I'm not complaining. it's just that it is so difficult to keep clients, working people who don't have time to spend on  configs - that just have work to do. Oh yeah .. for sure .. with any OS there are always probs with upgrades. Windows xp , security software .. Iv'e spent hours and hours trying to fix upgrade bugs there. also. But I don't think it would be too difficult to solve this problem and some of the proposals are pretty bright.

---

### Post by madjr on 2011-10-18
> **23dornot23d said:**
> I would prefer to see something similar to this .....

[IMG]http://img171.imageshack.us/img171/4637/buttons1upgrade.jpg[/IMG]



This way you should never end up with a system that does not work .......

Install 11.10 in the clean partition ...... if this works ..... ( We have a clean install on the disk that works )

If the install in the clean partition.should fail ......     ( We still have our main system untouched )

If we choose to upgrade after the clean install and it should fail ( We still have the first clean install that works )


[COLOR=Red][B]
Should we choose to upgrade without taking note of the warnings and it  fails ( Then its our own fault - as we have no options but to re-install  )



Which is the way it is now and many of these users below ...... have fewer options or a long process trying to recover things
[/B][/COLOR]

@23dornot23d

thanks for v0.01 of your mockup!

anyway if you like you can fix it a bit with the others feedback and bring it in to the [bug report]("https://bugs.launchpad.net/ayatana-design/+bug/876146")?

all ideas are welcome!

---

### Post by madjr on 2011-10-18
> **ventrical said:**
> This is a vid of the last part of an upgrade from natty to oneiric. At the end I can be heard saying "seamless install" which it was not. (me, have high hopes!) :) Looks like the Broadcom drivers seem to persist to be an issue here - at least on some of my machines.

Please forgive the bad video quality . I'm really busy , up to my elbows so to speak.

thanks

it' s a 6 min video. I capped some other stuff - may use that in a bug report.

[http://www.youtube.com/watch?v=F0zIb8Ij9fY](http://www.youtube.com/watch?v=F0zIb8Ij9fY)


@ventrical

thanks for sharing your experience. My brother had same experience and lost his wireless on his work machine, yeah he was pretty annoyed as he couldn't afford having it broken that day... he ended up spending  a few hours backing up and reinstalling the old version since he didnt had more Cds

now he will clearly avoid clicking on upgrade again...

if you want you can also add this to the bug report from this thread

Thanks

---

### Post by 23dornot23d on 2011-10-18
Possibly to a Flash disk as they are getting faster and more common ... 8 to 16 Gigs ... should suffice to test.

In six months time a lot can happen ...  version 2 ....... 

[IMG]http://img269.imageshack.us/img269/9044/buttons1upgradev002a.jpg[/IMG]

---

### Post by arpanaut on 2011-10-18
Although I agree with many of the concerns and suggestions in this thread and would like for the upgrade process be more seamless.
I think that offering "Try on a Fresh Partition"  probably would have a possibility for more confusion and troubles for an inexperienced user than first expected.

Such as:
What if the user already has four primary partitions used.
Where do you take the space for the new partition from... Windows? Ubuntu? Other? (could cause confusion)
What about separate /home? use existing or create another?
Vista and Seven don't like to be altered by gparted. (confusion and damage could result)
What about people that have disk space issues?
Where does Grub get installed? old install controls? new install controls? what if new install fails = more trouble for newbs.
This list could go on and on... given the many possible variables on an existing system.

Given Ubiquity's flakiness, and it balking in certain scenarios I've got to question this proposal as a "One Click Solution" I just think it would in many cases cause more confusion and problems for the inexperienced.

Now if this could be implemented in a maner that was nearly failsafe that would be great great!
I just think it may be a great deal more complicated than what appears at first glance.

Now, I am all for improvement in the upgrade process, I just see this as very difficult to bring to fruition.
I could be wrong.  Bottom Line it has to be easy for the inexperienced.

Great Ideas here, keep them coming!

---

### Post by madjr on 2011-10-18
> **arpanaut said:**
> Although I agree with many of the concerns and suggestions in this thread and would like for the upgrade process be more seamless.
I think that offering "Try on a Fresh Partition"  probably would have a possibility for more confusion and troubles for an inexperienced user than first expected.

Such as:
What if the user already has four primary partitions used.
Where do you take the space for the new partition from... Windows? Ubuntu? Other? (could cause confusion)
What about separate /home? use existing or create another?
Vista and Seven don't like to be altered by gparted. (confusion and damage could result)
What about people that have disk space issues?
Where does Grub get installed? old install controls? new install controls? what if new install fails = more trouble for newbs.
This list could go on and on... given the many possible variables on an existing system.

Given Ubiquity's flakiness, and it balking in certain scenarios I've got to question this proposal as a "One Click Solution" I just think it would in many cases cause more confusion and problems for the inexperienced.

Now if this could be implemented in a maner that was nearly failsafe that would be great great!
I just think it may be a great deal more complicated than what appears at first glance.

Now, I am all for improvement in the upgrade process, I just see this as very difficult to bring to fruition.
I could be wrong.  Bottom Line it has to be easy for the inexperienced.

Great Ideas here, keep them coming!

i agree with you on the confusion, but info solves confusion.

On the other hand any alternative mentioned here is better than seeing the **black screen of death** from an unbootable upgrade:
[http://ubuntuforums.org/showthread.php?t=1860359](http://ubuntuforums.org/showthread.php?t=1860359)

[IMG]http://farm4.static.flickr.com/3062/5777675155_a2bd843f6f.jpg[/IMG]

[IMG]http://www.windows7password.net/wp-content/uploads/2011/03/unbootable-150x150.jpg[/IMG]

---

### Post by ronacc on 2011-10-18
assuming a good cd to start with the main places that serious things seem to occur are things that require additional drivers or firmware and "non default" systems . perhaps the installer could scan for potential problems and bring up a warning if it finds any . I usually do 2 upgrades on my test box one from the system that has been through the wringers of testing the current release and one from a fresh install. I have never had a major problem with the fresh install , a few minor glitches like the wireless I mentioned above but nothing that locked me out of a gui .

---

### Post by Gyokuro on 2011-10-18
> **arpanaut said:**
> Although I agree with many of the concerns and suggestions in this thread and would like for the upgrade process be more seamless.
I think that offering "Try on a Fresh Partition"  probably would have a possibility for more confusion and troubles for an inexperienced user than first expected.

Such as:
What if the user already has four primary partitions used.
Where do you take the space for the new partition from... Windows? Ubuntu? Other? (could cause confusion)
What about separate /home? use existing or create another?
Vista and Seven don't like to be altered by gparted. (confusion and damage could result)
What about people that have disk space issues?
Where does Grub get installed? old install controls? new install controls? what if new install fails = more trouble for newbs.
This list could go on and on... given the many possible variables on an existing system.

Given Ubiquity's flakiness, and it balking in certain scenarios I've got to question this proposal as a "One Click Solution" I just think it would in many cases cause more confusion and problems for the inexperienced.

Now if this could be implemented in a maner that was nearly failsafe that would be great great!
I just think it may be a great deal more complicated than what appears at first glance.

Now, I am all for improvement in the upgrade process, I just see this as very difficult to bring to fruition.
I could be wrong.  Bottom Line it has to be easy for the inexperienced.

Great Ideas here, keep them coming!

One of the possibilities is to make use out of LVM and that's some kind of software which is not new and well tested. Which is flexible to even make a backup of the existing system and in case something goes wrong it can be switched back to old working state.

---

### Post by buzzmandt on 2011-10-18
How about a search of hardware and a statement if found. A ride along script to jockey maybe. ? > WARNING: Broadcomm chip found. Upgrading is NOT recommended

---

### Post by SeijiSensei on 2011-10-18
Might I suggest that in any instructions presented to potential upgraders, the first instruction be only to upgrade if there is some problem the upgrade actually solves for you?

Rather than techy-sounding "release notes" or breathless marketing speak about new this-and-that, I'd start by telling users that, in most cases, upgrading isn't necessary and presenting a list of things that might be resolved or improved upon by upgrading.

One of the the biggest problems with Ubuntu in my mind is the too-frequent release cycle.  I would actively discourage upgrades except to new LTS releases.  Tell users in no uncertain terms that upgrading is a potentially dangerous business and recommend that they download and run a LiveCD of the new version first to insure that upgrading won't break anything.

---

### Post by 23dornot23d on 2011-10-18
[COLOR=Blue]**@ **[/COLOR] **arpanaut**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11362195#post11362195")
[COLOR=Blue][B]
Such as:
What if the user already has four primary partitions used.

[COLOR=Black]Good Question ..... I did revise it to use a 8 - 16 Gig Flash drive

[IMG]http://img269.imageshack.us/img269/9044/buttons1upgradev002a.jpg[/IMG]

( reason in 6 months time they will be inexpensive and there is enough room on one to test out things you want to know - before overwriting your main system )
[/COLOR]
Where do you take the space for the new partition from... Windows? Ubuntu? Other? (could cause confusion)

[COLOR=Black]Not needed with a Flash Drive ...... but if the user has a 2 TB disk 20 Gig
is lost in its extended partition - and if UBUNTU installer is set up for this
20 Gig can be set aside for just this ....... ready ....... it only has to be done once ........ next time - it is there again for the same purpose ...... 
[/COLOR]
What about separate /home? use existing or create another?

[COLOR=Black]Its a great idea .... we automatically back the /home up if the USER requests it ........ some may not .......[/COLOR]

Vista and Seven don't like to be altered by gparted. (confusion and damage could result)

[COLOR=Black]Flash drive does not touch them ..... and the boot can be written to the Flash drive ...... its very handy ...... saved my setup when the main one dissappeared and the gparted reported unallocated space ..... still booted ok from the flash drive ......[/COLOR]

What about people that have disk space issues?

[COLOR=Black]Flash drive is their option then ......[/COLOR]

Where does Grub get installed? 

[COLOR=Black]Onto the Flash drive as previously stated ..... its a good backup .... too[/COLOR]

old install controls?
 new install controls?

 what if new install fails = more trouble for newbs.

[COLOR=Black]Then they know not to overwrite their main data ,,,,, alternatively ?

Leave it as it is ..... and what if it fails ...... see the list below ..... its not stopped growing yet ......
[/COLOR]
This list could go on and on... given the many possible variables on an existing system.

[COLOR=Black]The list can go on and on and I can give you answers for each and every one

The list below can go on and on too ..... 
( I belive it may have helped showing the problems and solutions - even that must have saved some repeats )

[COLOR=Red]You do not believe I spent 5 days solid tracking all of this just to say - ok ..... there is no solution
lets just carry on as before because it may be a little difficult ....... to sort out .....

Easy solutions you want just tell them ...... it is going to fail for some of them - but upfront

[COLOR=Black]This gave no indication that there was even the slightest chance of it failing ....

[IMG]http://img818.imageshack.us/img818/2209/welcometoupgrade.jpg[/IMG]


and the ask me later button did not work on my system ....


[/COLOR][/COLOR][/COLOR] [/B][/COLOR]

---

### Post by ventrical on 2011-10-18
> **madjr said:**
> @ventrical

thanks for sharing your experience. My brother had same experience and lost his wireless on his work machine, yeah he was pretty annoyed as he couldn't afford having it broken that day... he ended up spending  a few hours backing up and reinstalling the old version since he didnt had more Cds

now he will clearly avoid clicking on upgrade again...

if you want you can also add this to the bug report from this thread

Thanks

Ok.. I sort of had a deja vu experience here. With this Dell Inspiron B130 it has the b4318 broadcom wlan. What I did to pen up my network was to remove the bcmwl-kernel-source and I got my network back. Then , I had to remind myself that on this Dell I have to TURN ON the wireless MANUALLY. There is an Fn key along with a F key (F2) that had a picture of a little wireless tower on it. Once I turn that on the wireless pops right up!! 

  Now I think i am on track of what one of the true bugs really are  that could be happening with the upgrade installer. About a week ago one of my clientsLUCID was complaining about these multiple pop-ups of <screenshot-saver> that came up everytime she went into e-mail and hit the <shift>@ key (to enter in e-mail. It was a keyboard macro bug on the HP keyboard that was erroneous. The fix was to disable the  instances of shortcuts in the keyboard shortcut config.

  I think what is happening is the same things with some older systems with broadcom drivers. By default , during the *upgrading process* the upgrade turns off the wirless and, by default, does not (or cannot) turn it back on. It has to be done manually. Once the wireless is turned on manually then it is set in a cue and so when you power down it will not remove the cue bit and so boot normally into wirless - but I suspect that the bug could be with some of the keyboard settings.

This is what I wrote in another thread on the issue:

[http://ubuntuforums.org/showpost.php?p=11300139&postcount=62](http://ubuntuforums.org/showpost.php?p=11300139&postcount=62)

But now after the *upgrade* the wireless works on Oneiric.

 So as I see it, it is an actual fix of the old Natty bug - and I bet that doesn't make any sense at all :)


  Now .. to file some sort of cohesive and comprehensive bug report :)

regards, venrtrical

---

### Post by effenberg0x0 on 2011-10-18
Something like this would be much better:

[[ATTACH]204731[/ATTACH]

[ATTACH]204734[/ATTACH]

[ATTACH]204735[/ATTACH]

[ATTACH]204738[/ATTACH]

[ATTACH]204739[/ATTACH]

---

### Post by 23dornot23d on 2011-10-18
More Linux USERS ..... how do we do it ...... ?

Reduce the number of failures .....

Questions My turn 

1 . Upgrading ..... what reversal process is there in place once it goes wrong

2. How does a user know if his graphics card is going to work once installed

3. How does a user know his wireless is going to work once installed

4. At what point does the USER give up trying to fix the system and then do a clean install

5. For people that use servers and they cannot access them after due to losing the lan
how do they reset it up agsin.

6. What information is given on that first screen .... to let them know now is a good time to back up their system ..... 

and then does the USER really matter ....... UBUNTU has so many now and none are leaving ...... due to the upgrade going wrong .....

They do leave some good renditions of what happened though .... 

[http://ubuntuforums.org/showpost.php?p=11344331&postcount=16](http://ubuntuforums.org/showpost.php?p=11344331&postcount=16)

---

### Post by madjr on 2011-10-18
> **effenberg0x0 said:**
> Something like this would be much better:

[[ATTACH]204731[/ATTACH]

[ATTACH]204734[/ATTACH]

[ATTACH]204735[/ATTACH]

[ATTACH]204738[/ATTACH]

[ATTACH]204739[/ATTACH]

lol i think i'll go with the first one for now...

keep em coming (but less sarcasm lol)

---

### Post by Gyokuro on 2011-10-18
> **23dornot23d said:**
> More Linux USERS ..... how do we do it ...... ?

Reduce the number of failures .....

Questions My turn 

1 . Upgrading ..... what reversal process is there in place once it goes wrong

2. How does a user know if his graphics card is going to work once installed

3. How does a user know his wireless is going to work once installed

4. At what point does the USER give up trying to fix the system and then do a clean install

5. For people that use servers and they cannot access them after due to losing the lan
how do they reset it up agsin.

6. What information is given on that first screen .... to let them know now is a good time to back up their system ..... 

and then does the USER really matter ....... UBUNTU has so many now and none are leaving ...... due to the upgrade going wrong .....

They do leave some good renditions of what happened though .... 

[http://ubuntuforums.org/showpost.php?p=11344331&postcount=16](http://ubuntuforums.org/showpost.php?p=11344331&postcount=16)

point 2 and 3 can be checked at the beginning of the installation/upgrade process, it already checks internet connectivity and HD space

point 5: depends on hardware too - thanks iLO on HP 

point 6: there are really good suggestions in this thread

point 1: that's the hardest and maybe it's useful to analyse other OS's how this task get achieved on other systems

---

### Post by ronacc on 2011-10-18
We do need to remember that failed upgrade or installs are not a unique Ubuntu or Linux problem .Almost all of us have seen the carnage resulting from an attempted windows upgrade and even the recent upgrade of OSX 10.6 to 10.7 left a few hurting and apple goes to extremes to prevent that . The first thing the 10.7 installer tells you is to backup your system and even if you do it makes you a recovery partition and still people managed to hose their macs .

---

### Post by effenberg0x0 on 2011-10-18
[ATTACH]204742[/ATTACH] [SIZE=4]
Hello! It looks like
 you're trying to destroy 
your PC?

[SIZE=3]
Maybe if we had Clippy, instead of pure text, users would pay attention to the risk they are taking when they upgrade a system with no information whatsoever on what to do in case the process fails. [/SIZE][SIZE=3]As far as I know Clippy is currently unemployed.[/SIZE]


[/SIZE]

---

### Post by madjr on 2011-10-18
> **effenberg0x0 said:**
> [ATTACH]204742[/ATTACH] [SIZE=4]
Hello! It looks like
 you're trying to destroy 
your PC?

[SIZE=3]
Maybe if we had Clippy, instead of pure text, users would pay attention to the risk they are taking when they upgrade a system with no information whatsoever on what to do in case the process fails. [/SIZE][SIZE=3]As far as I know Clippy is currently unemployed.[/SIZE]


[/SIZE]

haha , what have u been drinking

---

### Post by madjr on 2011-10-18
> **ronacc said:**
> We do need to remember that failed upgrade or installs are not a unique Ubuntu or Linux problem .Almost all of us have seen the carnage resulting from an attempted windows upgrade and even the recent upgrade of OSX 10.6 to 10.7 left a few hurting and apple goes to extremes to prevent that . **The first thing the 10.7 installer tells you is to backup your system and even if you do it makes you a recovery partition and still people managed to hose their macs **.

that is a good start (much better than what we have now).

I'll be adding this to the report.

anyone has pics ?

---

### Post by arpanaut on 2011-10-18
@23dornot23d

I find your efforts commendable and was not trying to discount your proposal.
But was just trying to point out some gotchas that may present.

I do think that you presume too much to assume people have flash drives or usb drives, or all have the means to purchase such.(inexpensive or not) My comments were directed at the pitfalls of Installing to a NEW partition on the same drive, and the difficulties that would present to many.

Yes, something needs to be done to make upgrades nearly failsafe, but if it is made too complicated or time consuming, they are just going to push the upgrade button.
Yes, warnings, and options need to be communicated up front, but in reality how many are going to really pay attention. I have a friend who when he gets pop-ups always says yes just to get them off the screen... Never reads what they say. Yup! Windows Mindset, but that is what we are dealing with quite often on these forums.

Again I appreciate, and commend your efforts and am not trying to argue with you.
More power to you if you can make something happen.

Maybe an auto-backup built into the upgrade system or some kind of cloning system can be activated BEFORE the upgrade takes place?  I just think that auto-partitioning built into the upgrade system would have difficulty in predicting all user case scenarios.

Good Luck with your efforts!

---

### Post by ventrical on 2011-10-18
On the flip side .. it is sometimes a good thing to bork a system once in a while. Back where I come from, if you hadn't fried a MoBo or dissed an hdd then you were not worth your salt as an tech.

But that was then and this is now .. ahem.. :)

---

### Post by madjr on 2011-10-18
> **ronacc said:**
> We do need to remember that failed upgrade or installs are not a unique Ubuntu or Linux problem .Almost all of us have seen the carnage resulting from an attempted windows upgrade and even the recent upgrade of OSX 10.6 to 10.7 left a few hurting and apple goes to extremes to prevent that . The first thing the 10.7 installer tells you is to backup your system and even if you do it makes you a recovery partition and still people managed to hose their macs .

ok i found a few good links:

[http://www.macworld.com/article/161664/2011/08/hands_on_with_lion_recovery_disk_assistant.html](http://www.macworld.com/article/161664/2011/08/hands_on_with_lion_recovery_disk_assistant.html)
[http://reviews.cnet.co.uk/software-and-web-apps/how-to-recover-os-x-lion-50004503/](http://reviews.cnet.co.uk/software-and-web-apps/how-to-recover-os-x-lion-50004503/)
[http://cellocean.com/analysis/lion-recovery-disk-assistant-by-apple.html](http://cellocean.com/analysis/lion-recovery-disk-assistant-by-apple.html)
[http://maciad.com/news/os-x-lion-recovery-detailed](http://maciad.com/news/os-x-lion-recovery-detailed)
[http://osxdaily.com/2011/07/20/upgrading-to-mac-os-x-10-7-lion/](http://osxdaily.com/2011/07/20/upgrading-to-mac-os-x-10-7-lion/)
[http://drive-recovery-mac.blogspot.com/2011/08/lion-recovery-disk-assistant.html](http://drive-recovery-mac.blogspot.com/2011/08/lion-recovery-disk-assistant.html)
[http://www.sinfuliphone.com/showthread.php?t=85170](http://www.sinfuliphone.com/showthread.php?t=85170)
[http://www.macgasm.net/2011/06/13/reinstall-lion-disc/](http://www.macgasm.net/2011/06/13/reinstall-lion-disc/)
[http://whatstechnology.com/2011/08/mac-101-creating-a-recovery-disk-using-recovery-disk-assistant/](http://whatstechnology.com/2011/08/mac-101-creating-a-recovery-disk-using-recovery-disk-assistant/)

[IMG]http://cellocean.com/images/cm_images/11/August/3111_Lion-Recovery-Disk-Assistant-by-Apple-02.jpg[/IMG]

[IMG]http://cellocean.com/images/cm_images/11/August/3111_Lion-Recovery-Disk-Assistant-by-Apple-03.jpg[/IMG]

[IMG]http://www.cnet.co.uk/i/c/blg/cat/software/mac-os-x-lion-recovery/mac-os-x-lion-recovery-2.jpg[/IMG]

[IMG]http://www.cnet.co.uk/i/c/blg/cat/software/mac-os-x-lion-recovery/mac-os-x-lion-recovery-5.jpg[/IMG]

[IMG]http://www.foto.pk/images/recoveylio.png[/IMG]

---

### Post by 23dornot23d on 2011-10-18
> **arpanaut said:**
> @23dornot23d

I find your efforts commendable and was not trying to discount your proposal.
But was just trying to point out some gotchas that may present.

I do think that you presume too much to assume people have flash drives or usb drives, or all have the means to purchase such.(inexpensive or not) My comments were directed at the pitfalls of Installing to a NEW partition on the same drive, and the difficulties that would present to many.

Yes, something needs to be done to make upgrades nearly failsafe, but if it is made too complicated or time consuming, they are just going to push the upgrade button.
Yes, warnings, and options need to be communicated up front, but in reality how many are going to really pay attention. I have a friend who when he gets pop-ups always says yes just to get them off the screen... Never reads what they say. Yup! Windows Mindset, but that is what we are dealing with quite often on these forums.

Again I appreciate, and commend your efforts and am not trying to argue with you.
More power to you if you can make something happen.

Maybe an auto-backup built into the upgrade system or some kind of cloning system can be activated BEFORE the upgrade takes place?  I just think that auto-partitioning built into the upgrade system would have difficulty in predicting all user case scenarios.

Good Luck with your efforts!

Cheers 

I like that idea ...... of auto backup as it waits for the internet downloads ..... 
must be a lot of CPU time spare ...... at that point in time especially the first few days where the servers are loaded up  ...... and this is when backups are needed.

I never get into a argument if I can help it anyway .....  and I will apologise if I came over too demanding or brash .

Love this forum and the things it produces ...... how the devs do it each release is beyond me ..... but it can be made better and in doing so may save them work and  headaches afterwards .

---

### Post by effenberg0x0 on 2011-10-18
Nice Lion. But is it oneiric? Our feline is.

---

### Post by ventrical on 2011-10-18
Hey,

I thought this was the Pangolin forum.

:)

---

### Post by ronacc on 2011-10-18
nah its the pornographic parrot forum .

---

### Post by ventrical on 2011-10-18
If some of you want to develop your own apps you can go here , join the group etc..

[http://developer.ubuntu.com/](http://developer.ubuntu.com/)

 It a new site for aspiring developers and there are tutorials on how to use the complier , Quickly. Compile, register, licence, package and release your app.

---

### Post by madjr on 2011-10-18
> **ventrical said:**
> If some of you want to develop your own apps you can go here , join the group etc..

[http://developer.ubuntu.com/](http://developer.ubuntu.com/)

 It a new site for aspiring developers and there are tutorials on how to use the complier , Quickly. Compile, register, licence, package and release your app.

yea thats great site with good info, personally the software center should have a link to it, but i think you posted to wrong thread lol

---

### Post by BwackNinja on 2011-10-18
I'll have to be the one dude against all of this.

To be telling people that they **shouldn't** upgrade is absurd. The people with problems are a fraction of the total people and each release has a limited time that its supported. What do you do when you're release is no longer supported? You upgrade of course. Upgrade problems will always exist, and an upgrade is no more than a more invasive update. This is why we have a backup program installed by default. Burning a recovery disk is mostly pointless because Ubuntu is distributed on livecd's anyway, the only possible difference is some customization, which shouldn't be an issue when what you want is just a working system. A system only gets worse the more you tweak it beyond just installing and removing packages. Installing things from source overwriting installed packages is bad.

We shouldn't put the idea into people's heads that linux is some scary adventure that might eat your cat. That's what we're told in the ubuntu+1 forums, and we disregard it because by now we're pretty good at defending our cats. To say a release might as well be an alpha is near slanderous to ubuntu as a whole project and implies that somehow we managed not to do our jobs as testers, basically at all. Maybe the upgrade process needs to be more resilient, fine. But putting a sign that says "enter at your own risk" isn't exactly the best way to get supporters, nor is it a very useful way at addressing the issue of problematic upgrades.

---

### Post by effenberg0x0 on 2011-10-18
I understand BwackNinja point as well. But, being absolutely honest, how do you think the next months will go: I can foresee that we will be here testing PP, we'll find out a lot of problems and things that an average user will never manage to solve. We will report, as much as possible, and defend that the groups responsible for each package pay attention to those particular bug report / feature requests in particular. In the end, more than 60% of what we insisted on having fixed won't be fixed for release, because that's the way Ubuntu releases software. Forums will be once again pilled with Unity haters, people disappointed. Blogs, twitter, etc full of people mad at Ubuntu. Again, very bad PR. WHy would we put users through that? Why would we put a OS we love through that? I mean, I like Ubuntu but I couldn't care less what Canonical thinks its the way to do things. It IS wrong.

Am I being negative? Do we have any reason to believe things won't be like that? We had discussed black screen, jockey not working, compiz crashes / desktop with no Unity Plugin, etc months ago. The focus was on making the dash more or less blurry by then. Now they'll make the launcher movable. Yey.

---

### Post by cariboo on 2011-10-19
> **effenberg0x0 said:**
> I understand BwackNinja point as well. But, being absolutely honest, how do you think the next months will go: I can foresee that we will be here testing PP, we'll find out a lot of problems and things that an average user will never manage to solve. We will report, as much as possible, and defend that the groups responsible for each package pay attention to those particular bug report / feature requests in particular. In the end, more than 60% of what we insisted on having fixed won't be fixed for release, because that's the way Ubuntu releases software. Forums will be once again pilled with Unity haters, people disappointed. Blogs, twitter, etc full of people mad at Ubuntu. Again, very bad PR. WHy would we put users through that? Why would we put a OS we love through that? I mean, I like Ubuntu but I couldn't care less what Canonical thinks its the way to do things. It IS wrong.

Am I being negative? Do we have any reason to believe things won't be like that? We had discussed black screen, jockey not working, compiz crashes / desktop with no Unity Plugin, etc months ago. The focus was on making the dash more or less blurry by then. Now they'll make the launcher movable. Yey.

Yes you are being negative, almost all the issues we are seeing, come up at every release, the black screen after boot problem has been around for years, and as you found out yourself, there isn't one particular cause for the problem.

Keep in mind that the people that successfully upgrade almost never post anything on the forums, they just merrily go on their way, happy with their newly upgraded distribution.

There is an old saying in retail:

> A happy customer tells one friend, an unhappy customer tells everybody

There is nothing we can do to change human nature, so I either put up with it, or I go away.

Changing the update notifaction won't stop people from having problems when upgrading. The only way to solve the problem, is to find the root cause, and so far even Microsoft with all it's resources hasn't found a way to guarantee a successful upgrade every time.

---

### Post by madjr on 2011-10-19
> **cariboo907 said:**
> Yes you are being negative, almost all the issues we are seeing, come up at every release, the black screen after boot problem has been around for years, and as you found out yourself, there isn't one particular cause for the problem.

Keep in mind that the people that successfully upgrade almost never post anything on the forums, they just merrily go on their way, happy with their newly upgraded distribution.

There is an old saying in retail:



There is nothing we can do to change human nature, so I either put up with it, or I go away.

Changing the update notifaction won't stop people from having problems when upgrading. The only way to solve the problem, is to find the root cause, and so far even Microsoft with all it's resources hasn't found a way to guarantee a successful upgrade every time.

yes, is almost impossible for upgrades to go perfect. I dont think even chrome OS will be able to do it all the time (and that has been one of its selling points: less upgrade headaches)

however, if we (or anyone else) cant make upgrades 100% reliable, then at least we need to **keep users data safe** and their computers working in some way. 

So am proposing at least what others are already doing: auto mandatory **backups and recovery** partition creation (internal or external) for those that want to ahead and try upgrading, which is not perfect but is the best we have to keep customer data safeguarded (its how is done on servers and enterprises and also what Apple/msft recommends, so no need to reinvent the wheel here.):
[https://bugs.launchpad.net/null/+bug/876146/comments/10](https://bugs.launchpad.net/null/+bug/876146/comments/10)

just like you press the **Undo button** in gimp or your text processor when you make a mistake or have an error, you should be able to do the same for your OS.

Another thing is to also promote clean installs.

With all the tools available (and with better integration, accessibility and friendliness) there is no reason for users to suffer unnecessary downtime or data loss.

Apart from all this, why not also go the extra mile and have longer release cycles or promote the use of the LTS exclusively for mainstream use? is better one upgrade every 2 years (problematic or not) than 2 per year...

---

### Post by Atamisk on 2011-10-19
> **madjr said:**
> 

So am proposing at least what others are already doing: auto mandatory **backups and recovery** partition creation (internal or external) for those that want to ahead and try upgrading, which is not perfect but is the best we have to keep customer data safeguarded (its how is done on servers and enterprises and also what Apple/msft recommends, so no need to reinvent the wheel here.):
[https://bugs.launchpad.net/null/+bug/876146/comments/10](https://bugs.launchpad.net/null/+bug/876146/comments/10)

just like you press the **Undo button** in gimp or your text processor when you make a mistake or have an error, you should be able to do the same for your OS.



I agree for the most part, but words like mandatory make me nervous. You're assuming everyone who uses ubuntu is stupid, which is a Microsoftian tendency. I can see a strongly worded popup (instead of okay, something like: I understand the risk, i know what i'm doing), but the second you make it mandatory, you'll see a ton of flak from people (like me) who want the program to 'get out of their way'. Remember, linux assumes you know exactly what you're doing, and i'd like to keep it that way somewhat.

---

### Post by 23dornot23d on 2011-10-19
And so it will continue ...... (black screens) 

> 
Keep in mind that the people that successfully upgrade almost never post  anything on the forums, they just merrily go on their way, happy with  their newly upgraded distribution.
I would love to know the percentage here to make any valid assessment ..... if its as high as 80% thats good ..... 

out of 100,000 users you only lost 20,000

How many users ...... actually bothered to try to sort there problems out too .....
do they all come back to the forums .... or do they just go back to WINDOWS as
its easier.

What sort of dint is UBUNTU having on Microsoft ..... this time around ...... Bill Gates .....
must be shaking in his boots .....

( so if striving for a better percentage means sorting out the problems properly ..... would it not be worth going back and re-thinking a few things ...... )

That leads me onto this statement ........

> 
the black screen after boot problem has been around for years
This has got worse ..... and mainly due to trying to show an intermediate screen to make it
look lets say more like windows ..... 

I for one would like to be able to switch it at boot .......  to bypass un-needed  screen changes ......

Mine now for instance ..... starts low res fine ..... then tries to load some splash screen at which point it shuts my monitor down completely ..... then it gets to the end of the display manager
uses xorg.conf ..... and sets it up properly .....

What that middle step does is cause confusion .... it should be switchable ..... 
I would much rather see error messages or [OK] messages than it switching my screen off ....

I am sure at this point for newbies they may end up switching the computer off ......

I also do not remember Grub1 having the same problems .... it could start off black but usually once it was set up to work ..... it worked ..... and was much more easily customizable .....


Also in Grub 1 
I could have gone and altered things manually ....... now with the new system ...... does anybody know how to alter it and get it working properly other than drs305 ......



Simplify things ......  if they need to go into edit mode .....

Make it so they can 

toggle on and off nomodeset
toggle on and off glx
toggle on and off the boot flash screen programs

Then give a way of saving the alterations at boot ....... that gives the user a chance at least to get it working. ( without needing to resort to the forums )

By picking up the commands from the file above with presets 
with the toggles only in it ..... so users cannot make drastic changes ..... 

but at least can set a few combinations that may get their graphics back.
and once fixed so it does work , allowing them to get written into grub2

Without having to start working out how to alter grub2 manually  ...... how many normal users will bother ? ......

> If the pop-up had been turned off ..... you would not have got all the feedback that you did .... but you
also would not have as many users going away with it in there minds that UBUNTU is not for them.

---

### Post by cariboo on 2011-10-19
Has the B(lack)SOD problem gotten worse, or are you just paying more attention to the problem. 

There is no way to tell how many people upgraded successfully, as Ubuntu doesn't do any reporting, which is a good thing.

Admittedly there are problems with this release, but all of the interim release have had problems. The time to start worrying, is if the LTS release has major bugs when released, especially as the development time is so much less for this release. Proper development won't start until all of the developers get over their UDS hangovers, which usually takes about a week, so development won't really be starting until the middle to late November.

---

### Post by madjr on 2011-10-19
> **Atamisk said:**
> I agree for the most part, but words like mandatory make me nervous. You're assuming everyone who uses ubuntu is stupid, which is a Microsoftian tendency. I can see a strongly worded popup (instead of okay, something like: I understand the risk, i know what i'm doing), but the second you make it mandatory, you'll see a ton of flak from people (like me) who want the program to 'get out of their way'. Remember, linux assumes you know exactly what you're doing, and i'd like to keep it that way somewhat.

**backups** are always mandatory, that's why they are called backups.

however, just like every linux tool, [B]there would be an _advance mode_ for us who already have 3 or 4 computers with 3 different linux/windows versions each, live-CDs everywhere and multiple backups already in place, so we dont care if we _bust / brake_ one or two of them.
[/B]
But still as advance users we made those backups prior, so we are **aware** of the importance of having them more than anyone else.

We **seriously** know how to avoid downtime and data loss. We have made huge investments of time and even money (multiple computers, storage devices, etc.)

However the inexperience users dont and so they would follow the "**recommended**". The upgrade assistant should be **smart** enough that you feel you have your own geeksquad at your side. And by smart enough is (if you choose the recommended path) it will not let you continue till a backup is made.

I hope that clears the confusion, Any other doubts ?

---

### Post by 23dornot23d on 2011-10-19
To be quite honest things have eased down considerably ......

I even did the Official Upgrade to test where it is now ...... just see for yourself
how seamless it can be ..... new users may not understand the error as I did .....


> [http://ubuntuforums.org/showthread.php?t=1864826](http://ubuntuforums.org/showthread.php?t=1864826)Although the Official Upgrade worked - its nothing like me using 
( aptitude dist-upgrade and replacing the sources.list for Oneiric ones ..... ) 
Which has not failed me yet in upgrading 4 past versions of 11.04 .......

_____________________________________________________________

Although I would still not recommend the Official one yet - as there are issues as you will see in the link - mainly the upgraded icons not working ...... for a new user they will
not drop to the terminal as I did ...... so what do they do ..... re-install or move on .....

> Has the B(lack)SOD problem gotten worse, or are you just paying more attention to the problem. This BSOD as you put it ..... is mainly with ATI cards .... but some are related to[[COLOR=Blue]_*** jockey***_[/COLOR]]("http://www.google.com/search?client=ubuntu&channel=fs&q=jockey&ie=utf-8&oe=utf-8#sclient=psy-ab&hl=en&client=ubuntu&hs=8Tc&channel=fs&source=hp&q=jockey+linux+2011+failed&pbx=1&oq=jockey+linux+2011+failed&aq=f&aqi=q-w1&aql=1&gs_sm=e&gs_upl=15563l17818l2l17884l7l6l0l0l0l0l471l1571l0.1.4.0.1l6l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=bd638b897581bb57&biw=905&bih=380") for installing other drivers and Plymouth trying to implement them for the splash screen .....
which I removed  .. ( re-installed the Nvidia driver I needed - which pulls in any required dependencies ).. and now my system is running fine ..... ;)

After seeing this thread 

[http://ubuntuforums.org/showthread.php?t=1864045](http://ubuntuforums.org/showthread.php?t=1864045)

Effen and others go into much more detail than I ever could ..... but its good
to see that there are options emerging .... 

I am sure as much effort as needs to be is being put into putting things right at this moment
in time - as things are now much better ...... ty

---

### Post by cariboo on 2011-10-19
I've create an upgrade/install experience thread in the Cafe:

[http://ubuntuforums.org/showthread.php?t=1865027](http://ubuntuforums.org/showthread.php?t=1865027)

There are also links to previous threads/polls, except for Natty, which we couldn't do due to technical problems, this may or may not give you more ammunition in your quest to get something done about the upgrade popup.

I've asked the admins to create a banner, so that everyone should see it, and be able to vote, and add their experiences, whether they be good, bad, whatever.

---

### Post by madjr on 2011-10-19
> **cariboo907 said:**
> I've create an upgrade/install experience thread in the Cafe:

[http://ubuntuforums.org/showthread.php?t=1865027](http://ubuntuforums.org/showthread.php?t=1865027)

There are also links to previous threads/polls, except for Natty, which we couldn't do due to technical problems, this may or may not give you more ammunition in your quest to get something done about the upgrade popup.

I've asked the admins to create a banner, so that everyone should see it, and be able to vote, and add their experiences, whether they be good, bad, whatever.

voted!

too bad multiple choice was missing thou..

anyway, thx for the extra ammunition (:D), but it seems some of our discussions are paying off and mpt has now decided to look into the problem, probably with a backup solution first.

If this gets well implement we can expect for PP safer upgrades that users can revert back if things go bad.

---

### Post by 23dornot23d on 2011-10-19
Would have actually given better results at the start ...... most of the disgruntled users may
have already left now - as the majority were in the last 5 days ..... and reading the testimonials may have already moved to other pastures ......

Next year the poll wants to be early on .... to get true results .....

But better late than never ..... ;)

> 
anyway, thx for the extra ammunition (:grin:),  but it seems some of our discussions are paying off and mpt has now  decided to look into the problem, probably with a backup solution first.

If this gets well implement we can expect for PP safer upgrades that users can revert back if things go bad.


Good news .... ty

---

### Post by ranch hand on 2011-10-19
> **effenberg0x0 said:**
> Something like this would be much better:

[[ATTACH]204731[/ATTACH]

[ATTACH]204734[/ATTACH]

[ATTACH]204735[/ATTACH]

[ATTACH]204738[/ATTACH]

[ATTACH]204739[/ATTACH]
All very good and a big improvement over the current one.  These should be added to the bug.

---

### Post by sirkeith on 2011-10-20
Its interesting to read this thread. I am no advanced user and have only been using Ubuntu since Lucid was a beta but the only problems I have had with installs are with ISO live CD's. And that is with good burns. Updates have gone much better other than the odd hardware issue which mainline kernel upgrading have fixed. Even so, I like Natty and am gonna avoid some of the testing this goaround. I have wondered if updates or installs should not be done in 2 or 3 parts.

---

### Post by ronacc on 2011-10-20
attempting to upgrade in parts would probably give more problems than all at once .

---

### Post by nanog on 2011-12-01
on quite a few of my boxes the iso fails to install due to known kernel driver bugs. i could, therefore, argue that ubuntu should have a big warning on its isos stating that this install could fail and waste you time. on the other hand, i've never had a problem upgrading an ubuntu install (at least one i did not hack to pieces).

upgrading is essential for people who install/compile a lot of stuff (me) and for the enterprise/professional environment. thus, i am very much against even the hint of a warning during the upgrade dialog. why put ubuntu at such a huge competitive disadvantage versus other OSes?

---

### Post by forcecore on 2011-12-02
Did not read whole topic but update messages should be off or very minimal because lot of older people has came to me and ask about those messages. 
I myself found cure for this by removing update manager and i use old Synaptic for updates.

---

