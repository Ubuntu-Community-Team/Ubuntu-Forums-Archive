---
title: "Snaps, Flatpak's, and Hard Drive Space"
date: 2024-09-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2024-09-16
I did an install of Kubuntu 24.04.1, and did a little testing.

I partition a 32g / (root) drive, and then use the rest of the disk space for /home.

I installed all of my usual apps.  The app installations on the root drive add up to about 14.1gb of space.
I decided to install all of the apps as FlatPak's instead...  This added up to 22.1gb of space
Then I loaded up all Snaps, and this added up to 25.7gb of space.

This is the total amount of space used on "/", including the OS.

I did not test AppImages.


Please tell me again what makes Snaps & Flatpaks so much better?
All of the problems have still not been taken care of.

They don't run as quickly.
They take up more disk space.
They don't integrate into your OS correctly.

Why do we keep pushing foward on these?

---

### Post by deadflowr on 2024-09-16
> Please tell me again what makes Snaps & Flatpaks so much better?
All of the problems have still not been taken care of.
Not sure what makes them better but the goal is having a single package that runs across a broad range of distributions and versions.
So you can have the same version on Fedora as you do on Ubuntu or Arch, and it doesn't matter which version of any of those you're using.

For end users it means very little, but for developers it means less time trying to get it to work on errant releases all the time.
Which means getting updated, possibly better, versions rolled out faster to everyone.

---

### Post by 1fallen on 2024-09-16
> **Shibblet said:**
> 

Why do we keep pushing forward on these?

One of the reasons why Snap and Flatpak were developed was to remove  the dependency issues found with traditional package managers. Snap and  Flatpak packages contain all the software necessary to install the  package in question, including dependencies. 
So, when you go to  install a certain piece of software via either Snap or Flatpak, you  don't have to worry about installing dependencies .

I have No issues with speed and Flatpaks, Now Snap's is a totally different experience....That's about as nice as I'm going to get on that matter.

On which flatpak are you speaking about that don't work?>>>Never Mind if your going to use any Buntu DE they will protect their snaps.

If I want Flatpaks or even appimages, I'll flat just use another Linux system like Arch, Pure Debian w/o snaps, or any .rpm based system

---

### Post by grahammechanical on 2024-09-16
There is a push for immutable operating systems with the containerization of applications. This is supposed to provide a less hackable computer OS. Snaps and Flatpaks provide the containers that applications run in.

Fedora has an immutable OS that uses Flatpaks for application containers. Canonical has Ubuntu Core as an immutable OS with Snap packaging providing the containers for the applications.

Unlike Silverblue Ubuntu Core does not have a desktop environment or user interface. But it is an immutable OS.

