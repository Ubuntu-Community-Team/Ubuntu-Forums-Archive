---
title: "Does Linux have a registry?"
date: 2009-03-25
forum: The Cafe
---

### Post by oo-boon-too on 2009-03-25
I feel I may get slapped in the face for this one but I'll give it a go anyway.
Do Linux-based systems use a registry file, similar to how Windows does?
There is no real reason to why I ask this other than just to know, so if there is a "Stupid Questions" section then direct me to that>.>
I just have no idea how linux-based systems work, and would like anyone to give me an idea if you can. For example, what does 'ext' in 'ext3 filesystem' mean, etc.
Thanks in advance!

---

### Post by coutts99 on 2009-03-25
Google is your friend

---

### Post by billgoldberg on 2009-03-25
> **oo-boon-too said:**
> I feel I may get slapped in the face for this one but I'll give it a go anyway.
Do Linux-based systems use a registry file, similar to how Windows does?
There is no real reason to why I ask this other than just to know, so if there is a "Stupid Questions" section then direct me to that>.>
I just have no idea how linux-based systems work, and would like anyone to give me an idea if you can. For example, what does 'ext' in 'ext3 filesystem' mean, etc.
Thanks in advance!

No.

[EXT3]("http://en.wikipedia.org/wiki/Ext3")

---

### Post by JackieChan on 2009-03-25
> **coutts99 said:**
> Google is your friend
This.

---

### Post by Delever on 2009-03-25
Gnome's configuration "gconf-editor" is something that looks like regedit. It is used to configure gnome applications.

Otherwise anything else uses text configuration files, editable by hand. Look in /etc.

Question to other posters: why bother posting "rtfm" answer? That won't save much space in database...

---

### Post by oo-boon-too on 2009-03-25
Lol, what's even the point in a forum then, if there is google?
If you aren't going to contribute, then don't.
But thank you billgoldberg for the info;D

---

### Post by Sealbhach on 2009-03-25
> **Delever said:**
> 
Question to other posters: why bother posting "rtfm" answer? That won't save much space in database...

Correct. I though these were perfectly reasonable questions but maybe would have got a better response in the Absolute Beginners forum.


.

---

### Post by coutts99 on 2009-03-25
> **oo-boon-too said:**
> Lol, what's even the point in a forum then, if there is google?
If you aren't going to contribute, then don't.
But thank you billgoldberg for the info;D

To answer questions google can't?

Whats the point in google if you aren't going to use it?

---

### Post by kpatz on 2009-03-25
Ok, I'll provide a useful answer then...

Linux doesn't have a centralized registry like Windows does.  For most programs, configuration settings are in text files, which is nice because you can edit them and tweak them more easily than poking around in regedit (though many programs do have GUI interfaces for setup).  This approach is simple and robust: mess up a config file in Linux, and it only breaks the app that uses that config file.  Mess up the registry in Windows, and you'll be pulling out the install CD.

---

### Post by beercz on 2009-03-25
> **oo-boon-too said:**
> I feel I may get slapped in the face for this one but I'll give it a go anyway.
Do Linux-based systems use a registry file, similar to how Windows does?
There is no real reason to why I ask this other than just to know, so if there is a "Stupid Questions" section then direct me to that>.>
I just have no idea how linux-based systems work, and would like anyone to give me an idea if you can. For example, what does 'ext' in 'ext3 filesystem' mean, etc.
Thanks in advance!
No such thing as a stupid question, just stupid answers and I think you may have had one or two in this thread.

---

### Post by Vadi on 2009-03-25
The "registry" which "ooo, speead tweaks, aaah, I broke it, noo, it needs cleaning!" does not exist. But a centralized place for admins to set privileges on and apps not to worry about using yet-another-config-file-format does exist, gconf.

---

### Post by Liviu-Theodor on 2009-03-25
> **beercz said:**
> No such thing as a stupid question, just stupid answers and I think you may have had one or two in this thread.

In fact there is one stupid question, the one not asked.
And no, Linux does not use anything like the registry found in the Windows OS. In fact, in Windows, the registry is one of the "weak spots".

---

### Post by chucky chuckaluck on 2009-03-25
comparing gconf-editor to the registry couldn't be more appropriate in my view. i don't understand why it has to be such a mystery mess.

---

### Post by eldragon on 2009-03-25
the closest thing to the registry, is the /etc folder which holds all the user modifiable settings to the system.

for user specific settings, you should search all the hidden folders in the user's home (all files/folders starting with a dot)

gnome itself holds many of its settings in a xml formatted structure which can be accessed with gconf-editor (this one lies within your home too)

---

