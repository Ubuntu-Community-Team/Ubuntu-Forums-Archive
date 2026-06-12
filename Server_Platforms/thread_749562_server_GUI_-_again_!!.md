---
title: "server GUI - again !!"
date: 2008-04-08
forum: Server Platforms
---

### Post by neill on 2008-04-08
hi

is there any way to load ubuntu (or xubuntu or whatever) on top of the ubuntu server base **but **whilst being able to select which packages i need ?

similar to the anaconda installer in RHEL/CentOS/FC where you can select in quite fine detail what you need at install 

i've done sudo apt-get install ubuntu-desktop before - works fine but i get all the games, chat stuff etc etc that i really don't want - and it seems like it'll be a ***major* **pain to manually uninstall it all afterwards

any ideas anyone ??

ta

/neill

---

### Post by lswest on 2008-04-08
well, you can just install the gnome package and set it up manually (e.g. sudo apt-get install gnome-2.22 i think is the command, not 100% sure though)

---

### Post by kostkon on 2008-04-08
You can install the *xubuntu-desktop* metapackage but say to *apt* **not** to install the recommended packages. This way you'll get a very clean *Xubuntu* desktop without any desktop application. You can do it by passing *--no-install-recommends* to *apt*.

Check what you can avoid by not installing the recommended packages for *xubuntu-desktop* [here]("http://packages.ubuntu.com/gutsy/xubuntu-desktop").

What do you think?

EDIT: although, I have to say that I have not tested this before. I don't know how well the Xubuntu desktop will work without installing the recommended packages.

---

### Post by ibutho on 2008-04-08
You could use the ncurses interface for aptitude to select and install the individual packages you need. If you prefer using Synaptic, then install a lightweight WM e.g. fvwm2 and synaptic. You could then start fvwm2, run Synaptic from there and choose the individual packages you need.

---

### Post by neill on 2008-04-08
thanks some great idea there

i'll have a play around and see how i get on then feed back

/neill

---

### Post by kerry_s on 2008-04-08
sudo apt-get install xorg xfce4
startx

add what ever else you want.

---

