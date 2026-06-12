---
title: "Xubuntu Question"
date: 2006-04-05
forum: The Cafe
---

### Post by Zodiac on 2006-04-05
I am not sure if this belongs here but...

I just have a quick question...

Can I install regular Ubuntu packages in Xubunu?

For example, Totem-Xine or Rythmbox-Gstreamer, or OpenOffice, will that cause a problem?

And, how can I add programs to the menu bars? I can't seem to drag and drop...

---

### Post by dragonfyre13 on 2006-04-05
[QUOTE=Zodiac]I am not sure if this belongs here but...

I just have a quick question...

Can I install regular Ubuntu packages in Xubunu?

For example, Totem-Xine or Rythmbox-Gstreamer, or OpenOffice, will that cause a problem?

And, how can I add programs to the menu bars? I can't seem to drag and drop...[/QUOTE]

Yes, you can install regular Gnome, and KDE packages with XUbuntu. Just go under the settings menu (search the forum, I'm not sure the exact location) and have Xubuntu start the gnome services, and/or kde services with xubuntu.

Also, to add things to the panel, you can only add things to the bottom panel. in that case, you just right click on it.

---

### Post by Darkriser on 2006-04-05
Of course! Xubuntu is just a regular Ubuntu server installation + xubuntu-desktop package. That's it.

[https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)

---

### Post by Zodiac on 2006-04-05
[QUOTE=dragonfyre13]Yes, you can install regular Gnome, and KDE packages with XUbuntu. Just go under the settings menu (search the forum, I'm not sure the exact location) and have Xubuntu start the gnome services, and/or kde services with xubuntu.[/QUOTE]

Okay I found that... very cool, will it slow my system down a lot??

[QUOTE=dragonfyre13]Also, to add things to the panel, you can only add things to the bottom panel. in that case, you just right click on it.[/QUOTE]

I see that I can right click, but for instance, if I want to add Gaim (with its little icon) to panel 1, how would I do that?


Also, this is going to seem really dumb but... how do I change my desktop background??

Thanks!

---

### Post by Zodiac on 2006-04-05
Here is something weird as well:

I cannot seem to play audio CDs using Xfmedia...

My fstab file looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0

---

### Post by bonzodog on 2006-04-05
To change the desktop background go to settings > Desktop Settings. There is a section there where you can choose the file to use.
Xfmedia seems to be funny with CD audio, I can't get it to play CD's either. It's something to do with the player, not your set-up.I have installed Xmms for an Audio player, and it does everything I want.
With XFCE, you can add stuff to either panel. right click on the panel and choose 'add to panel'. When the dialog pops up, choose 'Program Launcher'. it will add a deafult icon to the panel and at the same time bring up a dialog to customise the launcher. The program name is simply gaim in your case, and the Icon can be found in /usr/share/icons. Change the Icon by clicking the it in the launcher settings.

---

### Post by Zodiac on 2006-04-05
[QUOTE=bonzodog]To change the desktop background go to settings > Desktop Settings. There is a section there where you can choose the file to use.

Xfmedia seems to be funny with CD audio, I can't get it to play CD's either. It's something to do with the player, not your set-up.I have installed Xmms for an Audio player, and it does everything I want.[/QUOTE]

Would you recomend against installing Gnome apps to take care of my needs?

I am thinking Rythmbox here...

[QUOTE=bonzodog]With XFCE, you can add stuff to either panel. right click on the panel and choose 'add to panel'. When the dialog pops up, choose 'Program Launcher'. it will add a deafult icon to the panel and at the same time bring up a dialog to customise the launcher. The program name is simply gaim in your case, and the Icon can be found in /usr/share/icons. Change the Icon by clicking the it in the launcher settings.[/QUOTE]

Perfect!!! Thanks :)!!

---

### Post by psychicdragon on 2006-04-05
[QUOTE=Zodiac]Would you recomend against installing Gnome apps to take care of my needs?

I am thinking Rythmbox here...[/QUOTE]Gnome apps run fine in Xfce, they just start up more slowly than in Gnome because extra libraries have to be loaded. If you're running Xfce because your computer doesn't have much memory you may want to avoid running Gnome apps.

---

### Post by Zodiac on 2006-04-05
hmmm... you make a good point....

I wish there was a wiki page with installation instructions and alternative programs to those found within gnome...

I am sure I can dig up something...

Thanks everyone for your help :)

---

### Post by mrgnash on 2006-04-05
[QUOTE=Zodiac]hmmm... you make a good point....

I wish there was a wiki page with installation instructions and alternative programs to those found within gnome...

I am sure I can dig up something...

Thanks everyone for your help :)[/QUOTE]

If you go to Sessions and Startup>Advanced in the control panel, and then select 'Launch Gnome Services on Startup' you may find that while this adds to the time Xfce takes to load initially, it will improve general performance while running Gnome applications.

---

### Post by dragonfyre13 on 2006-04-06
[QUOTE=mrgnash]If you go to Sessions and Startup>Advanced in the control panel, and then select 'Launch Gnome Services on Startup' you may find that while this adds to the time Xfce takes to load initially, it will improve general performance while running Gnome applications.[/QUOTE]


THERE's where it is. I couldn't find it. As for the configuration questions you had, they are all in the setup menu.

So far as applications, I would search for "xfce" in synaptic, and take a look. also, you may want to have a look at the xfce site, they have some good stuff on there.

---

