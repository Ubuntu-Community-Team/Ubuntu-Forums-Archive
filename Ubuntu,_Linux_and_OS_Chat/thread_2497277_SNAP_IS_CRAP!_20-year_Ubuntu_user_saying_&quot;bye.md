---
title: "SNAP IS CRAP! 20-year Ubuntu user saying &quot;bye bye&quot;"
date: 2024-04-28
forum: Ubuntu, Linux and OS Chat
---

### Post by mnealbarrett on 2024-04-28
I hate snap with the fiery passion of a thousand suns. Since Canonical is making snaps more and more mandatory with every new version, I am now researching new Linux distributions that do not use it. I wish there was a Ubuntu disto that eliminates the snap crap, like how Ubuntu Mate eliminated Gnome 3.  I am leaning toward Mint, but PopOS looks promising also.

---

### Post by oldfred on 2024-04-28
Still running Kubuntu with no snaps. 

I used this to install Firefox.
You also have to reset priorities as shown or it will reinstall the Firefox snap.
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)

With 24.04 I will have to do the same for Thunderbird.

---

### Post by guiverc on 2024-04-28
You do realize you can install even 24.04 without *snapd *infrastructure...

You mention Ubuntu MATE, thus aren't worried about *flavors*, where I performed QA (*Quality Assruance*) testing of *flavors* of 24.04 that installed a *minimal* system which is actually *snap free* too.  Those systems have no *disabled* snap, so it can be easily installed too, but Ubuntu *developers* have documented many times how to disable *snapd* so it won't install.

Note:  the *minimal* system was not the default install, it was optional.

---

### Post by VMC on 2024-04-28
Snap is easy to remove. I never run Ubuntu using snap of any kind.

---

### Post by TenPlus1 on 2024-04-29
I got tired of removing snap with every install and quite happily moved to Linux Mint 21.3 Cinnamon Edition which works really well and is still based on ubuntu LTS.  I am eagerly awaiting LM 22 which will be based on the newer 24.04 LTS.

---

### Post by Morbius1 on 2024-04-29
Just keep in mind that Mint = Ubuntu - snap + flatpak

---

### Post by ian-weisser on 2024-04-29
> **mnealbarrett said:**
> I hate snap with the fiery passion of a thousand suns.

Healthy folks do not feel such passion for software that they did not create.

---

### Post by gezzer2 on 2024-04-29
im not a lover of snaps but in Ubuntu 24.04 they have managed a vast improvement with the snap packages.
the only one that i found to have problems was Gnome Boxes everything is running as expected ..

---

### Post by zebra2 on 2024-04-30
> **ian-weisser said:**
> Healthy folks do not feel such passion for software that they did not create.

+1
I use all snap where available. It all takes care of itself with no problems.  I don't get what all of the highchair banging is about.

---

### Post by spinnekop1962 on 2024-04-30
If it works I really couldn't care less whether it is deb, snap or flatpak. (Only a 12 year Ubuntu user though)

---

### Post by TheFu on 2024-04-30
I switched to Linux Mint for my desktop about a year ago.  I'm not much of a desktop DE user, so it is less about the GUI and more about which apps are there and how they work.  I like to control the constraints for certain applications. Snap constraints happen to conflict with my standard setup, so snaps haven't worked on most of my systems already. Useless.  I find the suggested work-arounds from the snap team to be highly undesirable.  Their work-arounds would impact EVER OTHER SYSTEM here, not just Ubuntu systems. That's unacceptable.

Got tired of fighting with Canonical's ideas on a few things, but mainly snaps.  I don't run stock Mint either, but not having to deal with snaps for many commonly used tools is great.  I'll probably switch to MX Linux next install to dump systemd too. Eventually, systemd will be production ready.  Someday.  Systemd was created to fix problems I never had.  Lots of things are added/replaced in modern Linux distros to solve problems that very few people actually have.

