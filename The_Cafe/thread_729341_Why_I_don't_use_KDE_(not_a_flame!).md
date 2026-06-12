---
title: "Why I don't use KDE (not a flame!)"
date: 2008-03-19
forum: The Cafe
---

### Post by sav2005 on 2008-03-19
I really like some KDE applications - Quanta, Kile and Kate come to mind, and I really don't mind its desktop. So why don't I use it? 

I'll tell you why - Knetwork manager will not log me into a WPA enterprise network that uses Dynamic WEP. Knetwork manager does not have a selector for Dynamic WEP. Gnome's nm-applet does, end of story. Why bother to boot into Gnome, access the network, log out and login to a KDE desktop? Once I'm in Gnome I'm ready to work.

Really, this is a serious issue if Kubuntu is to find a use on enterprise desktops.

---

### Post by Nythain on 2008-03-19
not the smartest man at wireless networking, but couldnt you skip the knetwork manager all together and just manually edit your /etc/network/interfaces file??? is there something super special about this WEP/WPA vs. others???

it seems an awful shame to let one little thing stop you from using a de you aparently like more than others (or you wouldnt have even bothered to post about it)

---

### Post by sav2005 on 2008-03-19
> **Nythain said:**
> not the smartest man at wireless networking, but couldnt you skip the knetwork manager all together and just manually edit your /etc/network/interfaces file??? is there something super special about this WEP/WPA vs. others???

it seems an awful shame to let one little thing stop you from using a de you aparently like more than others (or you wouldnt have even bothered to post about it)

I use several wireless networks and nm-applet is pretty good at identifying and logging in to each. Because of my mobility I don't want to hard-code my wireless configuration.

---

### Post by LaRoza on 2008-03-19
> **Nythain said:**
> is there something super special about this WEP/WPA vs. others???


Security.

---

### Post by p_quarles on 2008-03-20
If you prefer other things about the KDE suite, there shouldn't be any problem with simply Gnome's nm-applet in KDE.

---

### Post by NightwishFan on 2008-03-20
Kde is excellent. I am going to use it from now on. All the applications look better and seem to work better than any gnome/windows counterpart. Not that the others are bad, but better for me of course. It just seems all more integrated and tweakable. Looks great too. If the beta for KDE4 works well I might switch to it sooner. I went back in forth a lot but some of the stuff I learned today by tweaking it really made it grow on me.

---

### Post by thenetduck on 2008-03-20
I think that is because they are using QT instead of GTK which we know, QT isn't 100% open source (unless i am mistaken?) 

This is what I atribute the good looking KDE smoothness too, however with XGL/Graphic Effects with Gnome, I would have to say there really isn't anything special about QT anymore unless your a developer and just like it better.

The Net Duck

---

### Post by p_quarles on 2008-03-20
> **thenetduck said:**
> I think that is because they are using QT instead of GTK which we know, QT isn't 100% open source (unless i am mistaken?) 
They're both released under the same license. That was true about 10 years ago or so, but not any longer.

---

### Post by Sef on 2008-03-20
> I think that is because they are using QT instead of GTK which we know, QT isn't 100% open source (unless i am mistaken?) 

It is dual licensed.  

From [Trolltech]("http://trolltech.com/downloads"):

> Which Downloads Are Right for You?

Using a Dual Licensing Business Model, Trolltech provides its Qt and Qtopia products under commercial licenses for proprietary development and under the GPL and similar Open Source licenses for free and open source development.

---

### Post by Sef on 2008-03-20
Moved to Community Cafe since OP is not looking for help.  Only stating their opinion.

---

### Post by chucky chuckaluck on 2008-03-20
what about wifi-radar? would that do what you need?

---

### Post by red_Marvin on 2008-03-20
Or wicd? I had some problems installing it but i solved it:

(
when apt-getting wicd check what it wants to uninstall and grab those from packages.ubuntu.com before proceeding, if it should fail, just 
uninstall and reinstall the uninstalled whith dpkg -i...
)

EDIT:  the configuration dialog is /opt/wicd/gui.py, it's gtk but you don't need anything in any tray for it to work (there is some sort of tray applet too, but I don't use it so I can't report on it's performance).

---

### Post by leroyc on 2008-03-20
I guess I will give my opinion too. KDE has a long way to go.

They are doing their best with the new KDE4, but the RC2 version still has a lot of bugs to be cleaned before they are ready to launch.

Anyway, Gnome remains the best solution.

---

### Post by linuxuser28 on 2008-03-20
My solution is Gnome with KDE apps. (Amarok, K3B, Kaffeine).
Has there ever been talk of a merger of Gnome and KDE?

---

### Post by SomeGuyDude on 2008-03-20
> **linuxuser28 said:**
> My solution is Gnome with KDE apps. (Amarok, K3B, Kaffeine).
Has there ever been talk of a merger of Gnome and KDE?

How would that work? They seem to have vastly different ideals when it comes to designing a desktop environment. KDE is about tweakability and comprehensiveness, GNOME is more about streamlining and simplicity.

---

