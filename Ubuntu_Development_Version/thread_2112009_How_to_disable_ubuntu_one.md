---
title: "How to disable ubuntu one"
date: 2013-02-03
forum: Ubuntu Development Version
---

### Post by Chelidze on 2013-02-03
So I did an update and now after the reboot i noticed a new icon in my panel "ubuntu one"
[IMG]http://i.imgur.com/HjchEVvl.png[/IMG]
[http://i.imgur.com/HjchEVv.png](http://i.imgur.com/HjchEVv.png)
Considering that i do not use ubuntu one I really do not want it to start on my start up and eat my ram 
 So is there a way to disable it 


 Thank you in advanced

---

### Post by mc4man on 2013-02-03
That's the indicator-sync icon which is for ubuntuone, dropbox, ect.
If you don't want the indicator then remove the indicator-sync package

If you don't want ubuntuone then search it in synaptic & start removing the various packages until  or if it wants to remove something you want or need
(also there is libsyncdaemon package

Don't think it uses much ram here, if you wanted to keep there may be some value in removing ubuntuone-launch from startup though all it does is check for any changes to sync

---

### Post by cariboo on 2013-02-03
Indicator-sync just dropped in Raring, see philinux's sticky at the top of the page. You should be able to remove indicator-sync if you don't need it.

---

### Post by Chelidze on 2013-02-03
Thank you for the reply but my intention is not to remove the app it's not to enable it on start up and I do not want it's icon to clunk up the top right panel 

 Is there a way to just do not start it on start up

---

### Post by mc4man on 2013-02-03
> **Chelidze said:**
> Thank you for the reply but my intention is not to remove the app it's not to enable it on start up and I do not want it's icon to clunk up the top right panel 

 Is there a way to just do not start it on start up
one way

```
gksudo gedit /etc/xdg/autostart/ubuntuone-launch.desktop
```
change "NoDisplay=true" to 
NoDisplay=false

Save, open Startup Applications & disable it

As far as the icon easiest to just remove the package (indicator-sync

---

### Post by cariboo on 2013-02-03
Apparently indicator-sync is supposed to work with other cloud storage type services, like dropbox. I haven't tried it out, as I really only use Ubuntu One on my tablet.

---

### Post by Chelidze on 2013-02-03
Can not I just remove this app from the start up ???
I started Startup applications software but sadly I can not see any of the software I have installed 

[IMG]http://i.imgur.com/MnbjvEjl.jpg[/IMG]


Sorry I looked in to this and as far as I am concerned this is a part of new ubuntu and not just ubuntu one's fence indicator

So most probably I must live it there

---

### Post by mc4man on 2013-02-03
Only ubuntuone would be seen in Startup Apps (if you make it visible) & then can be disabled if desired
(don't see the point as it just runs for a moment 30 secs after login

As far as the indicator (indicator-sync-service) don't see where that is optional if installed

---

### Post by cheapodonuts on 2013-11-16
> **mc4man said:**
> one way

```
gksudo gedit /etc/xdg/autostart/ubuntuone-launch.desktop
```
change "NoDisplay=true" to 
NoDisplay=false

Save, open Startup Applications & disable it

As far as the icon easiest to just remove the package (indicator-sync

Perfect! Thanx mc4man you da man! :cool:

---

### Post by coffeecat on 2013-11-16
Closed - this was a Raring thread. We are now in the Trusty dev cycle.

---

