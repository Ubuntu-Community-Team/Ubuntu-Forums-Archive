---
title: "criticism about ubuntu. seeking information about it"
date: 2022-07-05
forum: Ubuntu, Linux and OS Chat
---

### Post by ronjjjg8885 on 2022-07-05
i've heard that there is a lot of criticism about ubuntu lately.
i want to know where i can read about it?
tnx

---

### Post by grahammechanical on 2022-07-05
It makes I laugh.

The Ubuntu, Linux and OS chat section of this forum is for the following purpose:

> This is the place for chat and discussion about any aspect of Ubuntu,  Linux or any operating system and its software. Technical support  requests should be posted in an appropriate support sub-forum.  Discussion of the politics of open source is permissible, but only the  politics of open source. Wider political discussion is disallowed in all  areas of the forum, as is discussion of religion. As with the Cafe,  this area is intended for fun and community building, not arguments.  Please take those elsewhere. Thanks!

Regards

---

### Post by ajgreeny on 2022-07-05
*Thread moved to **Ubuntu, Linux and OS Chat**.* which is more appropriate and a better fit as this is not a request for help with a problem but just chat.

I also deleted the final rude, provocative line; totally unnecessary!

---

### Post by zebra2 on 2022-07-05
Anything can be criticized.  I have been criticizing Fords for years even though I have never owned one.  


Back in 2010 there was a hue and cry on these forums about the possibility of Ubuntu being released with a larger than 700M ISO, which could not be copied to a CD disk. 


Then there was the Natty release which dropped Gnome 2  in favor of Ubuntu&#8217;s own desktop called UNITY.  It was suppose to ultimately run on desktop, phone, and tablet. The desktop release became popular in time but the other two couldn&#8217;t compete with Android and was discontinued. While all of that was going on the Gnome 2 lovers persisted in their disgust of not just Unity but the Gnome Shell  desktop which was Gnome&#8217;s answer to Ubuntu Unity. Gnome Shell actually was more popular than Unity for a time since it was used on many of the other distros. 


Then there was the switch from INIT to SystemD which required a learning curve that may have been a bit steep for many users. I think this change was driven from outside of Ubuntu and mostly due to the need for the Linux file servers to have the more sophisticated structure than provided by INIT.  


Then there was the rewrite of Grub which was modernized to produce Grub2.  Grub2 had a learning curve because of changes in the configuration file and the way that it was implemented system wide. 


Then there was the dropping of the Unity desktop which by this time was very popular even with the people that originally hated it. It was replaced with Gnome 3 (now Gnome 4.2) which in my opinion was very immature compared to Unity (but I switched to it anyway). Canonical needed a desktop that had strong development that they could partner with. 


There has been much discussion about the performance of various softwares in the latest releases of Ubuntu. Probably due to the fact that the development platform of the software is much slower than Ubuntu itself so that what I would call a catch-up time was created.

Then there is a plethora of posts regarding the problem with dual booting non Linux OS's with Ubuntu. These time consuming posts have been graciously handled by mostly the moderators on this forum.  Many of these attempts end with a non usable "other OS" partition and in many instances on hardware not vetted for Ubuntu. 



Then with the current release 22.04 the boot partitions have been changed to work with the many requirements of the EUFI secure boot and also the subsequent changes in the modern computer hardware.  This included a rewrite of Grub once again to accommodate all of the changes.  These changes in the boot partition are even required if using a Legacy boot.  Hence a new learning curve for setting up a fresh install or even updating a previous version to the new release. 



Note:  I&#8217;m not going to do your home work for you but you can find these conversations going back some 13 years (and beyond) by using the search function in this forum. There are many others.  Most seem to me to be a resistance to progress more than anything else.  I doubt that most would want to drive a Model-T Ford on the Interstate Highways.  If I had to drive a Ford I would prefer that it was modernized to Interstate standards.

---

