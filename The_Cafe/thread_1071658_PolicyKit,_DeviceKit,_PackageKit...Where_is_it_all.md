---
title: "PolicyKit, DeviceKit, PackageKit...Where is it all going?"
date: 2009-02-16
forum: The Cafe
---

### Post by ghindo on 2009-02-16
I've noticed that all of these new projects coming out - [PackageKit]("http://en.wikipedia.org/wiki/PackageKit"), [DeviceKit]("http://en.wikipedia.org/wiki/DeviceKit"), [PolicyKit]("http://en.wikipedia.org/wiki/PolicyKit"), [ConsoleKit]("http://freedesktop.org/wiki/Software/ConsoleKit") - but my question is, where are they all going?  Are all of these projects leading to a more unified Linux desktop?  Are they helping at all?  How are they related?

---

### Post by cardinals_fan on 2009-02-16
> **ghindo said:**
> I've noticed that all of these new projects coming out - [PackageKit]("http://en.wikipedia.org/wiki/PackageKit"), [DeviceKit]("http://en.wikipedia.org/wiki/DeviceKit"), [PolicyKit]("http://en.wikipedia.org/wiki/PolicyKit"), [ConsoleKit]("http://freedesktop.org/wiki/Software/ConsoleKit") - but my question is, where are they all going?  Are all of these projects leading to a more unified Linux desktop?  Are they helping at all?  How are they related?
I personally think that PackageKit is an utter abomination that should be sacrificed to the fiery bowels of a volcano.  So I don't use it.

---

### Post by OutOfReach on 2009-02-16
All I know is that DeviceKit is an alternative to HAL. I haven't used it, but I heard good things.

---

### Post by ghindo on 2009-02-16
> **cardinals_fan said:**
> I personally think that PackageKit is an utter abomination that should be sacrificed to the fiery bowels of a volcano.  So I don't use it.I've never actually used PackageKit, so why do you say that?  I would think that a unified front-end for various package managers would be a good thing.

---

### Post by Slug71 on 2009-02-16
> **OutOfReach said:**
> All I know is that DeviceKit is an alternative to HAL. I haven't used it, but I heard good things.

Devicekit is going to replace HAL.

I like Packagekit. Its still in development though so i dont know how people can complain about it. Write to the devs/maintainers and let them no what you want or what is wrong and maybe they will do something about it.
I bet in a couple years when most distros or at least the big ones have it by default, no other frontend will be able to touch it.

---

### Post by cardinals_fan on 2009-02-16
> **ghindo said:**
> I've never actually used PackageKit, so why do you say that?  I would think that a unified front-end for various package managers would be a good thing.
The problem isn't so much with PackageKit as it is with all the distros who have jumped on the bandwagon when it is not anywhere near ready yet.  PackageKit holds the award for the buggiest piece of software I've ever tried to use.  Every system I've used it on (Fedora, Foresight, openSUSE) has had issues.  The package manager crashes randomly, but the biggest issue is the update-applet-thingy.  It was very unstable, used a ton of resources, and essentially grabs control of the system.  Example: I had a clean new Fedora install.  I wanted to update it.  The PackageKit update icon sat there in the corner for five minutes apparently doing nothing, so I opened up a shell and tried to update with yum.  No can do because PackageKit had control over the system.  Finally it popped up an upgrade box, then proceded to crash halfway through the update.

To be quite frank, I don't see the point.  The biggest "issue" regarding Linux packaging is the existence of different formats (something I don't personally oppose), and PackageKit does nothing there.  All it does is provide the same GUI for many different underlying systems.

---

