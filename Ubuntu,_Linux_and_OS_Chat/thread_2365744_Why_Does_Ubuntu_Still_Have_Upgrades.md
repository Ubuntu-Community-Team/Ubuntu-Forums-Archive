---
title: "Why Does Ubuntu Still Have Upgrades"
date: 2017-07-10
forum: Ubuntu, Linux and OS Chat
---

### Post by Jyscal on 2017-07-10
I am not trying to start something, but I just cannot understand.

Why do the makers of Ubuntu even bother having the Upgrade option in place? It has never worked properly. Even the countless posts i have seen advice against upgrading. What is the point of even having it then? 

Again, not fighting. Just can't see the point of keeping a feature that is pointless and has always been broken. Done many upgrade from Win 7-8-10 etc. Flawless. NEVER had a single error i could see. Ubuntu? Nothing but errors.

---

### Post by vasa1 on 2017-07-10
Moved here because there's no specific support requested.

---

### Post by poorguy on 2017-07-10
The decision to upgrade is up to the end-user.

I have found upgrades to be problematic in my experience using any OS.

The preferred method and best method is to always do a new clean install using any OS.

---

### Post by vasa1 on 2017-07-10
And I haven't had a failed upgrade.

---

### Post by coffeecat on 2017-07-10
> **Jyscal said:**
> It has never worked properly.

Not so. The upgrade option is there because most times it works properly - period. I have done so many times without problems.

Yes, there are a lot of posts advising against upgrading. And there are a lot of posts from people asking for help who started an upgrade and then ran into problems. 

There are also a lot of people who generalise from their particular by thinking/saying "**my** upgrade failed, therefore it will fail for everyone." And there are a lot of people who simply and unthinkingly repeat popular tropes

And there are a lot of people who unwisely add far too many PPA repositories to their systems (which can lead to dependency hell), and/or make irregular and non-standard modifications to configurations, and then wonder why things break. They'd rather blame Ubuntu rather than their own - er - folly. And these are the sort of people who, when asking for help here, fail to admit to these salient points - at least until challenged. Or even deny that they were responsible for modifications which are blatantly evidenced in terminal output they provide. Believe me - when you've administered a forum such as this for as long as I have, you [s]begin to despair for the future of the human race[/s] wonder whether some are capable of true rational thought.

Yes, upgrades do go wrong occasionally. But not as often as you would conclude from the oftentimes misinformed statements I see on these forums almost daily.

---

### Post by poorguy on 2017-07-10
> **coffeecat said:**
> 
And there are a lot of people who unwisely add far too many PPA repositories to their systems (which can lead to dependency hell), and/or make irregular and non-standard modifications to configurations, and then wonder why things break. 
I have to agree as everything I read about doing an upgrade from version to version always says to remove any and all PPA packages prior to the upgrade.

> **coffeecat said:**
> wonder whether some are capable of true rational thought.
Some end-users fail to follow the protocol on how to properly perform an upgrade.

> **coffeecat said:**
> Yes, upgrades do go wrong occasionally.
The chance an end-user takes as no guarantees.

I just like new installs as everything is fresh. :)

---

### Post by wyliecoyoteuk on 2017-07-10
As ever, your mileage may vary.
The huge range and differing combinations of software and hardware out there means that there will always be some users who have problems
I run several different flavours of Ubuntu at home and at work, and I have upgraded continuously, e.g. from Mythbuntu 11.04 to 16.04 with only minor issues.
I also manage a mainly Windows based network (since windows 3.11) and have had major issues with some Windows upgrades in the past. 
Although things have generally improved, even Windows 7 to 10 left me with applications that didn't work or needed reinstalling.

---

### Post by deadflowr on 2017-07-10
People don't tend to complain when things work.
So it's hard for us to gauge how many people have done successful upgrades versus those who did not.
You would think that Ubuntu's developer teams have a better gauge than we do.
Maybe they do, and maybe they don't.

For what it's worth we start a poll after every release asking people to post their experiences upgrading to the new release; whether upgrading or installing it)
[Current Zesty upgrade poll and war stories]("https://ubuntuforums.org/showthread.php?t=2359321")