I have found a use for a few snap packages.  I use lxd, though I'd much rather it not be a snap package.  I also use the nextcloud snap, which has drastically simplified my nextcloud install and maintenance, though it does break addons periodically. It is better, overall, than manually maintaining nextcloud. Just wish the auto-upgrade disable commands actually worked.  I wanted to stay on v24 of nextcloud and entered snap commands to prevent updates to any new major release.  Alas, today, it is running ... NC29 ... er ... somehow.  That's a bunch of major upgrades that I didn't want.

---

### Post by lammert-nijhof on 2024-05-01
Bye bye

---

### Post by 909mjolnir on 2024-07-01
To be honest, as much as I like the Ubuntu family, I'm not runing on them anymore either, for a similar reason set.  
But I'm OK with AppImages and the old fashioned octopi / pacman / synaptic / gdebi / dpkg type of stuff.  
I'm sometimes on Arch instead of Debian or Ubuntu, but across the Linuxes, I think AppImage is the way to do it.  
It's the nicest to the end user.  I still like alternatives.  

I do think Cannonical is sometimes kinda bossy and wierd, but so are so many other devs, it's just commonpace, unfortunately.  
Programmers are their own special breed.  But I'm still thankful for them.  

Good luck ou there, don't forget distrowatch.org

---

### Post by 909mjolnir on 2024-08-07
wierd.  yesterday i noted snap showing up in my system, but i don't use it.  i had to delete it.  it's kinda fussy having to do all that.  
i wish devs wouldn't be like that making us use stuff that we don't want and don't need.

---

### Post by VMC on 2024-08-07
Snap on Ubuntu is not going away. Just get use to it. If you can't, there are other options, other distros that don't have it. Mint comes to mind.
Its rather easy to remove Snap.

---

### Post by TheFu on 2024-08-07
> **909mjolnir said:**
> wierd.  yesterday i noted snap showing up in my system, but i don't use it.  i had to delete it.  it's kinda fussy having to do all that.  
i wish devs wouldn't be like that making us use stuff that we don't want and don't need.

It isn't the devs.  It is a corporate decision by Canonical. Make no mistake.

---

### Post by #&amp;thj^% on 2024-08-07
> **TheFu said:**
> It isn't the devs.  It is a corporate decision by Canonical. Make no mistake.

+1
Sad but very true....

---

### Post by Shibblet on 2024-08-07
> **VMC said:**
> Snap is easy to remove. I never run Ubuntu using snap of any kind.

I tried that... then watched in horror as "sudo apt-get install chromium-browser" installed SnapD and then used SnapD to install Chromium-Browser.

---

### Post by currentshaft on 2024-08-07
.

---

### Post by #&amp;thj^% on 2024-08-07
> **currentshaft said:**
> Fresh 24.04 installation. Uninstalled cupsd because I don't print on this machine.

Few weeks later ... "sudo snap refresh" ... cupsd gets installed and starts listening on the network.

What the actual f?

sudo apt purge "snap*" is now the first command I'll run on fresh Ubuntu installations.

:lolflag:
I feel you....

---

### Post by werewulf75 on 2024-08-09
> **spinnekop1962 said:**
> If it works I really couldn't care less whether it is deb, snap or flatpak.
Yeah, I second that. If it does the job, who cares? "If it ain't broke don't fix it" is a healthy principle.

---

### Post by TheFu on 2024-08-10
> **werewulf75 said:**
> Yeah, I second that. If it does the job, who cares? "If it ain't broke don't fix it" is a healthy principle.

If it worked perfectly, you are right. Nobody would care.  But snaps don't, not for everyone. What then?  

Or if it uses 20% more CPU and 20% more RAM on a system that is restricted in RAM, CPU and storage?  Now that system cannot perform the same tasks it has done for years.

Linux has always been about the users having control.  If the OS doesn't do something the way we need, we are used to working around that to get what we need/want.  Snaps block that far too often.  That's the complaint.  If snaps were optional, we wouldn't be so vocal.  Heck, I removed Firefox (snap) and get Firefox ESR (non-snap) to use for a browser.  That isn't really a big deal.  It is all the things where there isn't an easy replacement.  It is great that you don't know about those issues, but many people do and are highly dependent on certain workflows that aren't possible due to snap constraints.

