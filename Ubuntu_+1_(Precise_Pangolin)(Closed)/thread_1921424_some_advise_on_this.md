---
title: "some advise on this"
date: 2012-02-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rburkartjo on 2012-02-06
first note that i had mint mate installed before i upgraded to 12.04 from the command line
if i run 
sudo apt-get update && sudo apt-get dist-upgrade
i get this
Calculating upgrade... Done
The following packages will be REMOVED:
  gtk2-engines:i386 gtk2-engines-murrine:i386 gtk2-engines-pixbuf gtk2-engines-pixbuf:i386 ia32-libs
  ia32-libs-multiarch:i386 ibus-gtk:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libgail-common:i386
  libgail18:i386 libgtk2.0-0:i386 libqt4-dbus:i386 libqt4-declarative:i386 libqt4-designer:i386 libqt4-network:i386
  libqt4-opengl:i386 libqt4-qt3support:i386 libqt4-script:i386 libqt4-scripttools:i386 libqt4-sql:i386
  libqt4-sql-mysql libqt4-sql-mysql:i386 libqt4-svg:i386 libqt4-test:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386
  libqtcore4:i386 libqtgui4:i386 libqtwebkit4:i386 librsvg2-common:i386 mint-artwork-gnome mint-artwork-mate
  mint-meta-mate wine1.3
The following packages will be upgraded:
  gedit gedit-common gir1.2-appindicator3-0.1 gir1.2-gtk-2.0 gir1.2-gtksource-3.0 libappindicator1 libappindicator3-1
  libgail-common libgail-dev libgail18 libgtk2.0-0 libgtk2.0-bin libgtk2.0-dev libgtksourceview-3.0-0 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql
  libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 python-appindicator qdbus
29 upgraded, 0 newly installed, 35 to remove and 0 not upgraded.
Need to get 22.9 MB of archives.
After this operation, 205 MB disk space will be freed.
Do you want to continue [Y/n]? n
if i run
sudo apt-get update && sudo apt-get upgrade
i get this
The following packages have been kept back:
  gtk2-engines-pixbuf libgail-common libgail-dev libgail18 libgtk2.0-0 libgtk2.0-bin libgtk2.0-dev libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 qdbus
The following packages will be upgraded:
  gedit gedit-common gir1.2-appindicator3-0.1 gir1.2-gtk-2.0 gir1.2-gtksource-3.0 libappindicator1 libappindicator3-1
  libgtksourceview-3.0-0 python-appindicator
9 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
Need to get 1,268 kB of archives.
After this operation, 732 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
which should i run and why
tks

---

### Post by ronacc on 2012-02-06
you can just run the upgrade ( not the dist-upgrade ) and wait for the dependencies of the held back packages to arrive . During a dev cycle you have to be very careful with dist-upgrade .

---

### Post by rburkartjo on 2012-02-06
ron tks that was what i was going to do but wanted some feedback

---

### Post by Linux Dutchman on 2012-02-07
Keep in mind that 12.04 is still in development. So, if you run into any kind of issues, i'm not surprised. It's still a beta version, or test version. Some packages might cause some issues with your 12.04 system.

---

### Post by grahammechanical on 2012-02-07
I recently purged a ppa. The action wanted to remove all kinds of stuff and like an idiot I clicked Yes and it removed several utilities and programs such as file manager, Ubuntu software centre and Libreoffice.

You have left over Mint stuff and there are i386 libraries that are slowly being replaced by multiarch libraries. And like me you will have stuff left over from 11.10.

Now is not the time to try to clear stuff out. This is what I have learnt from my experience.

You could of course use synaptic to try to remove some of those Mint libraries and then check what else will be removed.

On a couple of occasions I have found synaptic wanting to remove Ubuntu Desktop. So, be careful.

Regards.

---

