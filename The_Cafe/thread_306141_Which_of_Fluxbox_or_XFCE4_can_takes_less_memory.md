---
title: "Which of Fluxbox or XFCE4 can takes less memory ?"
date: 2006-11-24
forum: The Cafe
---

### Post by burek on 2006-11-24
To have lightest-weight but either xfce4 or fluxbox


Thank you for the information

=> ==================
update:
[COLOR="Red"]I investigated: XFCE is definitely not a very lightweight one  !!! (for up to 128MB ram PC) [/COLOR]
XFCE (140MB) takes me ~40% more than fluxbox (70MB).

[B][I]List of lightweight window manager:
 (default install, no tuning) (classment from the minimalist)
 (first, we have quite a lot of windows manager under linux, whihc is great)[/I][/B]
(legend: 
[COLOR="Red"]THEMES1[/COLOR] quite minimalist theme chooser and freshmeat.org visit adviced and terminal too but theme working !
[COLOR="Red"]THEMES2[/COLOR] Window THEMES chooser from the apt-get or already available !!))
[COLOR="Red"]THEMES3[/COLOR] High-Tech themes levels

(I should do to a binding level window chooser... (bindingswm))

[INDENT]
**== ultra light == level 0 ===**
0 - TinyWM  (you cannot find lighter)  50 lines of C
1 - twm 
2 - jwm (and sisters)


**== minimalist == level 1 ===**
2 - **Openbox 65MB**  **fvwm **and **blackbox**  (the two lightest) 65-69 MB [COLOR="Red"]THEMES1[/COLOR]

3 - fvwm  based 

4 - Icewm (69,9 MB) [COLOR="Red"]THEMES1-2 [/COLOR]
 
 
 
 

**== minimalist advanced === level 2 ====**
5 - fluxbox (70-72MB)   [COLOR="Red"]THEMES1[/COLOR]
5 - Metacity (70-72MB) (apt-get install metacity) [COLOR="Red"]THEMES3[/COLOR] bindings
... fvwm based advanced ; metacity is very great since you can use the stuffs from gnome
and still very light. [nfo]("http://en.wikipedia.org/wiki/Metacity")
 
 
 

**=== level 3 ====**
6 - light-xfce4 (tuned) (75MB) [COLOR="Red"]THEMES2[/COLOR] (bindingswm)

7 - sawfish (80-82MB) [COLOR="Red"]THEMES2[/COLOR] (bindingswm)
 
 
 


**=== level 4 ====**
8 - (XFCE = quite slow for very old machines for museums) [COLOR="Red"]THEMES2[/COLOR]
(Please stop saying that a ultra lightweight,  it is medium )
(flubox is great for very old machines for museums)
110MB (bindingswm)

 
 
 

**==== level 5 === Userfrienly === **
... and far away: 
10 - gnome / KDE (hug of memory damn !! but we like it this so userfriendly) (bindingswm) [COLOR="Red"]THEMES3[/COLOR][/INDENT] 
  

UPDATE II:KS 
==========
After fighting with mw linux machine in config files; I just found the way to make it lighter thsi xfce with keeping the possibility of changing your windows styles and so on:
> 
apt-get -f install thunar orage xfmedia xfce4-mixer
apt-get install python2.4-xfce python-xfce
apt-get install python-dev
apt-get -f install libxfce4util4 libxfce4util-dev 
apt-get -f install python-xfce

You can edit go in /usr/share/xsessions
cp xfce4.desktop lightxfce.desktop 
into lightxfce.desktop ; 
change to make the name lightxfce
and replace startxfce4 by /usr/bin/xfwm4

restart gdm /etc/init.d/gdm restart

then; 
select for sessions from the gdm lightxfce

your lighterxfce starts I guess
to configure your bindings and lightxfce ; type : [COLOR="Red"]xfce-setting-show[/COLOR]


[COLOR="Red"]qnd eveerythings works like it was more or less : windows styles; bindings ....[/COLOR]

