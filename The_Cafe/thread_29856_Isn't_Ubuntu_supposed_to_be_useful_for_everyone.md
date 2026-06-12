---
title: "Isn't Ubuntu supposed to be useful for everyone?"
date: 2005-04-26
forum: The Cafe
---

### Post by StarkD on 2005-04-26
I'm a new user of Linux in general and yesterday I installed Ubuntu. I very impressed by Ubuntu and I like it very much. I like the whole "humanity to others" thing. But I don't like GNOME or KDE. They are as bloated and as clumsy as Microsoft Windows. If I only cared about performance and GUI I might as well use Microsoft Windows. Since I installed my sound card GNOME isn't able to start anymore at all [http://www.ubuntuforums.org/showthread.php?t=24586](http://www.ubuntuforums.org/showthread.php?t=24586) Therefor I installed XFCE I fell in love with it instantly. It took me only a couple of minutes to customize it to get it exactly as I wanted it the first time I used it! For me XFCE uses **half** as much memory as GNOME which means a lot on my old computer. Is there any graphical interface to hide the taskbar and the panel and such in GNOME? I didn't find it and now I'm not able to try.

Some day I'm going to do a custom install and only install XFCE since I've only got a 3.5 GB hard drive. It doesn't seem that difficult. I what Ubuntu with only XFCE installed. I've got the interest, the time and the will to do such a thing.

What happend with "humanity to others"?
What about people who only can afford cheap computers?

---

### Post by JDay on 2005-04-26
[QUOTE=StarkD]Is there any graphical interface to hide the taskbar and the panel and such in GNOME? I didn't find it and now I'm not able to try.[/QUOTE]
Right click a panel and select properties. Two of the options are for autohiding the panel and showing hide buttons on it.

---

### Post by Turin Turambar on 2005-04-26
Although XFCE is really blazingly fast, even on old machines, I find GNOME much faster and much more slick than WinXP. It's the KDE that looks bloated and clogged with features and visually reminds me a lot on Windows.

---

### Post by defkewl on 2005-04-26
I agree to that. Gnome is so heavy and I use Windows when Ubuntu doesn't satisfy me. I ran Java apps it goes much faster in Windows rather than in Ubuntu :( 

I think Gnome took almost all of my memory and CPU resources
I have a 128 MB RAM and P4 2,2 GHz and it doesn't go as fast as it should be. Windows are much faster under these specs. I might as well install xfce. I tried installing wmaker but didn't succeed.

---

### Post by az on 2005-04-26
"What happend with "humanity to others"?
What about people who only can afford cheap computers"



What, the man pointing a gun to your head forcing you to install Ubuntu did not explain that you could install a simple base system and then add lighter window managers?  He should be fired!

He should have told you to:
Boot the install cd with the server option.  Go though the install to the end..
log in
sudo nano /etc/apt/sources.list
uncomment the universe repository
sudo apt-get update
sudo apt-get install xterm x-window-system-core gdm xcfe icewm abiword mozilla-firefox menu

Enjoy your lean machine.

---

### Post by TravisNewman on 2005-04-26
Whenever someone doesn't like something about Ubuntu, they say it's violating "humanity to others." Whenever someone likes something that others don't and they're trying to promote it, they say it is "humanity to others."

Please, and this goes for everyone, stop evoking the Ubuntu Code of Conduct to suit your needs. I find it ridiculous that you're saying that because Gnome is included by default, and not XFCE, that it's violating the humanity that Ubuntu stands by.

If you want help, ask for help. Instead of asking a question and trying to make a point, you simply bashed the way Canonical decided to take things.

---

### Post by StarkD on 2005-04-26
[QUOTE=azz]
Boot the install cd with the server option.  Go though the install to the end..
log in
sudo nano /etc/apt/sources.list
uncomment the universe repository
sudo apt-get update
sudo apt-get install xterm x-window-system-core gdm xcfe icewm abiword mozilla-firefox menu