[https://fedoraproject.org/atomic-desktops/silverblue/](https://fedoraproject.org/atomic-desktops/silverblue/)

[https://pages.ubuntu.com/rs/066-EOV-335/images/Ubuntu_Core_4_pager_DS_revised_may_2024.pdf?version=0&_gl=1*184hgft*_gcl_au*MTQyNDc0OTg1Ni4xNzI0ODc3NTc0&_ga=2.46989799.1104590114.1726515983-1550261412.1715731804](https://pages.ubuntu.com/rs/066-EOV-335/images/Ubuntu_Core_4_pager_DS_revised_may_2024.pdf?version=0&_gl=1*184hgft*_gcl_au*MTQyNDc0OTg1Ni4xNzI0ODc3NTc0&_ga=2.46989799.1104590114.1726515983-1550261412.1715731804)

Canonical was working on a desktop environment for Ubuntu Core. A development version was supposed to be released during 2024 but there has not been much news about it. But then again, I do not do much Canonical reading.

There is this:

[URL="https://cdimage.ubuntu.com/experimental/ubuntu-core-desktop/24/stable/20240209/"]https://cdimage.ubuntu.com/experimental/ubuntu-core-desktop/24/stable/20240209/
[/URL]
I might give it a try,  Regards

---

### Post by TheFu on 2024-09-16
Constraints and the fact that the OS running doesn't limit you from having the latest version of a specific program. Some people are running their Ubuntu desktops using ESM/PRO support for 10 yrs, so they could be on Ubuntu Desktop 18.04 still and need/want the latest version of Firefox to "just work".

For most people, using a few GB extra isn't a big deal.  It is for you and for me.  We aren't typical users with 1TB storage devices.

Of course, the constraints can be limiting for some people - perhaps you are in that group.  I am as well.

But most people don't care much if the OS and packages use 50G or 100G.  It isn't important, so they don't worry about it and move on.
As for RAM use, whenever we have 3 or more versions of Qt and GTK+ on a system and run programs that require all 6 of those to be in RAM, then it isn't unreasonable to expect the price of that flexibility to be more RAM used.  It is less important on newer releases, but much more important on older, but still supported, OS releases.

If snaps and flatpaks aren't for you, that's fine. Don't use them.  If you don't want to fight Canonical's choice, there are other distros which don't mandate using either.  For example, MX Linux doesn't use systemd, which seems to be a requirement for snaps to work. Linux Mint has been vocal about not wanting to mandate snap packages, so it isn't required there, but we have the choice to use them, or flatpaks, if we like. I'm certain there are other distro that leave the choice to us as well.

In theory, 24.10 will allow more local control over the constraints required in snap packages. We shall see and I'll wait until 26.04 to see it myself.  By then, hopefully, we'll be allowed to have HOME directories anywhere we like, not just to hard-coded /home/ locations and NFS support will be a 1st class citizen for anything related to snaps.  I can hope.

---

### Post by Shibblet on 2024-09-16
> **deadflowr said:**
> For end users it means very little, but for developers it means less time trying to get it to work on errant releases all the time.
Which means getting updated, possibly better, versions rolled out faster to everyone.

So, what you're saying is that it's more beneficial for the developer, and not necessarily the end-user?

> **1fallen2 said:**
> One of the reasons why Snap and Flatpak were developed was to remove  the dependency issues found with traditional package managers. Snap and  Flatpak packages contain all the software necessary to install the  package in question, including dependencies.

Even if you already have the dependencies required?  The Snap and Flatpak has them reduntantly?

> **grahammechanical said:**
> Fedora has an immutable OS that uses Flatpaks for application containers. Canonical has Ubuntu Core as an immutable OS with Snap packaging providing the containers for the applications.

I like the concept of an immutable OS, but that gives too many limitations.  One set of dependencies is all that is needed.  i.e. If Telegram needs "whatevertheheck.xml," and so does Signal, there is no point in having it twice.

> **TheFu said:**
> For most people, using a few GB extra isn't a big deal.  It is for you and for me.  We aren't typical users with 1TB storage devices.

Not as a whole... but it can REALLY mess up smaller partitions.

---

### Post by Tadaen_Sylvermane on 2024-09-16
> So, what you're saying is that it's more beneficial for the developer, and not necessarily the end-user?

The typical average user doesn't know the difference other than "why are my packages on this distro but not that one?" type of thing. They don't generally have any philosophical reasons to be against them nor does it impact them in any noticeable way. And it's a good thing to make it easier for developers. Contrary to popular belief just because you have access to source code doesn't mean you can successfully build it. Most people cannot do that, much less port it to match a given library difference or whatever. And the developers are working on new stuff and fixing bugs. Why should they waste time making a separate package for each of the billion distros when they can make one agnostic package that doesn't rely on anything specific from any specific distro. Makes to much sense to not do it. In cases where distros package stuff for their prized distro then that is duplicated effort all over the place for almost no real benefit to the average normal day to day user who doesn't give a crap and just wants it to work.

The shared library distro specific packages are very fitting in a server environment. Desktops are different, the end goals are different. It just can't work because there will always be a distro or hundred that are left out of some software for some ridiculous or arbitrary reason. People should be able to pick a distro they like (personally I think there are to many options and it needs tamping down) but they can't do that when they have to pick the one that runs the software they need without jumping through hoops.

An example. I enjoyed my time with Fedora Silverblue. I like the immutable concept and really didn't want to layer packages on top of it. I couldn't get Makemkv to build properly and run in a home directory bin to save my life. Fedora doesn't include non free packages. So Fedora is out the door for me. The flatpak just stopped working on me for some reason so I had to leave Silverblue to rip my dvds. I picked immutable for a reason. I didn't pick it so I could modify the base image.

People who care about the philosophical stuff like this are an ever decreasing minority. I think the arrival of appimage, flatpak, and snaps is a harbinger of this. People just want their software to work and care less and less everyday about the little things that the "older" generation of *nix users cared about. Now they just want to run their games or whatever. They don't want to have religious discussions on why distro X is better than distro Y or vise versa. They just want their software with no fuss.

It's ironic. We see this daily in governments. The younger generations want something different than the older generations. The older generations fight tooth and nail to keep things the way they always were, even when people benefit from some of the changes. It's human nature to change over time. Things that were once important aren't as much anymore.

---

### Post by 1fallen on 2024-09-16
> **TheFu said:**
> 
In theory, 24.10 will allow more local control over the constraints required in snap packages. We shall see and I'll wait until 26.04 to see it myself.  By then, hopefully, we'll be allowed to have HOME directories anywhere we like, not just to hard-coded /home/ locations and NFS support will be a 1st class citizen for anything related to snaps.  I can hope.

It's still in theory, I'm on 24.10 currently and I see no changes on that front.

What I do "see" is from 24.04 thru 24.10 is they seemly are making what was working to not working without some sort of work around.(Flatpaks and Appimages)

---

### Post by lammert-nijhof on 2024-09-17
I experience an advantage every week. I still use Ubuntu 16.04 ESM (Extended Security Maintenance).  I also installed the latest stable snaps of Firefox and LibreOffice, Ubuntu 16.04 LTS already had almost full support for snaps. I only have to drag the icon of the refreshed snap back to the Unity dock. 

Note that Ubuntu 16.04 ESM now has the same releases of Firefox and LibreOffice than Ubuntu 24.04 LTS and for LibreOffice Ubuntu 16.04 ESM is sometimes ahead on the deb version in 24.04 LTS :) :)

