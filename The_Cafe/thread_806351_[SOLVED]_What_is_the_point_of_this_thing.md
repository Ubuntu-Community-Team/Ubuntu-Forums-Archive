---
title: "[SOLVED] What is the point of this thing?"
date: 2008-05-24
forum: The Cafe
---

### Post by Jordanwb on 2008-05-24
I'm talking about that thing on the USB cable. I feel like breaking it open but I don't want to.

[Edit] Yay someone gave me a "Thanks".

[Edit #2] Someone thanked me for this post. :confused:

---

### Post by Dr Small on 2008-05-24
Maybe a power reducer or something.

---

### Post by Chilli Bob on 2008-05-24
It's a chunk of ferrite.  It reduces RF interference in the cable by absorbing it and releasing it as heat.  That's the short answer anyway.

EDIT: Check this..

[http://www.ce-mag.com/archive/02/11/may.html](http://www.ce-mag.com/archive/02/11/may.html)

---

### Post by Jordanwb on 2008-05-24
Hmm but RF could be picked up anywhere between that and the connector. Or maybe I'm misunderstanding it. How come they don't put that on other equipment like networking cables or computer monitor cables.

---

### Post by Chilli Bob on 2008-05-24
> **Jordanwb said:**
> Hmm but RF could be picked up anywhere between that and the connector. Or maybe I'm misunderstanding it. How come they don't put that on other equipment like networking cables or computer monitor cables.

I think that network and video cables have an earthed shielding sheath that negates the need.  This however would make them too stiff and heavy for convenient use on light wiring like a usb cable.

As for the first question, that's just how science works.  10 years ago I could have given a better answer, sorry.

---

### Post by Jordanwb on 2008-05-24
> **Chilli Bob said:**
> I think that network and video cables have an earthed shielding sheath that negates the need.  This however would make them too stiff and heavy for convenient use on light wiring like a usb cable.

Not all networking cable has shielding. The general public use unshielded network cables because they're cheap (the cables). Hospitals use shielded though.

> **Chilli Bob said:**
> As for the first question, that's just how science works.

That's not the first time I've heard that.

---

### Post by kef_kf on 2008-05-24
my laptop power cable has it. also a pair of them came with my dvd player, they were not attached to anything or mentioned in the manual, so i took them back to the electronics shop to ask the guy who sold me the player. it turns out he didnt know what they were either. its been 3 years and my player hasnt caused any problems so far. i guess we dont really need them.

---

### Post by Jordanwb on 2008-05-24
It's on my laptop's power cable too. However I have several usb/networking cables that have no shielding and I don't have any problems. So even though they're useful I don't see a relavent use.

---

### Post by Chilli Bob on 2008-05-24
I think they are a nice feature but not absolutely neccessary.  The expensive cables that came with my iRiver and Canon camera have them, the cheap ones that came with supermarket usb hub and card reader don't have them.

---

### Post by Steve413z on 2008-05-24
you usually don't need those things.  Those help prevent RF interference (but are rarely installed correctly)

I'm a ham radio operator, and I have to put those on alot of things in my house, for example, I put one on my desktops keyboard, because if you transmit with enough power, sometimes a bunch of gibberish will get typed on the screen unintentionally.

the correct way to run a cable through one of those, requires the wire to be looped around a few times

---

### Post by melrom on 2008-05-25
Our Circuit Theory teacher told us that was an inductor... lol. Perhaps wrong?

---

### Post by tamoneya on 2008-05-25
> **Chilli Bob said:**
> I think that network and video cables have an earthed shielding sheath that negates the need.  This however would make them too stiff and heavy for convenient use on light wiring like a usb cable.

As for the first question, that's just how science works.  10 years ago I could have given a better answer, sorry.

A lot of other cables (cat5 etc) use whats called twisted pair.  They send a signal and the opposite of the signal on two wires.  These wires are then twisted together and they cancel each other out and this helps to run cable longer distances.  Otherwise the signals on different wires would interfere with each other.  It doesnt help much to deal with outside interference but it helps to prevent interference if you have 20 cat5 cables all in a row since otherwise you would have EMI all over the place.

It does in some ways act as an inductor.  Notice on how some of them it loops back around.  Since an inductor is really just a coiled wire you will get some inductance in the line which will help to filter out any transients in the waveform.

---

### Post by Steve413z on 2008-05-25
> **melrom said:**
> Our Circuit Theory teacher told us that was an inductor... lol. Perhaps wrong?

toroids are often used in inductors, and they do add inductance to the line

---

### Post by Jordanwb on 2008-05-25
> **tamoneya said:**
> A lot of other cables (cat5 etc) use whats called twisted pair.  They send a signal and the opposite of the signal on two wires.  These wires are then twisted together and they cancel each other out and this helps to run cable longer distances.  Otherwise the signals on different wires would interfere with each other.  It doesnt help much to deal with outside interference but it helps to prevent interference if you have 20 cat5 cables all in a row since otherwise you would have EMI all over the place.

Yes that's true. (I'm in Cisco's CCNA class in High School) But in the average house the only thing (that I know of) that would cause EMI are Wireless Routers and other such wireless devices.

---

### Post by Steve413z on 2008-05-25
> **tamoneya said:**
> A lot of other cables (cat5 etc) use whats called twisted pair.  They send a signal and the opposite of the signal on two wires.  These wires are then twisted together and they cancel each other out and this helps to run cable longer distances.  Otherwise the signals on different wires would interfere with each other.  It doesnt help much to deal with outside interference but it helps to prevent interference if you have 20 cat5 cables all in a row since otherwise you would have EMI all over the place.

It does in some ways act as an inductor.  Notice on how some of them it loops back around.  Since an inductor is really just a coiled wire you will get some inductance in the line which will help to filter out any transients in the waveform.


A good example of why networking cable and phone line cables are twisted, the power companies are trying to add internet access available through the power lines, the problem is most power lines aren't twisted like phone lines or network cables, and they arn't shielded like cable, so it causes a huge amount of interference.
[http://www.arrl.org/news/stories/2004/06/18/8/BPL-and-HF-web.mpg](http://www.arrl.org/news/stories/2004/06/18/8/BPL-and-HF-web.mpg)

---

### Post by d.kusummmanth@gmail.com on 2008-05-25
> **Jordanwb said:**
> I'm talking about that thing on the USB cable. I feel like breaking it open but I don't want to.

[Edit] Yay someone gave me a "Thanks".

[Edit #2] Someone thanked me for this post. :confused:

it's a step-down transformer

---

### Post by Jordanwb on 2008-05-25
> **d.kusummmanth@gmail.com said:**
> it's a step-down transformer

Did you even read the rest of the thread?

---

