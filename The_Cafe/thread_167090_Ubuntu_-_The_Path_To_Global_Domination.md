---
title: "Ubuntu - The Path To Global Domination"
date: 2006-04-27
forum: The Cafe
---

### Post by jonathansizz on 2006-04-27
Here's a list I have compiled of the most important improvements yet to be made to Ubuntu. These are the things that I think need to be done before Ubuntu will be taken seriously by the PC-using masses.



1] Preinstallation on new PCs and Notebooks. OEM's could also preinstall propretary stuff.

2] 'Easy Ubuntu' or similar officially-supported tool for non-OEM installations - a simple & reliable method of downloading (as necessary), installing and setting up all the non-free stuff that cannot come preinstalled for licensing reasons: multimedia codecs, graphic card drivers, proprietary software like Realplayer, Java, Adobe Reader, etc.

3] Easy & reliable upgrade between releases (because people don't want to reinstall every 6-months - thay want to upgrade to the newest version of Ubuntu to get the latest features, but they want their personal files & system settings to remain untouched as far as practicable). Windows and even FreeBSD have had this for years.

4] It is more important to get currently existing features working universally than to introduce new features - professionalism matters. Features that cannot be guaranteed to be working as advertised should be hidden or perhaps moved to an 'experimental' folder.

5] One-click install & uninstall of .deb packages - for stuff that is not included in official synaptic repositories (for example, when a new version of Firefox is released, users could simply download it & click to upgrade to new version, as seen in Windows).

6] Settings that presently need to be adjusted from the command-line, post-install, should be defaulted to how most people (i.e. non-technophiles) would likely want them, eg. DMA should be ON by default.

7] Making choices easier to navigate is good, but removing choices is bad - the gnome screensaver crippleware is an obvious example. Another (that Ubuntu is directly responsible for) is the new GDM with options buried in the corner. Show me someone who was confused by the old layout. The new layout is clumsy and annoying to use.



Ubuntu is a wonderful operating system and the developers deserve huge respect & congratulations for getting it to its' present level in such a short period of time. The above are simply suggestions for making Ubuntu even better. What does everyone else think?

---

### Post by ssam on 2006-04-27
1) there are a few places selling ubuntu pcs, but more would be good.

2) maybe click and run from linspire (i am hoping mark shutleworth is keeping it as a supprise for the dapper release)

3) this works pretty well in my experience, maybe if update manager could ask you if you wanted to upgrade on the release day, and sort out the new sources for you. there is a single command you can run now to upgrade to dapper

4) six weeks extra polish for dapper, with (almost) no new features being added.

5) gdebi is in dapper, and does this pretty well. there is also backports to get new versions of software.

6+7) i think what needs to be done is choose the right settings. i dont want to have to worry about what sound server i am using, or which backend totem is running. things like that need sensible autodetection and defaults (i think dma on by default can cause problems, a hardware whitelist/blasklist is needed).
i do want to be able to select a wireless network from a list. choose my theme colours etc.
it needs a carefull balance.

so i think ubuntu 6.06 will be ready for world domination. or at least used by a few more people.

---

### Post by BoyOfDestiny on 2006-04-27
3) Is already here. The update manager support updgrading the next release (and with a command can support alpha/beta releases, at least for the dapper beta it's like that)

4) Not sure what those are...

5] Already in dapper with gdebi (for installing anyway, gathers dependencies and everything...This is probably the most important) Removal on the other hand is trivial with synaptic or commandline... Even if installed elsewhere, as long as it's from a deb, synaptic will see it.

6] DMA should be ON by default. Indeed it is, and I'm very glad about that.

7] Should be customizable, there is always Add/Remove, and right clicking on a menu to edit (to tick checkbox for more menu options etc)

---

