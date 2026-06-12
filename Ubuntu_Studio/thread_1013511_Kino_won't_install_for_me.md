---
title: "Kino won't install for me"
date: 2008-12-16
forum: Ubuntu Studio
---

### Post by jimbo12d on 2008-12-16
I have been trying this process: [http://www.kinodv.org/article/view/155/1/13/](http://www.kinodv.org/article/view/155/1/13/)
 
It is not working. I have been using ubuntu for a year but mostly for firefox and gaim, so I rarely install programs.

First, I don't know what in means to enable universe.

I tried "sudo apt-get install  build-essential" and the others, but it almost always has a failed to fetch file outcome.

I tried skipping installing these things and just do the "./configure" thing, but then I get: 
"checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details."

Please tell me if there is an easy way to install Kino

Thanks for the help.

---

### Post by dave101101 on 2008-12-21
it's easiest to install from a package than from source unless you know all the steps required for compiling from source.

to enable universe/multiverse/etc open synaptic and look in the settings menus for 'software sources' and check the box(es) beside the ones you want to add.

main = default, where you'll find most things that are fully open-source with no license restrictions

universe = similar to above

restricted = not hard to figure it out from the descriptions

multiverse = is where they hide more of the goodies

don't forget to 'reload' the package database when you've changed software sources.

as far as i know, you don't need to addresses for servers unless you have some obscure software source.

cheers, and good luck

ps. if you can't find software in a menu, open synaptic and check the properties page for software you want... you'll find where it installed to.

---

### Post by jimbo12d on 2008-12-21
Thanks a lot. I'll try it soon.

---