### Post by Skripka on 2009-02-16
> **cardinals_fan said:**
> The problem isn't so much with PackageKit as it is with all the distros who have jumped on the bandwagon when it is not anywhere near ready yet.  PackageKit holds the award for the buggiest piece of software I've ever tried to use.  Every system I've used it on (Fedora, Foresight, openSUSE) has had issues.  The package manager crashes randomly, but the biggest issue is the update-applet-thingy.  It was very unstable, used a ton of resources, and essentially grabs control of the system.  Example: I had a clean new Fedora install.  I wanted to update it.  The PackageKit update icon sat there in the corner for five minutes apparently doing nothing, so I opened up a shell and tried to update with yum.  No can do because PackageKit had control over the system.  Finally it popped up an upgrade box, then proceded to crash halfway through the update.

To be quite frank, I don't see the point.  The biggest "issue" regarding Linux packaging is the existence of different formats (something I don't personally oppose), and PackageKit does nothing there.  All it does is provide the same GUI for many different underlying systems.

Must I say "I agree1111!!!!!!" or can I just say "+1"?

PackageKit is worse than the new Adept at finding things you have already installed on your machine.

---

### Post by ghindo on 2009-02-16
> **OutOfReach said:**
> All I know is that DeviceKit is an alternative to HAL. I haven't used it, but I heard good things.I found [this]("http://lists.freedesktop.org/archives/hal/2008-May/011560.html"), which details DeviceKit pretty thoroughly, and why it's replacing HAL.  Interesting stuff.

---

### Post by bruce89 on 2009-02-16
> **Skripka said:**
> PackageKit is worse than the new Adept at finding things you have already installed on your machine.

The great thing about Free Software is the fact it improves.

You missed out WebKit (only the name is similar in this case).

---

### Post by cardinals_fan on 2009-02-16
> **bruce89 said:**
> The great thing about Free Software is the fact it improves.
Not necessarily.  Because the source is available, floundering projects with promising ideas will generally fork and grow, but that doesn't mean that everything gets better all the time.

---

### Post by Skripka on 2009-02-16
> **bruce89 said:**
> The great thing about Free Software is the fact it improves.


Except in the case of Adept...which is going extinct, and unfortunately Kubuntu is moving to kPackageKit instead.....Grrrrrrrrrrrrrrrrrrrrrrrrrrrrr.

Oh well, I needed a kick in the pants to try out Arch and KDEmod.

---

### Post by Polygon on 2009-02-16
i tried adept when i tried kubuntu. its laughably bad compared to synaptic.

---

### Post by lzfy on 2009-02-16
> **Skripka said:**
> Except in the case of Adept...which is going extinct, and unfortunately Kubuntu is moving to kPackageKit instead.....Grrrrrrrrrrrrrrrrrrrrrrrrrrrrr.

Oh well, I needed a kick in the pants to try out Arch and KDEmod.

Adept on KDE3 was ok, but on KDE4 it's the worst piece of software I've ever used.

---

### Post by ghindo on 2009-02-16
PackageKit seems to have a lot more potential than Adept, as it's become the *default* yum front-end for Fedora, and seems to have the full blessing of freedesktop.org.  Is there any word about Ubuntu incorporating it?

---

### Post by HermanAB on 2009-02-17
The only problem I have with these projects is the use of XML for configuration files, since it is impossible to edit XML by hand.

Cheers,

Herman

---

### Post by ghindo on 2009-02-17
> **HermanAB said:**
> The only problem I have with these projects is the use of XML for configuration files, since it is impossible to edit XML by hand.

Cheers,

HermanI thought that XML was sort of becoming the defacto standard for these types of things.  I would have thought that this sort of standardization would be a good thing?  After all, it seems better to have a W3C recommendation than a different type of configuration file for almost every program.

---

### Post by RiceMonster on 2009-02-17
> **HermanAB said:**
> The only problem I have with these projects is the use of XML for configuration files, since it is impossible to edit XML by hand.

Cheers,

Herman

Agreed. I hate it when stuff stops working, and I have to add some obscure XML stuff to a file to fix it.

---