---

### Post by Tadaen_Sylvermane on 2024-08-10
> Linux has always been about the users having control.  If the OS doesn't  do something the way we need, we are used to working around that to get  what we need/want.  Snaps block that far too often.  That's the  complaint.  If snaps were optional, we wouldn't be so vocal.  Heck, I  removed Firefox (snap) and get Firefox ESR (non-snap) to use for a  browser.  That isn't really a big deal.  It is all the things where  there isn't an easy replacement.  It is great that you don't know about  those issues, but many people do and are highly dependent on certain  workflows that aren't possible due to snap constraints.

Said control extends to various distros with different goals. No one is locked into Ubuntu. May be more difficult to switch for some than others but that is part of the technology game. I don't get the hate only because no one is forced into it. You don't like it, they aren't holding you hostage. Door is there, people just need to walk through it. Beats sitting around beating a  dead horse about something that they have no control over. Once Ubuntu went commercial, which has been a benefit in a number of ways it also came with baggage.

---

### Post by garethjenkinsuk on 2024-08-11
There are some problems with snap.  For several years I used Inkscape to work my vinyl cutter.  When I upgraded to Ubuntu 24.04 I installed Inkscape as a snap.  The vinyl cutter no longer worked.  Many hours spent trying to sort the issue out.  Finally uninstalled the snap, installed Inkscape using apt and the cutter started working again.  Conclusion: there are real problems with some snaps not working properly.

---

### Post by lammert-nijhof on 2024-08-14
I use Ubuntu since 8.04 LTS.  I love snaps and I have a good reason!  I run the latest stable snaps of Firefox; Thunderbird and LibreOffice in Ubuntu 16.04 ESM and it did run out-of-the-box. 
Occasionally Ubuntu 16.04 ESM runs newer application versions than Ubuntu 24.04 LTS, especially for LibreOffice.

I run it in a VirtualBox VM for my banking with a 20 GB disk and 2 GB of memory.  The VM runs in the 2nd slowest Ryzen ever, the Ryzen 3 2200G; 16GB DDR4 and from a 2019 nvme-SSD.

---

### Post by Shibblet on 2024-08-14
One of Linux's greatest strengths has always been the major cause for division.

The reason we have so many different distributions is because different people like doing things differently.
Arch has a very different way of installing packages than Debian, as well as Fedora, and SuSE.  

Heck, just look how packages are handled within the Ubuntu Branch of Linux distributions...  Mint has a different storefront than Ubuntu, and Pop_OS, etc.
.DEB, APT, YUM, PACMAN, PAMAC, etc.

Now, we have Snap, AppImage, and FlatPak.

The best part of these, as far as I can tell, is that you can run all of the above on any Linux system by just installing the new package manager.  From what I understand, you can install FlatPak on Ubuntu, and Snap on Fedora.

So, if you think "Snap is Crap," I'd urge you to try a distribution like Manjaro, EndeavorOS, or Garuda.  All of which are Arch based, and can install packages from "all of the above."

And the only reason I'd say that, is that Ubuntu has certain packages that are forced as a Snap.  Firefox and Chromium are the first that come to mind.  So, if an application that you truly want is only available in Snap, and you can't use that... sounds like you really have no choice but to find a distribution that does.

---

### Post by TenPlus1 on 2024-08-15
Thankfully for users who with to avoid snaps we have Linux Mint 22 which is still based on a stable ubuntu 24.04 base and has apps like Firefox, Thunderbird and Chromium supplied in .deb formats in the repository.

---

### Post by Shibblet on 2024-08-15
> **TenPlus1 said:**
> Thankfully for users who with to avoid snaps we have Linux Mint 22 which is still based on a stable ubuntu 24.04 base and has apps like Firefox, Thunderbird and Chromium supplied in .deb formats in the repository.

I really wish Mint had a KDE variant.  I really prefer FlatPak's to Snaps...  But I can't do the Gnome or Cinnamon at this point, I'm married to KDE.

---