I am still looking for a light menu to logout/ I used logout via bindings
and xfce-setting-show taht I define as flag + pause

and the New Dude is as LIGHTWEIGHT as flubox !! a bit lighter even ! 
and I have my windows styles and can change them as much as xfce-pluging themes as

  
  
Burek
=====

---

### Post by dca on 2006-11-24
Fluxbox probably takes up the least amount of memory.  That and maybe IceWM compared to XFCE...

---

### Post by mips on 2006-11-24
Probably Fluxbox, I don't have the proof but I suspect Fluxbox is lighter.

---

### Post by dbbolton on 2006-11-24
i've never heard of fluxbox :(

but i thought the whole point of xfce was to be lightweight...

---

### Post by deanlinkous on 2006-11-24
flux probably lighter in general, but if you add features to it that xfce already has, well.....obvious :D

---

### Post by GStubbs43 on 2006-11-24
Well, XFCE is an actual Desktop Environment, like GNOME or KDE.
Fluxbox is a Window Manager, which requires another Desktop Environment such as GNOME or KDE.

So... Fluxbox is lightwheight, but you must also have another DE, with XFCE you can *just have* XFCE, nothing else. :)

Edit: nevermind... this is messed up... ;)

---

### Post by mips on 2006-11-24
> **GStubbs43 said:**
> Well, XFCE is an actual Desktop Environment, like GNOME or KDE.
Fluxbox is a Window Manager, which requires another Desktop Environment such as GNOME or KDE.

So... Fluxbox is lightwheight, but you must also have another DE, with XFCE you can *just have* XFCE, nothing else. :)

Since when, never heard of this before. You just do a server install, X11 & fluxbox and bobs your uncle. no need for gnome or kde.

Where did you hear this ?

---

### Post by GStubbs43 on 2006-11-24
> **mips said:**
> Since when, never heard of this before. You just do a server install, X11 & fluxbox and bobs your uncle. no need for gnome or kde.

Where did you hear this ?

Ok, you're right. I got confused... but...
A desktop Environment *does* needs a Window manager to display stuff.
:mrgreen:

---

### Post by MedivhX on 2006-11-24
Go for Flux.

---

### Post by WalmartSniperLX on 2006-11-24
Im using flux now as a primary wm (other than my kde session). 

If I remember correctly, fluxbox uses less than 100MB of ram on boot (somewhere like 70-90MB)

I put xfce on a friends computer. I think it uses more than a 100MB on boot (maybe close to 200MB)

:cool:

---

### Post by kerry_s on 2006-11-24
I use a command-line install & fluxbox, my system is very light.

---

### Post by burek on 2006-11-24
I updated my first post of this thread ; study made.

---

### Post by IYY on 2006-11-24
It basically goes... Gnome/KDE is heavier than Fluxbox is heavier than everything else. IceWM is my favourite.

---

### Post by lapsey on 2006-11-24
IceWM is great in that it has all the basics you need.

I like FVWM but it could be even greater if there were a tool for creating the environment, like a graphical desktop creation thingy. Otherwise you have to spend a ton of time programming a desktop in code or suffer someone else's idea of a DE. Even FVWM Crystal suffers from the "ricer effect"

---

### Post by shining on 2006-11-24
> **lapsey said:**
> IceWM is great in that it has all the basics you need.

I like FVWM but it could be even greater if there were a tool for creating the environment, like a graphical desktop creation thingy. Otherwise you have to spend a ton of time programming a desktop in code or suffer someone else's idea of a DE. Even FVWM Crystal suffers from the "ricer effect"

I believe ricing is more about useless customizations.
Being able to configure your environment to be exactly like you want can be useful IMHO, so I wouldn't call that ricing.
It's just the dilemma between configurability and simplicity.

---

### Post by burek on 2006-11-24
> 
I believe ricing is more about useless customizations.
Being able to configure your environment to be exactly like you want can be useful IMHO, so I wouldn't call that ricing.
It's just the dilemma between configurability and simplicity.
I kind of replied to your dilemma !!!



