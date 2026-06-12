---
title: "Audio interface and Jack?"
date: 2010-03-22
forum: Ubuntu Studio
---

### Post by oleink on 2010-03-22
Hey I don't have Ubuntu Studio but I figured this is a good place to ask.  How can you get an audio interface (usb device) working with Jack and also what are the best softwares for recording and editing (what has good effects and should I use different software for effects like the effects manager for Jack and the guitar effects program)

---

### Post by AutoStatic on 2010-03-25
> **oleink said:**
> How can you get an audio interface (usb device) working with JackWhich USB device are you referring too? Do you already own such a device or are you planning on getting one? It should be fairly simple with a class compliant USB1 device: plug it in, do an **aplay -l** in a terminal, copy the hardware name of the card, open QjackCtl, use 'hw:hardware-name' as Interface, save your settings and start JACK.

> **oleink said:**
> and also what are the best softwares for recording and editing (what has good effects and should I use different software for effects like the effects manager for Jack and the guitar effects program)Ubuntu/Linux uses mostly a modular approach so you can use practically all effects in all recording programs, as long as they support the plugin standards (LV2, LADSPA, DSSI). If not you can use something like JACK-Rack and route stuff through it. And what are the best programs, I like Qtractor for recording and Audacity for editing. Don't know if they are the best programs, I personally like them and they suit my needs.

---

### Post by mkloch on 2010-04-25
I've got [Lexicon Alpha]("http://soundsoflinux.blogspot.com/2010/04/lexicon-alpha-works-with-linux.html") and it works out of the box with Linux :guitar:. For recording Ardour is my favourite.

---

### Post by oleink on 2010-07-29
> **AutoStatic said:**
> Which USB device are you referring too? Do you already own such a device or are you planning on getting one? It should be fairly simple with a class compliant USB1 device: plug it in, do an **aplay -l** in a terminal, copy the hardware name of the card, open QjackCtl, use 'hw:hardware-name' as Interface, save your settings and start JACK.

Ubuntu/Linux uses mostly a modular approach so you can use practically all effects in all recording programs, as long as they support the plugin standards (LV2, LADSPA, DSSI). If not you can use something like JACK-Rack and route stuff through it. And what are the best programs, I like Qtractor for recording and Audacity for editing. Don't know if they are the best programs, I personally like them and they suit my needs.

Alright i know its been a few months.  My plan is to use the behringer uca222 because for the price it has excelent audio and very few extra settings (thats what the point of mixers are that get attached to it.)  My question would be could that usb sound card replace my onboard soundcard in jack because the onboard sound card still makes crackling noises at 44100 sample rate and 128 frames/period.  It is starting to slow music stuff down way to much if i lower those anymore (well technically if i raise the frames/period and lower the sample rate).

---

### Post by RaumTrug on 2010-07-29
I think that card should work, I've found positive reports...just hit google with "behringer uca222 linux" to make yourself a picture of it, seems like "plug & play" in terms of hardware recognization, the soundsystem needs to be config'ed to actually use it, of course.

and yep, you can use jack with any of the recognized soundcards in your system, you just tell the program that configures jack (for example qjackcontrol) to use the thingie, and it will be the main interface.

but don't give up too early with your onboard, have you already tried to disable desktop effects, and put your cpu(s) into performance mode to get rid of the xruns/crackles? might be rewarding... ;)

---

### Post by oleink on 2010-07-29
> **RaumTrug said:**
> I think that card should work, I've found positive reports...just hit google with "behringer uca222 linux" to make yourself a picture of it, seems like "plug & play" in terms of hardware recognization, the soundsystem needs to be config'ed to actually use it, of course.

and yep, you can use jack with any of the recognized soundcards in your system, you just tell the program that configures jack (for example qjackcontrol) to use the thingie, and it will be the main interface.

but don't give up too early with your onboard, have you already tried to disable desktop effects, and put your cpu(s) into performance mode to get rid of the xruns/crackles? might be rewarding... ;)

yeah.  I actually did most of that so my computer would be gaming capable

---

### Post by oleink on 2010-07-30
> **RaumTrug said:**
> I think that card should work, I've found positive reports...just hit google with "behringer uca222 linux" to make yourself a picture of it, seems like "plug & play" in terms of hardware recognization, the soundsystem needs to be config'ed to actually use it, of course.

and yep, you can use jack with any of the recognized soundcards in your system, you just tell the program that configures jack (for example qjackcontrol) to use the thingie, and it will be the main interface.

but don't give up too early with your onboard, have you already tried to disable desktop effects, and put your cpu(s) into performance mode to get rid of the xruns/crackles? might be rewarding... ;)

PS:  Either way i need an interface to record music anyway so its good to have the interface in either case

---

