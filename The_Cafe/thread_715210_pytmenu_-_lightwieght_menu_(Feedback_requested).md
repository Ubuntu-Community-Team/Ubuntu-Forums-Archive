---
title: "pytmenu - lightwieght menu (Feedback requested)"
date: 2008-03-04
forum: The Cafe
---

### Post by uzusan on 2008-03-04
I've created a small menu app that im using in openbox with xcompmgr (though it works in gnome with compiz, others im not sure of).

The idea was to create a menu you could activate with a keyboard shortcut that would show applications, then you can hit enter to launch them.

Its my first python program (and my first linux program that does something useful) so its probably full of bad ways of doing what it does, but it seems to work for me.

At the moment the list of programs are just stored in a list, which is then accessed based on its position. I know this isn't the best way to do it, but i need to get my head round pythons dictionaries, tuples etc before i can change this.
EDIT: Updated links
If you want to try it, you can find it here: (You'll need all 3 files)
[http://www.fillermaterial.co.uk/pytmenu.py](http://www.fillermaterial.co.uk/pytmenu.py)
[http://www.fillermaterial.co.uk/pytconfig.py](http://www.fillermaterial.co.uk/pytconfig.py)
[http://www.fillermaterial.co.uk/pytmenu.dat](http://www.fillermaterial.co.uk/pytmenu.dat)

I've also created an ogg theora video demostrating it here: [http://www.fillermaterial.co.uk/pytmenu.ogg](http://www.fillermaterial.co.uk/pytmenu.ogg)  (3.2mb)

I've attached some screenshots showing it in action.
Description:
1. Before running pytmenu
2. pytmenu running
3. after hitting enter on Firefox
4. pytmenu running again, after having pressed right a few times
5. after hitting enter on Terminal (which runs a script that launches urxvt)

---

### Post by 23meg on 2008-03-05
Moved to Community Cafe.

---

### Post by K.Mandla on 2008-03-05
Interesting. Any plans to keep an external list of programs, rather than editing the script? What about reading out of the apps directory?

---

### Post by CaptainCabinet on 2008-03-05
Sounds like a useful app. :)
I'll try it in the morning.

---

### Post by uzusan on 2008-03-06
> **K.Mandla said:**
> Interesting. Any plans to keep an external list of programs, rather than editing the script? What about reading out of the apps directory?

Yes, the next thing i will be doing is making it work with an external list. I was going to go along the lines of pypanel and have the programs in a config file, perhaps with a seperate program that allows you to edit the list.

I'm not sure about reading the apps directory, it could get a bit unwieldy then. (i know that ive got apps in there that i only use once in a while, there would be hundreds on the menu if i read all of them)

---

### Post by gunnihinn on 2008-03-06
Hmm... very interesting. This is actually pretty much exactly what I've been looking for in the past few months. Good job, mate. :D

One tiny question; can you have the list loop around?

---

### Post by gunnihinn on 2008-03-06
> **gunnihinn said:**
> Hmm... very interesting. This is actually pretty much exactly what I've been looking for in the past few months. Good job, mate. :D

One tiny question; can you have the list loop around?
Nevermind, I figured out how to do it.

You can replace the if-else structures for gtk.keysyms.Right and gtk.keysyms.Left in key_press_imp by
```
    applen = len(applist)
    if event.keyval == gtk.keysyms.Right:
        label.set_text(applist[(ind - 2) % applen])
	 label2.set_text(applist[ind % applen])
        label3.set_text(applist[(ind + 2) % applen])

    if event.keyval == gtk.keysyms.Left:
        label.set_text(applist[(ind - 2) % applen])
	 label2.set_text(applist[ind % applen])
        label3.set_text(applist[(ind + 2) % applen])
```
and then replace the label definition in main by
```
label = gtk.Label(applist[ind-2])
```
and now the list will loop around. :)

Note: While Python supports negative indexes in lists (which is the reason applist[ind-2] works in the last line) it apparently has a problem if the negative indexes get too big, which is why we can't skip the % applen calls above.

---

### Post by uzusan on 2008-03-06
> **gunnihinn said:**
> Hmm... very interesting. This is actually pretty much exactly what I've been looking for in the past few months. Good job, mate. :D

One tiny question; can you have the list loop around?

Yeah that shouldn't be too hard. I might add in an option to do either (personally i prefer it the way it is, but i can see why you would want it to loop).

I'll have a look at it this afternoon, im in work at the moment.

---

### Post by uzusan on 2008-03-06
> **gunnihinn said:**
> Nevermind, I figured out how to do it.

You can replace the if-else structures for gtk.keysyms.Right and gtk.keysyms.Left in key_press_imp by
```
    applen = len(applist)
    if event.keyval == gtk.keysyms.Right:
        label.set_text(applist[(ind - 2) % applen])
	 label2.set_text(applist[ind % applen])
        label3.set_text(applist[(ind + 2) % applen])

    if event.keyval == gtk.keysyms.Left:
        label.set_text(applist[(ind - 2) % applen])
	 label2.set_text(applist[ind % applen])
        label3.set_text(applist[(ind + 2) % applen])
```
and then replace the label definition in main by
```
label = gtk.Label(applist[ind-2])
```
and now the list will loop around. :)

Note: While Python supports negative indexes in lists (which is the reason applist[ind-2] works in the last line) it apparently has a problem if the negative indexes get too big, which is why we can't skip the % applen calls above.

Cheers :) I was originally trying something like that and kept getting out of range errors, probably because of the negative indexes as you say.

I would quite like to have the option of either, so ill maybe add in an if statement or two to switch between the 2 methods as needed.

---

### Post by uzusan on 2008-03-06
I've updated pytmenu to include the following:

New config program, that allows you to change the background colour and whether the programs loop or not.
Updated pytmenu to load above changes from data file
example datafile (light blue background, loop on)

The links are as follows:
[http://www.fillermaterial.co.uk/pytmenu.py](http://www.fillermaterial.co.uk/pytmenu.py)
[http://www.fillermaterial.co.uk/pytconfig.py](http://www.fillermaterial.co.uk/pytconfig.py)
[http://www.fillermaterial.co.uk/pytmenu.dat](http://www.fillermaterial.co.uk/pytmenu.dat)

(i've added these to the first post)

Next plans are as follows:

add ability to add / remove programs and store these in datafile.
Package all of this up.
Add to an svn server so other people can work on this too.

---

### Post by uzusan on 2008-03-06
Another thing to add to the to-do list:

Font changing (including colour).

---

### Post by aimran on 2008-03-27
Good job! Bump for great justice!

Edit: Subscribed too :)

---

### Post by 23meg on 2008-03-27
[QUOTE=uzusan]Add to an svn server so other people can work on this too.[/QUOTE]

How about registering a project at Launchpad instead?

---