(as you can see the poll is not highly popular, perhaps because it's for a middling in-between lts release)
If you have installed or upgraded to zesty, please add your voice to the poll.

---

### Post by QIII on 2017-07-10
> **deadflowr said:**
> People don't tend to complain when things work.

This.

In the medical world this is called "referral bias".  That is, only those with arthritic knee pain tend to complain to their rheumatologist.  Nobody goes to a rheumatologist to complain that their non-arthritic knees feel fine.

From the point of view of the rheumatologist, whose practice is all about arthritis, it might seem that everyone has arthritis -- but s/he's aware of the phenomenon of referral bias.

Anyway, the quickest way to a significant emotional event when upgrading is to leave proprietary drivers and third-party apps (and their PPAs) active on the machine.  Best to uninstall them and remove the PPAs entirely.  Upgrading works just fine on a "clean" installation.

Like many others, I never had a problem updating.  The reason I do fresh installs these days is to get rid of dross left over from using and playing around with the previous release.

---

### Post by 1clue on 2017-07-10
I've been the guy who advises against upgrades.

Having started my Linux experience in the mid 90s you might understand how I "grew up" with distribution upgrade procedures which were not especially flawless.

Things have come a long way since then. Forums have come around (not just mailing lists) and documentation is better, and automated updating software has come into existence when there was none before. Yes, that automated update software went through some rough years, of course it did. With so many Linux users insisting they could do it themselves more reliably, or insisting on a wipe-and-reinstall, you can maybe understand how it took awhile for upgrade scripts to get traction.

What's more, commercial for-profit entities have come around and dumped highly trained and organized resources into the community. IBM had what we called BlueHat back then, before Linux was even announced to the public. RedHat started making RHEL, Suse started targeting the Enterprise, and of course Canonical worked on Ubuntu and its variants. All of Linux changed with this step, even if the distros had no direct input from commercial software. Good ideas were implemented, projects were better organized.

Commercial software also benefited from Open Source. AFAICT it was the Linux community that came up with live updates and the idea of days or weeks between the discovery of a vulnerability and its fix being released to the public.


So some critical points were made above:
[LIST=1]
[*]People with non-standard hardware always have a tougher time. This includes bleeding edge or high-performance options in what would be considered mainstream hardware.
[*]People with lots of extra PPA repositories added in tend to have a tough time.
[*]People with heavily modified installs tend to have a tough time.
[/LIST]

If your install is on pretty common equipment and you pretty much left everything as-is, then you could expect your dist-upgrade to go fairly smoothly.

If you spent a lot of time screwing around with your system to see how much it can bend before it breaks (been guilty of that myself) then you can expect problems with a dist-upgrade and you might consider wiping and reinstalling.

---

### Post by QIII on 2017-07-10
Except that *dist-upgrade* only upgrades packages within the current release.  ;)  It's a good thing to do that before upgrading to a new release, though.

You're thinking of *do-release-upgrade*.

---

### Post by 1clue on 2017-07-10
> **QIII said:**
> Except that *dist-upgrade* only upgrades packages within the current release.  ;)  It's a good thing to do that before upgrading to a new release, though.

You're thinking of *do-release-upgrade*.

Yeah, it's been awhile.

---

### Post by mikodo on 2017-07-10
I wonder how well release upgrades will go from Ubuntu Unity to Ubuntu Gnome3 in 18.04? I hope they, (devs and release teams) can swing it, for the masses that depend upon upgrading releases especially, LTS's.

---

### Post by pauljw on 2017-07-12
> **mikodo said:**
> I wonder how well release upgrades will go from Ubuntu Unity to Ubuntu Gnome3 in 18.04? I hope they, (devs and release teams) can swing it, for the masses that depend upon upgrading releases especially, LTS's.

As is normally the case, there'll be issues.  I would recommend not upgrading in April of 2018 just because you can.  16.04 is fully supported till 2021 so give 18.04 time to work out the kinks before doing the upgrade.  I'm still running 14.04 on my laptop and won't upgrade until I'm about to lose support as it runs about as perfect as can be.  I am currently typing this in a VM running 16.04 which I run most of the time and it runs perfect for me as a VM.  My laptop was purchased in 2013 w/13.10 pre-installed.  I had a flawless upgrade to 14.04LTS when I got the word from System76 that it was ready for the upgrade.  I don't know if this machine will still be going by 2019, 6yrs of rather continuous usage takes it's toll, but if it is, I'll make the move to newest well behaving LTS available at the time.