UPDATE II
==========
After fighting with mw linux machine in config files; I just found the way to make it lighter thsi xfce with keeping the possibility of changing your windows styles and so on:

UPDATE in my first post of this thread


:KS :KS :KS :KS

---

### Post by Albi on 2006-11-24
> **IYY said:**
> It basically goes... Gnome/KDE is heavier than Fluxbox is heavier than everything else. IceWM is my favourite.

I'm pretty sure IceWM is heavier than fluxbox...by your post it makes it sound like fluxbox is only SLIGHTLY ligher than gnome, and it's much less

---

### Post by burek on 2006-11-25
> **Albi said:**
> I'm pretty sure IceWM is heavier than fluxbox...by your post it makes it sound like fluxbox is only SLIGHTLY ligher than gnome, and it's much less

Indeed; oki; it ll update to improve it. thx

---

### Post by happy-and-lost on 2006-11-25
> 
I put xfce on a friends computer. I think it uses more than a 100MB on boot (maybe close to 200MB)

Wow. My GNOME uses 140mb RAM and 0 swapspace on boot. It's just that hungry Firefox which bumps it up beyond 200 for me.

---

### Post by burek on 2006-11-25
i updated first post of this thread, 

even better now with the memory usage and themes informations

---

### Post by burek on 2006-11-25
> **happy-and-lost said:**
> Wow. My GNOME uses 140mb RAM and 0 swapspace on boot. It's just that hungry Firefox which bumps it up beyond 200 for me.

try this : 
apt-get install metacity
run it
and you will see; that you will have much more memory with your desktop

---

### Post by deanlinkous on 2006-11-25
woops sorry

---

### Post by bonzodog on 2006-11-25
*cough*

```
$sudo apt-get install openbox obconf pypanel
```.

Try Openbox, it's even lighter than Fluxbox, but has very similar features.

---

### Post by maddog39 on 2006-11-25
I would have to argue with you when u say that XFCE takes up 130MB because when I used to use Xubuntu (6.10), just sitting on my desktop after boot I would only use 92MB of ram.

---

### Post by burek on 2006-11-25
> **maddog39 said:**
> I would have to argue with you when u say that XFCE takes up 130MB because when I used to use Xubuntu (6.10), just sitting on my desktop after boot I would only use 92MB of ram.

I tried again and got 110MB. I guess as you say we can decrease it. But the problem it is that xfce needs to open some processses when you start to click a bit; that are using memory
I reduced to 110 MB
Dont know; could yuou try all the windows manager and make too investigation of memory ;..
we could make a small nfo webpage.

Cheers

---

### Post by burek on 2006-11-25
> **bonzodog said:**
> *cough*

```
$sudo apt-get install openbox obconf pypanel
```.

Try Openbox, it's even lighter than Fluxbox, but has very similar features.

69-74MB ; openbox is cool
it is too nice
btw how do you alt+rightmouse for resize 
and also for workspace wrap... 
i got odconf:
```
~$ obconf 
obconf: error while loading shared libraries: libobrender.so.1: cannot open shared object file: No such file or directory

``` that I am fixing now ...
[https://launchpad.net/distros/ubuntu/+source/obconf/+bug/71863](https://launchpad.net/distros/ubuntu/+source/obconf/+bug/71863)

---

### Post by maddog39 on 2006-11-25
Wow, well I was surprised to find that GNOME only uses 108MB just sitting on my desktop. This means right after i've just logged in and I open system monitor and it's using 108MB of RAM. When I open firefox this of course jumps 20MB.

---

### Post by Rui Pais on 2006-11-25
I have an very old pentium MMX 200 Mhz and tried fluxbox, openbox and windowmaker on it. 
Windowmaker is the fast and the more responsive of those. 
Don't take much care on memory used, most of the time some app will be eaten more mem then the all window manager.

---

