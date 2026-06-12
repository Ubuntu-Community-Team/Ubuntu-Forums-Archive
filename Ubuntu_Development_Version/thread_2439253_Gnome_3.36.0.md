---
title: "Gnome 3.36.0"
date: 2020-03-25
forum: Ubuntu Development Version
---

### Post by P-I H on 2020-03-25
After updates today Gnome is now on Gnome 3.36.0.
Extension settings on Openweather and Dash to panel is now working. However installation of **gnome-shell-extension-prefs** isn't done and you have to do this.

---

### Post by dino99 on 2020-03-25
> **P-I H said:**
> After updates today Gnome is now on Gnome 3.36.0.
Extension settings on Openweather and Dash to panel is now working. However installation of **gnome-shell-extension-prefs** isn't done and you have to do this.

gnome-shell-extension-weather: simply get a dot, not directly temp; need to click on date then select a city (or geolocalisation)

journalctl -b | grep weather
 gnome-shell[1553]: Usage of object.actor is deprecated for OpenweatherMenuButton
                                            [email]_init@/usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/extension.js[/email]:192:9
                                            [email]enable@/usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/extension.js[/email]:1648:23

extension-prefs is a dupe of tweaks

---

### Post by amano on 2020-03-25
Hmm. What is Openweather? Are we officially supposed to install that?

Currently my weather forecasts are very slow to show up in the notification area. And it takes ages from within GNOME-weather directly.

Those weather related packages are installed:
ir1.2-gweather-3.0/focal,now 3.34.0-1 amd64  [installiert]
gnome-weather/focal,focal,now 3.34.0-1 all  [installiert]
libgweather-common/focal,focal,now 3.34.0-1 all  [installiert]

I had that once, but it went away with the update to the final GNOME version a year ago. BUT this time there is no gnome-weather 3.36 version to update to.

---

### Post by P-I H on 2020-03-25
@dino99 "extension-prefs is a dupe of tweaks"
In a way yes, but some extensions e.g Openweather and Dash to panel uses this app to enable settings. In case it isn't installed settings will not work.

Openweather is a gnome extension. I suppose you customize your installed system as you like. In case you install [B]gnome-shell-extensions gnome-tweaks
[/B]you get a lot of extensions in gnome tweaks. I have installed 4 myself Alternatetab, Dash to panel, Openweather and Sensory perception.

---