Enjoy your lean machine.[/QUOTE]That sounds easy enough but that's not my point. Wouldn't it be better if Ubuntu had a lightweight desktop manager (like XCFE or whatever) as default and then you can do the above to get a bigger alternative (like GNOME or whatever)?

[QUOTE=panickedthumb]
I find it ridiculous that you're saying that because Gnome is included by default, and not XFCE, that it's violating the humanity that Ubuntu stands by.[/QUOTE]You got me there panickedthumb and I apologize. I got very excited over XFCE. My point isn't that specifically XFCE should be used. Any lightweight desktop manager would do for the point I'm trying to make.

Imagine the following person wanting to install and use Ubuntu:
- a computer newbie
- has an old computer
- has no Internet connection

Wouldn't it better for this person if a lightweight desktop manager is default?

I interpret "humanity to others" as that the person above would find Ubuntu useful. Or am I taking this to far? My guess is that there are a lot of these persons around the world. There are many situations where I would like to be able to say "Install Ubuntu it's great! It's in Swedish, free as in freedom, easy to install, you don't need Internet to install it and works on your old computer"

---

### Post by fordfan753 on 2005-04-26
[QUOTE=panickedthumb]Whenever someone doesn't like something about Ubuntu, they say it's violating "humanity to others." Whenever someone likes something that others don't and they're trying to promote it, they say it is "humanity to others."

Please, and this goes for everyone, stop evoking the Ubuntu Code of Conduct to suit your needs. I find it ridiculous that you're saying that because Gnome is included by default, and not XFCE, that it's violating the humanity that Ubuntu stands by.

If you want help, ask for help. Instead of asking a question and trying to make a point, you simply bashed the way Canonical decided to take things.[/QUOTE]

Good on you!!
I'm sick of people not being able to do things properly and just taking it out on Ubuntu...really, it's not an Ubuntu problem if people can't read and/or think for themselves.

---

### Post by Stormy Eyes on 2005-04-26
[QUOTE=StarkD]What happened with "humanity to others"?
What about people who only can afford cheap computers?[/QUOTE]

Last time I checked, "humanity to others" doesn't mean putting up with whinging.

---

### Post by elasticwings on 2005-04-26
You know, if you really want, you could just start working on making an Ubuntu based distro with XFCE as the default desktop upon install.  I would very much be interested in seeing one.  I personally enjoy the Gnome interface myself, but I would definitely try installing an Ubuntu spawn with XFCE or another lightweight window manager as the default desktop interface.  You should try to get together a project with some coders/hackers and make it happen.

---

### Post by rpm on 2005-04-26
I agree to include xfce for older system on the install cd

but not refere to humanity instead of choices 

is better to speak about accessibility for everyone here

bye

rpm

PS: if you are interested in this I posted 3 topics named "xubuntu ..."

bye

---

### Post by az on 2005-04-26
Kubuntu is a customisation suppoerted by the community.  Instead of whining about Ubuntu not including KDE, they made it.

Get the point?

Go to the wiki and look at the current customisation projects.

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=StarkD]
What about people who only can afford cheap computers?[/QUOTE]


They can do a minimal install and add XFCE. XFCE should never be the default. Why? Same reason I won't use it for a desktop environment despite its cool themes.



Steps to understand why XFCE will never be the default DE:

1. Insert a CD, or plug in a USB disk (such as a pen drive) while in XFCE.

2. Notice how nothing happens. No desktop icons, no file manager opening up. Nothing.

---

### Post by TravisNewman on 2005-04-26
Well, that's one of quite a few reasons poofy.

---

### Post by Brunellus on 2005-04-26
[QUOTE=poofyhairguy]They can do a minimal install and add XFCE. XFCE should never be the default. Why? Same reason I won't use it for a desktop environment despite its cool themes.



Steps to understand why XFCE will never be the default DE:

1. Insert a CD, or plug in a USB disk (such as a pen drive) while in XFCE.

