---
title: "Differences between the kde meta packages in ubuntu 14.04"
date: 2014-08-15
forum: Ubuntu, Linux and OS Chat
---

### Post by user1397 on 2014-08-15
I've been trying to understand the difference between all the meta packages for kde in the latest ubuntu release, mostly to try and figure out what would be the smallest (minimal) install of kde I could find in ubuntu.  I know these might become obsolete once kde plasma 5 becomes the default, but for now kde 4 is still the default.

The main meta-packages I've been able to find are:


[LIST]
[*]plasma-desktop
[*]kde-workspace
[*]kde-plasma-desktop
[*]kde-standard
[*]kubuntu-desktop
[*]kde-full
[/LIST]

plasma-desktop and kde-workspace seem to install the same number of programs so I conclude they're the same for all intents and purposes.

If you install any of these from the mini.iso minimal ubuntu image, these are the number of applications they install:


[LIST]
[*]plasma-desktop = 505
[*]kde-workspace = 505
[*]kde-plasma-desktop = 539
[*]kde-standard = 736
[*]kubuntu-desktop = 1202
[*]kde-full = 1128
[/LIST]

If you have the normal ubuntu desktop installed, and want to install any of these alongside it, this is how many additional packages they install:


[LIST]
[*]plasma-desktop = 209
[*]kde-workspace = 209
[*]kde-plasma-desktop = 243
[*]kde-standard = 374
[*]kubuntu-desktop = 477
[*]kde-full = 677
[/LIST]

Interesting to note that kde-full is bigger than kubuntu-desktop if installed after a ubuntu desktop install, but it is smaller if installed from a minimal ubuntu image.

I am currently installing plasma-desktop, kde-plasma-desktop, and kde-standard in virtual machines from the mini.iso to see the visual/user experience differences in each.  I'll report back when I've installed and used them a bit.

*****EDIT/UPDATE**:

So I installed all three (plasma-desktop, kde-plasma-desktop, and kde-standard) of the more basic kde meta-packages each in a clean minimal install of ubuntu using the mini.iso and through virtualbox.

This is what I found.

First of all, all three (including plasma-desktop) pull in enough packages so that after restarting, you are taken to a graphical login manager automatically and kde is installed.

plasma-desktop uses lightdm, while kde-plasma-desktop and kde-standard both install lightdm and kdm, and let you choose one as default during installation.

In the applications menu, **plasma-desktop** just has these entries:

system settings
info center (kinfocenter)
system monitor (ksysguard)
nepomuk cleaner
clipboard tool (klipper)

**kde-plasma-desktop** pulls in these entries in addition to the ones from plasma-desktop:

terminal (konsole)
file manager (dolphin)
text editor (kwrite)
web browser (konqueror)

and **kde-standard** pulls in these in addition to the ones from kde-plasma-desktop:

document viewer (okular)
imagemagick (display)
image viewer (gwenview)
screen capture program (ksnapshot)
feed reader (akregator)
instant messenger (kopete)
mail client (kmail)
sieve editor
music player (juk)
sound mixer (kmix)
video player (dragon)
contact manager (kaddressbook)
personal organizer (korganizer)
wallet management tool (kwalletmanager)
advanced text editor (kate)
archiving tool (ark)
kmail import wizard
popup notes (knotes)
scientific calculator (kcalc)
system cleaner (sweeper)


So there you have it.  Honestly, I think I'm going to try and just install the plasma-desktop one from a minimal install and then add the packages I want.  Seems like the cleanest kde experience possible on ubuntu, but of course I have to try it and see if it's missing anything really essential that might be annoying to configure.

Thoughts?

---

### Post by coffeecat on 2014-08-15
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by user1397 on 2014-08-15
> **coffeecat said:**
> *Thread moved to **Ubuntu, Linux and OS Chat**.*
makes sense, should've figured that one :)

---

### Post by ibjsb4 on 2014-08-15
I don't do kde, but thought this may help.

To find a list of all packages installed, go to Ubuntu Packages.  Example ..

[http://packages.ubuntu.com/trusty/kubuntu-desktop](http://packages.ubuntu.com/trusty/kubuntu-desktop)

Using this as an example, you can further reduce the size of the install by leaving off the recommended packages (the ones with a green dot).
```
sudo apt-get install --no-install-recommends kubuntu-desktop
```

---

### Post by user1397 on 2014-08-28
> **ibjsb4 said:**
> I don't do kde, but thought this may help.

To find a list of all packages installed, go to Ubuntu Packages.  Example ..

[http://packages.ubuntu.com/trusty/kubuntu-desktop](http://packages.ubuntu.com/trusty/kubuntu-desktop)

Using this as an example, you can further reduce the size of the install by leaving off the recommended packages (the ones with a green dot).
```
sudo apt-get install --no-install-recommends kubuntu-desktop
```Indeed sir, that is a way to thin out the meta-package even more.  I guess I didn't try to do it with the smaller meta-packages because they were already so tiny, but I do wonder now what if I placed this parameter on the smallest one (plasma-desktop) how many packages would it omit?

Hmm, gotta fire up virtualbox again :P

---

