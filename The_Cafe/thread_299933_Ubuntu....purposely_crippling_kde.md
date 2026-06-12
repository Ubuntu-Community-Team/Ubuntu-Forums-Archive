---
title: "Ubuntu....purposely crippling kde?"
date: 2006-11-14
forum: The Cafe
---

### Post by maniacmusician on 2006-11-14
I know the title seems absurd, even stupid; but this is a concern of mine. I don't want to start a flamewar so if you've got a wise-*** comment, keep it to yourself please. 

Here's the thing; a while back, I did a vmware server install of edgy (possibly an RC version) . I installed a command-line system first, and then I installed kde, xorg, xserver-xorg, usplash, kubuntu-artwork-usplash, and I think that was it. Here's what I noticed; The kcontrol Display module was disabled by default. Why? I don't know. (The way to fix it, by the way is: sudo nano /usr/share/applications/kde/display.desktop. Change NoDisplay=true to NoDisplay=false). This was okay, though a little cumbersome.

Then yesterday, I did the same thing at my school. The Display module was still disabled; but some other things were missing from kcontrol too! such as:

1. User Management (adding/removing users, etc)
2. System Services (to enable/disable services, control what runs at boot)
3. Disks and Filesystems (allows you to mount hard drives, etc)
4. power manager applet
5. HAL device manager

The first 3 items are part of a package called kde-guidance. the 4th is kde-guidance-powermanager, and the 5th is kde-hal-device-manager. Now, I ask...these items used to be installed along with the kde package. Now, they're not...why? And these are just the ones I noticed...I can't imagine how many more there are. I think that at least the first 3 and number 5 are integral components, so why were they removed? And I don't think the Display module should be disabled either. 

After thinking about it a little, I'm thinking that word has gotten around about how most people like using  server+xorg+kde better than using Kubuntu, and this is an attempt to make the kde package installation look worse. Sure, it's a far out theory, but I'm a little pissed right now. 

I spent hours frustrated in front of the computer at school trying to figure out what was wrong. I needed to add multiple users to the computer because people were interested in trying Linux. I didn't know the names of all the kcmshells off the top of my head, so I couldn't figure out what I needed to install to get the userconfig shell (i didnt know it was called userconfig). It was bad enough that Kubuntu was crippling Konqueror and removing a bunch of options, but at least I had the kde package as an alternative. Now, I have to remember to install a bunch of extra packages every time I install kde. And because of this, people were unable to use that computer for a couple of days, and it made linux look complicated, and hard to learn to those people. A bad first impression. 

Does anyone know why this was done? I'll be honest, I can't think straight on account of being pissed off.

---

### Post by The Noble on 2006-11-14
It may be for those who want the _bare_ minimum kde for their system and can't stand the extra bloat, but frankly that doesn't make too much sense. You are quite justified in being pissed off, as I would be too. Have you searched for any metapackages that could help? Anything you overlooked? If not, I'll be severely dissappointed in Ubuntu if we have been leaving kde users out in the cold.

---

### Post by tubasoldier on 2006-11-14
I sure like KDE but I also think Kubuntu sucks. Its the worst KDE distro I have used. Based on Ubuntu is its only saving grace. Good luck with it.

---

### Post by maniacmusician on 2006-11-14
> **The Noble said:**
> It may be for those who want the _bare_ minimum kde for their system and can't stand the extra bloat, but frankly that doesn't make too much sense. You are quite justified in being pissed off, as I would be too. Have you searched for any metapackages that could help? Anything you overlooked? If not, I'll be severely dissappointed in Ubuntu if we have been leaving kde users out in the cold.

well as I said in my post, I've figured out which packages were the culprits...I just want to know WHY they aren't automatically installed with kde anymore. It makes my job a hell of a lot harder. 

For anyone that's wondering; the package is kde-guidance for the first 3 things, if you didn't catch it above I looked again, and kde-guidance actually installs a Display module as well. A different version, but it's still good. So they need to make kde-guidance a dependency of kde again. I dont know why the hell they removed it in the first place.

> **tubasoldier said:**
> I sure like KDE but I also think Kubuntu sucks. Its the worst KDE distro I have used. Based on Ubuntu is its only saving grace. Good luck with it.

Kubuntu really isn't that great...but I like the kde package. command line+ xorg +kde is pretty good.

---

### Post by kuja on 2006-11-15
so are you installing the kde package, or the kde-core package? I wouldn't expect kde-core to have them, but kde on the other indeed. I never use the kde package though, because as I recall from a year ago installing it in debian sarge/etch it installed a crapload of packages... 

