---
title: "Connecting an external usb keyboard?"
date: 2009-07-09
forum: Ubuntu Studio
---

### Post by jmate24 on 2009-07-09
hi, i have used ubuntu since 5.10 and am wondering about ubuntu studio and how it will work with my laptop.


i have a casio wk-200 piano keyboard that i would like to connect using free software (ubuntu studio preferably) instead of buying the $100.00US audio software for windows...

i have a lenovo y510 laptop that has midi capabilities, but with ubuntu 9.04 i am unable to use it with nted. but with windows i can use midi just fine.

my question is: can ubuntu studio recognize my midi on my laptop and if so, will it and the software be able to link to my keyboard. (my lsusb -v shows that it is connected)

jmate24:)

---

### Post by kayosiii on 2009-07-09
Everything should work if the keyboard is a class compliant device. If it says anything in the manual about connecting to Mac OS X then it almost certainly does it should work and run without a hitch. Every midi keyboard I have plugged in has worked this way.

What you typically need to do is to route the midi to the application you want to use the keyboard with. The application I use for this is called Patchage (The version included in the repos for the current Ubuntu release is a little old and requires jack to be running in order to work). Jack Control (qjackctl) will allow you to route midi ports without jack running.

Zynaddsubfx is a pretty good app to test with. Start this application then
start
a) Patchage -- locate midi port for your keyboard and drag from it to the midi in port in Zynaddsubfx. 
**or**
b) QJackCtl -- press the connect button, Select the Alsa tab (There are two types of midi if you are interested). Locate the Keyboard source on the left and the Zynaddsubfx tab on the right and press the connect button.

---

### Post by jmate24 on 2011-11-03
it connected but i cannot hear any sound from my computer when i hit the keyboard do i have to disable alsa? or do i just use timidity?
i am currently running lubuntu 11.10 now with ubuntustudio-desktop apps installed.

---

### Post by sgx on 2011-11-03
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

the 4th and 8th link at the wiki have screenshots and info to
get your keyboard and soundcard connected in qjackctl,
and then running with the zynaddsubfx softsynth. 

To access zynaddsubfx soundbanks, use the menu 
Instrument -->show instrument bank

When the panel opens, its empty, so click the little black triangle widget by the 'Refresh bank list' button, and the list of soundbanks appears.

Cheers

---