2. Notice how nothing happens. No desktop icons, no file manager opening up. Nothing.[/QUOTE]
 ..which is why I run fluxbox, but cheat and run the gnome volume manager in the background.  

Suddenly, my removeable devices automount nicely...without having to deal with gnome
s other bloat...er, features :).  yay!

---

### Post by jdodson on 2005-04-26
[QUOTE=Brunellus]..which is why I run fluxbox, but cheat and run the gnome volume manager in the background.  

Suddenly, my removeable devices automount nicely...without having to deal with gnome
s other bloat...er, features :).  yay![/QUOTE]

LOL!  thats a way to do it.  i used to run fluxbox when i had a lower end machine.  now that i have my AMD 64 3000+ with a gig of ram, i really don't need to run a lightweight window manager, i can run a desktop enviornment with no speed issues.

then again i do much from the console, so its not like i am all GUI or anything.  some stuff is just easier via console anyway.

as to the original poster.  i agree with panikedthumb and azz's sentaments.  cool thing about ubunt is you can twist it up.  so a XFCE ubuntu distro could be in the works, if you want to work it.  XFCEbuntu anyone? O:)

---

### Post by escuchamezz on 2005-04-26
XFCE has that beautifully irresistable Windows 3.11 look  :)

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=Brunellus]..which is why I run fluxbox, but cheat and run the gnome volume manager in the background.  

Suddenly, my removeable devices automount nicely...without having to deal with gnome
s other bloat...er, features :).  yay![/QUOTE]

Yeah, I did that to XFCE. But then the speed decreased, to the point where on my hardware it felt like Gnome anyways....

Maybe the newest version is faster. I did that a few months ago.

But I guess for somethign really old, that fluxbox might do the trick. Is there like a reasource for Fluxbox noobs? I can't find one. I can't grok the thing by myself.

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=panickedthumb]Well, that's one of quite a few reasons poofy.[/QUOTE]

It the reason for why I don't use it. It implies the reason that Ubuntu doesn't use it: its not a complete desktop environment.

Its like the only thing in the middle in between the KDEs and Gnomes and the Fluxboxs and Windowmakers.

I personally don't mind spending the money on RAM to get Gnome to work well. CPU wise its no worse than XFCE:

[http://ubuntuforums.org/journal.php?do=showjournal&j=7](http://ubuntuforums.org/journal.php?do=showjournal&j=7)

My own experiance proves this. Its faster on systems with less than 256mb of ram. But at 256 or more, its about the same....

---

### Post by StarkD on 2005-04-26
[QUOTE=poofyhairguy]
Steps to understand why XFCE will never be the default DE:

1. Insert a CD, or plug in a USB disk (such as a pen drive) while in XFCE.

2. Notice how nothing happens. No desktop icons, no file manager opening up. Nothing.[/QUOTE]Great with some facts poofyhairguy! That's an argument for not choosing XCFE. But I guess that this is fixed with xfce4-mount-plugin?

Give me more arguments, I'm curious.

---

### Post by az on 2005-04-26
[QUOTE=escuchamezz]XFCE has that beautifully irresistable Windows 3.11 look  :)[/QUOTE]

No.  FVWM does.
[http://packages.ubuntu.com/hoary/x11/fvwm](http://packages.ubuntu.com/hoary/x11/fvwm)

Lets split this tread into a zillion just-barely-on-topic rants!

---

### Post by TravisNewman on 2005-04-26
[QUOTE=azz]
Lets split this tread into a zillion just-barely-on-topic rants![/QUOTE]

Agreed-- this started off with a point (though veiled in a rant) and has been nothing but more and more rants ever since (and I admit to contributing a bit to that). This has gone as far as it needs to, and has incredible potential to explode.

You're more than welcome to make your points be heard, but not by flaming and trolling please-- flaming and trolling lead to threads like these, which cause others to flame and troll, and it gets out of hand.

---