I wonder about those modules though. I wondered why it seemed like there were something missing, and I guess that is it. 

The behavior regarding the display module is indeed a nuisance. Really strange having it basically disabled by default. 

As for myself, I take a hybrid approach to things. I do the server install + kde-core + whatever I want. However, I also install the Kubuntu artwork and default-settings packages. This way I don't have all those extra services I don't need running ...

---

### Post by maniacmusician on 2006-11-15
I prefer to start with a fuller package and then weed out the stuff that I want. Saves me a lot of hassle. Which is why I use the KDE package; it should have all those things there by default. and yeah, the kde package does install a lot of stuff. they mainly show up in the "utilities" sections. the useless ones anyways...I use most of the ones in other parts of the menu.

---

### Post by kuja on 2006-11-15
The only reason I take the route I do is because I tend to use only one of each thing. I probably installed more than one of the kde metapackages, but there's certainly no need to have 4 image viewers, 5 media players, 3 text editors, &c, or whatever it was (I have a feeling I'm close). In doing so my install could almost be considered light, up until the point where I install over a gig of development packages :rolleyes: 

Anyhow, thanks for the display note, as well as the mention of the kde-guidance package. On a side note, I personally never use the monitor and display module in kde-systemsettings... I only ever used it once and the time I did it trashed my xorg.conf file. It's part of the kde-guidance package, I believe. 

I think the main reason I didn't miss the things quite as much is because I always use the terminal for those things anyway...'

---

### Post by Castar on 2006-11-15
Sorry if I misunderstood, but why not install kubuntu-desktop? It has all the  things you said were missing, right?

---

### Post by maniacmusician on 2006-11-15
kubuntu-desktop is even more crippled, but in a different way. On all the computers i've tried it on, the kde package runs a lot faster. Plus, kubuntu does things like take most of the options out of konqueror, so you have less stuff to work with. It's worse.

---

### Post by MWAAAHAAA on 2006-11-15
Thanks man, I have been looking for this Display option ever since I upgraded from 5.04 to 5.10. Never could find it and had to resort to using gnome-display-properties. Beats me why they disabled it by default. As for the rest, I can't really complain about Kubuntu.

---

### Post by maniacmusician on 2006-11-15
oh, but you havn't tried server+xorg+kde yet as an alternative ;) It's weird to me that for the same functionality I actually get a speed boost from when I used Kubuntu. 

If you want a **real** speed boost go with kde-core...but then you'll find yourself missing some stuff here and there and will have to figure out how to get it back if you need it. Some people find it worth the effort, however.

---

### Post by Velotix on 2006-11-15
The reason is quite simple: check the size of the LiveCD ISOs. Aside from Xubuntu, they're 700MB each. (Xubuntu is about 525MB.)

I would assume then that Kubuntu is "crippled" for the sole purpose of making a Kubuntu LiveCD possible. Also, some of the features you mention show up as standard on my Kubuntu installation already anyway.

I assume that the absent libraries you mention are easily reinstalled via aptitude *et al* as well, yes?

---

### Post by claydoh on 2006-11-15
if you look around a stock Kubuntu install (kubuntu-desktop) you will see that most of the "missing" things are either in System Settings or in Konqueror's settings. There are still some kcontrol modules missing from System Settings, and I believe they are being addressed.

The overall focus in that area is de-cluttering KDE's administrative interfaces by simply removing redundant Admin areas. (why have Konq settings in two places, for example?) It still needs work though as there are still a couple of things that you have to go to kcontrol for (Security and Privacy, for example).

Far from being crippled in my opinion. But unfortunately still a work in progress for those that need some of these things. As Kubuntu's KDE desktop grows and develops as Ubuntu's Gnome desktop has, I think that these issues will surely be addressed. But installing only parts of the desktop will always have some of your issues I'm afraid.

---

### Post by maniacmusician on 2006-11-15
@Velotix: yes, but it took me hours to figure out which package to install; I didn't know the names of the kcmshells of the top of my head. and i shouldn't have to, really.

@claydoh: Uhh, actually, kde **is** the full desktop, and then some. fitting it onto an ISO can not be used as an excuse, because it's not meant to be an ISO! 

sudo aptitude kde

takes over 1 GB of space! so the things both of you mention are totally irrelevant.

All I want to know is if kde-guidance was a dependency of kde before, why isn't it now? it's a tiny tiny package. if they wanted to save space, they should've removed something stupid like KMouth, KMag, KSayit; all of which were default.

I'm going to be a radical and say this is ubuntu's attempt at making the kde package look bad and trying to get people to use kde. because this is an absolutely ridiculous thing to do.

