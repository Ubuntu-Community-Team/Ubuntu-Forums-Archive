---
title: "Guitar to PC"
date: 2010-08-11
forum: Ubuntu Studio
---

### Post by xwindowsfan on 2010-08-11
i have a guitar hooked up with an alesis guitarlink 1/4" to usb cable.i use lucid ubuntu studio upgrade.the cable is recognized as a device it shows level as imput.everything including jack control is configured correctly.my sound card is a bgears b-enspirer.even rakarrack responds by level meters to the guitar but i simply cannot get the output to go to my speakers.s/pdif out to onk607 .the cable is not stated as being linux compatible.i am aware of the other methods such as preamp audio interfaces.thank you.

---

### Post by Jormeliini on 2010-08-11
Only really basic things come to my mind. Don't be offended if you're advanced with Linux audio. Can you get output to speakers from an application or from any other input? Can you see Guitarlink in Jack Control (qjackctl) application -> Connections -> Audio tab? If so, have you tried connecting it to system playback?

Hope you get it working. Many devices are not stated as being Linux compatible but they still work.

---

### Post by xwindowsfan on 2010-08-11
yes,yes,and yes.which is why it compels me.everything is perfect yet no output sound.for example the usb device is shown under hardware in pulse sound preferences,but it fails the "speaker test".thanks

---

### Post by xwindowsfan on 2010-08-12
upon closer examination of your post and of jack control the usb device is not specificly addressed.there is only system/capture1 and system/playback 1 and 2.my estimation is that "capture1" is it.the device is listed under setup/imput device as c-media usb audio device.thanks

---

### Post by xwindowsfan on 2010-08-12
i have sucessfully gotten sound out of the same configuration on fedora 13.thanks

---

### Post by Jormeliini on 2010-08-13
Do you have the same number of inputs on Fedora? I was just thinking that your sound card could have 2 inputs. Bgears web site does not specify that.

Just a random idea. Check ALSA versions. If they are different you could try getting a newer version to Ubuntu. Maybe it's a driver issue.

---

### Post by maghoxfr on 2010-08-15
So you have an usb device as an input and a sound card as output. Did you selected them in JACK's setup? I mean if you chose the Guitar link as IN and the sound card as out. Maybe jack is only set up for the guitar link and therefore you have no physical output for the sound. Just an idea.

---