### Post by gnomeuser on 2009-02-17
> **ghindo said:**
> I've noticed that all of these new projects coming out - [PackageKit]("http://en.wikipedia.org/wiki/PackageKit"), [DeviceKit]("http://en.wikipedia.org/wiki/DeviceKit"), [PolicyKit]("http://en.wikipedia.org/wiki/PolicyKit"), [ConsoleKit]("http://freedesktop.org/wiki/Software/ConsoleKit") - but my question is, where are they all going?  Are all of these projects leading to a more unified Linux desktop?  Are they helping at all?  How are they related?

PackageKit aside giving us one set of tools to manage packages will give application developers an interface to install things on demand. Now you can see this in gstreamer capable multimedia applications which will search for the required plugins and offer to install them. Work is also being done to let the command line install app when the typed command is not found, fonts on demand and so on. Before we had a unifying framework for this applications could not rely on such functionality. In the end this will lead to a slimmer desktop with only what you need installed, when you need it.

ConsoleKit handles seats, it is needed to make things like fast user switching work correctly. Imagine user 1 and 2 switching, user 1 is using the sound card when user 2 is switched to.. what happens to the state of the soundcard and how do we handle switching back.

PolicyKit allows us to directly elevate a single task to a higher level of privilage. You get a fine grained system for setting policy for users. Say user 1 may update the system and alter the system time but he may not remove packages or install new packages. This is instead of elevating the entire application, meaning that the toolkit and everything runs as root - which is bad for security. For a single user machine you still benefit as you get to set the things you never want to be asked to authenticate for.

DeviceKit is the replacement for HAL, HAL is good at it's job but a lot of functionality has snuck in there that is a duplicate of things like udev. It is also quite a cluttered codebase. DeviceKit is a smaller, neater codebase with a cleaner interface. Every bit of functionality is then added as modules, so we have DeviceKit-disks and DeviceKit-power today. As a user you shouldn't notice the switch, functionality is retained at a desktop level as well as expanded. E.g. we have been able to pull out a bunch of code from gnome-power-manager making it cleaner and more reliable, there is also being added such things as SMART notifications for harddrive problems and a new module for nautilus that uses DeviceKit-disks to format inserted media. This list will naturally grow as work progresses.

In short, these are all pieces of the puzzle to allow the desktop to function more uniformly, with greater reliablity and functionality.

---

### Post by lzfy on 2009-02-17
> **ghindo said:**
> PackageKit seems to have a lot more potential than Adept, as it's become the *default* yum front-end for Fedora, and seems to have the full blessing of freedesktop.org.  Is there any word about Ubuntu incorporating it?

It's available with the latest beta of Kubuntu, don't know about Ubuntu though.

---

### Post by Slug71 on 2009-02-17
> **ghindo said:**
> PackageKit seems to have a lot more potential than Adept, as it's become the *default* yum front-end for Fedora, and seems to have the full blessing of freedesktop.org.  Is there any word about Ubuntu incorporating it?

Adept is being dropped for Kpackagekit for 9.04 if i'm correct. If not then definitely 9.10.

Packagekit will also make its way to Ubuntu by default in 9.10.

---

### Post by Skripka on 2009-02-17
> **Slug71 said:**
> Adept is being dropped for Kpackagekit for 9.04 if i'm correct. If not then definitely 9.10.

Packagekit will also make its way to Ubuntu by default in 9.10.

I think for 9.04 at least on Kubuntu, as all development on Adept has ceased.  Too bad-PackageKit is one of the reasons I tried Fedora10 and hated it.

The new Adept was really flakey...I've tried KpackageKit from the repos and it is gawd awful-Adept at least had a pretty GUI and you could make a fair amout of sense, even if it couldn't find any packages installed on your system.

One of the reasons I tried Fedora10, and it didn't live on my machine longer than an hour-was due to how bad PackageKit is.

Niether of these tools in the Ubuntu repos, in their current state of development, is even in the same league of functionality and reliability as Synaptic on *Buntu.