---

### Post by Perfect Storm on 2024-09-18
I always advise people to get rid of Snap and rely on .deb and in cases flatpaks. Snap is sloooooooooow when you try to use an app that is packaged that way, also snap.d has a great impact on the bootup speed in a negative way.

---

### Post by Paddy Landau on 2024-09-19
> **grahammechanical said:**
> Canonical has Ubuntu Core as an immutable OS with Snap packaging providing the containers for the applications.
Ubuntu Core is 100% snap — even the kernel itself!

As an immutable system, you can't easily best that.

That's why Canonical is going with snap, and not using an existing system such as flatpak.

---

### Post by werewulf75 on 2024-09-19
> **Perfect Storm said:**
> I always advise people to get rid of Snap and rely on .deb and in cases flatpaks. Snap is sloooooooooow when you try to use an app that is packaged that way, also snap.d has a great impact on the bootup speed in a negative way.
Snap apps are neither slow here, nor does snap.d seem to have any impact on boot  speed. And that's in all three flavours I run here - (vanilla) Ubuntu 22.04, Ubuntu Unity 22.04, and Ubuntu Mate 22.04.

And my advice to people is and always has been, use whatever works for you from what's available.

---

### Post by Perfect Storm on 2024-09-20
> **werewulf75 said:**
> Snap apps are neither slow here, nor does snap.d seem to have any impact on boot  speed. And that's in all three flavours I run here - (vanilla) Ubuntu 22.04, Ubuntu Unity 22.04, and Ubuntu Mate 22.04.

And my advice to people is and always has been, use whatever works for you from what's available.

We have a hoard of people complaining about slowness due to Snap on the Zorin forum (based on Ubuntu 22.04) which where I work as a staff. And by running journalctl shows that Snap is a bottleneck.

---

