---
title: "BUG: Cannot Rename Registry Keys"
date: 2010-11-02
forum: Wine
---

### Post by Jamie White on 2010-11-02
As it says in the title, I cannot rename newly created wine registry keys through regedit.

I've tried all of the ridiculous solutions like knock on wood, walk around the table three times, throw salt over my shoulder and resize the windows to remove the horizontal scrollbar.
It seems like a bunch of people had this problem and no one new what to do so they ignored it.

I'm trying to edit the user.reg in gedit but I'm not sure about bits and pieces.
There seem to be unique  number combinations beside the keys, but what do I use on a key I created? Do i just make it up?
Also the sites say (for the appropriate keys) to "enable" things. But when I got into tweaking my actual Windows install ages ago and messed with the registry, enable/disable meant 0 or 1. Then there is a tutorial that says some accept Y or N. So I'm not sure how to enable/disable options.

This would be much more simple with regedit. As it is I'm forced to endure crashes and slow games, or only play games supported by PlayOnLinux.

I'm using the most up to date WINE as far as I know and I'm using Maverick.

Any suggestions?

---

### Post by cogadh on 2010-11-03
Only one suggestion for now: give us specifics, not generalities. Tell us exactly what you are trying to do with the registry, which keys are you trying to change/edit and for what purpose? We can't really help much if you don't tell us much more than "it don't work".

---

### Post by Jamie White on 2010-11-03
Hey.
Thank you for the reply. I was general though because nothing works. I can't rename any newly created key, in any directory. Regardless, I'm trying to set up the Direct3D directory under HKCU>Software>Wine, which annoyingly hasn't automatically been created.

I'm following this tutorial: 
[http://www.overclock.net/linux-unix/213952-how-advanced-wine-configuration-gaming.html](http://www.overclock.net/linux-unix/213952-how-advanced-wine-configuration-gaming.html)

I've looked everywhere.
And I recognise you becuase you were on one of the google results that led to these forums, that I also replied to. You were advocating text editing the registry. Which I then proceeded to do but I cant figure out what number combination I'm meant to put. Here, this is from the thread that you were in

> 3. Chances are you are missing the following key
[Software\\Wine\\X11 Driver] xxxxxxxxxxxx
"UseXVidMode"="N"

The xxxx should be replaced by the number you see against adjacent keys. Then it works a charm!

But what should XXXXXXXXXXXXXX be? The rest are unique, if I just copy and past it wont work will it?

Basically, Left For Dead 2 doesn't work on steam through PlayOnLinux. So after googling I found that copy and pasting the steam install into my normal .wine folder runs it fine. But I now can't enable multisampling and set my video memory size. I am under the assumption that regedit is the only way to do it.

---

### Post by Jamie White on 2010-11-03
Okay, so far as I can tell when editing the Wine Registry in user.reg via a text editor you do not need to enter a number combination. This is automatically done for you. Just create and populate a key, save and then by the looks of it, when the registry is next accessed, the number code is added automatically. 
After I posted I launched Left For Dead 2 with the text edited registry in place, believing it wouldn't work. I was very wrong. It works so much better it surpasses that of my windows install. It so much smoother and cleaner. I find that when games work on linux, they do so far better than windows.

This still leaves the problem of what format "enable/disable" should take.
0 and 1
Y and N
enabled and disabled.

So for example:

"UseGLSL"="enabled"

Would this work? And would it work for all settings that require such a binary input?

---

### Post by cogadh on 2010-11-03
Well, you figured it out before I could tell you, so that's great.

As far as the enabled/disabled thing, yes, you actually need to use the word "enabled", however, you shouldn't need to enable that particular key, it is enabled by default in Wine. In the past, it was optional, but not anymore (well, you can still disable it). See here for other helpful information about the registry in Wine:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by Jamie White on 2010-11-04
I did see that website but I'm sure I'm not alone if my dismay at the format. I just couldn't read it easily.
After following you're link and re-reading, I can see the last bits of info i needed, that I must've missed.

Thanks for your help, even if I beat you to it, I wouldn't have been able to if it wasn't for the other thread you were on :)


So, to conclude in case of google searches:

If you can't rename a key in RegEdit
go to /home/username/.wine and make a backup of user.reg called userBAK.reg or similar
then open the original in a text editor like Gedit
add your required keys in this format:

[Software\\Wine\\Direct3D]
"DirectDrawRenderer"="opengl"
"Multisampling"="enabled"
"VideoMemorySize"="1024"


Don't worry about the unique numbers after [Software\\Wine\\Direct3D] they are automatically assigned on next use of Wine.

And be sure to follow this link from codagh:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

