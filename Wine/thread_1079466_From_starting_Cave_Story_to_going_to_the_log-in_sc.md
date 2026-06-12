---
title: "From starting Cave Story to going to the log-in screen."
date: 2009-02-24
forum: Wine
---

### Post by Kobayashi-kun on 2009-02-24
I have Kubuntu Intrepid installed on my laptop. Ive installed WINE and when I start up Cave Story, it goes onto a black screen then the log-in screen appears. What do I do to stop this from happening so I can play Cave Story?

---

### Post by Hellstudios on 2009-02-24
i asked the same exact question, twice. no one has answered. i am running Ubuntu. no one seems to be answering these questions. i wonder why. D:<

---

### Post by Kobayashi-kun on 2009-02-24
Yes, this always seems be a problem here. A load of people are online here, yet no-one answers.

---

### Post by cogadh on 2009-02-24
Actually, at least in this particular circumstance, the reason probably is no one really knows the answer. Cave Story is one of those games that ["just works" in Wine]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=3304"), so what you are encountering is not likely to be a commonly known issue with a commonly known solution.

If I am understanding the issue correctly, when you run the game, it appears to be logging you out of Ubuntu, correct? Most likely that is not what is really happening, but rather it is restarting the X server. Some additional information may help with diagnosing this, i.e. what Wine version are you using, how do you have Wine configured, what method are you using to launch the game, etc. Normally, the terminal output from Wine would help with figuring this out, but if it is logging you out/restarting X, then you are probably losing that output. You could try configuring Wine to run the game in a virtual desktop window, which may prevent the logout/X restart and allow you to gather more useful info.

---

### Post by Kobayashi-kun on 2009-02-24
I think im using the latest stable version. How do I get it to open in a window? My configuration setting are pretty much the same as when you first install it.

---

### Post by cogadh on 2009-02-24
If you installed it from the normal Ubuntu repositories, then you have the current stable version. You can confirm that by opening a terminal and running "wine --version". The virtual desktop settings are found in winecfg on the Graphics tab (see pic). Check the "Emulate a virtual desktop" option and make sure it is set to a minimum of 800X600, otherwise you may have difficulties making other configuration changes later.

[IMG]http://www.tipotheday.com/wp-content/uploads/2007/09/winecfg-video.png[/IMG]

---

### Post by wolfyking2 on 2009-02-26
You people do know that the awesomest game ever (aka Cave Story :popcorn:) has a linux client =.=

---

### Post by cogadh on 2009-02-26
Nope, didn't know that, but that is a much better explanation for why no one has answered these questions in the past. Got a link to a source download or an Ubuntu package for it?

---

### Post by FrozenFox on 2009-02-27
The source wasn't released, as pixel doesn't want to turn that over. He gave it to a third party whom he trusted to fix it up for linux and released the binary, it seems.

A quick google search can find the .deb for it, or you can grab the rpm and convert it to deb with alien (as i believe the deb in question was) or just unpack it or whatnot here:

[http://www.rpgameplace.de/rpms/2008.1/i586/doukutsu-1.01-1mdv2008.1.i586.rpm](http://www.rpgameplace.de/rpms/2008.1/i586/doukutsu-1.01-1mdv2008.1.i586.rpm)

---