---

### Post by Polygon on 2009-02-17
surely synaptic development is still going on, and you can just apt-get install synaptic and use that instead of packagekit.

---

### Post by ssam on 2009-02-17
> **HermanAB said:**
> it is impossible to edit XML by hand.

< :-) >
i used to have that problem with ascii files. you just miss out one bit and then you characters all get shifted. really fiddly.

then i discovered 'text editors'. they let you enter a letter with a single keystroke. every time i save the file i can be sure that the output will be a valid ascii file.

</ :-) >

if you are editing XML files with a text editor, then that would be hard. you need something that makes it impossible to write something that is not valid XML.

---

### Post by Vadi on 2009-02-17
The *Kit thing is just a naming scheme used by one particular programmer.

PackageKit is probably one the less useful tool out of the family - it's aim is to create a single interface for different package formats. No, this does not mean that a single distro will support multiple package formats. All it means is that all distros, with their different package formats, will have the same interface.

Quite stupid if you ask me. Something like... a single package format would have been way more productive.

---

### Post by RiceMonster on 2009-02-17
> **ssam said:**
> < :-) >
i used to have that problem with ascii files. you just miss out one bit and then you characters all get shifted. really fiddly.

then i discovered 'text editors'. they let you enter a letter with a single keystroke. every time i save the file i can be sure that the output will be a valid ascii file.

</ :-) >

if you are editing XML files with a text editor, then that would be hard. you need something that makes it impossible to write something that is not valid XML.

I don't think he meant literally impossible, I think he was saying it's a bit of a pain, which is the case of PolicyKit, it really is.

---

### Post by Slug71 on 2009-02-17
> **Polygon said:**
> surely synaptic development is still going on, and you can just apt-get install synaptic and use that instead of packagekit.

From what i understand, Synaptic will still be there.

Just add/remove and Update Manager will be replaced by Packagekit's.

---

### Post by Slug71 on 2009-02-17
> **Vadi said:**
> The *Kit thing is just a naming scheme used by one particular programmer.

PackageKit is probably one the less useful tool out of the family - it's aim is to create a single interface for different package formats. No, this does not mean that a single distro will support multiple package formats. All it means is that all distros, with their different package formats, will have the same interface.

Quite stupid if you ask me. Something like... a single package format would have been way more productive.

Again, Packagekit is still in development. Once it becomes adopted more across the board i think you will see development for it move along a lot faster and become a lot more stable too. Distros will probably be able to customize the interface to make it unique to them too.

A cross-distro frontend is a big step forward for Linux and its package management  IMO.

Next we just need a backend to become cross-distro. I think that may happen with Smart Package Manager.

Once that happens and they are nicely tied in with each other i think we may see a universal package format become available while still being able to use native packages.

---

### Post by Dekkon on 2009-02-17
> **ghindo said:**
> I've noticed that all of these new projects coming out - [PackageKit]("http://en.wikipedia.org/wiki/PackageKit"), [DeviceKit]("http://en.wikipedia.org/wiki/DeviceKit"), [PolicyKit]("http://en.wikipedia.org/wiki/PolicyKit"), [ConsoleKit]("http://freedesktop.org/wiki/Software/ConsoleKit") - but my question is, where are they all going?  Are all of these projects leading to a more unified Linux desktop?  Are they helping at all?  How are they related?

There will never be a unified desktop, sadly, people have to work to create there own projects instead of creating one or two good products. 

Quality over quantity is just something I believe the open-source community does not understand.

---

### Post by ghindo on 2009-02-17
> **Vadi said:**
> Quite stupid if you ask me. Something like... a single package format would have been way more productive.I would be really surprised if a single package format ever happened.  Every different package format has its advantages, disadvantages, advocates and haters.  It would be virtually impossible to unify the Linux community with one package format.  

On the other hand, attempting to standardize the front-end for all of these various package management systems seems much more realistic.

---

