---
title: "Howto: Customize default guest settion panels"
date: 2012-10-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-10-01
I have attached a quick setup that will give you a couple more options
to install it just run the install script from a terminal
This will give you the option to give a default xubuntu session the panel layout of gnome2, windows, or xubuntu (stock)
You can change the layout at any time from the settings under system
all dependencies are present on a clean install of xubuntu 12.10 beta 2
**if you dont care about making your own layout skip to the attachment

You can make your own layout by adding a xml file to (the changer will support any layout you add to this folder)
[FONT=Courier New]/etc/xdg/xdg-xubuntu/xfce4/panel/[/FONT]
you can base your xml file off any of the xml files in that folder as well as
[FONT=Courier New]~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml[/FONT]

the applets to not have to be ordered by number i just think the xml looks better if you do, they don't have to start at 1 either

some applets use setting located in 
[FONT=Courier New]~/.config/xfce4/panel/[/FONT]
this is the equivalent location for the default session
[FONT=Courier New]/etc/xdg/xfce4/panel/[/FONT]
the number in [FONT=Courier New]weather-12.rc[/FONT] means that in the xml file weather is plugin number 12 ([FONT=Courier New]plugin-12[/FONT])

feel free to share any xml files you make here feel free to ask any question :), sharing also makes for a good backup of your layout

[B]The .tar.bz2 has a couple fixes (leading 0 in windows clock and missing exit command in configuration app)
also compressed it on my 10.04 install where the file roller actually compresses data[/B]

---

### Post by jbicha on 2012-10-01
How about contributing to the community help wiki?

[https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession)

---

### Post by pqwoerituytrueiwoq on 2012-10-01
not sure where to insert my stuff at... (and i don't want my full name on it)
but here are some screenshots to help people understand how the xml files work
[[IMG]http://i.imgur.com/LTiwFs.png[/IMG]](http://imgur.com/LTiwF) [[IMG]http://i.imgur.com/LiSBgs.png[/IMG]](http://imgur.com/LiSBg) [[IMG]http://i.imgur.com/omumrs.png[/IMG]](http://imgur.com/omumr)

---

