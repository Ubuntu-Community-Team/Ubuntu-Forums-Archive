---
title: "Presenting Ejecter, a quick way to unmount devices right from your system tray"
date: 2008-09-25
forum: Ubuntu Dev Link Forum
---

### Post by fredp on 2008-09-25
Hello everybody,
I just released the first public version (0.0.9) of **Ejecter** ([http://launchpad.net/ejecter](http://launchpad.net/ejecter)), a little tool which makes it possible to unmount external devices and eject cd-roms without having to right-click on device icon either on the desktop or in nautilus.
It sits in background and shows an icon in the system tray when one or more peripherals are connected to your pc: once clicked it a window appears with the list of the devices (volume name and device type, much clearer than the similar thing available on Windows) and the related eject button.

Mandatory screenshot: 
[IMG]http://i425.photobucket.com/albums/pp337/fredpel/Ejecter/shot2.jpg[/IMG]

It is written in Vala, so no overhead due to vm like Python (it is compiled as C code) and no strange requirements once compiled (just GTK/GLib). Installation instructions (really simple) and requirements are included in the source tarball.

I'd like to have some feedback about it: whether it is useful or not, how can I improve it, any found bug or any suggestion are really appreciated.
I'd also like to collect a nice number of translations in order to release 0.1, and the go on improving it (some features are already planned).
It would be great if somebody could package a .deb of Ejecter (as I don't know how to do it) to make it easier for people to install and test it.

[http://launchpad.net/ejecter](http://launchpad.net/ejecter)

---

### Post by Teamgeist on 2008-09-26
I translated it into German.
Where do you want to the .po file to be sent?
email? or should I file a bug in Launchpad?

/edit: translated it on launchpad also. ;-)

---

### Post by lisati on 2008-09-26
> **Teamgeist said:**
> I translated it into German.
Where do you want to the .po file to be sent?
email? or should I file a bug in Launchpad?

/edit: translated it on launchpad also. ;-)

Spotted it on launchpad

---

### Post by UbuWu on 2008-09-26
Yes, this is very useful! Perhaps you could even try to get this shipped with jaunty?

---

### Post by UbuWu on 2008-09-26
I put a request for packages on ubuntu as well as getdeb:

[https://bugs.launchpad.net/ubuntu/+bug/274782](https://bugs.launchpad.net/ubuntu/+bug/274782)
[https://bugs.launchpad.net/getdeb.net/+bug/274783](https://bugs.launchpad.net/getdeb.net/+bug/274783)

---

### Post by UbuWu on 2008-09-26
On my intrepid system, configure stops with this message:

pkg-config cannot find gtk+-2.0 >= 2.12.0 

Synaptic tells me that I have 2.14.3 installed though.

---

### Post by UbuWu on 2008-09-26
fredp, can you please have a look at the getdeb bug? they also have trouble compiling it.

---

### Post by fredp on 2008-09-26
> **UbuWu said:**
> On my intrepid system, configure stops with this message:

pkg-config cannot find gtk+-2.0 >= 2.12.0 

Synaptic tells me that I have 2.14.3 installed though.
Do you have libgtk+2.0-dev packaged installed?

Instead the getdeb bug should be due to a old release of Vala, they're using 0.1.6 but Ejecter needs 0.3 (available in hardy-backports).

---

### Post by UbuWu on 2008-09-26
Ah no didn't have that one (it is called libgtk2.0-dev).

---

### Post by smartboyathome on 2008-09-28
The problem I see is that it uses the system tray (frowned upon). Instead of that, I think it should be an applet for GNOME, and it might have a better chance of getting into Ubuntu (and possibly even GNOME :D).

---

### Post by kostkon on 2008-09-28
> **fredp said:**
> It would be great if somebody could package a .deb of Ejecter (as I don't know how to do it) to make it easier for people to install and test it.

[http://launchpad.net/ejecter](http://launchpad.net/ejecter)
Since you are using *Launchpad* it would be a good idea to use your PPA to distribute this app. You'll only need to learn how to make source packages. The rest is done by *Launchpad*.

> **smartboyathome said:**
> The problem I see is that it uses the system tray (frowned upon). Instead of that, I think it should be an applet for GNOME, and it might have a better chance of getting into Ubuntu (and possibly even GNOME :D).
You can debate whether it should appear in the system tray or not, since it is a fact that the tray functionality is abused by some apps.

But since the dev wants it to appear only when a device is plugged (i.e. to also act as an notification), then I don't think this could have been done easily if it was an applet.

It could be changed to an applet, of course, and have its icon change when a device is plugged or something similar; but this has the added requirement that the user adds it to his/her panel.

---

### Post by fredp on 2008-09-29
> **kostkon said:**
> Since you are using *Launchpad* it would be a good idea to use your PPA to distribute this app. You'll only need to learn how to make source packages. The rest is done by *Launchpad*.


I'll have a look.

> **kostkon said:**
> 
You can debate whether it should appear in the system tray or not, since it is a fact that the tray functionality is abused by some apps.

But since the dev wants it to appear only when a device is plugged (i.e. to also act as an notification), then I don't think this could have been done easily if it was an applet.

It could be changed to an applet, of course, and have its icon change when a device is plugged or something similar; but this has the added requirement that the user adds it to his/her panel.

Yes, I thought about making this an applet, but I went for using the system tray because I wanted Ejecter to be invisible when it has no function (i.e. no device connected). Also, Ejecter in this way is not tied to Gnome, and can be used within other DEs.

---

### Post by UbuWu on 2008-09-29
It is now available from getdeb.

---

### Post by Stefanie on 2008-09-29
nice app. it would be perfect if it could be used to mount drives as well. now the unmounted drives are greyed out but clicking on them doesn't mount them again.

---

### Post by fredp on 2008-09-29
> **Stefanie said:**
> nice app. it would be perfect if it could be used to mount drives as well. now the unmounted drives are greyed out but clicking on them doesn't mount them again.
Could be a nice idea, please file a bug at launchpad.net/ejecter.


Glad to see Ejecter available at getdeb.net :D

---

### Post by Stefanie on 2008-09-30
I filed the bug report and I also added a Dutch translation.

---

### Post by fredp on 2008-09-30
> **Stefanie said:**
> I filed the bug report and I also added a Dutch translation.
Thank you very much :D

---

### Post by fredp on 2008-10-24
**[COLOR="Red"]Just released Ejecter 0.1 "Cosmos rocks"![/COLOR]**

Finally featuring translations, bugfixes and the icon that disappears.

You find all the info here: [http://launchpad.net/ejecter/+announcement/1299](http://launchpad.net/ejecter/+announcement/1299)

---

### Post by fredp on 2008-12-15
**[COLOR="Red"]Released Ejecter 0.1.90[/COLOR]**

After some time I got back onto Ejecter and tried to fix the issues which came out with Gtk 2.14 (on which it depends).
This version is meant as a preliminary release before 0.2, in order to test new features and fixes.

For 0.2 I hope to distribute .debs through my ppa and not to have to depend on Gtk >= 2.14 (in that case loosing some minor things, so I've to find out how to check at compile-time if I can use new functions from 2.14).

Download & file bugs at: **[http://launchpad.net/ejecter/+announcement/1626]("https://launchpad.net/ejecter/+announcement/1626")**

---

### Post by tramir on 2009-06-07
Is there any way to modify the "eject" command so that it runs the script at [http://elliotli.blogspot.com/2009/01/safely-remove-usb-hard-drive-in-linux.html]("http://elliotli.blogspot.com/2009/01/safely-remove-usb-hard-drive-in-linux.html") after unmounting?

---