### Post by Dekkon on 2009-02-17
> **ghindo said:**
> I would be really surprised if a single package format ever happened.  Every different package format has its advantages, disadvantages, advocates and haters.  It would be virtually impossible to unify the Linux community with one package format.  

On the other hand, attempting to standardize the front-end for all of these various package management systems seems much more realistic.

It's a start but I believe one package management system would benefit users in more advantages, but because people can't get along, we can't agree on one. :( 

So were stuck with the problem of looking for packages, if there not made, compiling, if that doesn't work, looking for tutorials, if there isn't tutorials then your screwed. Come on people, do you really expect people to go through this every time to install software.

---

### Post by ghindo on 2009-02-17
> **Dekkon said:**
> It's a start but I believe one package management system would benefit users in more advantages, but because people can't get along, we can't agree on one. :( 

So were stuck with the problem of looking for packages, if there not made, compiling, if that doesn't work, looking for tutorials, if there isn't tutorials then your screwed. Come on people, do you really expect people to go through this every time to install software.I would think that most of those problems would be solved by the massive software repositories that most distributions have.  When have you run into these problems?

---

### Post by Dekkon on 2009-02-17
> **ghindo said:**
> I would think that most of those problems would be solved by the massive software repositories that most distributions have.  When have you run into these problems?

Proprietary software.
Apps from Websites, packages for this distro but not this distro. 
Independent Developers, they usually only package for there distro only. Good example is the many programs on KDE-Apps.org. 

It happens more then you think, just because people use Linux doesn't mean people don't use Proprietary software, or software that is not in the repos.

---

### Post by Vadi on 2009-02-17
> **Slug71 said:**
>  Distros will probably be able to customize the interface to make it unique to them too.


The whole point of PackageKit is one interface, not many.

---

### Post by ghindo on 2009-02-17
> **Dekkon said:**
> Proprietary software.
Apps from Websites, packages for this distro but not this distro. 
Independent Developers, they usually only package for there distro only. Good example is the many programs on KDE-Apps.org. 

It happens more then you think, just because people use Linux doesn't mean people don't use Proprietary software, or software that is not in the repos.That's true.  Although, it seems to me that most Linux software comes available in .deb, .rpm, and source code.  And if I'm not mistaken, there have been moves to make .rpm the standard format, but those have fallen through.

---

### Post by Polygon on 2009-02-17
> **Slug71 said:**
> 

Once that happens and they are nicely tied in with each other i think we may see a universal package format become available while still being able to use native packages.

again, LINUX IS NOT BINARY COMPATIBLE 

even if there was one standard package format, there would still have to be different packages for debian, suse, mandrivia, arch, etc etc. 

so we might as well have different package formats, cuase even if everything used one format, we would be even more confused

"is this a debian deb or a suse deb?"

---

### Post by Dekkon on 2009-02-17
KPackageKit integrates right into the KDE System Settings, thats enough to get my vote, also never had a problem with it on Fedora. :)

I am sick of having 148 different applications in my start menu that could easily be inside one Control Panel. Another example is Opensuse has Yast and KDE System Control both installed, that means there is two apps for Video, Sound, Network, etc., which is very redundant In My Opinion. 

Integration is a great thing, and something I think some distributions need to work on.

---

### Post by bruce89 on 2009-02-17
> **Vadi said:**
> The whole point of PackageKit is one interface, not many.

Technically PackageKit is just a specification. Each distro could have its own UI on top, but they won't.

> **Polygon said:**
> again, LINUX IS NOT BINARY COMPATIBLE 

even if there was one standard package format, there would still have to be different packages for debian, suse, mandrivia, arch, etc etc. 

so we might as well have different package formats, cuase even if everything used one format, we would be even more confused

"is this a debian deb or a suse deb?"

It's a thing people overlook. The libraries in different distros can be incompatable, so a unified package would be impossible without limiting what versions of libraries you're allowed to use like LSB does.

