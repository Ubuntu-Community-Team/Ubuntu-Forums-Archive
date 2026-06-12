---
title: "Kubuntu vs ????"
date: 2021-05-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2021-05-17
So... I have been a Kubuntu user since 8.04 LTS Hardy Heron.  Looks like we just rounded the Alphabet back to H for Hirsute Hippo.  ;-)

Most of the features available in the Kubuntu distributions have been EXACTLY what I have wanted for many years.  Most of the issues, (sound card drivers, wi-fi drivers) have all been resolved with kernel patches, and updated drivers, and I have had a great working distribution for over 13 years.

I am currently running 20.04.2 LTS, and am playing around with 21.04 on a separate partition.  So far with 21.04, I have had two problematic "new-release" kernels, and had to go back to the previous one.  But, I understand that 21.04 is an interim-release, and isn't necessarily 100% "stable."

So, needless to say, I am a huge Kubuntu fan, and happy user.  

HOWEVER (is "but" in a Tuxedo)

**Are there any other distributions out there that use a Minimalist Software Setup** (Like Kubuntu Minimal Install), **as well as just the basic KDE applications** (again, like Kubuntu Minimal Install), **that can measure up to Kubuntu 20.04.2, in terms of usage?**

Now, this is not meant to be a "which one is better" thread, it is meant to point out differences in distributions, and personal opinions of preference.

---

### Post by malspa on 2021-05-17
If I was replacing my Kubuntu LTS installation, I'd probably go with a Debian netinstall and add KDE Plasma to that.

---

### Post by tea for one on 2021-05-17
PClinuxOS publish a minimal KDE ISO called Darkstar.