### Post by Paddy Landau on 2024-09-20
> **Perfect Storm said:**
> We have a hoard of people complaining about slowness due to Snap on the Zorin forum (based on Ubuntu 22.04) which where I work as a staff. And by running journalctl shows that Snap is a bottleneck.
I don't know if Zorin is a good yardstick. Snap used to be excruciatingly slow to start after a reboot, when Canonical stupidly released it well before it was ready, but that problem has since been solved, and right now it's every bit as fast as flatpak and deb on Ubuntu (I've been using both snap and flatpak for a long time). Maybe Zorin is doing something that slows down snap?

In any case, there's no need to recommend to Ubuntu users to uninstall snap. If they choose not to use snap apps, it just sits there (as with any other app) doing nothing. All that happens is that those people lose out should they want to use snap in future, e.g. for Ubuntu Pro (which I believe is available with Zorin) or the few apps that are unavailable anywhere else (e.g. Adobe Reader).

---

### Post by Perfect Storm on 2024-09-20
> **Paddy Landau said:**
> I don't know if Zorin is a good yardstick. Snap used to be excruciatingly slow to start after a reboot, when Canonical stupidly released it well before it was ready, but that problem has since been solved, and right now it's every bit as fast as flatpak and deb on Ubuntu (I've been using both snap and flatpak for a long time). Maybe Zorin is doing something that slows down snap?

In any case, there's no need to recommend to Ubuntu users to uninstall snap. If they choose not to use snap apps, it just sits there (as with any other app) doing nothing. All that happens is that those people lose out should they want to use snap in future, e.g. for Ubuntu Pro (which I believe is available with Zorin) or the few apps that are unavailable anywhere else (e.g. Adobe Reader).

Personally I can't say as I don't use Snap, but when users reports back why the bootup is slow, we ask them to run some tests. But good if the slowness is solved. On zorin OS both flatpak and snap repositories are enable, so people can choose - but the problem which OP addressed is still real, both flat and snap requires insanely amount of space and newcomers from Windows can't understand why the 256GB SSD is full especially when they use both snap and flat at the same time, but that's a Zorin problem. So my advice to Zorin users on our board is to get rid snap ... well in most cases I ask if they use it at all, same goes to flat.

Now from an artists perspective; I really loath that snap apps icons is un-themable. :D Canonical should really change that.


Note: I'm using Pop OS where there's only flat enabled.

---

### Post by Paddy Landau on 2024-09-20
> **Perfect Storm said:**
> … both flat and snap requires insanely amount of space and newcomers from Windows can't understand why the 256GB SSD is full
The extra space is a result of the fact that they have to duplicate software to prevent dependency hell, and to sandbox the dependencies. There's no way around that with snap, flatpak, AppImage and the like. The price you pay for reliability and easy updatability is increased space.

It must be stated that Ubuntu is aimed primarily at organisations that can afford modern computers. Ubuntu really isn't the best choice for someone with an old machine with only 256 GB — you could try Xubuntu or, for severe cases, Lubuntu for those machines. Having said that, I have a 500 GB SSD containing everything including the UEFI partition, the boot partition, my home partition, all my photos and home videos, and I've installed a lot of snaps and flatpaks as well as debs. Even so, less than a third of the space has been used.

---

### Post by Perfect Storm on 2024-09-21
Just because you and I can afford good hardware, we see a lot of poor people with secondhand computers which have more than 10 years on their backs. It's not uncommon we see people running out of space.

and here I thought Ubuntu was for the people. I guess Canonical is just another faceless cooperation. It surely has changed since then.
Other than that we can agree on disagreeing on this matter.

---

### Post by Paddy Landau on 2024-09-21
> **Perfect Storm said:**
> Just because you and I can afford good hardware, we see a lot of poor people with secondhand computers which have more than 10 years on their backs. It's not uncommon we see people running out of space.

and here I thought Ubuntu was for the people. I guess Canonical is just another faceless cooperation. It surely has changed since then.
Other than that we can agree on disagreeing on this matter.
If you have an older computer and still want to stick with the Ubuntu environment, it's best to go to Lubuntu. That has rescued quite a few old computers in my time.

If the computer is too old even for that, try Debian.

---

### Post by TenPlus1 on 2024-09-22
@paddy - I've found that Bodhi Linux 7.0 works really well on older systems and is based on ubuntu 22.04 with a separate debian release as well just incase.

---

### Post by Paddy Landau on 2024-09-22
> **TenPlus1 said:**
> @paddy - I've found that Bodhi Linux 7.0 works really well on older systems and is based on ubuntu 22.04 with a separate debian release as well just incase.
Bodhi is good, and although it's based on Ubuntu, it isn't an official derivative. But, it's fine to use; it has a low footprint, even lower than Lubuntu. I still supports 32-bit, but I don't know for how long that will last. It would be interesting to know how many 32-bit systems using Linux are still in use worldwide.

---

### Post by Rubi1200 on 2024-09-22
I have Bodhi Linux on an old Intel Atom 1GB netbook. 

Runs very smoothly for me.

---

### Post by grahammechanical on 2024-09-22
> and here I thought Ubuntu was for the people. I guess Canonical is just  another faceless cooperation. It surely has changed since then

Here we go. It is now political.

I remember the years, and you must also remember them, when Ubuntu could be installed from a CD-ROM. Then a DVD-ROM was needed. Now, the Ubuntu ISO would not fit on a DVD-ROM. This is nothing to do with Snap packaging.

Ubuntu is built on Debian and the Debian developers discarded Canonical's Upstart software for Redhat's SystemD software to start and stop Linux services. Many Debian developers were against SystemD because it would develop to take control of so much of the OS. And it has. Those developers forked Debian and begun to develop Devuan.

Then there is the part the Gnome organisation played when it dropped Gnome 2 for Gnome 3 desktop environment and the Gnome 3 shell. Initially, Ubuntu was to run a Canonical user interface on Gnome DE that was called Unity. There were a lot of complaints about that.

Mark Shuttleworth also received a lot of abuse because Canonical was not going to help develop display managers using the Wayland protocol. Ubuntu was going to use a Canonical display manager called Mir.

In the end Unity and Mir were dropped and we have Ubuntu + Gnome 3 DE + Gnome 3 shell + SystemD + a Wayland compositor. This is the reason why Ubuntu will no longer fit or run on a lower specification computer. Those days were long gone before snap packaging was introduced into Ubuntu.

You may be aware that the Ubuntu mini ISO no longer exists. Install the latest Ubuntu (24.04) and the user gets two options - Just the Essentials (DE + utilities + Firefox) 0r a Full installation (minus the games).

The issue that people will have with 10 year old machines is the video adapter not having enough video memory; not having more than 1 GB RAM; small hard drive; and possibly not having a USB port to install Ubuntu from.

I do not forget that whatever edition of Ubuntu I want to use I can download it for free (as in beer). It does not matter if I am a home user (I am such) or a corporate user. Canonical makes its money from selling services and mainly to corporate organisations.

I can even get an additional 5 years support for Ubuntu LTS for up to five machines. Corporate users have to pay for more than five machines.

I have done very well out of Canonical. They have my thanks.

Regards

---

### Post by Perfect Storm on 2024-09-22
> **grahammechanical said:**
> Here we go. It is now political.



in the end is everything political to a degree. Our world is formed by it. ;)

---

### Post by Shibblet on 2024-09-23
> **Perfect Storm said:**
> in the end is everything political to a degree. Our world is formed by it. ;)

