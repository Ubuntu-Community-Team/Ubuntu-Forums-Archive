---
title: "Trying to make a mate panel applet for ubuntu-mate 16.04"
date: 2016-04-09
forum: Ubuntu Application Development
---

### Post by pqwoerituytrueiwoq on 2016-04-09
I am looking at moving to ubuntu mate for the next few years, but i need to make a few applets, mainly to send commands to my raspberry pi and monitor it, i may need to make a applet to monitor my GPU temperature (if the built in sensor applet does not work)

I managed to find this:
[http://wiki.mate-desktop.org/docs:devel:mate-panel#python_applets](http://wiki.mate-desktop.org/docs:devel:mate-panel#python_applets)
but i need to know how to set icons, click actions, and tooltips
i will also need to update the label every few seconds

in regards to the updating of labels, does the applet_factory function need to return or can i just use a while True loop before it returns
if it does not need to return i could just put a inf loop the applet_fill function

---

### Post by caz88888 on 2016-11-27
i don't know about making applets but i do know a little about the sensor pannel applet.

it is esentialy limited by the quality of your sensors.
if your sensors work then the applet will (to the best of my knowlege work).
sometimes the sensors don't work the tempriture sensor on (what i think is) the motherboard of my vostro 400 reads about 68 most of the time on most systems with most CPU options which seems a bit high given that the CPU's are about 50-ish.
sometimes they are baddly labled so the GPU and motherboard might like mine be labled temp0 or temp1 (i only found out because of the forementioned possible bug in the mobo tempriture sensor.

good luck.

---