---

### Post by Dual Cortex on 2006-11-15
Isn't the disk mounting tool found in the 'advanced' section?

Anyway, aren't all of those 'missing' tools found on kcontrol?

---

### Post by .t. on 2006-11-15
Jonathan Riddell is the Ubuntu KDE developer. He is not a GNOME fanatic, and wants the distro to be the best it can. I don't think he is trying to make the KDE package look bad, rather simplified, as has been done with Ubuntu. It is for human beings remember. That, and (as has also been said in this thread) it is supposed to fit in 700MiB (compressed, of course).

---

### Post by maniacmusician on 2006-11-15
](*,) as my post (two above yours) states, it does not have to fit in an ISO, as it's seperate from the one that in included on the CD. The total installation of all the things composing the kde metapackage culminates in over 1 GB, almost 2 GBs. so size is NOT an issue.

@Dual Cortex: what "advanced section" are you talking about? It's supposed to be in Settings>System Administration>Disks & Filesystems.

Please see post #14 for an acute summary of what's pissing me off.

---

### Post by .t. on 2006-11-15
I don't know what you mean size is not an issue. I've read all the posts in this thread. A CD is only 700MiB big, and 700MiB < 2GiB. Unless they use serious compression, I doubt they'll fit all 2GiB into the CD.

---

### Post by Bloodfen Razormaw on 2006-11-15
Most of those controls you mention aren't standard KDE controls.  A standard KDE installation handles things like users and filesystems with the kdeadmin module, which puts applications in the KMenu, not in KControl.

---

### Post by claydoh on 2006-11-15
Sorry, somehow I thought you had installed kde-core instead of kde.

The package 'kde' imo is redundant and should either be removed or renamed to follow the concepts of kde-core and Kubuntu-desktop, perhaps. It is not the metapackage Kubuntu uses to install KDE. kubuntu-desktop is as it has the selected packages plus tweaks, dependencies , etc. I think the unused (universe) 'kde' metapackage simply has the Debian default dependencies, so the things that have been modified or added may not be included in that dependency list. I am guessing that as 'kubuntu-desktop' is used instead of 'kde' to install a Kubuntu environment, perhaps there was a dependency change that caused kde-guidance to not be included in the 'kde' metapackage, whether by design or by accident (it is *not* a default kde application I believe). If you want the whole hog KDE, you must install kubuntu-deskop first, *then* install kde. Not logical, maybe but that's the way it is.

so ```
sudo aptitude install kubuntu-desktop
``` gets you Kubuntu's ideas of a kde desktop, uncrippled.

---

### Post by maniacmusician on 2006-11-15
> **.t. said:**
> I don't know what you mean size is not an issue. I've read all the posts in this thread. A CD is only 700MiB big, and 700MiB < 2GiB. Unless they use serious compression, I doubt they'll fit all 2GiB into the CD.

size is not an issue because  I'm talking about the kde metapackage...which is not included on the CD. The kde metapackage is **already** 2GB, so it cant be fit on a CD anyways. The package I'm angry about is tiny, less than 1 MB, and packs a punch in terms of adding to usability.

> **Bloodfen Razormaw said:**
> Most of those controls you mention aren't standard KDE controls.  A standard KDE installation handles things like users and filesystems with the kdeadmin module, which puts applications in the KMenu, not in KControl.

If that was the case, there would be nothing to complain about, but they did not show up in the KMenu either.

I'll state it again; a while back when i did this with an Edgy RC installation, these modules were installed by default as a dependency of the kde metapackage. Why aren't they now?

---

### Post by qpieus on 2006-11-15
> **maniacmusician said:**
> kubuntu-desktop is even more crippled, but in a different way. On all the computers i've tried it on, the kde package runs a lot faster. Plus, kubuntu does things like take most of the options out of konqueror, so you have less stuff to work with. It's worse.
Could you elaborate on how/what options are taken out of konq? I have not heard this before. Thanks.

---

### Post by maniacmusician on 2006-11-15
> **claydoh said:**
> Sorry, somehow I thought you had installed kde-core instead of kde.

The package 'kde' imo is redundant and should either be removed or renamed to follow the concepts of kde-core and Kubuntu-desktop, perhaps. It is not the metapackage Kubuntu uses to install KDE. kubuntu-desktop is as it has the selected packages plus tweaks, dependencies , etc. I think the unused (universe) 'kde' metapackage simply has the Debian default dependencies, so the things that have been modified or added may not be included in that dependency list. I am guessing that as 'kubuntu-desktop' is used instead of 'kde' to install a Kubuntu environment, perhaps there was a dependency change that caused kde-guidance to not be included in the 'kde' metapackage, whether by design or by accident (it is *not* a default kde application I believe). If you want the whole hog KDE, you must install kubuntu-deskop first, *then* install kde. Not logical, maybe but that's the way it is.

