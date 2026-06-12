---
title: "I'm finally starting my final year engineering project. need advice please!"
date: 2008-08-16
forum: The Cafe
---

### Post by knadoor on 2008-08-16
Hi!!

just to set the tone im in 3rd year computer engineering (experience with C/C++, 68HC12 micro-controller assembly &  with C programming, embedded hardware).

My partner for the project since we're working in groups of our choice, well she's in 3rd year bio-medical engineering. We're both in the department of Electrical & Computer Engineering.

We've decided to do our 3-semester final year engineering project on a portable embedded device to assist blind people to walk.

Basically in essence it's a device which shall be as portable as possible (size of a mobile phone, light, rechargeable battery powered), it's a device which the user will wear as in on his/her belt (given to him via the device) as a strap-on around his waist. The sensors will be around the strap on the outside to detect motion and objects.

Basically the target user is someone who is blind and/or visually impaired. Our idea is that a person should not have to rely on a Cane or a guide dog.

The general idea is with the device on, when the user is walking closer to an object the "beeping" will get faster and faster, signally object is closing in. Several objects can be detected at the same time but each beep will have different tones so they sound difference and on the same principle. Advanced features like audio enabled: turn left, slow down, inclined path ahead etc... we're thinking of including if possible.

-------------
Now that the general idea has been set these questions have popped in my mind and my partners:

1) Which micro-controller would possibly be the best one to use? It needs to be as small as possible but also cater for the features and extra advanced features mentioned above. I've had a look aty the AVR 8-bit RISC Micro-controller from Atmel's AVR micro range.

2) Power source. My partner suggested we could have dual power sources, that is, with solar panels. Are there any solar panels that can be bought online or locally (im in australia) that is small enough? Also does this idea even sound sensible?

3) We need to have temporary memory storage...I'm guessing we can use a programming ram chip of some sort? Since we want the user to be able to "customize" the device to an extent, and this data will need to be stored somehow.

4) Her "work-mate" (thanks a lot genius for the silly idea :P) suggested to her we could use as a power source those batteries that are found in the light-up shoes when you walk on the bottom. He said to her that a wire can be connected from the shoe to the chip, so it recharges by itself. I think this is a stupid idea and impractical. However curious, is this viable? Also noting this is useless when the person is in the home. Who wears shoes to walk outside in-doors and on carpet anyway??

5) In terms of sensors and sensing objects, well we are not going to use GPS or whatever - which is what similar products use. Instead, we're planning on using either ultra-sound, infrared or sonar. We're leaning more towards the ultrasound since our local electronics shop has a small ultrasound emitter that we could use (no data-sheet with it as well!! :mad:). However we don't know of any sonar/infrared emitters-sensors that are small enough around??

We're funding this whole project our selves since it's our own thought-up one.

Well that's just about it from my end, any or all advice/suggestions, positive criticism appreciated!!

PS: Sorry it's kind of long, but it is I believe an interesting read and I'll be forever thankful for your advice.  :)

---

### Post by knadoor on 2008-08-16
also just to add upon it we are students afterall and on a bit of a limuted budget....$500 or so...

the micro-controller for me at least is a big issue.

---

### Post by knadoor on 2008-08-17
bump! please help. thnx.

---

### Post by grossaffe on 2008-08-18
> **knadoor said:**
> bump! please help. thnx.

I suggest you look for help in a more hardware based forum for stuff like this.

---

### Post by regomodo on 2008-08-18
#

---

### Post by regomodo on 2008-08-18
#

---

### Post by mips on 2008-08-18
> **knadoor said:**
> 
-------------
Now that the general idea has been set these questions have popped in my mind and my partners:

1) Which micro-controller would possibly be the best one to use? It needs to be as small as possible but also cater for the features and extra advanced features mentioned above. I've had a look aty the AVR 8-bit RISC Micro-controller from Atmel's AVR micro range.

2) Power source. My partner suggested we could have dual power sources, that is, with solar panels. Are there any solar panels that can be bought online or locally (im in australia) that is small enough? Also does this idea even sound sensible?

3) We need to have temporary memory storage...I'm guessing we can use a programming ram chip of some sort? Since we want the user to be able to "customize" the device to an extent, and this data will need to be stored somehow.

4) Her "work-mate" (thanks a lot genius for the silly idea :P) suggested to her we could use as a power source those batteries that are found in the light-up shoes when you walk on the bottom. He said to her that a wire can be connected from the shoe to the chip, so it recharges by itself. I think this is a stupid idea and impractical. However curious, is this viable? Also noting this is useless when the person is in the home. Who wears shoes to walk outside in-doors and on carpet anyway??

5) In terms of sensors and sensing objects, well we are not going to use GPS or whatever - which is what similar products use. Instead, we're planning on using either ultra-sound, infrared or sonar. We're leaning more towards the ultrasound since our local electronics shop has a small ultrasound emitter that we could use (no data-sheet with it as well!! :mad:). However we don't know of any sonar/infrared emitters-sensors that are small enough around??

1. Try and use what you know but if you can code in assembler you should be fine on most. Me, because of what I know whould take a PIC.

2. Lithium-Ion batteries. I recall the Nokia 2110 having a battery with solar panels on the outside to recharge in the sun.

3. Maybe Flash memory or the combination of flash/ram. Some micro controllers might already have this on the uC already.

4. Skip unless you want to trip the blind person.

5. Honestly dont know.

---

### Post by regomodo on 2008-08-18
#

---

### Post by Keen101 on 2008-11-08
This is what you probably want.

[http://www.arduino.cc/en/Main/ArduinoBoardLilyPad](http://www.arduino.cc/en/Main/ArduinoBoardLilyPad)

[http://www.sparkfun.com/commerce/product_info.php?products_id=8465](http://www.sparkfun.com/commerce/product_info.php?products_id=8465)

there are tons of sensors available. Not ultrasonic to my knowledge, but accelerometers, and others that you could probably adapt. Good luck.

---

