---
title: "Screensaver based on webcam motion detection."
date: 2016-05-07
forum: Ubuntu/Debian BASED
---

### Post by XOIIO on 2016-05-07
Hey all, so I turned a shoddy old netbook into a wall mounted weather station (or really, station for any other info, I'll probably try and get info from my servers on it too), and it works and looks great running xubuntu. [http://imgur.com/a/NbLIh](http://imgur.com/a/NbLIh) [https://youtu.be/sTfK8WCZoNs](https://youtu.be/sTfK8WCZoNs)

Now, it does look good with the screen on all the time, and it does only draw 17 watts, but I want to play with the functionality, and since there is a webcam mounted in the middle of it, I think that it would be pretty cool to have it turn on the display whenever motion was detected and after 30 seconds or so, turn the display back off. 

It's in a somewhat high traffic area but I think that it would be neat to try out, I'm just wondering if there are any packages out there that are capable of this without having to do bunch of custom stuff. (still pretty much a linux noob, used to be a bit more familiar with it, but that was quite some time ago, but I can make my way around the terminal to install things/update, etc)

I do have motion installed, I'm not sure if that is able to do something like this, I think it's mostly just for surveillance.

edit: Well, actually I found this shortly afterwards, trying it out now, seems it will be simpler than I thought though. [http://fuzzytolerance.info/blog/2012/10/26/2012-10-26-waking-your-monitor-by-motion-in-linux/](http://fuzzytolerance.info/blog/2012/10/26/2012-10-26-waking-your-monitor-by-motion-in-linux/)

Not exactly sure which characters are used on either side of the qdbus section but there's only a couple options. (can't copy paste them to find out sadly lol).

I'd also need to find out how to get motion to start with ubuntu, since adding "run motion" to the start applications doesn't do it.

---

### Post by XOIIO on 2016-05-07
Hmm, it seems like motion isn't following the config file, or possibly some other issues combined with that.

Firstly, I'm not sure if I need to use the grave accent, or the single quotation mark on either side. I also had the default noise level set, and the screen would never shut off, but I changed it to 150, and it did work, but would not wake with motion.

However, motion is still saving image files even when I have output_normal set to off, so it might not even be paying attention to the config file. the folder is there in place from a previous installation though so maybe that's why, it did seem a bit odd that it didn't delete that as well as the program files.

Pretty tired right now so going to call it a night for now.

---