### Post by kurt18947 on 2022-07-06
I think the latest complaint is about snaps and there is some reason for it. One complaint is that the snap repository is the only source of snap packaged apps and it's controlled by Canonical/Ubuntu, there are no 3rd party repositories possible for snap packages AFAIK. Some find snap applications slow to open on lower powered machines compared to the .deb equivalents. The only problem I've had with snaps was with LibreOffice 7.3.x.x on Ubuntu 20.04. It was VERY slow to open password protected files on flash drives and did not see USB 3.0 flash drives as file storage. Flatpak worked fine. LibreOffice in 22.04 which I assume (haven't checked) is a snap works as expected.

I hypothesize that Ubuntu is working to be accepted by cloud and IoT companies. What may be accepted or desired by the bleeding edge hobbyist may not be seen as desirable by those companies. Bleeding edge apps is one. Companies that have to support what they sell probably prefer apps that have been out for a few weeks and the worst bugs squashed so the company's product isn't viewed as buggy absorbing lots of support resources. Those same cloud/IoT companies might prefer repositories and update mechanisms be controlled by the company they're licensing their software from. So no 3rd party snap repositories. 

All this is just my thoughts on why Canonical is behaving as they are. I have no insight beyond "what I read in the papers".

---

### Post by ameinild on 2022-07-06
"... a lot of criticism about ubuntu lately" is extremely vague. Maybe you could elaborate on which criticism exactly, and maybe point to some sources? Maybe the criticism is well deserved, maybe there are workarounds, and maybe it's just a matter of preference. But we'll never know in your case, since you haven't stated anything that can actually be used as a basis for discussion. :-k

---

### Post by poorguy on 2022-07-06
> **kurt18947 said:**
> I think the latest complaint is about snaps and there is some reason for it. One complaint is that the snap repository is the only source of snap packaged apps and it's controlled by Canonical/Ubuntu, there are no 3rd party repositories possible for snap packages AFAIK. Some find snap applications slow to open on lower powered machines compared to the .deb equivalents. The only problem I've had with snaps was with LibreOffice 7.3.x.x on Ubuntu 20.04. It was VERY slow to open password protected files on flash drives and did not see USB 3.0 flash drives as file storage. Flatpak worked fine. LibreOffice in 22.04 which I assume (haven't checked) is a snap works as expected.

I hypothesize that Ubuntu is working to be accepted by cloud and IoT companies. What may be accepted or desired by the bleeding edge hobbyist may not be seen as desirable by those companies. Bleeding edge apps is one. Companies that have to support what they sell probably prefer apps that have been out for a few weeks and the worst bugs squashed so the company's product isn't viewed as buggy absorbing lots of support resources. Those same cloud/IoT companies might prefer repositories and update mechanisms be controlled by the company they're licensing their software from. So no 3rd party snap repositories. 

All this is just my thoughts on why Canonical is behaving as they are. I have no insight beyond "what I read in the papers".

I read a lot of complaining about Snaps but that's been happening quite awhile ago.

Snaps are slow to open that first time after a cold power on or a system restart but after that first time Snaps open in a few seconds leastwise does on my desktop.

I do experience some issues with certain settings in 22.04 Ubuntu ain't sure if it's due to Snaps or compatibility with the newer Kernel that is used in 22.04 Ubuntu.

I'm not saying that 22.04 Ubuntu ain't got some issues and it sure ain't 20.04 Ubuntu however 22.04 Ubuntu ain't all that bad imo or maybe I've just gotten used to the way it works which is pretty good imo.

I have a newer more powerful desktop computer but it's 9 years old but it's a quad core processor with 8.0 GB of memory so a lot faster than my old dual core processors and 4.0 GB of memory.

I've used AppImage and Flatpak and since Snaps is already integrated in Ubuntu why not see how they work.

The way I see it is if ya don't like the new Ubuntu 22.04 than don't use it ain't no one forcing no one to use it.

A lot of users complained about systemd and now ya hardly hear anyone complain.

I don't like some of the changes in Ubuntu 22.04 but it installs and works OOTB on my computer so I'm willing to give it a chance and see what patches and fixes come about with 22.04.1 Ubuntu.

Besides ya can't really complain about free can ya.


Have a great day I am. ;)

---

### Post by deadflowr on 2022-07-06
> LibreOffice in 22.04 which I assume (haven't checked) is a snap works as expected.


This would be news (big news) if it was.
As such I have not heard of them moving LibreOffice to the snap version on 22.04.

---

### Post by SeijiSensei on 2022-07-06
My most recent version of LibreOffice is libreoffice-common_1%3a7.3.4-0ubuntu0.22.04.1_all.deb with a date of June 10th. I abhor snaps. I routinely remove the snap version of Firefox that ships with 22.04 in favor of the deb in the mozillateam PPA (see, for instance, [https://linuxiac.com/install-firefox-from-deb-on-ubuntu-22-04-lts/](https://linuxiac.com/install-firefox-from-deb-on-ubuntu-22-04-lts/)).

---

### Post by grahammechanical on 2022-07-06
> I have not heard of them moving LibreOffice to the snap version on 22.04. 				 			  			   		 			 				 			 			 				[FONT=comic sans ms][SIZE=1][/SIZE][/FONT]

They have not. Libreoffice in 22.04 is still the deb version

Regards

---

### Post by grahammechanical on 2022-07-06
Years ago an American aircraft manufacturer set up a project where it would develop military aircraft in complete secrecy. The public would be not given any information about what was being developed until the aircraft was completed, tested and ready for production. And then there would be a very public unveiling. The company called this part of their manufacturing base a skunk works.

A few years ago Mark Shuttleworth had the idea of setting up a Ubuntu skunk works. And received a lot of criticism along with accusations of secrecy. The idea was to invite community developers to work with Canonical employees on software projects that would not be released to the public until the code was complete and polished. One Ubuntu community developer and Ubuntu member joined in the criticism until he re-read the email that invited him to join the skunk works project. 

Mark Shuttleworth used to publish a blog but stopped doing that because so many posted insulting comments. I have not forgotten the long period when some would regularly post insults about Ubuntu on this forum. Thankfully, the moderators were on to this even to the point of blocking those who were the culprits.

When threads of a certain type appear on this forum I am tempted to reply "Ask for your money back." And then I remember to code of conduct that I signed. :)

Regards

---

### Post by DuckHook on 2022-07-06
> **grahammechanical said:**
> When threads of a certain type appear on this forum I am tempted to reply "Ask for your money back." And then I remember to code of conduct that I signed. :)
Your self discipline and etiquette have long been noted and long been appreciated.

As a counterpoint, it is worth noting that those you allude to&#8212;who come on these forums to deliberately provoke and intentionally cause argumentation and bad blood&#8212;are also noted. We call them "trolls" and the staff will not hesitate to take action, including banning outright.

---

### Post by ronjjjg8885 on 2022-07-08
i had a lot of trouble to update the system..

there were other things too..

after years of using ubuntu i've switched to zorin os and i hope all the small problems with zorin will disappear after i ask how to fix them.

you wrote a lot here and i find it hard to read so much..

---

### Post by zebra2 on 2022-07-08
> **ronjjjg8885 said:**
> i had a lot of trouble to update the system..

there were other things too..

after years of using ubuntu i've switched to zorin os and i hope all the small problems with zorin will disappear after i ask how to fix them.

you wrote a lot here and i find it hard to read so much..

There is much imperfection in this spacetime continuum.  More than enough to go around.  Therefore much opportunity to criticize.  Best of luck to you with Zorin OS. As it is I use Ubuntu 22.04 and 22.10 straight out of the box and don't complain about anything. In the over all OS part of the continuum it approaches perfection.  That isn't to say that the application programmers couldn't tighten up a bit.

---

### Post by exploder on 2022-07-10
The Firefox snap's performance has been GREATLY improved! I would never know it was not a deb after the recent fixes came in. I like 22.04 and have been happily running it for some time now. People are always going to complain! Ubuntu is popular and makes it an easy target for complainer's, lol. Ubuntu pushes for new things, they deserve some credit for sticking with snaps. I like the idea behind them and the areas the developer's are pushing for improvements in. It just takes a little time and patience.

---

### Post by VMC on 2022-07-10
I often read on lesser forums criticism regarding Ubuntu and/or Windows. Their front runners , and that's the reason. The other  criticism is systemd , and snap
All the criticism I've ever read about Ubuntu, I personally have never had their issues. Then again, look at the comments on consumer products. any product.

---

### Post by DuckHook on 2022-07-11
Perhaps we should do ourselves the kindness of noting that all of us, including long&#8209;time forum members, engage in critiques of Ubuntu from time to time. I know that I do.

I think the key difference is being constructive rather than destructive—a choice between thoughtfulness and griping.

So many sign up just to gripe. That is not only bad forum netiquette but pointless and a waste of everybody's time. If one is not asking for help, not interested in solving anything, not even interested in running Ubuntu anymore, then what is the point in posting here except to be childish or to troll other members?

I don't use Windows or Apple anymore. But I don't sign up on their forums just to stir their pot.

---

### Post by QIII on 2022-07-11
Perhaps if we use the word "criticism" as it applies to works of literature or art -- where it has no intrinsic negative connotation.  Surely we can discuss the merits and faults of Ubuntu, or any Linux distro, dispassionately?

---

### Post by ajgreeny on 2022-07-11
> **DuckHook said:**
> Perhaps we should do ourselves the kindness of noting that all of us, including long&#8209;time forum members, engage in critiques of Ubuntu from time to time. I know that I do.

<snip>
Same here.

Just for information, I'm one of the Ubuntu users (actually Xubuntu as I can't stand gnome) who dislikes and refuses to use any snaps, and so far I have always totally removed the snap infrastructure from my machines, ie all the snap applications and snapd, the snapstore, and replaced all the applications with alternatively installed, usually .deb, versions.
My machines are all now getting fairly old but still run Xubuntu very snappily (excuse the pun) as long as I do not try to use snaps which take so long to open first time in a session that I have no way of knowing if the snap has even begun to start. 
5 or even 10 seconds might just about be acceptable, but snaps on my systems all took far longer than that to open the first time and this was not acceptable to me so I just get rid of them but I don't really criticise Ubuntu for that, I simply don't use the snap system.

As for systemd, my experience of it has not been too much of a problem and I now understand it better than I ever did the init system which it replaced.  It took a little while to understand things but it is now beginning to make some sense to me.

OK, Ubuntu is not perfect and never will be, but for my use of a computer it's nearer perfect than Windows ever was, though I have to admit that I haven't used that for 17 years, and I know nothing of any Apple software or hardware.

---

### Post by TheFu on 2022-07-11
I'm guilty of criticizing Ubuntu, but still use it for nearly all my systems.  It isn't like we don't have a choice or that I'm not capable of running almost any other distro out there, but I still "choose" LTS Ubuntu over all others for some carefully considered reasons.  There's a link in my signature below about why I use LTS Ubuntu.

So, while I might criticize Ubuntu, it is still the best for my needs, over every other distro.  When looked at in that light, that should speak volumes about all the good-to-great things they are doing, even when I'm less than happy about certain subsystems ... which I won't list here. ;)

