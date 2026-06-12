---
title: "Problem to install some packages"
date: 2005-12-01
forum: Repositories &amp; Backports
---

### Post by Luis Miguel on 2005-12-01
Hello,

	I'm trying to install mgeups-psp (software for a Merlin Gerin UPS) on a Kubuntu computer, it's a fresh installation. I'm able to edit /etc/apt/sources.list and apt-get update. When I do an apt-get install mgeups-psp I get this message:

Los siguientes paquetes tienen dependencias incumplidas:
  mgeups-psp: Depende: libglibmm-2.4-1 (>= 2.6.1) pero no es instalable
              Depende: libgtkmm-2.4-1 (>= 2.6.1) pero no es instalable
              Depende: libsigc++-2.0-0 (>= 2.0.2) pero no es instalable

	I have searching the internet without luck, the question is: how can I install this files?

	Thanks in advance, and sorry for my bad English, I'm Spanish :-)

---

### Post by r0ll3r on 2005-12-01
This is from mgeups.com:
Debian GNU/Linux

MGE UPS SYSTEMS distributes the PSP package for Debian GNU/Linux through the APT method.

To install Personal Solution Pac, add the following line in the "/etc/apt/sources.list"
     deb [http://opensource.mgeups.com/debian](http://opensource.mgeups.com/debian) binary/

[K]Ubuntu users must replace the above line with:
     deb [http://debian.cri74.org/ubuntu-cri](http://debian.cri74.org/ubuntu-cri) hoary extra

Then, type the following commands, in a console as root:
     apt-get update
     apt-get install mgeups-psp

Note that you can also use the graphical method through Synaptic, Kynaptic and Kpackage.

Launch Personal Solution Pac from the menu "System" and enter the root password when prompted. 

But i assume you did that way. My idea is that maybe these dependencies are a bit hard, i mean they depend on unstable packages. I am not sure this is OK for you or not. You may get those packages one by one, by hand, if you really need.

---

### Post by wickwire on 2005-12-09
Hi,

I have an mge Protection Center 500 - I followed your instructions and the Personal Solution Pac installed without effort, however when I run "sudo psp", the window shows up for brief seconds, I can see my ups, and then it crashes with the output that follows:

akuma@Loki:~$ sudo psp
Password:

(psp:8554): Gtk-WARNING **: Attempting to add a widget with type gtkmm__GtkFixed  to a container of type gtkmm__GtkViewport, but the widget is already inside a c ontainer of type gtkmm__GtkViewport, the GTK+ FAQ at [http://www.gtk.org/faq/](http://www.gtk.org/faq/) exp lains how to reparent a widget.
Segmentation fault
akuma@Loki:~$ sudo psp
Segmentation fault
akuma@Loki:~$ sudo psp
Segmentation fault


How can I solve this?

Thanks

---