I've never understood the need to jump to the latest release for no other reason than it's new.  If it ain't broke, don't fix it...

---

### Post by deadflowr on 2017-07-12
LTS releases won't get the upgrade option to the next LTS release until after the first point release (typically July/August)
Otherwise to upgrade earlier you need to invoke the development flag,
either with update-manager -d or do-release-upgrade -d.

---

### Post by mastablasta on 2017-07-13
> **poorguy said:**
> I have to agree as everything I read about doing an upgrade from version to version always says to remove any and all PPA packages prior to the upgrade.


PPAs are disabled automatically upon upgrade since "i do not know what version".

i had no issues with upgrades before (as long as upgrade is not interrupted and is done via wired connection). though i am thinking if i should perform the 14.04 to 16.04 (systemd and new plasma make me think)...

---

### Post by kansasnoob on 2017-07-13
> **mastablasta said:**
> PPAs are disabled automatically upon upgrade since "i do not know what version".

i had no issues with upgrades before (as long as upgrade is not interrupted and is done via wired connection). though i am thinking if i should perform the 14.04 to 16.04 (systemd and new plasma make me think)...

But just disabling the PPA's does not revert the changes made by that PPA. I filed a bug report one year ago suggesting that the user be notified of which PPA's are in use, and then given the choice of purging same:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1602052](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1602052)

But it just got wishlisted so nothing will happen unless a bunch of people turn up the heat.

---

### Post by mastablasta on 2017-07-14
but wouldn't the changes to the OS made by PPA get overwritten on upgrade anyway? while the ones not related to OS should be handeled when doing the second upgrade stage - upgrading the PPAs.

---

### Post by deadflowr on 2017-07-14
> **mastablasta said:**
> but wouldn't the changes to the OS made by PPA get overwritten on upgrade anyway? 
Only if the packages coming from the ppa are lower versions than what would be in the new release.

---

### Post by kansasnoob on 2017-07-14
> **deadflowr said:**
> Only if the packages coming from the ppa are lower versions than what would be in the new release.

And sometimes the owner of the PPA uses a soname for packages that is simply not compatible with the Ubuntu libraries. I've been guilty of that myself.

---

### Post by grahammechanical on 2017-07-15
The developers who design the release upgrade scripts cannot take into account modifications that users have made to the system. There are simply too many ways in which a user can modify Linux. This is why I recommend reverting the desktop to a default condition as far as possible before running the upgrade. 

Right now I am using the development version of Ubuntu 17.10 that I upgraded from Ubuntu 17.04. The difference in code between the two versions is not that great at the beginning of the development period. I am watching the OS transform from Ubuntu + Unity to Ubuntu + Gnome 3 shell. The OS now has both Unity & Gnome 3 shell and there are Wayland options. 

There is one thing to watch out for when, in future, upgrading from 17.04 to 17.10. You will be asked to choose to use either LightDM or GDM as the display driver that takes over from Grub and brings us to the login screen. The upgrade does need user input at that point. GDM will load Unity 7 as well as LightDM does.

I doubt if the upgrade will remove Unity 7 without user approval.

Regards.

---

### Post by forrestcupp on 2017-07-16
I haven't used Ubuntu for a really long time, but even back when I did, I never had any problem with upgrading. I saw everyone saying clean installs are better, but I never had an issue with it. Maybe it was partly because I was smart about what hardware I was using.

---

### Post by 1clue on 2017-07-17
Clean installs ARE better. The question is, are they worth it?

There's no way an upgrade script can handle every scenario for a system with unknown software on it, or for that matter upgrade a config for a complex app like apache httpd or any full-scale mail server and deal with every possible configuration scenario. The chance of a failure in the upgrade is significant.

That said, most upgrades even on commercial software have basic configurations and complex software has only a few mainstream configurations active, which means it most likely will upgrade fine, with a high probability of some old files hanging around.

---

