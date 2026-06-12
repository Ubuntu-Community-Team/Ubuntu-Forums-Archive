---
title: "No Recording Sound in Audacity"
date: 2009-03-21
forum: Ubuntu Studio
---

### Post by mystik10801 on 2009-03-21
Hello,

I've installed Audacity, and can import wav files into the interface just fine, but I can't record.. the record button works, but there's no feed... It was set by default to use Jack, and I no nada about Jack. I got Hydrogen to work on ALSA drivers, and Audacity has that option, but there's still no sound... If someone could explain Jack to me in laymens terms, or help me figure out what drivers to use... I think they're 8237, but not sure about the hwd0,1 bit.

Thanks

---

### Post by Reeman on 2009-03-22
> **mystik10801 said:**
> Hello,

I've installed Audacity, and can import wav files into the interface just fine, but I can't record.. the record button works, but there's no feed... It was set by default to use Jack, and I no nada about Jack. I got Hydrogen to work on ALSA drivers, and Audacity has that option, but there's still no sound... If someone could explain Jack to me in laymens terms, or help me figure out what drivers to use... I think they're 8237, but not sure about the hwd0,1 bit.

Thanks

You need to launch jackd, if you want to run audacity with jack.  

There is a gui program called Qjackctl that most use for this purpose. With it you can setup the connections between jack and Audacity with the gui. If pulse is not setup to use the jackd then this will block the jackd and it will not even launch and will give you errors....a very common and annoying thing about the Ubuntu desktop sound server.](*,)](*,):roll:  

There is also the distinct possibility that the pulse audio server is blocking access to functions in /dev when you try to set a record input for Audacity.

Which source are you trying to record from? From the pcm of your soundcard should be available in audacity edit/preferences. If you are trying to record from a source that has been muted by the Gnome/pulse mixer crap then this could explain things. 

Try the command alsamixer -c 0 and see if you have your input source muted.

Sometimes you have to completely shut down the pulse server and not use any of the pulse audio crap to get Audacity to work properly!

---

### Post by rendon on 2009-03-23
I'm sorry I can't get into my system right now to check exactly where, but I know there is an option somewhere in the menu up top that allows you to choose your input/output devices, you can try fiddling with the input devices and/or drives a little to see if anything works.

That's what I did last time anyway...

---

