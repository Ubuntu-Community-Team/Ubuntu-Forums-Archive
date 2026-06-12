---
title: "Locked out after clicking on -&gt;accessibility &gt;magnify"
date: 2014-03-28
forum: Ubuntu Development Version
---

### Post by geonel on 2014-03-28
I tried -clicked on- the magnify option but it corrupted my desktop. I then clicked it (accessibility->magnify) at the login screen thinking that would globally correct the setting in my profile - I know, stupid, I was tired. Anyway, now I can't even get the login screen to come up after booting up because magnify makes it unusable. 

 I upgraded my Ubuntu recently to 14.04 so I'm using gnome 13.10. I tried to purge gnome-accessibility-extensions but that does not seem to help. Anyone have a suggestion for me to try in a terminal session?

---

### Post by bapoumba on 2014-03-28
Thread moved to Ubuntu +1.

---

### Post by zika on 2014-03-29
[http://ubuntuforums.org/showthread.php?t=786327](http://ubuntuforums.org/showthread.php?t=786327)

---

### Post by geonel on 2014-03-29
Thanks for the pointer zika. If I read the string correctly, I need gui in order to follow the disabling process. I am looking for the command line equivalent because I'm locked in to magnify and can't get out because it corrupts the gui.

---

### Post by zika on 2014-03-30
> **geonel said:**
> Thanks for the pointer zika. If I read the string correctly, I need gui in order to follow the disabling process. I am looking for the command line equivalent because I'm locked in to magnify and can't get out because it corrupts the gui.When reading that thread (even though I myself did not have that kind of trouble, at least not lately...) I found several keyboard shortcuts that could help You... Also, pointers about ccsm are usable in {g,d}conf-editor or directly from the command line (CLI)...
I'm in time-shortage now but take a look in: [https://help.gnome.org/admin/gdm/stable/configuration.html.en](https://help.gnome.org/admin/gdm/stable/configuration.html.en) (5.6)...

---

### Post by geonel on 2014-03-30
zika, the keyboard shortcuts do not work. The only thing I seem to be able to do is ctrl-alt-f1 to log into a command line session. Thank you for the pointer.

Re clarification: (an attempt to better describe where I am at and to discard non essentials)
I have a desktop Ubuntu installation that includes gnome not unity. I built that two or three months ago and was fairly happy. A week ago I decided to upgrade to 14.04 test to help in debug the next release. Things were as good as I would expect.

Cause of existing problem:
At the login screen that comes up after booting, the accessibility icon is visible, I clicked on the icon which brought up a drop down list and I selected "magnify on" from that list effectively setting the "magnify on" flag to true.

Current problem:
After setting "magnify on" my screen went to near total blank except for the mouse cursor. The cursor is all I see. Key combinations to alter the "magnify on" flag do not seem to have any effect - ctrl-mousewheel etc. I tried booting in recovery mode but cannot get to the login screen (explanation on request but I will not go into now).

What I think I need to do:
I think I need to change identify the configuration file that contains the value flag the says the "magnify on" is true and I need to do that from the command line.

Last resort:
I'll unwind to two weeks ago and rebuild the entire disk, upgrade to 14.04, set "magnify on" to true - just to verify that I didn't have something else cause the issue.

---

### Post by geonel on 2014-03-30
Update: Using zika's last pointer to gdm administration I found /desktop/gnome/applications/at/screen_magnifier_enabled so I did a google search and went to [http://ubuntuforums.org/archive/index.php/t-1672819.html](http://ubuntuforums.org/archive/index.php/t-1672819.html) and decided to try from "stinkeye":
ubuntu-prompt% sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false


I will update later since I ma writing this while booted up on an older installation on the same computer.

it is now later - that did not work for me.
I was able to get by the login magnification by reloading gdm.  Now I have to get by magnification after loggin in. When I click on anything in the top navigation bar, it crashes and starts compiling an error report. The error reports have been sent so I'm going to wait a week or so before I go back to fixing it.

---