[https://www.pclinuxos.com/?page_id=180](https://www.pclinuxos.com/?page_id=180)

It is one of the distros which include a built-in Remaster utility, so you can add/subtract packages ad infinitum.

Whether it compares favourably to Kubuntu 20.04 - as the market research survey stated [COLOR="#0000FF"]50% of those polled expressed a positive interest[/COLOR].

I just made up the last bit................

---

### Post by guiverc on 2021-05-17
> **Shibblet said:**
> 
I am currently running 20.04.2 LTS, and am playing around with 21.04 on a separate partition.  So far with 21.04, I have had two problematic "new-release" kernels, and had to go back to the previous one.  But, I understand that 21.04 is an interim-release, and isn't necessarily 100% "stable."


I'll dispute the "*isn't necessarily 100% stable*"

From your description you've had issues with the 5.11 kernel, which is the same stack 20.04 gets if using the HWE stack at 20.04.3.  Ubuntu 21.04 just gets it first.

Releases are declared *stable* at release time, why there are *freeze* dates giving time to ensure stack is *stable* prior to the scheduled release date.

Either way you'll likely have the same issues with 20.04, **if** using the HWE stack once it moves to it...  (*it could be you're using the more stable **GA** stack on 20.04, but that's a choice you made, 20.04 being a LTS offers both stacks*).


ps:  I like Lubuntu, it's using the same Qt5 base and is lighter, though if using KDE apps that require KF5 the *lighter* LXQt will somewhat be moot.

---

### Post by CatKiller on 2021-05-17
I don't get it. You're experienced with Kubuntu. You *like* Kubuntu. Why would you want to use something else?

Personally, the only thing that I'd switch away from Kubuntu for is KDE Neon.

---

### Post by coffeecat on 2021-05-18
*Moved to ULOS chat*

---

### Post by Dragonbite on 2021-05-18
When talking about KDE the first thing(s) that come to mind is Kubuntu and KDE Neon. 

KDE Neon's non-KDE bits are from Ubuntu 20.04, which you said works on your system.  The KDE bits, however, is constantly being updated with the latest (ultra-latest or stable-latest).  It's a very good semi-rolling-release for KDE goodness!  It may be the smoothest choice for you until maybe 22.04 (*that's the next LTS, isn't it?*)

Otherwise when I have system-type of issues I go between Ubuntu, Fedora and sometimes openSUSE.  In the past when hardware didn't work out-of-the-box (like Broadcom wireless adapters) I went between the distros to see who was the first to support them by default.  For all of the issues I've had, it differed who "won" though once one distro got it, the others followed suit usually by the next release.

Fedora's KDE implementation is pretty good and at one point it included all KDE apps (Calligra office instead of LibreOffice for example) though of course you have the option to install anything. 

I think Fedora does, and I am pretty sure openSUSE, provide an all-inclusive DVD or a net-based installer so that you can select what you want installed right in the beginning.

But for Ubuntu-familiar Kubuntu alternative you may want to look at KDE Neon.  

Oh, and I don't remember if they include Snaps, or Flatpak by default.

---

### Post by malspa on 2021-05-18
Doe KDE Neon have some kind of minimal installation option like Kubuntu?

---

### Post by Dragonbite on 2021-05-18
> **malspa said:**
> Doe KDE Neon have some kind of minimal installation option like Kubuntu?

Does not look like it does specifically.
[LIST]
[*]User Edition = stable
[*]Testing Edition = pre-release
[*]Unstable Edition = same-day pre-release
[*]Developer Edition = like Unstable Edition but with development libraries included
[/LIST]
It does run a Live environment so you can throw it on a USB and test it out and see what it does come with.

---

### Post by Shibblet on 2021-05-18
> **guiverc said:**
> I'll dispute the "*isn't necessarily 100% stable*"

From your description you've had issues with the 5.11 kernel, which is the same stack 20.04 gets if using the HWE stack at 20.04.3.  Ubuntu 21.04 just gets it first.

Releases are declared *stable* at release time, why there are *freeze* dates giving time to ensure stack is *stable* prior to the scheduled release date.

Either way you'll likely have the same issues with 20.04, **if** using the HWE stack once it moves to it...  (*it could be you're using the more stable **GA** stack on 20.04, but that's a choice you made, 20.04 being a LTS offers both stacks*).

ps:  I like Lubuntu, it's using the same Qt5 base and is lighter, though if using KDE apps that require KF5 the *lighter* LXQt will somewhat be moot.

Hey!  Thanks for that.  I didn't know how the kernel releases came out.  That makes sense to release the newer kernel patches to an interim release before sending them to the LTS version.

I'm not disputing the way the function works.  However, with 21.04, I have already had 2 Kernel Update patches that completely "borked" the system.  Like a toddler with no shoes, I got "no bootie."
However, when I booted to a previous kernel, everything seemed to work just fine.  So, maybe "stablity" isn't the right word, because with the right kernel, it ran great.

> **CatKiller said:**
> I don't get it. You're experienced with Kubuntu. You *like* Kubuntu. Why would you want to use something else?

Personally, the only thing that I'd switch away from Kubuntu for is KDE Neon.

Well... there are two problems here.  I really like Kubuntu, and legitimately do not want to go with a different distribution.

The first problem is the direction that Ubuntu is going with Snaps... moreso, the direction Ubuntu has already gone with Snaps.
I am not a big fan of Snapsl (yet).  I like the idea of how they work, but they currently limit some system functions, and tend to launch slower than standard packages.  Regardless... at this point, I would rather stick with standard packages.

Ubuntu just pulled a bad-bad with Chromium.  The standard package for Chromium is no longer available.  You can add a Chromium PPA if you like, but it does not matter.  You can remove Snap itself, and it does not matter.  When it comes to installing Chromium, you have NO CHOICE, but to install the Snap.

And to be perfectly honest, my second problem is that this doesn't bode well for the future...  Removal of choice is really against most of the fundamental principals of GNU/Linux in general.  I'm not going to go full on Stallman here, but a pretty popular application has just been thrown under the bus.  This may be the direction Canonical goes with all of their applications.  And they haven't worked out all the bugs yet.

---

### Post by grahammechanical on 2021-05-18
To get back to topic ...

I would not be surprised if the Kubuntu minimum ISO image is in fact the Ubuntu minimal ISO image from which we can choose whatever desktop environment and software we wish.

It seems that there actually is a mini ISO for Ubuntu 20.04. I was not sure if there was one.

[https://askubuntu.com/questions/1233746/download-ubuntu-minimal-iso-20-04lts](https://askubuntu.com/questions/1233746/download-ubuntu-minimal-iso-20-04lts)

Seeing that it is available from an archive called legacy-images I am not sure for how long the mini ISO will be available from Canonical. I think the preference of Canonical is that we use the server ISO and install whatever desktop environment and software we want.

Shall I? Yes, I will! I will throw the cat among the pigeons and say that I guess that Canonical is intending that Ubuntu Core becomes the mini ISO once it becomes possible to install desktop environment and User Interface snaps on Ubuntu core. 

Read what Redhat is going to do to Fedora to make it an Immutable operating system. It reads very much like what Ubuntu core is but is further advanced in the desktop environment area. Canonical has been focused on the Internet Of Things and is only now considering making Ubuntu an immutable OS.

[https://fedoramagazine.org/what-is-silverblue/](https://fedoramagazine.org/what-is-silverblue/)

Regards

---

### Post by Shibblet on 2021-05-18
> **grahammechanical said:**
> To get back to topic ...

I would not be surprised if the Kubuntu minimum ISO image is in fact the Ubuntu minimal ISO image from which we can choose whatever desktop environment and software we wish.

It seems that there actually is a mini ISO for Ubuntu 20.04. I was not sure if there was one.

[https://askubuntu.com/questions/1233746/download-ubuntu-minimal-iso-20-04lts](https://askubuntu.com/questions/1233746/download-ubuntu-minimal-iso-20-04lts)

Seeing that it is available from an archive called legacy-images I am not sure for how long the mini ISO will be available from Canonical. I think the preference of Canonical is that we use the server ISO and install whatever desktop environment and software we want.

Shall I? Yes, I will! I will throw the cat among the pigeons and say that I guess that Canonical is intending that Ubuntu Core becomes the mini ISO once it becomes possible to install desktop environment and User Interface snaps on Ubuntu core. 

Read what Redhat is going to do to Fedora to make it an Immutable operating system. It reads very much like what Ubuntu core is but is further advanced in the desktop environment area. Canonical has been focused on the Internet Of Things and is only now considering making Ubuntu an immutable OS.

[https://fedoramagazine.org/what-is-silverblue/](https://fedoramagazine.org/what-is-silverblue/)

Regards

Thanks for the info!

I'm trying to picture "kde-desktop" as a Snap package.  ;-)

---

### Post by CatKiller on 2021-05-18
> **Shibblet said:**
> I'm trying to picture "kde-desktop" as a Snap package.  ;-)
I'd imagine that it would work quite well, since KDE applications use the same set of frameworks libraries. You'd just make a snap of those, like [this one](https://snapcraft.io/kde-frameworks-5-qt-5-15-core20), and then all the KDE applications snaps would connect to that using the standard snap connections mechanism.

---

### Post by Shibblet on 2021-05-18
> **CatKiller said:**
> I'd imagine that it would work quite well, since KDE applications use the same set of frameworks libraries. You'd just make a snap of those, like [this one](https://snapcraft.io/kde-frameworks-5-qt-5-15-core20), and then all the KDE applications snaps would connect to that using the standard snap connections mechanism.

And I guess I am going to de-rail my own thread here... but what causes Snaps to run so much slower than packages?   In almost every Snap I have downloaded, I do not get the same "quality" of use as I do with the basic packages.

---

### Post by CatKiller on 2021-05-18
> **Shibblet said:**
> And I guess I am going to de-rail my own thread here... but what causes Snaps to run so much slower than packages?   In almost every Snap I have downloaded, I do not get the same "quality" of use as I do with the basic packages.
They don't run slower. They *start* slower, the first time you launch them, since the squashfs filesystem they come in needs to be decompressed, and the sandboxed environment provided for the application needs to be set up, but they don't *run* any slower at all.

The slow startup and the restrictions for the sandbox are the issues that people have with them. The devs have been experimenting with different compression routines, so the former is better than it was, and the latter is a necessary part of the sandbox; I'd imagine that there will be less friction there as developers get more experience.

Plus, people that aren't using Ubuntu are suspicious of the snaps being maintained by either the application developers themselves, helpful passers-by (just like PPAs), or by Ubuntu devs. As an Ubuntu user, that's exactly what you'd want, though. Plus there's lots of noise because the Mint developer was grumpy that everyone talks about Pop OS these days instead of Mint, and he wanted some publicity.

---

### Post by Dragonbite on 2021-05-19
> **CatKiller said:**
> Plus, people that aren't using Ubuntu are suspicious of the snaps being maintained by either the application developers themselves, helpful passers-by (just like PPAs), or by Ubuntu devs. As an Ubuntu user, that's exactly what you'd want, though.

I don't know.  I really didn't like having to rely on PPAs so I am happier with Snaps than PPAs and am most happy if it is maintained by the project themselves in any format.

> **CatKiller said:**
> Plus there's lots of noise because the Mint developer was grumpy that everyone talks about Pop OS these days instead of Mint, and he wanted some publicity.

Ha! :lol::-({|=  Haven't quite heard it that straight forward, but I can see it though.

Funny thing is Pop! OS has moved to Flatpak instead of Snaps.

---

### Post by mastablasta on 2021-05-21
> **grahammechanical said:**
> To get back to topic ...

I would not be surprised if the Kubuntu minimum ISO image is in fact the Ubuntu minimal ISO image from which we can choose whatever desktop environment and software we wish.

it's a basic OS with some tools and utilities, but without any extra apps (e.g. without office, browser etc). as if you really installed only basic desktop and kernel. as i remember when i ran Xubuntu in virtualbox, you would get this by installing Ubuntu minimal, then adding only XFCE. so you would get the XFCE but not the full Xubuntu "experience".

> **Shibblet said:**
> 
However, when I booted to a previous kernel, everything seemed to work just fine.  So, maybe "stablity" isn't the right word, because with the right kernel, it ran great.

stability means packages don't change and stay the same. on LTS they remain more or less the same through the 5 year support (which can be extended). i am on 18.04 currently with kernel 4.15. as i have very old hardware this doesn't matter too much. but on my kids PC we installed HWE kernel which brought in kernel from 19.10 at the time but kept other packaged same.

> 
The first problem is the direction that Ubuntu is going with Snaps... moreso, the direction Ubuntu has already gone with Snaps.
I am not a big fan of Snapsl (yet).  I like the idea of how they work, but they currently limit some system functions, and tend to launch slower than standard packages.  Regardless... at this point, I would rather stick with standard packages.

well, if it works...

these kind of packages bring all sorts of possibilities for the future and rather than dislike them we should help improve them. just saw a video of Linus complaining how difficult it it to package and maintain for Linux distros as there are so many of them and have different library versions. Debian stable (see meaning of stable above) for example has very old packages and the diving app he is making really needs the new ones. but if you install the new ones you break the OS (dependency hell?!). anyway snap is one of the solutions for such cases. you pack once and it works on many distros (old and young). additionally you can have multiple version of same app. maybe version 8 of Libre office had really good MS office compatibility, but that version 5 really had no issues with certain file you use. well you can now easily have version 8 and 5 installed at the same time.

> 
And to be perfectly honest, my second problem is that this doesn't bode well for the future...  Removal of choice is really against most of the fundamental principals of GNU/Linux in general.  I'm not going to go full on Stallman here, but a pretty popular application has just been thrown under the bus.  This may be the direction Canonical goes with all of their applications.  And they haven't worked out all the bugs yet.

not really. you can always create your own chromium PPA and maintain it. the freedom is still there. maybe not so convenient for the user, but it's not like you are locked into repos (like with Apple store).

Flatpack, snap and similar need to improve, but at the same time they offer so many new possibilities to the OS and are the right step ahead.

as for the original post - check out OpenSUSE KDE. give it a spin in virtualbox or with live boot. i was seriously considering it due to its ease of use. however eventually basic Kubuntu won me over after Mint KDE (at the time) had too many mistakes upon release.

---

### Post by malspa on 2021-05-21
How nice that Snaps opens up all sorts of possibilities for the future. But if that's the only option I have for installing one of my favorite apps in Kubuntu, I'll probably dump Kubuntu. (I don't use Chromium.) But that's okay; as I mentioned in post #2, I'd go with a Debian netinstall. I'm a long-time Kubuntu user, but it isn't the only distro I run, and I can get along fine without it. I'll wait and see what happens with the next LTS. I'm not really liking the way Canonical pushes things at users sometimes, I guess.

---

### Post by SeijiSensei on 2021-05-21
I'm running Kubuntu 20.04 and 21.04 on a few machines. Never was I required to install a snap except for Chromium which I hardly ever use. Every other package on my system was installed using apt. Why do you think snaps are a part of Kubuntu?

If I had to run snaps for every piece of software I use regularly, I would change distros. So far, though, that's not the case with Kubuntu, at least for me.

---

### Post by VMC on 2021-05-21
Yes. The first thing to go is snap. Kubuntu apt installs all the programs I need without snap.

---

### Post by Shibblet on 2021-05-24
> **mastablasta said:**
> not really. you can always create your own chromium PPA and maintain it. the freedom is still there. maybe not so convenient for the user, but it's not like you are locked into repos (like with Apple store).

Well, that's the problem specifically.  Chromium cannot be replaced by a PPA at this point (i.e. 21.04)... At least, if there is a way, it's not as simple as adding a new PPA.  I have gone to the point of not only removing the Chromium Snap package, but actually removed Snap and SnapD to make sure the Chromium PPA was installed over the Snap.  Lo-and-behold, when I went to install Chromium, I sat there in utter amazement as I watched APT install Snap and SnapD, then install the Chromium Snap on top of it.

So, this is what I am afraid of.  It's all about choice, and that choice was removed.  Is Canonical going to remove the choice of Regular Packages and PPA's in lieu of Snaps.

> **SeijiSensei said:**
> I'm running Kubuntu 20.04 and 21.04 on a few machines. Never was I required to install a snap except for Chromium which I hardly ever use. Every other package on my system was installed using apt. Why do you think snaps are a part of Kubuntu?

If I had to run snaps for every piece of software I use regularly, I would change distros. So far, though, that's not the case with Kubuntu, at least for me.

I use Brave Browser regularly, and there is both a Snap on [snapcraft.io]("snapcraft.io"), and a Package that can be added with a GPG key from here: [https://brave.com/linux/#linux]("https://brave.com/linux/#linux").

So, if I use the Snap... there are problems with the actual interface.  I cannot save files to anything besides the Primary Download Directory, nor can I load my saved bookmarks from any other drive.
Similar problems with MakeMKV as a Snap.  If I use the PPA, I can install the application, and save my MKV's to my secondary (physical) hard drive.  However, if I download the Snap, the interface will not allow me to change to that drive.  Not really sure why...

For the time being, I am not big on Snaps, due to usability.  I actually like the idea of applications being somewhat independent of the OS, and of course, being universally usable across distributions.  This not only makes maintaining these apps easier for developers, but users as well.   You wouldn't have to worry about a new distribution not having a package available for you.  If these functions change in the future, then I may be more **APT** to use **SNAPS!**

BWAHAHAHAHA.... Sorry.

---