so ```
sudo aptitude install kubuntu-desktop
``` gets you Kubuntu's ideas of a kde desktop, uncrippled.
I would hate it if this happened. the kde package is my only solace from Kubuntu. It even runs faster, for some reason. I don't like the default kubuntu so this is a great option for me. And Kubuntu's ideas of uncrippled are pretty widely unaccepted. sudo aptitude install kde     is much better, when kde-guidance is included. Otherwise, it could induce headaches.

kde-guidance definitely should be included by default, or else it's contents should be implemented in a different way. Where would I go to tell people to make it a dependency again? it was very useful. It'll help people on a large scale.

---

### Post by maniacmusician on 2006-11-15
> **qpieus said:**
> Could you elaborate on how/what options are taken out of konq? I have not heard this before. Thanks.
oh, a bunch of options. Mostly options from the Location, Tools, and Settings  menus. I don't remember which Kubuntu is missing, since I'm not running kubuntu-desktop anymore

---

### Post by Bloodfen Razormaw on 2006-11-15
kdeadmin *is* a dependency of KDE.  Be sure you installed the kde metapackage, not just kde-core.  The later is, as the name implies, just the core of KDE.  No extras.

---

### Post by maniacmusician on 2006-11-15
I know; I installed the kde metapackage. The huge-*** one with lots of unnecessary things. I do have kde-admin installed. I don't see any options equivalent to those modules in my KMenu

---

### Post by kerry_s on 2006-11-15
I feel you man. I gave up on kde/konqueror when i upgraded all my systems to edgy. I went back to fluxbox with thunar as the filemanager and use dillo & firefox for web browsers. They tie all that kde crap together so if any daemon screws up it all starts to chain react. I just got tired of screwing with it to make it work right.

---

### Post by kuja on 2006-11-15
Are you sure (like, absolutely positive) it(kde-guidance) was a dependency of it(kde) before? 

Anyhow, .t, kde doesn't fit on one cd, and is not distributed as a part of the kubuntu cd either. kubuntu-desktop is, and has different dependencies than kde. 

> I don't think he is trying to make the KDE package look bad, rather simplified, as has been done with Ubuntu. It is for human beings remember.Are you saying human's are simpletons? j/k

Of course he (Riddell)isn't trying to make it look bad, and IMO he isn't making it look bad either. He in fact isn't in charge of the kde package anyway. The Debian KDE/Qt Maintainers are. 

Anyway, as per the major gripe many people have with Kubuntu's "crippled" Konqueror, I think I all one needs to do is this:
> How do I change Konqueror back to the default KDE profiles?
 Kubuntu comes with a simplified Konqueror profile to make things more user friendly compared to default KDE. To get back to the default KDE profiles: 
 Open a terminal by choosing K-Menu->System->Konsole (Terminal Program) from the desktop menu system. 
 Execute the following commands 
sudo rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror
sudo cp /usr/share/apps/konqueror/konqueror-orig.rc /usr/share/apps/konqueror/konqueror.rc

---

### Post by maniacmusician on 2006-11-15
yes, I am absolutely sure. I went back into that vmware image, and checked. I'd only run a totaly of like 25 commands on it. The only things I installed were kde, kubuntu-artwork-usplash, xorg, xserver-xorg, and I think that was it. I installed those things on the newer installation as well.

---

### Post by Bloodfen Razormaw on 2006-11-15
If you have kdeadmin installed and it doesn't put launchers in the KMenu then I'd call it a bug and suggest you report it.

---

### Post by maniacmusician on 2006-11-15
Before I do so, where are they supposed to appear?

---

### Post by GameManK on 2006-11-15
kde-admin should install things like kuser in k-menu>system i believe, or maybe utilities.

kde-guidance is a set of modules that IS NOT part of KDE.  It was created to replace the buggy modules of kde-admin and kde's display module.  It is one of kubuntu-desktop's enhancements on kde.

this crippling claim is ridiculous.

---

### Post by maniacmusician on 2006-11-15
System and utilities are there, but no equivalents of these modules as Bloodfen says there are supposed to be.

The claim is pretty ridiculous, yes. I said it in part to at least stir people up. The actual issue I had was that kde-guidance got automatically installed before, and now it doesn't. This act of taking it away made it a lot harder for me to set up that system, because I had no idea what was missing.

---

