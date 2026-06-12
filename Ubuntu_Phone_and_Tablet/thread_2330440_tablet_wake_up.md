---
title: "tablet wake up"
date: 2016-07-11
forum: Ubuntu Phone and Tablet
---

### Post by Johan_Helsingius on 2016-07-11
Is there any way to get the tablet to wake up without using the power button once it has blanked out the screen?

---

### Post by donquichot2016 on 2016-07-14
Connect a keyboard/mouse, either via Bluetooth or USB, and press any key. Alternatively, plugging in the usb cable will also turn the screen on. But the cable has to be connected to the charger or a computer.

---

### Post by Johan_Helsingius on 2016-07-16
Thanks, but it doesn't really help my situation where I would like to mount the tablet on the wall (and having to use the power button every time the screen has gone black is rather inconvenient).

---

### Post by krusty8 on 2016-07-16
I think you can configure it to never blank. And I remotely remember unblanking is somehow possible from a shell, eg ssh

---

### Post by Johan_Helsingius on 2016-07-18
> **krusty8 said:**
> I think you can configure it to never blank.

Not sure that is good for the longevity of the display.

---

### Post by krusty8 on 2016-07-18
> **Johan_Helsingius said:**
> Not sure that is good for the longevity of the display.

I really do not know. I think the commandline thing was something with powerd, or powerdcli or so. And I think it was also somehow possible to do it via a dbus command.

Maybe you can elaborate a bit more on what you want to achieve. Is an ssh command an option? Should it turn on because you clap? Why is the power botton off limits? Would people touch it at all?

---

### Post by Johan_Helsingius on 2016-07-19
> **krusty8 said:**
> Maybe you can elaborate a bit more on what you want to achieve. Is an ssh command an option? Should it turn on because you clap? Why is the power botton off limits? Would people touch it at all?

I want to mount the tablet in a semi-overhead panel. Touching it is easy (and that is how I want to use it, but reaching over to push the button every time you want to wake up the display is a hassle, and really restricts mounting options (can't use a bezel etc.).

---

### Post by krusty8 on 2016-07-19
> **Johan_Helsingius said:**
> I want to mount the tablet in a semi-overhead panel. Touching it is easy (and that is how I want to use it, but reaching over to push the button every time you want to wake up the display is a hassle, and really restricts mounting options (can't use a bezel etc.).

Ok. I guess that is a no to my question!?
> Is an ssh command an option?

I recall someone talking about double-tap-to-wake. The Jolla phone and some Android phones do that. That person was talking lengthily about how he initially had a version of Android and it allowed double-tap-to-wake, then he moved to Ubuntu Touch and even though Ubuntu has no understanding of this feature it continued to work. For that person it actually constituted a bug he tried to resolve (pocket-dialing from the phone), but maybe you can research that. It was either on the mailing list or in launchpad. Shouldn't be too hard to find.

---