It's our fault too.

It's funny... everyone despises politicians.  Just being involved in politics gives you a negative branding.
And yet, we keep electing them.

---

### Post by werewulf75 on 2024-09-25
> **grahammechanical said:**
> ...I do not forget that whatever edition of Ubuntu I want to use I can download it for free (as in beer). It does not matter if I am a home user (I am such) or a corporate user. Canonical makes its money from selling services and mainly to corporate organisations.

I can even get an additional 5 years support for Ubuntu LTS for up to five machines. Corporate users have to pay for more than five machines.

I have done very well out of Canonical. They have my thanks.

Regards
+1

And they have my thanks too. Sometimes you could be forgiven for getting the impression that Canonical and Mark Shuttleworth are a lot of people's favourite abuse objects, instead of being appreciated for what they have done and keep on doing - innovating.

---

### Post by werewulf75 on 2024-09-25
> **Shibblet said:**
> It's our fault too.

It's funny... everyone despises politicians.  Just being involved in politics gives you a negative branding.
And yet, we keep electing them.
Because as a mass, as a species, humans are exceptionally stupid. :P 

Never make the mistake of underestimating mankind's stupidity.

---

### Post by 1fallen on 2024-09-25
> **werewulf75 said:**
> 
Never make the mistake of underestimating mankind's stupidity.
Got the Tee Shirt, makes for some interesting conversations

---

### Post by grahammechanical on 2024-09-25
Someone once said: "I never vote. The government always gets in." How true.

Regards

---

### Post by Shibblet on 2024-09-25
> **werewulf75 said:**
> Because as a mass, as a species, humans are exceptionally stupid. :P 

Never make the mistake of underestimating mankind's stupidity.

[IMG]https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQXFLvks9zaAdvsnNSpIBE2y-i9NYgPWRyb6A&s[/IMG]

