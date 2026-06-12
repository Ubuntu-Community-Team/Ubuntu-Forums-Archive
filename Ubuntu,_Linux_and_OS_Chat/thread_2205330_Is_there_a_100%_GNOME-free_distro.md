---
title: "Is there a 100% GNOME-free distro?"
date: 2014-02-13
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2014-02-13
Just curious whether such a distro exists. Even Kubuntu 13.10 has things like gsettings and gnome-keyring and network manager.

My bad ... explained here: [http://ubuntuforums.org/showthread.php?t=2205330&p=12928189#post12928189](http://ubuntuforums.org/showthread.php?t=2205330&p=12928189#post12928189)

---

### Post by mastablasta on 2014-02-13
yes i saw a pure KDE distro but can't remember it's name. i saw it on distrowatch.

besides try mini.iso + KDE (not kubuntu desktop metapackage). ;-)

hmm it has gnoem keyrign? are you sure you didn't pull it in with any gnome application? i mean it uses KWallet. an network manager should be from KDE.

---

### Post by vasa1 on 2014-02-13
> **mastablasta said:**
> yes i saw a pure KDE distro but can't remember it's name. i saw it on distrowatch.

besides try mini.iso + KDE (not kubuntu desktop metapackage). ;-)

hmm it has gnoem keyrign? are you sure you didn't pull it in with any gnome application? i mean it uses KWallet. an network manager should be from KDE.

I'm sorry! You're probably correct. I looked at [http://cdimage.ubuntu.com/kubuntu/releases/saucy/release/kubuntu-13.10-desktop-amd64.manifest](http://cdimage.ubuntu.com/kubuntu/releases/saucy/release/kubuntu-13.10-desktop-amd64.manifest) but then quite a few items are *deleted* as part of the automatic clean-up after installation. And so it's quite likely that some (or all?) GNOME items are removed.

I should have looked at [http://packages.ubuntu.com/saucy/kubuntu-desktop](http://packages.ubuntu.com/saucy/kubuntu-desktop) for the real picture.

---

### Post by dave2001 on 2014-02-13
+1 for Mastablasta's suggestion.

I'm actually running that exact setup of 13.10 on this laptop. First I used the mini.iso to install a base system, which you can dl here in your preferred architecture/version: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD). Just make sure you skip the step called "choose which software to install" or something like that.

I then used apt-get to install kde-plasma-desktop metapackage. That is **not** the full kubuntu desktop, there is another meta-package for the full "Kubuntu" desktop.  The metapackage I used includes **only a couple very basic applications**, like konsole, dolphin, and kwrite, which you will want anyway. To my knowledge there is absolutely no gnome or gtk-based anything in this setup.

Keep in mind that doing an install like this will probably give you some extra work to do. You'll need to manually install some things you take for granted on a normal 'buntu install. Packages you'll probably want to add in are: 
**kmix**  -for sound integration into desktop
**kdesudo** -really not sure why this isn't included
**kscreen ** -to have full control over resolution, etc
**gdebi-kde**  -package installer
**plasma-nm**  -gives you the taskbar widget to control the KDE version of network manager (not the gnome network manager) keep in mind you'll have to edit out your connections in /etc/network/interfaces or network manager won't "see" them

doing a base-system install will also leave you lacking some cli tools which you might want, so far I've added in:
man-db
nano
lshw

---

### Post by mips on 2014-02-13
Your best bet is to roll your own from a base of your choice (arch, debian, ubuntu, slackware, manjaro, gentoo etc) and choosing your own packages. This way you get exactly what you want and nothing more.

---

### Post by mastablasta on 2014-02-14
my guess is firefox pulled in dependencies. i just checked and i too have a couple of gnome stuff installed. among others the keyring. eventhough the install is vanilla Kubuntu + Firefox&TB. i am not sure if i have any other gnome application.

i need to check again since i forgot if i installed gimp or inkscape to this PC. those two also use gtk i believe.

---

### Post by buzzingrobot on 2014-02-14
Chakra is all KDE.  GTK apps, if added, are segregated in quasi-sandboxes so as not to interfere with the "purity" of the KDE install.

Hafta to say I don't really understand this purge-all-Gnome thing, but don't confuse GTK with Gnome. I'm not especially fond of KDE, but don't really care if dependencies bring pieces of it, and certainly not pieces of QT. (E.g., VLC typically brings in a kdelibs package.) If I don't interact with it, it's just object code.

---

### Post by Rob Sayer on 2014-03-13
I just installed kde-plasma-desktop on my lubuntu 13.10 netbook.  The kickoff launcher is empty ... no favorites or even applications.  This is on both openbox and plasma.

Can't seem to find anything on how to deal with this ...

Maybe it'd be a better idea to just install kubuntu and *remove* stuff?

---

### Post by mJayk on 2014-03-13
Rob tried installing ubuntu server edition, then apt-get kubuntu-desktop?

---

### Post by walterorlin on 2014-03-16
Aren't all distributions without a GUI usually free from gnome? But do you still want a desktop?

---

### Post by QIII on 2014-03-16
I'm not at home so I can't check my Fedora machine, but I believe the KDE spin of Fedora 20 has no GNOME dependencies unless you happen to add a package that draws them in.

I'm pretty sure that KDE 4.11 is "clean" in that respect, but I couldn't say for certain.

---

### Post by Rob Sayer on 2014-03-17
> **mJayk said:**
> Rob tried installing ubuntu server edition, then apt-get kubuntu-desktop?

Thanks for the response, but I'm trying to avoid the full kubuntu package on this netbook unless I bump the RAM from 1Gb to 2Gb.  I had kubuntu before but the latency in 1Gb is frustrating, though it can be made to work surprisingly well.

Actually, I've got kde-plasma-desktop running ok now.  Used this ...

[http://askubuntu.com/questions/262888/how-to-get-openbox-as-kdes-window-manager](http://askubuntu.com/questions/262888/how-to-get-openbox-as-kdes-window-manager)

... and there are still a few rough edges but it's not bad so far.

May still just bump up the ram and install kubuntu though.

This is really OT though ... I don't see any *reason* to avoid gnome apps myself ...

---

### Post by codingman on 2014-03-19
Same! Don't hide from the gnome, it isn't going to hurt you!

Very true again! KDE can be changed to be lightweight, just too much hassle for me.

My favorite quote was made by someone either on these forums or on the #! ones: KDE is like snow, it's nice for a while, but then I want somebody to take it all away.

---

### Post by llanitedave on 2014-03-20
Heh.  KDE, at least in Kubuntu, does have its annoyances.  But then, so does Unity, so does Xfce, so does LXDE.  About the only one I haven't tried at all is pure Gnome, but it looks annoying just from the examples I've seen.

There's no such thing as the perfect desktop, and trying to be "pure" with any single one just amplifies the existing annoyances -- kind of like inbreeding.

---

### Post by TeamRocket1233c on 2014-03-20
Arch or Gentoo come to mind, along with a base Ubuntu or Debian netinstall, as you wouldn't have a desktop to start with in either of the four directions listed, requiring you to install ALSA, X, and a display manager/desktop environment combo yourself. My recommended display manager/desktop environment combo is LXDM + MATE or Xfce4* + Compton.

*Vanilla Xfce4 preferred, although the Xubuntu desktop is cool too.

---

### Post by su:bhatta on 2014-03-27
Have a look at KaOS, : [http://kaosx.us/](http://kaosx.us/)

---