### Post by kevdog on 2009-03-25
Isn't gconf only applicable if you use Gnome?  If using another window manager that doesn't rely on gnome packages, then wouldn't gconf be nonapplicable?

---

### Post by Delever on 2009-03-25
> **kevdog said:**
> Isn't gconf only applicable if you use Gnome?  If using another window manager that doesn't rely on gnome packages, then wouldn't gconf be nonapplicable?

gconf is for applications. You can run gnome applications under KDE, and they will use gconf.

---

### Post by dspari1 on 2009-03-25
All of your configurations for all of your software is located and hidden in your home directory. Example: /home/.Mozilla

---

### Post by Polygon on 2009-03-25
> **chucky chuckaluck said:**
> comparing gconf-editor to the registry couldn't be more appropriate in my view. i don't understand why it has to be such a mystery mess.

in gconf's defence, its a bit more human readable then the windows registry

for example, changing something in gconf involves going to (for example), apps > nautilus > changing whatever key, and these are all named appropriately

in windows, changing the registry first involves choosing between HKEY_SOFTWARE, HKEY_LOCAL_MACHINE_, etc etc (what is the difference?), then navigating through a non-standard folder hierarchy, then figuring out which key you need to change, cause some are named in English, and others are named gibberish like {123gwr-EFAJ3I0-e3r321343}

i dunno, it seems gconf is the way to change all the nitpicky things that gnome feels would clutter up the options menu of all of its programs. Either way, its still MUCH easier to navigate and use then the windows registry.

---

### Post by Vadi on 2009-03-25
Why did you have to fall for the troll?

---

### Post by Mr. Picklesworth on 2009-03-25
> **Polygon said:**
> in gconf's defence, its a bit more human readable then the windows registry

for example, changing something in gconf involves going to (for example), apps > nautilus > changing whatever key, and these are all named appropriately

in windows, changing the registry first involves choosing between HKEY_SOFTWARE, HKEY_LOCAL_MACHINE_, etc etc (what is the difference?), then navigating through a non-standard folder hierarchy, then figuring out which key you need to change, cause some are named in English, and others are named gibberish like {123gwr-EFAJ3I0-e3r321343}

i dunno, it seems gconf is the way to change all the nitpicky things that gnome feels would clutter up the options menu of all of its programs. Either way, its still MUCH easier to navigate and use then the windows registry.

Thank you, sir! Further, gconf stores its settings in plain text XML files at ~/.gconf. I bet if you just gave the knee-jerk "eeew registry!" people that directory and said "these are configuration files for your programs," they wouldn't notice the difference (and would probably like it).

As for "why?", it's simple: gconf lets software monitor the status of keys, reacting as soon as they change without each program individually parsing big text files. It lets administrators set default and mandatory keys, which is really cool, and it allows those keys to be set progromatically without the risk of breaking the config files since everything relies upon the same engine for parsing and generating them. (Contrast that to how often tools like nvidia-settings break xorg.conf and how short-lived Ubuntu's displays and graphics configuration tool was).

---

### Post by Seaco on 2009-03-25
and thats the reason my post are 0, before asking try to discover yourself, its more fun (to me at least) and you learn more...
but ok people dont like to google the problem and thats the reason we have so many posts with the same question
this not a critic just a personal opinion

---

### Post by scottuss on 2009-03-25
To be fair, some people are a bit rude sometimes BUT in this case:

[http://www.google.co.uk/search?hl=en&q=does+linux+have+a+registry&btnG=Google+Search&meta=]("http://www.google.co.uk/search?hl=en&q=does+linux+have+a+registry&btnG=Google+Search&meta=")

First hit summary (don't even need to go to any site) 

> Linux does not have any system registry

---

### Post by daithy on 2012-10-27
> **oo-boon-too said:**
> Lol, what's even the point in a forum then, if there is google?
If you aren't going to contribute, then don't.
But thank you billgoldberg for the info;D

Absolutely agree, I am new to linux as well, my 1st day using Ubuntu 12.04 , have been using back track 5  for the past few weeks as well. and it is a lot to cram in the head! I have been using windows since I was a kid, that's I how I was brought up, Linux always was Tabu, now I am curious about linux so I am trying it out and believe me it can be hard if you are used to windows and seems confusing and the dicrectory stucture is so differenrent so many folders o_O , so ya everytime I need to do something I gotta use google, sure that's fine I do enjoy the process of learning and dicovering all the samem, but what tips me off and I see it very often if not only in linux forums, snobby members & grumpy Mods always reluctant to help referring the asker to google and whatnot. Well I went to goole and it led me here it was the very 1st post on top, thanks to this member because he asked it.
What's wrong with everyone nowadays :mad:

---

### Post by lisati on 2012-10-28
Whoa there! Old thread that has been asleep for years!

---

