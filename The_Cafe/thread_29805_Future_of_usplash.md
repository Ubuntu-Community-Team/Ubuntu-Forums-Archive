---
title: "Future of usplash"
date: 2005-04-25
forum: The Cafe
---

### Post by TravisNewman on 2005-04-25
According to jriddel's blog ([http://www.kdedevelopers.org/node/view/992](http://www.kdedevelopers.org/node/view/992) ), the talks at the Ubuntu conference seem to say that usplash has been dumbed down to just displaying a jpeg over fb0. 
[indent][i]USplash seems to have been stopped in favour of a simpler system just doing cat foo.jpg > /dev/fb0
  [/i][/indent] 
Your thoughts?

---

### Post by totalshredder on 2005-04-25
[QUOTE=panickedthumb]According to jriddel's blog ([http://www.kdedevelopers.org/node/view/992](http://www.kdedevelopers.org/node/view/992) ), the talks at the Ubuntu conference seem to say that usplash has been dumbed down to just displaying a jpeg over fb0. 
[indent][i]USplash seems to have been stopped in favour of a simpler system just doing cat foo.jpg > /dev/fb0
  [/i][/indent] 
Your thoughts?[/QUOTE]

Well, I kind of hate them for that; but I'm sure it's a lot easier to show the jpeg. We'll see though, but I put my money on usplash coming back around.

Luke

---

### Post by TravisNewman on 2005-04-25
I hope it does. I mean, a jpeg takes the "scary text" away from the user, but it's not quite functional. I know the reprocussions of doing so, but framebuffer/bootsplash looks good right about now.

But wait a sec-- I thought they weren't going to do framebuffer because of it's stability issues,  so that's why bootsplash was out-- but if they're using a framebuffer with a jpeg, why not just go all the way bootsplash?

---

### Post by jdodson on 2005-04-25
i know i am in the minority on this one, but i would rather them spend time making ubuntu more stable and feature rich than a fancy usplash.

i mean, the fedora splash is SWEET, don't get me wrong.  however, a cheezy jpg to framebuffer dump is sufficent to make people happy.  at least then people will be like "well they have a graphical boot now."  though nice spinning widgets and eyecandy would be good, i would rather more energy be spent into package stability and other features.

just my .02.  

if they decide to go all the way with the bootsplash, i wont argue with it though.

---

### Post by TravisNewman on 2005-04-26
I, for one, don't care about splashes. I'd be perfectly happy with  text mode. However, if they DO decide to do some sort of splash, I'd prefer one that's functional, such as the Fedora/SuSE/etc, where it shows you what's happening and allows you to view the messages in a window inside the bootsplash. 

Doesn't bother me either way, as long as I can diagnose problems, but the splash is a psychological thing.

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=jdodson]i know i am in the minority on this one, but i would rather them spend time making ubuntu more stable and feature rich than a fancy usplash.
[/QUOTE]

Thing about it is, I tried the bootsplash that is here on the forums, an it works great. Much like the live cd.

The only effort would be making it the default.

EDIT: I don't mind the text, but is scary for some people.

---

### Post by nautilus on 2005-04-26
Well jeez, why don't we just link X with Init and be done with it?

