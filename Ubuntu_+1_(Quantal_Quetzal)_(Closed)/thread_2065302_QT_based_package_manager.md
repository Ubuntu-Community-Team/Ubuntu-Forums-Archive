---
title: "QT based package manager"
date: 2012-10-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by odror on 2012-10-01
Currently (ubuntu 12.10) GTK application are not working well in KDE. I really need a package manager that will work under KDE. Is there a Qt base package manager.

Thanks

---

### Post by Gavin77 on 2012-10-01
> Currently (ubuntu 12.10) GTK application are not working well in KDE. I really need a package manager that will work under KDE. Is there a Qt base package manager.

They work fine for me.  If you just mean the way they look by default just run ```
kdesudo systemsettings
``` and make sure the Gtk Configuration is set correctly.

---

### Post by odror on 2012-10-01
> **Gavin77 said:**
> They work fine for me.  If you just mean the way they look by default just run ```
kdesudo systemsettings
``` and make sure the Gtk Configuration is set correctly.

Except that mine is different from yours.

---

### Post by Fitoschido on 2012-10-01
> **odror said:**
>  I really need a package manager that will work under KDE. Is there a Qt base package manager.

Isn't [Muon]("http://www.wonderly.com/2011/05/muon-kde-package-manager-and-software-center/") working for you?

---

### Post by Gavin77 on 2012-10-01
> **odror said:**
> Except that mine is different from yours.

Make sure you have kde-config-gtk-style installed.

---

### Post by odror on 2012-10-01
> **Fitoschido said:**
> Isn't [Muon]("http://www.wonderly.com/2011/05/muon-kde-package-manager-and-software-center/") working for you?

Thank you. It is exactly what I was looking for. 

Until the GTK issues are solved I'll be living in the Qt/KDE world

---

### Post by odror on 2012-10-01
> **Gavin77 said:**
> Make sure you have kde-config-gtk-style installed.

Yes that package was missing. I still have problem with GTK under KDE.

As a side note. Installing pasma desktop. Was incomplete installation of the KDE desktop. For example Dolphin and other critical packages were not included. It is possible that there is additional missing package that may be the culprit.

---

### Post by 67GTA on 2012-10-01
Gnome 3 broke all theme work done up to that point as far as interoperability. I use Synaptic under Kubuntu. The only solution is to use qtcurve for KDE and Gnome themes. You can configure KDE to use the ozone theme (very similar to oxygen style) and set the KDE GTK theme to qtcurve. To make synaptic use the ozone theme, run ```
sudo cp .gtkrc-2.0-kde4 /root/.gtkrc-2.0
``` in a terminal.

---

### Post by kio_http on 2012-10-03
Why not install kubuntu-desktop if you want to be in the KDE world for a while? That way you will get the essential apps etc.

---

