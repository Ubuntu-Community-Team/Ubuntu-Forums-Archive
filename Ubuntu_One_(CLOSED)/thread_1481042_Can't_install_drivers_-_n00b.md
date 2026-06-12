---
title: "Can't install drivers - n00b"
date: 2010-05-12
forum: Ubuntu One (CLOSED)
---

### Post by BunnyDee on 2010-05-12
Hello.

I think I should warn you about this: I am a total n00b, just came here from... well, win7, at the end.

I've installed Ubuntu 10.04 LTS (Lucid Lynx), updating from 9.04 (Jaunty Jackalope) pretty much straight away.

What seems to be the problem now, after I've installed all the programs that interest me and, well, doing an 'aptitude update' and then an 'aptitude upgrade' that I was told to do, is that I don't seem to have my printer drivers and my sound card drivers installed. For one, it won't print when I tell it to from wherever I write something that I want to print, and the sound seems to work whenever it wants to, and will only work if I reboot whenever it decides not to.

My printer is a Canon PIXMA iP1800 - which seems to be the only Canon one not in the list when I was asked what drivers to install.

My sound card is a Sound Blaster Audigy.

The thing is, if I download the drivers from the relevant makers' websites, I have absolutely no idea what to do with them if I do. They just sit there, smile at me, and I smile back at them - and then delete them, as they don't seem to do anything of their own volition. You know, like in Windows, which my mom still runs.

And, yes, I repeat, I'm a total newbie.

sudo helpme imst00pid

(does this do anything?)

---

### Post by BunnyDee on 2010-05-12
Oh, sorry, posted this in the wrong topic - it should be in "Absolute Beginner Talk"...

How do I move a topic after I post it, BTW? Is there a way to do this here if one is not an admin?

---

### Post by bertmanphx on 2010-05-12
BunnyDee,
Until the Admin moves this topic, perhaps this will help:

Sound - Make sure you open up the full "rack" of sliders, not just the single slider.  This will show all of the options, and allow you to choose the item you want to control when you adjust the sound from the speaker icon on the panel.

Print Drivers -   As you were updating from 9.04, did you apply all of the available updates from within 9.04 first?  Doing so helps make sure upgrades go smoothly.

You could delete the printer, logout, then log back in.  Or, open a web browser, and type in "localhost:631"  This will bring you to the Web Gui for CUPS  When you go to perform a function there that required admin rights, the user name will be "root" and the password will be yours.  This is a slight deviation from the credentials you need to supply when working from within the printer app in Ubuntu, and I'm not quite sure why. 
From this screen, you can see all of the same information that can be displayed from the printer gui, but it's setup a little different.  

bertmanphx

---

### Post by BunnyDee on 2010-05-13
Thank you very much, bertmanphx. The thing is, my problem is not really solved at all yet.

Sound - Where are these 'sliders' you talk of? :P I'm pretty much looking for Audigy drivers, and how to install them if found... Wherever there seems to be a 'volume' slider, I always move it up, but the thing is that sometimes the sound works, en masse, and sometimes it doesn't. If there's a hidden thing somewhere, that controls the sound in total, well, I have no idea where to find it. :(

Print drivers - Yes, I did apply everything there was to apply, but I pretty much had the same issue back then, but I only ran it for a very short while, and therefore didn't have all the drivers etc installed there either.

There's no printer to delete, the thing is. Plus, I don't know how to access the drivers, wherever it has them installed. I'll look at some point, gotta rush off to work now (I just finished my morning coffee :P)

---

### Post by koanhead on 2010-05-13
The fact that your sound is working at all indicates that a driver is loaded and working with the card. It may or may not be the correct driver. You can look here to see which driver (more properly referred-to as a "module" in linux) is the correct one for your specific Audigy model.
If you are in doubt as to exactly which card you have, use the "lspci" command.
To check which modules are in use by your system, use the "lsmod" command. In your specific case, the output of "lsmod |grep sound" may be useful.

---

