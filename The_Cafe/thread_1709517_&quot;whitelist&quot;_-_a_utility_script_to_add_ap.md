---
title: "&quot;whitelist&quot; - a utility script to add apps to Unity's whitelist."
date: 2011-03-18
forum: The Cafe
---

### Post by fuduntu on 2011-03-18
As you all know, Ubuntu Natty will enforce a notification area whitelist that will break a lot of applications that haven't or won't migrate to indicator applets.  To work around this, I installed Natty this morning and wrote a script that will empower you all as users to whitelist anything that you want, without having to hack gsettings.

It's available on my blog if you want it - [http://www.fewt.com/2011/03/whitelist-utility-script-to-allow-apps.html](http://www.fewt.com/2011/03/whitelist-utility-script-to-allow-apps.html)

:D

---

### Post by slackthumbz on 2011-03-18
Thanks for that, I've heard it's possible to kill the unity plugin altogether within a unity session so you can just use an alternate dock (like docky or AWN) does anyone know if that's true or not? I think it'd be rather handy to be able to knock out that stupid sidebar and menubar, disable global menu and effectively have a gnome 2.x desktop without gnome-panel etc. 

I know everyone keeps saying "just use the classic desktop session" but that's a time limited option and some way of preserving my current desktop style post gnome 2.x would be very handy. I can't stand unity or gnome-shell.

---

### Post by fuduntu on 2011-06-09
Based on my web stats, this tool seems to be pretty popular, I'm glad that I wrote it and that it's helping people. :)

---

### Post by PGScooter on 2011-06-18
this is a nice script, thank you

---

### Post by beew on 2011-06-18
I have noticed that whitelisting applications in dconf-editor enable tray icons to show up, but when there are tray icons of non default applications such as VLC or the LibreOffice quickstart tray icon on the panel volume control stops working (clicking it has no effect)

---

### Post by jerenept on 2011-06-18
> **beew said:**
> I have noticed that whitelisting applications in dconf-editor enable tray icons to show up, but when there are tray icons of non default applications such as VLC or the LibreOffice quickstart tray icon on the panel volume control stops working (clicking it has no effect)

Click the power button, and then move the mouse over to the other icons.

---

### Post by beew on 2011-06-20
> **jerenept said:**
> Click the power button, and then move the mouse over to the other icons.

That is weird. If I do what you say then the volume control works again but the other icons stop working, repeat the same procedure makes no difference. This has to be a bug resulting from trying to implement the global menu. So many problems for a bad feature that only gain a few more pixels on the top..

---

