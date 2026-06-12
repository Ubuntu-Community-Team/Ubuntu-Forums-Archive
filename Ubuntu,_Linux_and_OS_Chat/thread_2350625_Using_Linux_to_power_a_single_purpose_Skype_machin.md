---
title: "Using Linux to power a single purpose Skype machine"
date: 2017-01-26
forum: Ubuntu, Linux and OS Chat
---

### Post by wolfjosh on 2017-01-26
Hello, not sure if I'm posting to the right place and happy to move it if I have.

I have an idea for a raspberry pi device (hopefully pi zero) that's only function is to operate the Skype website that replaces outdated Linux Skype software.

Ideally It would resemble a picture frame and have either a touch screen or possibly physical buttons. 

It is designed to be used by seniors and others who want to use the technology but for some reason or another can't use conventional computers.

The question I have for this forum is, is it possible to have Linux open to a single website by default? 

Happy to answer any questions,

Cheers,

Josh.

---

### Post by ajgreeny on 2017-01-26
> The question I have for this forum is, is it possible to have Linux open to a single website by default?
The answer is a resounding "Yes" you can open a website directly on starting the OS.

You will need to install a web-browser of your choice, of course, but you can probably manage with a smaller, low resource needing browser such as midori rather than chromium or firefox, both of which use more of your machine resources.

In the OS on your Raspberry pi you will need to add midori to the autostart list using command midori and have the skype webapp site as the home page for midori.

I can't help with the hardware, but the software needed should be that easy, always assuming running it on a Raspberry pi works as I imagine it should.

---

### Post by Habitual on 2017-01-26
> **wolfjosh said:**
> only function is to operate the Skype website that replaces outdated Linux Skype software.
You sound confused. "outdated Skype software" vs "single purpose skype machine"?
That or you aren't describing your goal very clearly.

Kiosk a single web  app and lock it down to use [Web Login]("https://login.skype.com/login?client_id=578134&redirect_uri=https%3A%2F%2Fweb.skype.com%2F") for Skype in a browser.
Only 'outdated' in real-time!

or [Repurposing Old Smartphones for Home Automation | Linux.com]("https://www.linux.com/news/repurposing-old-smartphones-home-automation") for some ideas?

---

### Post by speedwell68 on 2017-01-26
TBH I doubt a Pi Zero would do it.  You mention outdated software, have you tried the new Skype for Linux?

---

### Post by mastablasta on 2017-01-26
they sell Lenovo's for about 45 EUR here that are not bound by contract to any operator. they can run skype for android. there might een be a chepaer simpler option. if you intend to sell the device i doubt you will get far. then again a new sucker is born every minute or how that saying goes. 

otherwise check the new Linux and also as others mentioned what you want is called "Kiosk mode".

---

### Post by wolfjosh on 2017-01-26
I was referring to an article I skimmed recently saying that people are moving to web based Skype rather than the installed program.

Thanks for the links!

---

### Post by wolfjosh on 2017-01-26
My aim is to make a completely fool proof device for mainly the elderly, I know many people who for one reason or another want the ability of skype but are unable or unwilling to deal with even navigating a tablet OS

---

### Post by wolfjosh on 2017-01-26
[QUOTE=ajgreeny;13599397]The answer is a resounding "Yes" you can open a website directly on starting the OS.

Thank you for this, it makes it simple to see how I could make it! also thanks to people who mentioned kiosk I'll look into it!

---