---

### Post by poorguy on 2024-12-24
Snaps have gotten better with every release imo.

I use Lubuntu with Snaps which seem to work well. 

Over time new Snap updates will use up hard drive space so the user must remove the previous Snap updates.

I found a script either here on the Ubuntu forums or perhaps I stumbled  across it online but the script can be downloaded and ran and it does  remove the previous Snap updates to free up hard drive space.

[https://itsfoss.com/clean-snap-packages/](https://itsfoss.com/clean-snap-packages/)

[https://www.debugpoint.com/clean-up-snap/](https://www.debugpoint.com/clean-up-snap/)

May not be a problem for users with massive hard drives but I'm still using small drives.

Anyway my whole point is as a home user Snaps work based on my experience and I have no problem with containers.

In Puppy Linux we have SFS packages which is a container and I believe Antix Linux may also us SFS packages.

I look forward to the time when Ubuntu offers a 100% immutable distro with a desktop environment.

I also understand some user's complaints with Snap and other containers.

It's** Christmas Eve** so** Merry Christmas** to all who celebrate it. :)

---

### Post by deadflowr on 2024-12-24
> Over time new Snap updates will use up hard drive space so the user must remove the previous Snap updates.
The default setting is to retain just 2. (3 on Ubuntu Core)
So you should only ever have no more than 2 or 3 at any time.

You can periodically run a simple command/script to remove older unused versions.
The point of the revisioning system is to allow new updates to come, but still have an easy fallback if they're broken.

You can also put a hold on snaps to never update if you want.

---

### Post by poorguy on 2024-12-25
> **deadflowr said:**
> The default setting is to retain just 2. (3 on Ubuntu Core)
So you should only ever have no more than 2 or 3 at any time.

You can periodically run a simple command/script to remove older unused versions.


Okay poor explaining on my part as I was referring to the older unused versions.


Thanks **deadflowr** for the correction and explanation.

---

### Post by AR_Kozz on 2024-12-25
I am done with snaps, not because they take up too much root partition space, but because they make the boot process take forever from an HDD.

Snap for whatever reason creates about 40 virtual devices, then mounts every installed app, none of which are marked for startup under the system. After login, the HDD stays busy with more shenanigans for a few minutes more. It's at least 5 minutes before I can do anything. 

systemd-analyze blame tells me each of these virtual devices takes about 6 seconds of boot time, then each specific app mount another couple seconds. Some of it may be concurrent, but when the whole thing takes 2 minutes, I think the blame is there. This is like a virtual machine. 

Windows 10/11 starts cold on the same machine in seconds from an SSD, so it's not the machine's fault. Ubuntu is obsoleting itself from HDD install, is what's going on.

What's the best distro that sticks to Debian?

---

### Post by Paddy Landau on 2024-12-25
> **AR_Kozz said:**
> Windows 10/11 starts cold on the same machine in seconds from an SSD…
You're not comparing like-for-like. First, you say that Linux is booting from an HDD, while Windows boots from an SSD. Second, when you shut down Windows, it doesn't really shut down; it uses a sort of hibernation (called Fast Startup) in order to provide a fast startup. That's why Windows takes longer to shut down than does Linux.

To compare like-for-like, you need to use the same disk, and turn off Windows Fast Startup.

I personally don't have a problem with boot time on my desktop. Including the computer's POST time, and the time for me to type my LUKS passphrase and my login password, it takes under a minute. I'm using an SSD (four years old already, for what it's worth), on Ubuntu 22.04.

On my old laptop with an HDD, the same setup with fewer installed apps takes about four minutes! On that laptop, Windows 10 was unusably slow, which is one reason why I got rid of it. Like-for-like, even with Windows Fast Startup, Linux is significantly faster on that machine. The hardware makes a massive difference!

---

### Post by VMC on 2024-12-25
@ 				 				 					 						 	[**[COLOR=#000000]AR_Kozz[/COLOR]**]("https://ubuntuforums.org/member.php?u=164199")**[COLOR=#000000], [/COLOR]**I've never used Snaps nor will I.

"What's the best distro that sticks to Debian?"
 Mint comes to mind. I'm sure there are more out there., 

My Windows also boots fast. powercfg=off, Fast start=off.

---

