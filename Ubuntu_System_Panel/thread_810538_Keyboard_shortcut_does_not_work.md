---
title: "Keyboard shortcut does not work"
date: 2008-05-28
forum: Ubuntu System Panel
---

### Post by perfran on 2008-05-28
Hello :)
My USP keyboard shortcut does not work. It worked with gutsy but now I'm on hardy it does not work anymore
It is <Alt>twosuperior  (the key just below escape; french keyboard layout)
and I am usins the latest svn (rev 324)

I tried other shortcut and they work but they are not as practical as <Alt>twosuperior

Does someone know what should I do to make it to work?
Thanks

---

### Post by Malac on 2008-05-29
> **perfran said:**
> Hello :)
My USP keyboard shortcut does not work. It worked with gutsy but now I'm on hardy it does not work anymore
It is <Alt>twosuperior (the key just below escape; french keyboard layout)
and I am usins the latest svn (rev 324)
 
I tried other shortcut and they work but they are not as practical as <Alt>twosuperior
 
Does someone know what should I do to make it to work?
Thanks
If you have upgraded it might be worth checking that the keyboard is still set up correctly.
If you open a terminal and run "xev" then it should tell you what the keypresses are being reported as.
 
Hope this helps.

---

### Post by perfran on 2008-06-01
Thanks Malac for this advice.
I tried xev and it tells me that the key is named twosuperior like it was before.
I tried again to set this shortcut and it worked.
I don't understand well why but the important it that it works again :)
Thank you

---

### Post by Malac on 2008-06-02
> **perfran said:**
> Thanks Malac for this advice.
I tried xev and it tells me that the key is named twosuperior like it was before.
I tried again to set this shortcut and it worked.
I don't understand well why but the important it that it works again :)
Thank youI'm glad it was sorted out.
Sometimes hotkeys can be a little flakey in gnome as I'm using the tomboy keybinder which I would prefer not to but I have yet to get round to writing my own. :)

---

### Post by Quikee on 2008-06-03
> **Malac said:**
> I'm glad it was sorted out.
Sometimes hotkeys can be a little flakey in gnome as I'm using the tomboy keybinder which I would prefer not to but I have yet to get round to writing my own. :)

I have read in some blog a while ago that someone is working to create a keybinding library (which could be easier to include in distros and write bindings for it) based on tomboys but I can't find it anymore. Something like this makes sense because other applets like Gimmie (I think) and Deskbar also use the same library from tomboy.

---

### Post by Malac on 2008-06-03
> **Quikee said:**
> I have read in some blog a while ago that someone is working to create a keybinding library (which could be easier to include in distros and write bindings for it) based on tomboys but I can't find it anymore. Something like this makes sense because other applets like Gimmie (I think) and Deskbar also use the same library from tomboy.I have been looking for this module for a while now. I came across one months back on a website but at the time didn't think anything of it. Now I want to look into it I can't find it anymore :(

---

### Post by Quikee on 2008-06-04
> **Malac said:**
> I have been looking for this module for a while now. I came across one months back on a website but at the time didn't think anything of it. Now I want to look into it I can't find it anymore :(

[Found it!]("http://www.grillbar.org/wordpress/?p=250")

---

### Post by Malac on 2008-06-06
> **Quikee said:**
> [Found it!]("http://www.grillbar.org/wordpress/?p=250")
This one uses the tomboy drivers too it's just a wrapper around them by the looks of it.
 
I've found another one, it's the gDesklets keybinder code. It uses a '.py' file and a 'c' module, though it seems to work on numeric keycodes and modifiers so I'd need to do some translation for the "<Shift>" type notation we are using at the moment. That way there should be no usability change for users.
I've got it working with the numeric codes but have yet to get to the string-keycode parsing, hopefully there will be an easy way to do this.
 
I'm working on both at the mo' so will see which one is the most stable/usable.
 
If you want to take a look at the gDesklets one.
 
KeyBinding.py
[http://www.koders.com/python/fidD8928919F50A2ACFF5608F084EEB1D1017F1BF45.aspx?s=gdesklets](http://www.koders.com/python/fidD8928919F50A2ACFF5608F084EEB1D1017F1BF45.aspx?s=gdesklets)
 
x11 module
[http://www.koders.com/c/fid808E00CB15BD3A9CB4EB6829B5DACE733147554B.aspx?s=gdesklets](http://www.koders.com/c/fid808E00CB15BD3A9CB4EB6829B5DACE733147554B.aspx?s=gdesklets)

---

### Post by Quikee on 2008-06-06
From my view both solutions are equal - in both you have some external c file you have to compile yourself. What I want is some library that is available in standard distributions that I can use - I don't have a motivation to "temporary" write my own one.    

libgtkhotkey has the goal to be "standard" gtk key-binding library (if it is based on tomboy it doesn't matter as long as it works) and possible in the future will be included in gtk. This is all that matters. 

The question I am asking myself is how can I help to push for this library. :)

---

### Post by Malac on 2008-06-06
> **Quikee said:**
> From my view both solutions are equal - in both you have some external c file you have to compile yourself. What I want is some library that is available in standard distributions that I can use - I don't have a motivation to "temporary" write my own one. 
 
libgtkhotkey has the goal to be "standard" gtk key-binding library (if it is based on tomboy it doesn't matter as long as it works) and possible in the future will be included in gtk. This is all that matters. 
 
The question I am asking myself is how can I help to push for this library. :)
I couldn't believe there wasn't a 'standard' python module that handles keybinding when I looked into implementing this for USP.
I thought it would be so easy; just import a new module and call the functions.
 
I don't think it matters which one is incorporated into python 'standard' as they all use a module to do the job. But a standard solution to this would help with alot of programming projects out there.
 
I think the only way to get things into python is to make feature requests of the dev's using Roundup.

---

### Post by Quikee on 2008-06-06
> **Malac said:**
> I couldn't believe there wasn't a 'standard' python module that handles keybinding when I looked into implementing this for USP.
I thought it would be so easy; just import a new module and call the functions.
 
I don't think it matters which one is incorporated into python 'standard' as they all use a module to do the job. But a standard solution to this would help with alot of programming projects out there.
 
I think the only way to get things into python is to make feature requests of the dev's using Roundup.

Well.. to be exact I wouldn't want to include it into python but rather gtk as it is gtk that lacks this feature and should provide it. It is also not only a python problem as you have the same problem in every language.

---

