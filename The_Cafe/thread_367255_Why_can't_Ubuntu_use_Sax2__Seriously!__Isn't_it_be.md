---
title: "Why can't Ubuntu use Sax2??  Seriously!  Isn't it better?"
date: 2007-02-21
forum: The Cafe
---

### Post by Yfrwlf on 2007-02-21
Dpkg-reconfigure xserver-xorg is great, but Sax2 in Suse seems more user-friendly.  Wouldn't it be beneficial to rip it out of Suse and allow Suse to benefit from it's use?  So many problems are due to monitors not being supported that I've run into that I think it may be a really important incorporation.  Problems obviously could spring up though if it's too hard to rip it out.

Anyone have any opinions on this?  Good idea bad idea?  Until monitor support is better, wouldn't it be good to utilize anything that could improve it?

Otherwise what about making dpkg-reconfigure xserver-xorg more accessible for beginners at least?  There are ways you could direct a user to use it when they have problems with monitor detection.

---

### Post by DoctorMO on 2007-02-21
I always thought SaX and SaX2 were proprietory; so we couldn't copy those parts of the SuSE system; but I last checked many years ago and perhaps it's not licensed better.

Besides you can't so a lot with SaX on the command line; we should create configuration which works with both GUI and command line.

---

### Post by cowlip on 2007-02-21
Xorg 7.3 (next release) hotplugging should put an end to needing to configure X and the bad multi-monitor situation, so hopefully this won't even be needed :)

---

### Post by futz on 2007-02-21
I'm writing a little utility in Python to make monitor adjustments easier. Hopefully someone who's a better programmer than I will beat me to it, but ya never know. I'm kind of a Python newb, so I'm learning as I go. Large chunks of code are already written and tested, but I have a ways to go yet...

It's getting built with a tkinter gui for now. Might rewrite for GTK later. And a text interface is a must, even if it's a second version of the same program. After all, if you can't get X to start, a gui isn't gonna do ya much good, right?

I want something like in windows, where you set what you want and hit Apply and it changes the res on the fly and waits like 15 seconds for you to click OK to keep that res. Otherwise it drops back to where it was with a message.

Speaking of someone beating me to it, has anyone tried Envy? Is it any good?
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by siimo on 2007-02-22
i have NEVER ever had Sax2 work on my system... out of the 3-4 times i have tried SUSE i have been left to a black command prompt window where i had to go and fix the xorg.conf so i could load the graphical desktop.  

Ubuntu works much better... only the resolution is wrong with ubuntu and i don't get left with a ****** command prompt.

---

### Post by Anthem on 2007-02-22
Sax2 is GPL, and so far superior to dpkg-configure that it hurts.

All I can figure is it's a case of Not Invented  Here, just like Anaconda.

---

### Post by ComplexNumber on 2007-02-22
[QUOTE=futz]
It's getting built with a tkinter gui for now. Might rewrite for GTK later.[/QUOTE]
write it for gtk now.....tk is really ugly :p

---

### Post by GameManK on 2007-02-22
> **futz said:**
> I'm writing a little utility in Python to make monitor adjustments easier. Hopefully someone who's a better programmer than I will beat me to it, but ya never know. I'm kind of a Python newb, so I'm learning as I go. Large chunks of code are already written and tested, but I have a ways to go yet...

It's getting built with a tkinter gui for now. Might rewrite for GTK later. And a text interface is a must, even if it's a second version of the same program. After all, if you can't get X to start, a gui isn't gonna do ya much good, right?

I want something like in windows, where you set what you want and hit Apply and it changes the res on the fly and waits like 15 seconds for you to click OK to keep that res. Otherwise it drops back to where it was with a message.

Speaking of someone beating me to it, has anyone tried Envy? Is it any good?
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

How about working on kde-guidance's displayconfig? It's in python :)

---

### Post by futz on 2007-02-22
> **ComplexNumber said:**
> write it for gtk now.....tk is really ugly :p
Yes it is, but I want to learn tkinter first (don't ask me why). 

Ok, I'll tell ya anyway... I'm an old programmer, from before the days of oop (object oriented programming). Oop messes with my mind. I understand it, sort of. I can see how good and sensible it is, but I still have nothing but trouble using it. And every gui uses it. You have no choice but to learn it, and learn it well.

I could be wrong, but in my experimentations I found tkinter a bit easier to get something happening than when I was playing with gtk. I just need time & practice with the oop thing to get my head around the way to make and use it properly.

On the other hand, you can use glade for gtk. That makes one big part of the job a LOT easier. I already did a screen layout for the program in glade, just to get a good idea how I was going to get things lined up in tkinter.

Once you get to my age it's harder to learn new things too. I hate that. Takes me much longer than it used to to pick up a new language or flavor of assembler. Have to really work at it. When I was young (there was no internet - only slow dial-up bbs's with almost no help there) I got a couple books and learned 6809 and Z80 assembler and C on my own. I was grindingly determined back then. Now I have so many distractions (stupid interweb :mrgreen:).

---

### Post by futz on 2007-02-22
> **GameManK said:**
> How about working on kde-guidance's displayconfig? It's in python :)
Never heard of it. Googling now...

---

### Post by ComplexNumber on 2007-02-22
> **futz said:**
> Yes it is, but I want to learn tkinter first (don't ask me why). 

Ok, I'll tell ya anyway... I'm an old programmer, from before the days of oop (object oriented programming). Oop messes with my mind. I understand it, sort of. I can see how good and sensible it is, but I still have nothing but trouble using it. And every gui uses it. You have no choice but to learn it, and learn it well.

I could be wrong, but in my experimentations I found tkinter a bit easier to get something happening than when I was playing with gtk. I just need time & practice with the oop thing to get my head around the way to make and use it properly.

On the other hand, you can use glade for gtk. That makes one big part of the job a LOT easier. I already did a screen layout for the program in glade, just to get a good idea how I was going to get things lined up in tkinter.

Once you get to my age it's harder to learn new things too. I hate that. Takes me much longer than it used to to pick up a new language or flavor of assembler. Have to really work at it. When I was young (there was no internet - only slow dial-up bbs's with almost no help there) I got a couple books and learned 6809 and Z80 assembler and C on my own. I was grindingly determined back then. Now I have so many distractions (stupid interweb :mrgreen:).
write it in gtkmm(ie C+ bindings for gtk) then. the bindings are always kept up to date with gtk. 
i learnt 6502 assembly when i were young because i had a bbc micro.

---

### Post by prizrak on 2007-02-22
Actually Feisty is supposed to have the bullet proof X with xrandr rather than xorg.conf that should take care of that issue completely. (So far the latest update broke my Beryl tho so I dunno)

---

### Post by Yfrwlf on 2007-02-22
> **cowlip said:**
> Xorg 7.3 (next release) hotplugging should put an end to needing to configure X and the bad multi-monitor situation, so hopefully this won't even be needed :)

Sweet that would rock ^^  I was explaining to my friend that it's really cool that even if a monitor is incompatible with Linux, you can still give it the specs and force it to work properly (usually).  The biggest snag he faced was dual monitor support.  If nvidia would just hurry up with their driver support and implement it then things would be better.  Sax2 is able to nicely configure a dual monitor layout, something I forgot to mention.  I hope that xorg 7.3 will be able to deal with dual monitors better as well! :)  It's too bad it won't be finished until after Feisty is released though, but that's what system updates are for.  Hope we don't have to wait til Ubuntu 8 to get awesomer hardware support.  Yes, I know awesomer isn't a word, but it should be! ;)

---

