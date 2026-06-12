---
title: "xfce desktop mix-up"
date: 2006-12-15
forum: Ubuntu Customization Guide
---

### Post by derby007 on 2006-12-15
Q. I want to install the XFCE (Xubuntu) desktop. I got the Edgy Alternate download, but i have Dapper installed. I brought home the CD and typed apt-get install xubuntu-desktop, BUT it says it is going to REMOVE alot of programs....!! i then did not go ahead with it, but my Power-Up & Shut-Down screens are gone, (actually it seems much faster !!) So, have i started something i cannot reverse, or should i go ahead with the update, or should i get the Dapper Xubuntu Alternate download??? any ideas, [SIZE="1"]NOTE: i dont ave an internet connection on this PC.[/SIZE] ](*,)

---

### Post by john.nicholls on 2006-12-21
> **derby007 said:**
> Q. I want to install the XFCE (Xubuntu) desktop. I got the Edgy Alternate download, but i have Dapper installed. I brought home the CD and typed apt-get install xubuntu-desktop, BUT it says it is going to REMOVE alot of programs....!! i then did not go ahead with it, but my Power-Up & Shut-Down screens are gone, (actually it seems much faster !!) So, have i started something i cannot reverse, or should i go ahead with the update, or should i get the Dapper Xubuntu Alternate download??? any ideas, [SIZE="1"]NOTE: i dont ave an internet connection on this PC.[/SIZE] ](*,)

If you already have Ubuntu installed, installing xubuntu-desktop will remove a lot of Gnome programs such as OpenOffice and replace them with smaller alternatives such as Abiword. If you want to keep the programs you already have installed, try apt-get install xfce, which will just give you the minimum installation of Xfce.

John

---

### Post by qamelian on 2006-12-21
> **john.nicholls said:**
> If you already have Ubuntu installed, installing xubuntu-desktop will remove a lot of Gnome programs such as OpenOffice and replace them with smaller alternatives such as Abiword. If you want to keep the programs you already have installed, try apt-get install xfce, which will just give you the minimum installation of Xfce.

John

Installing xubuntu-desktop to an already installed ubuntu should not remove or replace anything. It just adds the components included in the xubuntu-desktop metapackage. You can have a complete install of each if you like.

---

### Post by derby007 on 2006-12-22
No, i ran 'apt-get install xubuntu-desktop' from the Xubuntu alternate CD & it messed up my whole Gnome set-up. I recovered Gnome from the Edgy Alt CD but I'm now without alot of splash screens, icons etc, (& Apache, as i had LAMP installed).....bummer.

---

### Post by qamelian on 2006-12-22
> **derby007 said:**
> No, i ran 'apt-get install xubuntu-desktop' from the Xubuntu alternate CD & it messed up my whole Gnome set-up. I recovered Gnome from the Edgy Alt CD but I'm now without alot of splash screens, icons etc, (& Apache, as i had LAMP installed).....bummer.

That is odd because, on top of my default Ubuntu install, I have added both the xubuntu-desktop and kubuntu-desktop metapackages with no issues. I use this setup on my demo machine to show curious friends the difference between the three environments as it's easier than trying to explain to them verbally. Been running like this since testing Dapper with no breakage or oddities yet.

---

### Post by qamelian on 2006-12-22
> **derby007 said:**
> No, i ran 'apt-get install xubuntu-desktop' from the Xubuntu alternate CD & it messed up my whole Gnome set-up. I recovered Gnome from the Edgy Alt CD but I'm now without alot of splash screens, icons etc, (& Apache, as i had LAMP installed).....bummer.

I should mention that I added the metapackages by installing from the repositories online, not from the CD.

---

### Post by derby007 on 2006-12-23
After restoring Gnome from CD, i was still missing a few items: like Gedit, Gnome games (my friends nearly killed me, 'what> no games!'), but managed to restore them by using Synaptic Package Manager. BUT....i'm still missing my EXIT cons/images & splash screens, its very anoying on boot-up / pwr-down :mad:  Pls respond if u know how to get them back...:-k

---

### Post by ahaslam on 2006-12-23
I suggest that you never install the full 'desktop' package, unless it's the first DE on a server install.
When I added xfce I just installed xfce4 & thunar, and when I added kde I just went with kdebase.

I also recommend that you use aptitude for installing packages that have many dependencies.

Tony.

PS. regarding your current situation, there should be a gnome/ubuntu artwork package that will sort you out ;)

---

