---
title: "Experience with Gnome 3 on Ubuntu 11.04"
date: 2011-05-20
forum: The Cafe
---

### Post by ivanovnegro on 2011-05-20
I want to ask for some experiences of people using Gnome 3 with Ubuntu 11.04 and how you install it or just like in general.
Are you using the Ubuntu Gnome Remix or the official Gnome 3 PPA etc etc.
How do you like Gnome 3 and what are the advantages of it?
Im really interested to try it out but did not have time yet.

So, I would appreciate some feedback before making my hands dirty. :smile:
So, for all Gnome lovers, Im waiting for your responses.

---

### Post by ratcheer on 2011-05-20
I use the Gnome 3 / gnome-shell and I like it very much. I got mine via the Gnome 3 Team PPA. It has been pretty good from the start, but there are fixes and improvements on a daily basis.

To install it, be out of Unity. Add the Gnome 3 PPA to your software sources. I use aptitude, so adjust the next steps per whatever package manager you use.

sudo aptitude update
sudo aptitude dist-upgrade

Reboot and you should be able to select the gnome-shell environment.

Make sure you have gnome-themes-standard installed. If it isn't, install it.

Install the Tweak Advanced Settings app. Sorry, I forget the exact package name, but you will see it on most sites that talk about Gnome 3 on Ubuntu. Use it to select a good theme (I use Adwaita) and icon theme (I downloaded and selected Faenza darkest).

Use gsettings to select a favorite wallpaper.

That should get you started. Be warned that it can mess up your system if something goes wrong, and it is not easy to back out. Is it worth it? IMHO, yes.

Good luck.
Tim

---

### Post by ratcheer on 2011-05-20
PS - the package name for Tweak Advanced Settings is gnome-tweak-tool.

Tim

---

### Post by ivanovnegro on 2011-05-20
Thank you for your reply and for some important details.
Yes, I know there seems to not be a way to go back.
Im on Xubuntu and also heard it should work well to build on top of it.
Maybe some Xubuntu users using the Gnome Shell could also explain here their opinions.
Anyway I will make backups before I start to play with Gnome 3.

---