### Post by #&amp;thj^% on 2024-08-15
> **Shibblet said:**
> I really wish Mint had a KDE variant.  I really prefer FlatPak's to Snaps...  But I can't do the Gnome or Cinnamon at this point, I'm married to KDE.

If Ubuntu can so let it be said Mint Can ;)
info: [https://linuxiac.com/how-to-install-kde-plasma-on-linux-mint-22/](https://linuxiac.com/how-to-install-kde-plasma-on-linux-mint-22/)

Plasma is my second choice, xfce first....:)

---

### Post by poorguy on 2024-08-15
As a home computer user I don't have any complaints with Snaps they seem to work okay for what I do.

I guess if I was an IT person running servers and such I guess I could understand the dislike for Snaps.

I learned enough about Snaps not to download the not tested and not certified Snaps.

I learned enough about Snaps to keep them updated and maintained.

I get the feeling Snaps may be around for awhile so I figure might as well learn to use them.

---

### Post by Rubi1200 on 2024-08-18
I'm also not sure what the fuss is about.

As a regular home user, I have never experienced any of the issues that are reported on the forums. I suspect the issues that people run into are not always related to the snaps but possibly to other problems such as configuration or customization settings.

I also have non-Snap systems and they also work perfectly fine for my needs.

---

### Post by ajgreeny on 2024-08-18
> **Rubi1200 said:**
> I'm also not sure what the fuss is about.

As a regular home user, I have never experienced any of the issues that are reported on the forums. I suspect the issues that people run into are not always related to the snaps but possibly to other problems such as configuration or customization settings.

I also have non-Snap systems and they also work perfectly fine for my needs.
Or still having older hardware with spinning disks rather then SSDs!
That is still my situation on two machines and I don't wish to update the hardware on them until I need complete new systems as they do not warrant the expense; the case of the laptop, for example, is now falling apart so it's certainly not worth messing with.

However I do have to use one snap for Skype as it is available only in that format now unless I'm prepared to use an old .deb version which does not work as well as the snap, and I have to admit that Skype as a snap starts fast enough for me, unlike Firefox and thunderbird which take so long I often do not know if they're starting or not!
What I dislike most about snaps is the comparative lack of control compared to normal package versions for updating and some configuration.

As for using kde on Mint, of course you can! Install it or one of its versions using terminal or synaptic and then just choose it when you log in.
Mint does not support it and suggest you will possibly lose some of the Mint utilities but if you're used to running Ubuntu and not Mint, that could be of absolutely no consequence to you.

---

### Post by nicolasdentremont on 2024-08-18
I use a few Snaps. Firefox, FreeCAD and Thunderbird. They were installed as Snaps by default after updating to 24.04 and I decided to leave them like that to see how they differ from the versions I had before. I haven't run into any issues so far.

---

### Post by #&amp;thj^% on 2024-08-18
Most Home users won't even notice much of difference, but IT and system admins sure will managing them via server...No Thanks....

---

### Post by sports fan Matt on 2024-08-18
I have also switched to Mint 22.  Not because of snaps, but I feel like Gnome is just too much like Mac OSX (like it has been for my liking)

---

### Post by Shibblet on 2024-08-19
> **sports fan Matt said:**
> I have also switched to Mint 22.  Not because of snaps, but I feel like Gnome is just too much like Mac OSX (like it has been for my liking)

It's funny you'd say that... I have heard people say that KDE is just like Windows.

The answer to that though, it just on the surface.  Only the direct desktop looks similar to Windows.  Everything else is completely different.

---

### Post by sports fan Matt on 2024-08-20
This makes sense ~ in all of my years of running Ubuntu , I never even thought about running Kubuntu.

---

### Post by Shibblet on 2024-08-20
> **sports fan Matt said:**
> This makes sense ~ in all of my years of running Ubuntu , I never even thought about running Kubuntu.

I highly like Kubuntu.  I'd still be using it if there weren't a couple of projects that I use that are only available in the AUR.  (well... easily, anyway)

But KDE has become a lot more memory friendly during the Plasma 5 era, and now Plasma 6 is out, and runs fantastically.  But Plasma 6 won't be included with Kubuntu until the next release.  I think you can run a back-port though.