---

### Post by doom52 on 2022-07-12
snap firefox really suck. Bad integration with desktop environment.

---

### Post by TheFu on 2022-07-12
> **doom52 said:**
> snap firefox really suck. Bad integration with desktop environment.

Integration with other tools is a security risk.

---

### Post by VMC on 2022-07-12
> **doom52 said:**
> snap firefox really suck. Bad integration with desktop environment.

Use this install instead:
[https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users)

---

### Post by agentl074 on 2022-07-19
The whole snap thing isn't really that big of a deal. If you don't like snap, install your desired apps manually via apt. Snap is still relatively new, so if you want the regular versions of apps, enable all of the repositories and install via apt.

---

### Post by yetimon_64 on 2022-07-20
> **agentl074 said:**
> The whole snap thing isn't really that big of a deal. If you don't like snap, install your desired apps manually via apt. Snap is still relatively new, so if you want the regular versions of apps, enable all of the repositories and install via apt.
In some cases from 22.04 and on apt packaging is no longer available for some packages. 

Unfortunately some packages like firefox (and chromium browser) are now only available as snaps (or with chromium-browser a PPA) and cannot be installed via apt without you unwittingly installing the whole snap framework as well. I am on Xubuntu 22.04 and if I use "apt-cache policy" to look at firefox I am only offered a snap package (which you may note from the next code box is NOT installed)...```
apt-cache policy firefox
firefox:
  Installed: (none)
  Candidate: 1:1**snap**1-0ubuntu2
  Version table:
     1:1snap1-0ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```
