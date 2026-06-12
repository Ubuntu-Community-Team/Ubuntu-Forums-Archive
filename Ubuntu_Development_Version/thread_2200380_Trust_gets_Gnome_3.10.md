---
title: "Trust gets Gnome 3.10"
date: 2014-01-19
forum: Ubuntu Development Version
---

### Post by mrfelker on 2014-01-19
Despite what developers had said I installed ubuntu-gnome-desktop over an install of Kubuntu 14.04.  Gnome-shell  3.10  is very stable and a welcome upgrade.  Upgrade to Gnome was about  2 days  ago Gnomeand did not involve adding experimental gnome ppas.

---

### Post by philinux on 2014-01-20
In proposed repo.

> Great news for Ubuntu GNOME / GNOME Shell fans: GNOME Shell 3.10 has landed in the Ubuntu 14.04 LTS Trusty Tahr repositories. Currently, the package is available in the Proposed repositories.

[http://www.webupd8.org/2014/01/gnome-shell-310-lands-in-ubuntu-1404.html](http://www.webupd8.org/2014/01/gnome-shell-310-lands-in-ubuntu-1404.html)

and 

[http://www.omgubuntu.co.uk/2014/01/gnome-3-10-install-in-ubuntu-14-04-lts?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2014/01/gnome-3-10-install-in-ubuntu-14-04-lts?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by xc3RnbFO8P on 2014-01-22
I accidentally delete the GNOME file in /usr/share/xsessions
is there anybody that can provide me a new one?
I have tried to re install without luck.

---

### Post by QDR06VV9 on 2014-01-22
> **Ringi said:**
> I accidentally delete the GNOME file in /usr/share/xsessions
is there anybody that can provide me a new one?
I have tried to re install without luck.
Ringi I am not sure that will work with anybody elses file But I am not opposed to share mine.
But have you tried Terminal
```
gnome-session --session=gnome
```
Should generate a new file.

---

### Post by xc3RnbFO8P on 2014-01-22
This what I get

> @rig-Aspire-R3600:~$ gnome-session --session=gnome

** (gnome-session-check-accelerated:3958): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

** (gnome-session-check-accelerated:3958): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

** (gnome-session:3957): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

** (gnome-session:3957): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist
gnome-session[3957]: WARNING: Failed to acquire org.gnome.SessionManager
rig@rig-Aspire-R3600:~$ 

gnome-shell --replace
 works

---

### Post by zika on 2014-01-22
> **runrickus said:**
> Ringi I am not sure that will work with anybody elses file But I am not opposed to share mine.
But have you tried Terminal
```
gnome-session --session=gnome
```
Should generate a new file.Are You sure? I've used that command for ages (xinit,startx) and never seen such effect...

---

### Post by QDR06VV9 on 2014-01-22
> **zika said:**
> Are You sure? I've used that command for ages (xinit,startx) and never seen such effect...
Hi zika, Nope not sure now! Still asleep more Coffee.
About the only other thing I could suggest is reinstalling gnome-shell & gnome-shell-extensions

---

### Post by zika on 2014-01-22
> **runrickus said:**
> Hi zika, Nope not sure now! Still asleep more Coffee.
About the only other thing I could suggest is reinstalling gnome-shell & gnome-shell-extensions[IMG]http://www.sherv.net/cm/emoticons/drink/coffee-break.gif[/IMG][IMG]http://www.sherv.net/cm/emoticons/hand-gestures/dap-greeting-smiley-emoticon.gif[/IMG]

---

### Post by xc3RnbFO8P on 2014-01-22
Dconf editor  org.gnome.SessionManager

[[img]http://farm8.staticflickr.com/7460/12086482346_9256d9357f_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/12086482346/)
[Screenshot from 2014-01-22 15:06:08](http://www.flickr.com/photos/96052779@N07/12086482346/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by QDR06VV9 on 2014-01-22
> **zika said:**
> [IMG]http://www.sherv.net/cm/emoticons/drink/coffee-break.gif[/IMG][IMG]http://www.sherv.net/cm/emoticons/hand-gestures/dap-greeting-smiley-emoticon.gif[/IMG]
I Like it!
I should have stuck to "*Better to remain silent* and be thought a fool *than* to speak out and remove all doubt." 
Good to see you zika.
Regards

---

### Post by zika on 2014-01-22
> **Ringi said:**
> Dconf editor  org.gnome.SessionManager

[[IMG]http://farm8.staticflickr.com/7460/12086482346_9256d9357f_c.jpg[/IMG]]("http://www.flickr.com/photos/96052779@N07/12086482346/")
[Screenshot from 2014-01-22 15:06:08]("http://www.flickr.com/photos/96052779@N07/12086482346/") by [ringi_is]("http://www.flickr.com/people/96052779@N07/"), on Flickr
You mean```
dconf write /org/gnome/gnome-session/auto-save-session true
```...? I do get lost in such big pictures... ;)
That might do the trick...

---

### Post by xc3RnbFO8P on 2014-01-22
> **zika said:**
> You mean```
dconf write /org/gnome/gnome-session/auto-save-session true
```...? I do get lost in such big pictures... ;)
That might do the trick...
I try that when I get this GNOME file :P

---

### Post by QDR06VV9 on 2014-01-22
Ok ringi if you willing to try this here it is.
When I put this in a .gz it got renamed to GNOME.desktop
You will no doubt have to rename it again to just GNOME and even possibly reset permissions.
Good Luck (fingers crossed)

---

### Post by xc3RnbFO8P on 2014-01-22
> **runrickus said:**
> Ok ringi if you willing to try this here it is.
When I put this in a .gz it got renamed to GNOME.desktop
You will no doubt have to rename it again to just GNOME and even possibly reset permissions.
Good Luck (fingers crossed)

Thanks @runrickus
it works  :popcorn:

---

### Post by QDR06VV9 on 2014-01-22
> **Ringi said:**
> Thanks @runrickus
it works  :popcorn:

Great! Good to know.

---