---

### Post by VMC on 2024-08-20
Yes, I like KDE also. Some things are much better than Ubuntu. I will keep them both though.

---

### Post by Shibblet on 2024-08-21
> **VMC said:**
> Yes, I like KDE also. Some things are much better than Ubuntu. I will keep them both though.

Even though I use a different distribution... I like to keep in mind that Ubuntu has been, and keeps trying new things.

Snaps still need some work.

The Unity desktop didn't stay, because they realized they could use Gnome 3 (and now 4)... and still keep the Unity layout.
Many people don't remember that Ubuntu was the distribution that started PPA's.  I think PPA's were made for all Debian distros, but really became popular with Ubuntu.
If you want to get technical, PPA's kinda evolved into Snaps.

Ubuntu even attempted to make a phone OS at one point.

For the OP to say "Snap is Crap!"  I can't blame him.  Why go through the process of "neutering" your OS in order to make it fit your needs.  Remove SnapD, change PPA's, etc.
I mean, most Linux users choose their distribution based on what works for them.

If you don't like RPM packages, you probably shouldn't use Fedora.
If you don't like KDE, why on earth would you use Kubuntu?
If you don't need processor specific compiled applications, why use Gentoo?

and ultimately... If you don't like Snaps... why use Ubuntu?

---

### Post by VMC on 2024-08-22
> **Shibblet said:**
> ...

and ultimately... If you don't like Snaps... why use Ubuntu?

Snap is easily removed.

---

### Post by Shibblet on 2024-08-22
> **VMC said:**
> Snap is easily removed.

I shall quote myself:

> **Shibblet said:**
> Why go through the process of "neutering" your OS in order to make it fit your needs.  Remove SnapD, change PPA's, etc.
I mean, most Linux users choose their distribution based on what works for them.

I shall also link myself:  [https://ubuntuforums.org/showthread.php?t=2464112&highlight=snapping+intensifies]("https://ubuntuforums.org/showthread.php?t=2464112&highlight=snapping+intensifies")

And I shall also say:  It's a fight.  It's not the simplest thing in the world to remove SnapD, and make it stay removed.  I'm not debating that it CAN'T be done, but if it can, it's not easy.  And 99% of all users don't want to fight their OS.

---

### Post by Perfect Storm on 2024-08-29
I have no good feelings for snap either. I find it notorious, at least in flatpak you got flatseal to tweak the permission and stuff. And not to mention it not themeable icon wise and you have to set it manually.
Good thing I have moved to Zorin and Solus on my systems. Sad after so many years of praising Ubuntu from the start that it's no more.

---

### Post by baltic on 2024-09-02
Just use Kubuntu. It doesnt use snap for anything. I am not sure its even got installed by default

---

### Post by deadflowr on 2024-09-02
> **baltic said:**
> Just use Kubuntu. It doesnt use snap for anything. I am not sure its even got installed by default

Firefox, Chromium, and Thunderbird are all snaps by default on all Ubuntu flavors, including Kubuntu.
(Thunderbird only on the latest releases; 24.04 and newer)

---

### Post by Erik1984 on 2024-09-02
> **deadflowr said:**
> Firefox, Chromium, and Thunderbird are all snaps by default on all Ubuntu flavors, including Kubuntu.
(Thunderbird only on the latest releases; 24.04 and newer)

And it's integrated om Discover (you can control a Snap's permissions graphically with it). Probably a good thing for the flavors to not diverge too much from Ubuntu in this regard. 

Still not 100% sure if Snaps are an improvement for desktop users (they might be for developers) over the traditional packages sources. As long as I see improvements though I'm mildly optimistic, like snapd now noticing when programs are shut down so they can be updated.

---

### Post by baltic on 2024-09-02
> **deadflowr said:**
> Firefox, Chromium, and Thunderbird are all snaps by default on all Ubuntu flavors, including Kubuntu.
(Thunderbird only on the latest releases; 24.04 and newer)
 
There are PPAs on their sites. I use all of them and have no snap installed

---