I like splashy, and even made my own Ubuntu splashy booter thinger, but it breaks when X fires up for some terrible, terrible reason :(

Hiding the text may be nice for the user, but what about the admin? :(

Why can't we all have our cake and eat it too? (like splashy lets us?)

---

### Post by TravisNewman on 2005-04-26
agreed, agreed, agreed. Splashy has already done the work, and I doubt they'd mind Ubuntu using it by default.

---

### Post by Goshawk on 2005-04-26
HI. I'm one of the main developer of Splashy.
I wanna just say that Splashy is going to agree with the ubuntu specifications about Usplash that are descrived in the wiki (server-client approach).
Another best solution could be: start X and gdm early as possible; yes i know that it's already done in ubuntu, but it's too late.
What fedora is going to do is to start X at first time before network detection an so on, just load the kernel and one of the first service to run is X.

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=Goshawk]HI. I'm one of the main developer of Splashy.
I wanna just say that Splashy is going to agree with the ubuntu specifications about Usplash that are descrived in the wiki (server-client approach).
Another best solution could be: start X and gdm early as possible; yes i know that it's already done in ubuntu, but it's too late.
What fedora is going to do is to start X at first time before network detection an so on, just load the kernel and one of the first service to run is X.[/QUOTE]
 

Sounds good. Fedora has the best splash screen IMHO.

---

### Post by TravisNewman on 2005-04-26
I like the way Fedora's works, but SuSE's LOOKS the best. Combine the two, with some Ubuntu graphics, and *drool*

But as jdodson said, that shouldn't be high priority.

---

### Post by TravisNewman on 2005-04-26
Since the discussion of Splashy came up, I decided to try it. Simple and slick. Doesn't add but about a second or two on to bootup time, if that, and installation is as simple as downloading 3 debs and "sudo dpkg -i *.deb."

Its not as connected to the boot process as Fedora is, for example. In Fedora you have things like "Starting up network processes", etc, and this is something that could be added to Splashy that I would LOVE, but as it is, it does it's job-- there's a progress bar telling you how far along you are, and you can hit F2 to get back to the verbose mode we all know and love.

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=panickedthumb]Since the discussion of Splashy came up, I decided to try it. Simple and slick. Doesn't add but about a second or two on to bootup time, if that, and installation is as simple as downloading 3 debs and "sudo dpkg -i *.deb."

Its not as connected to the boot process as Fedora is, for example. In Fedora you have things like "Starting up network processes", etc, and this is something that could be added to Splashy that I would LOVE, but as it is, it does it's job-- there's a progress bar telling you how far along you are, and you can hit F2 to get back to the verbose mode we all know and love.[/QUOTE]


It does the job better than a picture would do it. I don't know why it isn't adopted. That and the menu editor.

---

### Post by TravisNewman on 2005-04-26
well, HOPEFULLY gnome will have they're own implementation of menu editing by the time breezy rolls around

---

### Post by poofyhairguy on 2005-04-27
[QUOTE=panickedthumb]well, HOPEFULLY gnome will have they're own implementation of menu editing by the time breezy rolls around[/QUOTE]


I'd rather Ubuntu still have it if Gnome decides to continue to go "na na".

---

### Post by Lovechild on 2005-04-27
Fedora will probably be dropping rhgb for FC4 in favor of something called early login, which basically hammers up gdm as soon as possible and then logs the user in after boot as finished.

the only thing that annoys me about rhgb right now is that it doesn't go directly from grub to graphics, it has these few text message displayed which is just ugly.. at least they could hammer a jpg on the screen or black the screen..

---

### Post by seven on 2005-04-27
[QUOTE=panickedthumb]Since the discussion of Splashy came up, I decided to try it. Simple and slick. Doesn't add but about a second or two on to bootup time, if that, and installation is as simple as downloading 3 debs and "sudo dpkg -i *.deb."

Its not as connected to the boot process as Fedora is, for example. In Fedora you have things like "Starting up network processes", etc, and this is something that could be added to Splashy that I would LOVE, but as it is, it does it's job-- there's a progress bar telling you how far along you are, and you can hit F2 to get back to the verbose mode we all know and love.[/QUOTE]

The verbose mode can be done like mandrake (mandriva), with a nice transparent background with the graphics behind. fedora really made a good splash

---

### Post by Mike Douglas on 2005-04-27
[QUOTE=Lovechild]Fedora will probably be dropping rhgb for FC4 in favor of something called early login, which basically hammers up gdm as soon as possible and then logs the user in after boot as finished.

the only thing that annoys me about rhgb right now is that it doesn't go directly from grub to graphics, it has these few text message displayed which is just ugly.. at least they could hammer a jpg on the screen or black the screen..[/QUOTE]
rhgb actually corrupts the terminals on some machines, which is the main reason they're dropping it. I actually had to use the nvidia binary drivers because rhgb + nv would just destroy the terminal.

---