Note where I've highlighted "snap" in the version offered.

The only way I can use a non snap version of firefox is as VMC posted to use the standalone version direct download from Mozilla. With a bit of work (note from VMC's link it is for advanced usage) it can be installed in /opt and in my installation is available as an alternative through "update-alternatives" along with google chrome stable and the PPA version of chromium browser due to system work I have done to my install. I have no distro included versions of firefox or chromium browser available due to the change over by Canonical to the use of snap packaging. I purge the snapd package and any snap packages included as one of the first steps after a new installation (as I personally have never liked snaps; purely a "personal taste" decision, I am not recommending anyone remove or stop using snaps etc).

Basically apt alternatives may be possible for some packaging but definitely not for all packages. I have mentioned 2 above that have to now be sourced from outside of the standard repos and apt as they are only now available as snaps and "enabling all the repositories" as you suggest will be of no help in getting them installed.

Regards, yeti.

---

### Post by ajgreeny on 2022-07-20
@ yetimon_64
You mention the use of a PPA for chromium but do not say anything about the PPA versions of firefox that are are also available.

Just like you, I also remove all the snap infrastructure and use alternatives, in the case of firefox it is the .tar.gz archive from Mozilla, and for chromium I use the .dev PPA from [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) which has worked very well for at least a couple of years.

My hardware is getting pretty old now and I'm afraid snaps are a non-starter for me, though I realise other users do not seem to have this difficulty.

---

### Post by yetimon_64 on 2022-07-20
> **ajgreeny said:**
> @ yetimon_64
You mention the use of a PPA for chromium but do not say anything about the PPA versions of firefox that are are also available...
Yes you are right, I'd forgotten to mention that. I actually have used a PPA for firefox in previous versions, though many many years ago. But I suppose I've forgotten about PPAs for firefox after I, a few years back, discovered a source download for the nightly version of firefox which was very similar to install and use to the current download linked to by VMC (I'm actually posting here now from the firefox tar-gz source in VMC's post).

My omission to mention the current firefox PPAs is purely due to my familiarity with and usage for so long of the direct downloads from Mozilla. I have used this source for so long I'd plain forgotten about firefox PPAs. The only reason I use the ppa for chromium is because I'd read up about the maintainer and heard he was a long time developer of the apt version of chromium-browser (seemed to have a good reputation by my reading). After researching about the dev and his history with chromium development I felt I could trust that PPA enough to use it; I just noted the link you included is the ppa I also have installed here from the dev I'm talking about.

Back on to the topic of criticism of Ubuntu; I personally find it hard to criticize Ubuntu myself as I've had a free OS to use for the last 15 years now. I have had problems with decisions made over the years but have always found alternatives to aspects of Ubuntu I did not like that keep me using flavors of Ubuntu. I don't like the gnome 3 DE so I use Xfce/Xubuntu. Originally back in 2011 I didn't like unity, I went to xfce; funny thing is I installed unity in 2014 and by 2016 found I loved it and a couple of years later it went away for the gnome DE :-).

Xfce has been a good alternative for over the last ten years or so for me. There has been constant change within Ubuntu over the years, as a result criticism will be heard on occasions; personally I've always found an alternative to keep me within the Ubuntu family of releases/flavors when such issues arise. There have been many hard to deal with changes but no deal-breakers yet for me. 

Cheers, yeti.

---

### Post by DuckHook on 2022-07-20
> **ajgreeny said:**
> @ yetimon_64
You mention the use of a PPA for chromium but do not say anything about the PPA versions of firefox that are are also available&#8230;for chromium I use the .dev PPA&#8230;

> **yetimon_64 said:**
> Yes you are right, I'd forgotten to mention that. I actually have used a PPA for firefox in previous versions, though many many years ago. But I suppose I've forgotten about PPAs for firefox&#8230;
The *dev* version of FF is also available by PPA along with the *esr* version. The PPA for both is:```
sudo add-apt-repository ppa:mozillateam/ppa
```
The crazy thing is that the standard version is also available in this PPA:
```
ubuntu@app:~$  apt policy firefox
firefox:
  Installed: (none)
  Candidate: 1:1snap1-0ubuntu2
  Version table:
     1:1snap1-0ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
     [b]102.0.1+build1-0ubuntu0.22.04.1~mt1 500
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages[/b]
```
&#8230;but installing it is a painful exercise in frustration and workaround. It's easy enough to install the first time using the **=** option in *apt install*: ```
sudo apt install firefox=102.0.1+build1-0ubuntu0.22.04.1~mt1
```&#8230;but thereafter, any *apt update* will invoke the repo version instead&#8212;which is a snap package&#8212;and automatically drags in snapd as a dependency even if you have already purged it from your system. I haven't figured out yet how to stop apt from pointing *firefox* to the Canonical repos and to substitute the PPA instead. I suppose one could apt-mark it *hold*, but that defeats the point of using a PPA.

Better to just install the dev or esr version and forget about the standard version altogether.
> The only reason I use the ppa for chromium is because I'd read up about the maintainer and heard he was a long time developer of the apt version of chromium-browser (seemed to have a good reputation by my reading). After researching about the dev and his history with chromium development I felt I could trust that PPA enough to use it&#8230;
The firefox PPA is maintained by a group of devs assigned to the task by Mozilla. That's trustworthy enough for me (and I'm rather paranoid about these matters). However, trust is a separate issue to compatibility. I'm aware of the fact that, though I won't have to worry about actual malicious intent, the addition of any PPA could still put me in dependency hell. It's a risk that all PPAs drag in with their use and I've decided that I'll just have to live with it.
> Back on to the topic of criticism of Ubuntu; I personally find it hard to criticize Ubuntu myself as I've had a free OS to use for the last 15 years now. I have had problems with decisions made over the years but &#8230; I've always found an alternative to keep me within the Ubuntu family of releases/flavors when such issues arise. There have been many hard to deal with changes but no deal-breakers yet for me. 
Thanks for this perfect summary of why I stick with Ubuntu as well.

When some aspect of Ubuntu irritates me, I always remind myself that at least I can find alternatives to those irritants. Were I still stuck in the proprietary universe, good bloody luck.

An example is Android. I thank f&#8209;droid endlessly for providing non&#8209;tracking alternatives to the apps in Google's play store, but there's nothing I can do about the base OS itself. Likewise with Windows and Apple. With Ubuntu, I can switch even the kernel if I have a mind to doing so.

---

### Post by TheFu on 2022-07-20
> **agentl074 said:**
> The whole snap thing isn't really that big of a deal. If you don't like snap, install your desired apps manually via apt. Snap is still relatively new, so if you want the regular versions of apps, enable all of the repositories and install via apt.

Please show me how to install lxd without a snap.  Please.


> An example is Android. I thank f&#8209;droid endlessly for providing non&#8209;tracking alternatives to the apps in Google's play store, but there's nothing I can do about the base OS itself. Likewise with Windows and Apple. With Ubuntu, I can switch even the kernel if I have a mind to doing so. 

There are non-Google versions of Android and if you have the skills, you can install those versions onto many of the popular Android devices.  Sadly, not all devices and the install may be 1-click or require building the entire OS, hunting down drivers, and likely violating some proprietary code licenses, but people do it.  If you have an itch, it is there with most of the source code available.  Just takes time and knowledge.

---

### Post by DuckHook on 2022-07-20
> **TheFu said:**
> There are non-Google versions of Android and if you have the skills, you can install those versions onto many of the popular Android devices.  Sadly, not all devices and the install may be 1-click or require building the entire OS, hunting down drivers, and likely violating some proprietary code licenses, but people do it.  If you have an itch, it is there with most of the source code available.  Just takes time and knowledge.
I did replace both an old phone and a tablet with an alternate Google&#8209;free Android derivative some time ago. In the end, it didn't work out:

[LIST=1]
[*]Voiding OEM's warranty. This is especially costly with new phones.
[*]Lack of scheduled system upgrades.
[*]Unreliable multistep process if manually upgrading system.
[*]Most replacement 'droid OSes work only on older models and not on new ones.
[*]Missing or flaky drivers.
[/LIST]
On the whole, my experience left a lot to be desired. Perhaps the newer OSes are easier to install and less bug&#8209;ridden. Since my initial foray, I've never been motivated to try again, as f-droid gives me all that I need and it's not hard to disable the Google apps on most phones.

---

### Post by lammert-nijhof on 2022-07-21
Like our great Dutch philosopher the soccer player Johan Cruyff once said: "Every disadvantage has its own advantages". I use for some vague nostalgic reason an encrypted Virtualbox VM with Ubuntu 16.04 ESM (Extended Security Maintenance) for my financial stuff. Ubuntu 16.04 has built-in snap support, so I installed the latest snaps of Firefox and LibreOffice. 

Firefox loads in ~4 seconds and LibreOffice in ~11 seconds. Subsequent Firefox loads are even faster. I'm happy with Firefox, my snap complaint would be about LibreOffice, however by default they are installed in Ubuntu from deb files.

My 2019 PC did cost $349 and it has a Ryzen 3 2200G (4C4T; 3.7Ghz OC; the 2nd slowest Ryzen); 16GB DDR4 (3000MHz) and a 512GB SP nvme-SSD (3400/2300MB/s). 

The load problems with Firefox snaps are largely solved in this week's Firefox release. I hope the LibreOffice snap will be updated in the same way as Firefox.  They will also make improvements on Multi-threaded CPU decompression, Software Rendering and Pre-caching in the next update.  Note that I have already the effects of pre-caching, because I run my VMs on OpenZFS with a 4GB memory cache (L1ARC). So there might be some parts of the snaps still present in the L1ARC of the Host-OS even after (re)booting Ubuntu 16.04 VM.

---

### Post by agentl074 on 2022-07-24
With a Ryzen 5 5500U/SSD machine, I never had an issue with Firefox speed -- it open fast and functioned fast enough for me to get the apt code for Brave browser lol. LibreOffice also started fast and performed well. I was able to apt my favorite game -- SuperTuxKart -- as well as the corefonts package. I enabled all repositories from installation -- including all proprietary and third party.... It may be that snaps are improving -- which would be a great thing; however, many packages can still be had with apt.

---

### Post by lammert-nijhof on 2022-07-26
I got Firefox 103 in FreeBSD 13.1 on Saturday 23-07-2022. Today I got  the updated Firefox 103 snap and it loads in ~2 seconds the first time  and in ~1 second afterwards.  However I do run the super-fast Ryzen 3  2200G. A bad day for all the Firefox Snap Haters.

---

### Post by TheFu on 2022-07-26
> **lammert-nijhof said:**
> I got Firefox 103 in FreeBSD 13.1 on Saturday 23-07-2022. Today I got  the updated Firefox 103 snap and it loads in ~2 seconds the first time  and in ~1 second afterwards.  However I do run the super-fast Ryzen 3  2200G. A bad day for all the Firefox Snap Haters.

I don't have 22.04 for a number of reasons.

Does it work over remote X?

Can I control how much RAM the container sees/uses?  I've been using firejail for years now to locally control where any program has access, where it doesn't and how much RAM it is allowed.  I got tired seeing that firefox was using 65G in top, so I put a limit on the RAM firefox inside a firejail can see/access.

Can I save files to my NAS? Or /tmp/?

My HOME is in /u/thefu/ and NFS mounted.  So far, no snaps ever work with that.  I understand they hard-coded /home/ as the only place for HOME directories.

Can I control when firefox is updated - perhaps delay the update for 3 weeks?

Can I limit the number of copies for each snap is stored locally?  The default is 3. I'd like 1.  When I looked, the minimal was 2, so I'm forced to waste 2x the storage if there are snaps.  That might not seem like much to most people, but I want to run a lite-Ubuntu on a Chromebook with 2G of RAM and 16G SSD, so wasting even 1GB is ... er ... wasteful.

Without local control for these and a few other things, snaps are broken by design.  The mothership doesn't always know what is needed locally. They just don't.

I look forward to the day when I don't dislike snaps.  That will require local control.  I'm still dumbfounded by the fact that HOME directories from the configured password DB (local or NIS+ or LDAP) aren't supported.  It isn't like the passwd DB shouldn't be trusted.  By definition, the passwd DB must be trusted. Period.  The possible workarounds of using a bind-mount to /home is useless, since they also expect people to change the HOME directory in the LDAP passwd entry to point to /home as well.  We aren't going to break 50 other servers, most not Ubuntu, just to support snaps.

Snap haters still have many reasons to dislike snaps. Don't worry.

---

### Post by Claus7 on 2022-07-26
Hello,

> **TheFu said:**
> I don't have 22.04 for a number of reasons.

...
Can I control when firefox is updated - perhaps delay the update for 3 weeks?

...

you may already know that, yet just now I made a check: having downloaded firefox from their website (either folder or zipped), if I do not click on Help->About Firefox, then firefox is not updated. If I do so though, then it will be updated and I do not have the chance to stop it.

Regards!

---

### Post by TheFu on 2022-07-26
> **Claus7 said:**
> Hello,



you may already know that, yet just now I made a check: having downloaded firefox from their website (either folder or zipped), if I do not click on Help->About Firefox, then firefox is not updated. If I do so though, then it will be updated and I do not have the chance to stop it.

Regards!

There are lots of ways to control non-snap packages.  The complaint I have is with snap being the default and sometimes, the only, way to get some packages.

Please, someone, show me how to get a current LXD without snap.  Anyone?  A few years ago, around the v2 release, Canonical decided to make lxd only available as a snap package. There's no other deployment method.  I suppose if I dug deeply enough into snaps, I could create a de-snap-if-fy tool, but I shouldn't need to.  LXD does some great things for container setup and management, it really does.  It would be much more widely used if Canonical would package it **any** other way.  During my LUG meeting a few days ago, we had 25 people and I wanted to take them through setting up an LXD container, but when they saw lxd was only available as a snap, everyone not already using snaps declined.  That left 2 people - me and a guy who was new and happened to have Ubuntu installed.  Nobody else, even with Ubuntu or debian-based distros would touch snap packages.  Previously, at the LUG, we've worked through software installs and setup using AppImages and Flatpaks. Neither have the same hesitancy.

Those are facts.

With APT, we can control if and when updates happen. We can hold old packages in definitely or we can simply NOT update the system at all to keep all packages at the known, good, working, level.  Snaps take that away, unless we block network access to the snap control servers, which shouldn't be required.

I don't have any real issue with snaps being available or any defaults the packaging team for a snap decides.  That's a fine thing.  My issue is that there aren't local overrides available and published.  They don't need to be easy.  They just need to be possible and documented.

---

### Post by lammert-nijhof on 2022-07-26
Why don't you try, what works and doesn't work, instead of asking me :) 

If I don't like a product from a company, I go somewhere else!  Fortunately Ubuntu has an excellent price/performance, so I was happy to give them some time to improve their product, exactly like I did around 2012 with Unity.

Begin of the year I installed Peppermint 10 on btrfs (lzo compressed) on a PC with also 2GB and a 40GB slow IDE HDD. You could install Ubuntu or a lighter flavor/derivate using btrfs (lzo) too and save some space on that 16GB SSD. By the way the Firefox snap is also lzo compressed, since the 17th of July. The snap stores 2 or 3 snapshots, but for the updates only the deltas will be send and only the deltas will be stored in the snapshots, just like with ZFS. So the gains of the LZO (or the old XZ) compression will beat the deltas of the 1 or 2 snapshots.

You can control the updates. You  can determine the time of day of the update and if it causes problems,  you can revert an update. It means, that version will be skipped from now on.

As retired chief-architect I can assure you, that snaps are not broken by design. The Snaps have been designed by an architect, almost always based on a compromise between budget and requirements. Often you already define the goals for the first 2 or 3 releases. A random local user has no clue about budgets and the goals for those releases. That local user might get into problems, if he separates the purpose and name of a system folder (Home). That is a general design convention broken by a confused user. It might be accepted by some programs, but not by all. 

Mozilla has its own password manager as used by Firefox, why should they as commercial company invest money to support all other password managers in the world. Maybe on request of big clients, they planned some support for one or two external password managers for release 104 or 105 and maybe I get my Dutch spell checker back in future  :)

---