---

### Post by rockin_goliath on 2009-02-17
Does anyone know for certain if Packagekit will be in Jaunty or not? Any links to mailing lists detailing this?

---

### Post by ghindo on 2009-02-17
> **rockin_goliath said:**
> Does anyone know for certain if Packagekit will be in Jaunty or not? Any links to mailing lists detailing this?Sure looks like [PackageKit will be in Jaunty](http://packages.ubuntu.com/jaunty/packagekit); [DeviceKit, too](http://packages.ubuntu.com/jaunty/devicekit).

**EDIT:**  Heck, it looks like all the "Kits" mentioned in this thread (DeviceKit, ConsoleKit, PackageKit, PolicyKit) will be included in Jaunty.  Not sure if any of them will come installed by default.

---

### Post by bruce89 on 2009-02-17
> **ghindo said:**
> Sure looks like PackageKit will be in Jaunty:

[http://packages.ubuntu.com/jaunty/packagekit](http://packages.ubuntu.com/jaunty/packagekit)

That doesn't mean it will be used by default. The fact however it is in main for Jaunty is interesting.

---

### Post by Slug71 on 2009-02-17
> **rockin_goliath said:**
> Does anyone know for certain if Packagekit will be in Jaunty or not? Any links to mailing lists detailing this?

I dont think so. I think it has moved to 9.10 but could be wrong.

---

### Post by Slug71 on 2009-02-17
> **Slug71 said:**
> 
Once that happens and they are nicely tied in with each other i think we may see a universal package format become available while still being able to use native packages.

> **Polygon said:**
> again, LINUX IS NOT BINARY COMPATIBLE 

even if there was one standard package format, there would still have to be different packages for debian, suse, mandrivia, arch, etc etc. 


Thats exactly what i said! .rpm Distros and .deb distros will still be able to use their own native packages as well as the universal one if one ever becomes available. 

Kinda like what Autopackage does. You have a universal .package format for Autopackage but you can still use the native package of whatever distro you have Autopackage on.

eg, I have Ubuntu with Autopackage. I can therefore install .debs and .package formats. If someone on Fedora also with Autopackage wants the same .package file that i have. They can just copy it from me and install it. But their system still uses .rpm packages too.

Super Ubuntu uses Autopackage by default.

---

### Post by bruce89 on 2009-02-17
> **Slug71 said:**
> Kinda like what Autopackage does. You have a universal .package format for Autopackage but you can still use the native package of whatever distro you have Autopackage on.

eg, I have Ubuntu with Autopackage. I can therefore install .debs and .package formats.

So, you advocate having another package format, like Autopackage, but not Autopackage. Surely this is slightly contrary to the original plan of having one format.

---

### Post by Slug71 on 2009-02-17
> **bruce89 said:**
> So, you advocate having another package format, like Autopackage, but not Autopackage. Surely this is slightly contrary to the original plan of having one format.

Slight being the key word. You have one format but you still have your native format too. That is the only way it will work.
I dont think die hard Linux vets would like their native formats taken away from them and im sure there will still be a need for native formats. There are lots of apps/software around that are made specifically for .rpm or .deb etc platforms. Therefore there is no need to do it as a .package or whatever format.

Well its not up to me what Ubuntu uses. If Ubuntu would use it then i'd be happy with it. But i think they want to go the Smart Package Manager route as a backend eventually.

---

### Post by kiersie on 2009-04-08
+1 for packagekit: If a xserver session fails the packagekit deamon goo's on, if i update my system i can install software from the repo's the deamon wil add them in the quie... etc

---

### Post by chris4585 on 2009-04-09
I don't care so much, as long as synaptic will always be in Ubuntu

---

### Post by hanzomon4 on 2009-04-09
> **Slug71 said:**
> I dont think so. I think it has moved to 9.10 but could be wrong.

It's in kubuntu for sure

---

