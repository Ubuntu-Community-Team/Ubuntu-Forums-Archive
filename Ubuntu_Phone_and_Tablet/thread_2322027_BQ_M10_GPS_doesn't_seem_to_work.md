---
title: "BQ M10 GPS doesn't seem to work"
date: 2016-04-25
forum: Ubuntu Phone and Tablet
---

### Post by davo4 on 2016-04-25
I have updated everything, have location switched on, the GPs switched on, yet the apps can't discover my location. When i go outside to hopefully lock onto a couple of satelites the ap locks up as I'm no longer in WiFi range.
 I notice that on page 36 of the User manual it says that the maps are not preloaded and I must be connected to the internet to use them? So what F**king good is GPS without a preloaded map or access to the net. Any suggestions?

---

### Post by David_Farkas on 2016-04-26
Check System settings > Security & Privacy > Location. There you can choose how to detect your location (GPS, Wifi or both), which apps can access your location. And yes, for now, if you want to use the navigation you need an internet connection because the maps are not stored on your mobile.

---

### Post by alj-3 on 2016-04-26
I'm having the same trouble. The problem is not in the system settings; everything is set correctly so that the apps all have access to location data. I installed the Location Test app, and it does, in fact, give the correct coordinates for my location. However, the Nearby and Weather scopes do not access that information, and instead default to a location that it stored during shipping (at the UPS warehouse). Meanwhile, uNav shows a location in London, or, sometimes, my correct location, which is in New England in the US.

This isn't a user settings problem, this is a system problem.

---

### Post by davo4 on 2016-04-26
Thanks alij-3 its good to know that there are others,out there with similar prob. I will also install the test location app to verify that the problem is software not hardware.

---

### Post by alj-3 on 2016-04-26
So I tried going to the Battery settings and turning off Wifi and GPS, and then rebooting. After doing that, the Weather scope has the correct location, the Nearby scope still puts me at the UPS depot, and now uNav has me in London. The Here map also has the correct location. Crazy. I'll be routed to Hartford by going over the Thames river, I guess.

---

### Post by Michael_Crees on 2016-04-27
Lots of people are finding the location service buggy, this one seems relevant: [https://bugs.launchpad.net/ubuntu/+source/location-service/+bug/1573168](https://bugs.launchpad.net/ubuntu/+source/location-service/+bug/1573168)

---

