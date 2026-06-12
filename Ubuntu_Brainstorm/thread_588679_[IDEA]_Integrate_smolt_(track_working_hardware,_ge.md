---
title: "[IDEA] Integrate smolt (track working hardware, get user metrics)"
date: 2007-10-23
forum: Ubuntu Brainstorm
---

### Post by gnomeuser on 2007-10-23
There is a complete lack of metrics on Ubuntu, we don't know how many users are on which hardware, we have no firm numbers to give to the press (which leads to Mark making wild and misleading estimates in the press instead - a practice that makes Ubuntu look really bad and dishonest).

But behold there is a solution, The Fedora Project has been shipping something called Smolt for 6 months now, what Smolt does iput in very simple terms is take a dump from HAL and send it to a wiki anonymously, each machine is then identified with a unique id. This means any distros using smolt can see what versions are installed of the OS, and what hardware people are running on. 

How do this help the average Ubuntu user, well first there is the obvious brag effect of having a hard number to brag about "we have so many million users" not really useful but cool. Second whenever Ubuntu issues an update for a driver they will know how many people report back that it doesn't work, they will also know how many people they potentially hurt or benefit with a given update.

If deployed during a development cycle we can track what kernels don't boot, what hardware stops work - all by automated response, no bug reports to open or anything, just run the hardware tester (which we can also cleverly automate to avoid asking to many unneeded questions).

Smolt is a work in progress but it does represent the first cross distro effort to collect such data, and just one end result will be that we can do a little compatibility app to put in the installer, so that a user can boot the livecd, then as part of the installer be warned of problems with his hardware on the current version of Ubuntu. The hardware database can also serve as a means of guiding users to picking good and well supported, known to work upgrades, as well as provide a guide to upstream vendors and the Linux Driver Project to spot commonly used hardware which does not have a driver.

I blogged about this and the implications long term of working together on getting this:

[Smolt, for make benefit glorious QA](http://lovesunix.net/blog/?p=187)

The Smolt page itself can be found here, please note it's a work in progress - more hands on deck will be needed but the infrastructure is there which is the important bit:

[Smolt main page](http://smolts.org/) - yeah it's kinda ugly, we are working on that.

---

### Post by Bou on 2007-10-23
I see this as a potentially very useful addition to Ubuntu, but I'm not sure if it wouldn't bring fear of Ubuntu "calling home" to inform on the user.

---

### Post by gnomeuser on 2007-10-23
> **Bou said:**
> I see this as a potentially very useful addition to Ubuntu, but I'm not sure if it wouldn't bring fear of Ubuntu "calling home" to inform on the user.

It's already handled by being anon upstream in smolt, it's opt in and you will be asked if you want to provide feedback - there are ways to ensure that you can retain your privacy but it's hard work.

What's still needed is some kind of userspace tester, I imagine we can use the existing Ubuntu hardware tester and just send stuff to smolt using the smolt uuid instead. But just having metrics would be very helpful as a first step.

---

### Post by r3m0t on 2007-10-24
I like it, but I don't like the constant prompts in Vista about the "Customer Experience Improvement program". To whit - one for Office, one for Live Messenger, one for Online Help, one for your search queries in the Help system and the Control Panel, and probably another one or two here or there.

Maybe we can present the option during install (I mean while it's actually copying files to the hard drive) and emphasise the complete lack of privacy implications. :-)

---

### Post by Bou on 2007-10-24
[QUOTE=r3m0t;3618854Maybe we can present the option during install (I mean while it's actually copying files to the hard drive) and emphasise the complete lack of privacy implications. :-)[/QUOTE]

Yup. We already have popularity contest anyway, so the installation could just ask if you want to send anonymous statistics to improve ubuntu and, if so, enable both (popcon and smolt, I mean).

But it would have to be more visible than it is now, I'm afraid.

---

### Post by Ubuntiac on 2007-11-14
As someone who's more concerned with privacy than most I agree that the privacy statements above are important, but... realistically far more pressing, to far more users is the extraordinary difficulty in finding out what hardware will actually work with Ubuntu (Fedora, Suse, Mandriva etc). Imagine when:

**1.** Hardware manufacturers who now imagine their product is all being used on windows, realising that _X million $$ of their current sales are from Linux_ (and they don't even currently mention Linux on the box...)

**2.** That when a device really *does* work well in Linux, that users flock to it, making that product more profitable, and the less compatible products less profitable. Suddenly _linux compatibilty starts to = easier profitability_.
[B]
3.[/B] As a result of point 2.b) above, _the average computer user starts seeing "Linux Compatible"_ in all the kinds of places they're used to seeing Windows XP/Vista Compatible" which, like it or not, they interpret as a sign of a "real" operating system that obviously enough people use for it to be advertised by hardware manufacturers. Seeing Linux mentioned everywhere (like Window$) people feel comfortable with it as a viable option to be explored. People are usually happy to try something they feel familiar with, _breaking the number 1 "sales" barrier to entry into Ubuntu / Linux today_.

**4.** Furthermore, by helping users to move towards more compatible hardware (and helping developers pinpoint less compatible hardware) we have yet another opportunity to _hugely improve stability, presumably the #1 goal of Hardy Heron_ as an LTS release.


These are some big, big opportunities that seem to be being held back for a few relatively small technical challenges on protecting privacy and possibly an unwillingness to break with the past of a pretty much unused older Hardware Database. Open-source is, obviously, all about openness and working together as a community to create something better for everyone. Fedora has offered us an open project olive branch to try and unite the distro's in a technically simple way that has big opportunities as far as I can see. How many posts have we seen from people begging to know what brand X will actually work... and getting no replies? How many hours have we all spent combing various old and outdated sites looking for support information for our next hardware purchase? How long are we prepared to suffer before making the decision to at least *ask* users directly  if these are benefits they're happy to contribute to and benefit from in Hardy Heron?

Personally, I'm ready now.

---

### Post by rsandu on 2007-12-01
Hello all,

I am 100% subscribing to this idea: integrating a tool like smolt in Ubuntu would be extremely beneficial for all GNU/Linux community and users in general !

The Fedora distro has found a way to minimise the impact of smolt on privacy: the hardware profiler is run, by default, at first boot, and user may choose if to send the hardware profile or not.

Afterwards, one may also *choose* if to run a daemon that sends the updated hardware profile, one a month.

In no case it presents the annoyance of the Windows counterpart pop-up tools.

It is a good idea to include smolt on Live CDs as well: personally, I am using Fedora Live images to test computers that don't run Linux yet, fancy laptops, unusual hardware configurations, etc. It is a great way to quickly obtain a workstation's hardware full details...


Regards,
R&#259;zvan

---

### Post by tjagoda on 2007-12-01
I think that this could be a very beneficial idea, as long as you include a way to turn it off for the privacy-concerned.

---

### Post by Ubuntiac on 2007-12-01
> **tjagoda said:**
> I think that this could be a very beneficial idea, as long as you include a way to turn it off for the privacy-concerned.

Absolutely. Lets give people the *choice*. At the moment the choice is being made for all of us to not participate by not having it available anywhere. Not in the installer. Not in the repo's. Heck there doesn't even seem to be a .deb floating around anywhere. The most important thing is to give us a choice anf make sure we all know that choice is available.

---

### Post by Ubuntiac on 2007-12-02
Speaking of choice...

Now (finally) there is a version of smolt for (K)ubuntu! So it may not be on the official smolt site, but it worked for me without any compiling or anything fancy like that. Just download the two files _[here]("http://xyzz.kexik.net/node/12")_.

Install by clicking on them (the urlgrabber one first) and run from the terminal/konsole with:
```
smoltSendProfile
```

Worked a charm for me! That's my 5 seconds aiding the revolution! :guitar:

---

### Post by rsandu on 2008-02-06
Hello again,

Since the functionality overlap in many ways, would you please consider integrating smolt with the older Linux Counter [http://counter.li.org](http://counter.li.org) ?

Linux Counter is a great tool, but it requires manual installation of the [update]("http://counter.li.org/scripts/machine-update") script. And there are no .rpm or .deb packages for the Linux Counter...

It's a pity that no Ubuntu box is listed at [http://smolts.org/static/stats/stats.html](http://smolts.org/static/stats/stats.html)

smolt should also be useful in Ubuntu derivatives, such as [Kiwi Linux]("http://kiwilinux.org/")

Regards,
R&#259;zvan

---

### Post by Cato2 on 2008-04-05
I think Smolt is a great idea, and would really like to see it supported by default in Ubuntu, with a simple opt-in perhaps.  Since it is very careful not to include any personally identifiable data, only information about your hardware, I personally would be OK if it was opt-out.  See [http://smolts.org/show?UUID=pub_7152989c-0fbc-4b3f-b9f8-c88f9a630453](http://smolts.org/show?UUID=pub_7152989c-0fbc-4b3f-b9f8-c88f9a630453) for an example, the site also has stats across all submitted entries.

It really is hugely important that Ubuntu users are counted by the hardware vendors, and this would also help Ubuntu developers prioritise work on the most popular hardware.  

I have tried installing the Ubuntu/Debian version of Smolt from [http://xyzz.kexik.net/node/12](http://xyzz.kexik.net/node/12) - it mostly works but doesn't actually send the data, due to what looks like a server side issue.  I've sent a bug report to the developer.

Would be interesting to hear others' experiences of smolt on Ubuntu.  It's very easy to install from the .debs, just do the following:
```
sudo wget http://xyzz.kexik.net/system/files/smolt_0.9.7.1.1-2_all.deb
sudo wget http://xyzz.kexik.net/system/files/urlgrabber_3.1.0-2_all.deb
sudo dpkg -i urlgrabber_3.1.0-2_all.deb smolt_0.9.7.1.1-2_all.deb
sudo smoltSendProfile 
```
It will prompt you before sending any data, so you can check what it's doing, and your system identifier is a random unique identifier (UUID).

Since smolt is already bundled in Fedora and runs by default, it already has huge takeup.  While I'm also signed up to the Linux counter, smolt is far more automated and is really focused on capturing hardware data that will improve Linux hardware support, so I think it's best to focus on smolt.

The one downside of smolt that I can see is that it currently requires DBUS/HAL, which are associated with GNOME/KDE and not with lighterweight Linuxes such as [Damn Small Linux]("http://damnsmalllinux.org") (an amazing tiny distro that can run very efficiently from flash or CD, and makes use of very old hardware, even back to [486s]("http://damnsmalllinux.org/486.html") and Pentiums with just 16 MB of RAM.)  So it's probably under-representing the use of such mini Linuxes, which is probably quite common as people often put Linux on an older second PC when trying it out.

---

### Post by Ubuntiac on 2008-04-07
Some interesting related things happening over at the Phoronix Test Suite (search @ phoronix.com). This seems to be more of a performance set of tests rather than compatibility though and doesn't have the support of any particular big distro's yet (they're still very new). Still, looks good and Phoronix has some good reach.

I just want the major Linux players to hurry up and start co-operating to get us some standardised, across the board hardware compatibility testing love happening soon!

---

### Post by rsandu on 2008-10-31
Hello,

My feeling is that there are little chances for smolt in Ubuntu to stay in sync with its dependencies (say urlgrabber) as long as it's not included in the **official** Ubuntu core distro.

From there, it will automatically propagate in other derivative distros, like Xubuntu, Kubuntu or KiwiLinux ([http://www.kiwilinux.org](http://www.kiwilinux.org) , which is an Ubuntu specifically adapted for Romanian/Hungarian users).

This will allow smolt statistics page at [http://smolts.org/static/stats/stats.html](http://smolts.org/static/stats/stats.html) to **start** to reflect the correct weight of each distro on the market.

IMHO, I will suggest submitting the current packages of smolt to Ubuntu's core repository, ASAP.


Best regards,
R&#259;zvan

---

### Post by staalmannen on 2008-11-18
I find it very puzzling that the [smolt statistics]("http://smolts.org/static/stats/stats.html") page still only shows fedora distros under the OS tab. Considering that Ubuntu was guesstimated at 8 million at around 2006, there surely should be more than 927 computers (the lowest fedora entry in the statistics) running ubuntu that have tried smolt and reported to the database? I would at least expect to see OpenSuse in the list, since this was one of the first non-fedora distros with smolt ported (and it will apparently be part of the 11.1 release during installation like in fedora).

I have even seen a screen with people running Sabayon who have uploaded to smolt... although there I guess the user base is so low so that it goes "below the radar" of the statistics. I would not expect the same of Ubuntu, since it keeps a strong first position in Distrowatch, and its derivatives are also quite high. Even if only early-adopters would actually try it at this moment, I would expect them to be quite numerous still within the Ubuntu user base (definitely larger than 927 people).

---

### Post by gnomeuser on 2008-11-18
> **staalmannen said:**
> I find it very puzzling that the [smolt statistics]("http://smolts.org/static/stats/stats.html") page still only shows fedora distros under the OS tab. Considering that Ubuntu was guesstimated at 8 million at around 2006, there surely should be more than 927 computers (the lowest fedora entry in the statistics) running ubuntu that have tried smolt and reported to the database? I would at least expect to see OpenSuse in the list, since this was one of the first non-fedora distros with smolt ported (and it will apparently be part of the 11.1 release during installation like in fedora).

I have even seen a screen with people running Sabayon who have uploaded to smolt... although there I guess the user base is so low so that it goes "below the radar" of the statistics. I would not expect the same of Ubuntu, since it keeps a strong first position in Distrowatch, and its derivatives are also quite high. Even if only early-adopters would actually try it at this moment, I would expect them to be quite numerous still within the Ubuntu user base (definitely larger than 927 people).

Smolt is not distributed with Ubuntu. Any user compiling smolt on his/her own might easily screw up and grab the distro information wrong for all I know (as the code has only been extensively tested on Fedora and openSUSE). It might also be an appliction bug or a server bug. It definitely warrents investigation, it is however the first I have heard of this issue. I also have never heard from a single Ubuntu user who consistently uses smolt, if you do not let smolt submit updates to your entry every month, it will eventually decay (I can't recall the exact timeout limit) and get removed from the stats as a outdated entry which might also explain the absence of such data.

I know that the latest openSUSE 11.1 beta integrates smolt so soon we should see them rise in the statistics. This incidently leaves Ubuntu as the only major distro not participating.

Smolt is an open community project, getting good stats is vital so I would encourage getting smolt into Ubuntu and helping to hammer out any issues Ubuntu users might see submitting data.

---

### Post by Progressive on 2008-11-18
Fantastic idea. How can we get it on launchpad? Is this already in Brainstorm?

---

### Post by staalmannen on 2008-11-19
Something really cool would be if the popcon (or a similar software profiling tool) was made distro agnostic too and that either smolt or popcon logged the unique ID of the other together with some sort of benchmark score (perhaps the phoronix one).

This could then be used in an andvanced multivariate analysis (like PCA) to identify performance effects from hardware, software and hardware*software components. I am thinking in analogy with quantitative genetics and gene-by-environment effects. The three programs (for software, hardware and benchmarking) would not have to be integrated more than that they would add an entry with the IDs of the other to be able to couple/merge the different data to a unique machine. All have good privacy policies so that would not be an issue.

I think this could be a powerful tool to find out where different bottlenecks can be found in linux for optimization of the software...

---

### Post by gnomeuser on 2008-11-19
> **staalmannen said:**
> Something really cool would be if the popcon (or a similar software profiling tool) was made distro agnostic too and that either smolt or popcon logged the unique ID of the other together with some sort of benchmark score (perhaps the phoronix one).


Popcon and smolt fill completely different niches, also we have a solution for popcon that might be good in agnostic setting. The GNOME Online Desktop work Red Hat has been doing has mugshot. Mugshot has opt-in support for collecting data not just on applications installed but what applications are actually used. It uses this data to arrage your most used application entries and to suggest applications when one is searched for (say you don't have a pdf reader, evince is popular so suggest that first).

---

### Post by staalmannen on 2008-11-21
I am fully aware that they fill different niches. I was talking about a way to utilize both informations though to analyze performance over a wide range of hardware/software combinations.

That was however just a wild idea of mine. Smolt itself is good as it is and will hopefully enable identification of hardware issues and help development in that respect.

I am just very curious about the actual user statistics... Hopefully it will update soon to include more distros than fedora. I could not find a discussion page or contact at the smolt page to ask about it.

---

### Post by staalmannen on 2008-12-02
Update:
The smolt stats page now shows fedora, red hat, centos, simplis/vixta, ojuba (=all RH based) and OpenSuse.
I hope this motivates more distros to join up, because getting as much stats as possible over hardware use and its functionality is really useful.

---

### Post by rockin_goliath on 2008-12-08
Great analysis, Ubuntiac!

Profitability is actually exactly what is keeping hardware vendors from dedicating more resources to Linux. It is often said that the exact number of Linux users can't be determined, since it's passed around freely. Let's turn that idea on its head!

I'm totally sold! Let's do it! I can't wait to see Tux on the outside of all the hardware boxes and computer cases!

---

### Post by rockin_goliath on 2008-12-08
Additionally, the option should be placed a little more conspicuously than the "Package Usage Survey" option in the installer, which is under Advanced on the last screen.

---

### Post by Gourgi on 2009-01-15
how can one istall smolt in ubuntu?
i tried the debs from here [http://xyzz.kexik.net/node/12](http://xyzz.kexik.net/node/12)
but they don't seem to work on my jaunty machine

---

