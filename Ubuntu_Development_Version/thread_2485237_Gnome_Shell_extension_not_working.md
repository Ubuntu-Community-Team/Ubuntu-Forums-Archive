---
title: "Gnome Shell extension not working"
date: 2023-03-23
forum: Ubuntu Development Version
---

### Post by jcrc-portinter on 2023-03-23
Running Lunar for a few days already.
None of the gnome shell extensions is working.
Is this normal at this stage of development or did I have done some thing wrong?
Even Ubuntu Desktop at Settings displays "report error to Launchpad"

---

### Post by zebra2 on 2023-03-24
Pre-release installs can be a problem even after the release date. Lunar should be considered a "testing" version. I use a Ubuntu/Gnome/Wayland default install and usually do ok. Regardless of using the default or tinkered installation if it is Lunar you are "testing".  I keep a fresh startup USB handy. Let the fun begin!

PS: It isn't unusual for an assortment of fixes to be held back until the final IOS.

---

### Post by Dennis N on 2023-03-24
That's not surprising. They need upgrading when the gnome-shell version is changed. The Extension Manager utility should inform you when upgrades become available for particular extensions. Be sure its installed. Maintainers also sometimes abandon their extensions and they just don't work anymore.

---

### Post by VMC on 2023-03-24
What message is shown at the top when you go to:
[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by jcrc-portinter on 2023-03-27
"An unexpected error occurred" is shown, 
but I must say I couldn't get this to work after switching to the snap version of firefox. Nevertheless, the extensions were working ok on kinetic.

GSConnect (now on v55): If I switch it on and go to settings, first it displays "waiting for service", if I refresh then it works. but still nothing in the Quick Settings menu.

Regarding [https://extensions.gnome.org/](https://extensions.gnome.org/), all the extensions I have installed are on the latest version and I think all of them ready for Gnome 44.

---

### Post by logix2 on 2023-04-04
The extensions are not working for me either. But I've found a workaround for now - after each boot or resume from suspend, I run this:

```
gsettings set org.gnome.shell disable-extension-version-validation false

gsettings set org.gnome.shell disable-extension-version-validation true
```

All extensions enabled in the Extensions app or Extension Manager then start working.

---

### Post by MyMurry on 2023-04-10
Is there a bug report for this? I haven't found one.

---

### Post by draki on 2023-04-10
I have the same issue. It's very annoying as I use a dock on the left of the screen which seems to actually be an extension
I've been toggling "Disable version validation" in [https://extensions.gnome.org/local/](https://extensions.gnome.org/local/) - same as the gsettings workaround above
Couldn't find a bug report either (I'm happy to raise one, just not sure where - Gnome or Ubuntu?)

---

### Post by VMC on 2023-04-10
"Disable version validation" is "grayed" out on my system, but extensions work.

---

### Post by Claus7 on 2023-04-16
Hello,

I upgraded just yesterday and upgrade went fine. Ubuntu flashback compiz is working as it should for now, yet trying to check ubuntu xorg, half of extensions were not working. Version is not an issue for the extensions that are not working, since those that are not updated from their developers, and as a result have an older version, are accompanied by a red clock icon, whereas the ones that are not working and are not having that clock icon, they have the correct gnome shell version and they should work. Going to ubuntu settings I faced the same problem as the OP, so the outcome is that there is something wrong with the upgrade.

I tried the following commands:
sudo apt purge gnome-shell
sudo apt install gnome-shell ubuntu-gnome-desktop

the latter proceeded until the following message appeared:
==> Installing the chromium snap
xxx (date and time) INFO Waiting for restart...

and the waiting time kept me waiting, so I killed the process and issued the command: 
sudo service snapd restart

Trying anew: sudo apt install gnome-shell ubuntu-gnome-desktop
didn't work so I restarted and entered flashback (as I had no other choice at that time) and from there I typed:
sudo dpkg --configure -a
sudo apt install gnome-shell ubuntu-gnome-desktop

the latter installed some packages until it gave an error about snapd firefox. Also it mentioned that some packages were not installed. So, I opened synaptic, purged firefox snap and saw that some packages were installed along the way. 

Then I did the following:
snap list (in order to check if another snapd package is installed)
sudo apt autoremove --purge snapd (to remove snapd entirely)

For now wayland ubuntu is not available from login screen any more. (edit: it is)
In the meantime gdm3 was removed and lightdm was used instead. Now is back on track.
Flashback had no problem even without gnome-shell in order to operate.

I suppose that in the final version this is an issue in order to get fixed.

Just a point: upgrading from 22.04 to 22.10 didn't have any issue at all.

Regards!

---

### Post by Claus7 on 2023-04-17
Hello,

adding a new user the problem vanished, as a result it is definitely the upgrade process.

Regards!

---

### Post by MyMurry on 2023-04-20
Unfortunately this doesn't help:

 dconf reset -f /

I read that beta tester had this problems too. Is a new user really the solution?

---

### Post by draki on 2023-04-20
I also tried `dconf reset -f /` - didn't help me either :(
I still have the same issue - I can't figure out what the problem is :(

---

### Post by Claus7 on 2023-04-20
Hello,

> **MyMurry said:**
> Unfortunately this doesn't help:

 dconf reset -f /

I read that beta tester had this problems too. Is a new user really the solution?

> **draki said:**
> I also tried `dconf reset -f /` - didn't help me either :(
I still have the same issue - I can't figure out what the problem is :(

I tried the same thing and it didn't work either, but to reset some settings. After all, this is what this command is supposed to do.

The problem seems to have a remedy, yet it needs experimenting. In order to do so I removed everything from my home folder that started with a . in front of its name to a backup folder. The most important folders were the .config and .local and maybe a couple of files at the end of home folder starting with a . in front of their name.  
From these folders remove the .local/share/ at first, reboot and check if things will work. Unfortunately, since I removed many things I do not remember exactly which of these fixed the issue. You can tell by transferring them to another folder and check after rebooting if things are working ok. This process didn't seem to cause any problem for now to my system, yet if you try this path, you have to be cautious.

Regards!

---

### Post by MyMurry on 2023-04-21
A clean profile is working.

---

### Post by draki on 2023-04-21
I found this thread - [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/2017173](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/2017173)
Removing `~/.local/share/gnome-shell/extensions` worked for me - obviously I needed to reinstall the extensions I wanted, but it seems to work now. Finally.

---

### Post by andythemckay on 2023-04-22
Within the local extensions folder removing [email]ding@rastersoft.com[/email] worked for me, can't quite remember how it got there in the first place but now extensions are working as they should.

---

