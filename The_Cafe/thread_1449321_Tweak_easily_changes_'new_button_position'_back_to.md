---
title: "Tweak easily changes 'new button position' back to normal."
date: 2010-04-07
forum: The Cafe
---

### Post by Rasa1111 on 2010-04-07
hey , 

Im not sure if this has been posted ( but probably has) lol
If so, please just delete. 

 But I recall all the commotion about the "buttons being switched to the left"
and what a big deal it was, (even though it was apparently easy enough to switch in gedit ...or whatever) lol

  Today I decided to change my theme in karmic 
to the new Lucid Theme and Icon set. 
and I really didn't mind the buttons being on the left, 
however, 
I was just playing around in tweak, 
and noticed that there is an option to switch the buttons into any positions you want them. 
 
 It is very easy, even for  a newb like meself.  lol
 Here:  Window Titlebar Button layout~


So, maybe this is useless to the pros, 
maybe it's useless to everyone, I dunno. 
 But I thought it was pretty sweet, 
and even sweeter that it worked!! :lol:

 No more 'buttons on the left side' commotion needed! lol
  :KS

 again, please delete if this will just be taking up bandwidth and this is something everyone knows already. lol

 peace

---

### Post by J V on 2010-04-07
Image.size > text.size:
```
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:shade,minimize,maximize,close"
```Post in the support forums so I get beans for this lol :D

---

### Post by chris4585 on 2010-04-07
Thats neat, but in the time it takes to download and install ubuntu tweak, someone could change the order many times with a single command.

```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```

---

### Post by Rasa1111 on 2010-04-07
good to know, thanks. :)

i agree, that is much faster, given one doesnt already have tweak.
but some newbs would be afraid to even put that into the terminal. lol
(some i know anyway) :lol:

but hey, 
lots of people do have tweak,
(and im betting many of them are n00bs!) lol

 but it is good to learn the commands, so thank you, 
much appreciated. 

 to be honest though, 
 If I hadnt noticed that option in tweak,
 I wouldnt have even bothered switching them,
 I was figuring ill prolly have to get used to it sometime eh? lol
but..... now that it is back to 'normal'... i do think i prefer it this way. 

 thanks again. 
n00bch1ld.  :lol:

---

### Post by mcduck on 2010-04-07
> **Rasa1111 said:**
> good to know, thanks. :)

i agree, that is much faster, given one doesnt already have tweak.
but some newbs would be afraid to even put that into the terminal. lol
(some i know anyway) :lol:

Then they can just use the gconf-editor, simple graphical tool for editing gconf settings (_all_ of them) and installed by default. ;)

---

### Post by juancarlospaco on 2010-04-07
The *"Normal"* position for you maybe is not the normal for all...

---

### Post by Rasa1111 on 2010-04-07
i know, my friend..
but that can also be quite confusing to complete n00bs/ window$ refugees. lol

ive been able to edit and change many things using gconf editor, 
and also many things ive tried that havent seemed to work, or i cant seem to quite figure out.. lol

 going by the majority of ubuntu/linux newbs i know at the moment..
i am sure that many of them are not even close to as comfortable as i am yet...
and i really only know the basic basics. lol

 good tip tho.  thanks! :)

---

### Post by Rasa1111 on 2010-04-07
> **juancarlospaco said:**
> The *"Normal"* position for you maybe is not the normal for all...

 that is why i put "normal" in quotes, in a later post..
i know that 'normal' is relative.
not absolute. :KS

i thought about changing the title to quote it also, but eh. lol
 just trying to help out any other n00bs!

---

### Post by mcooke1 on 2010-04-07
I use Tweak I think it's good, but I will not use it to move the buttons because they have been moved for a reason, apparently to make way for something new may as well get used to them where they are.

---

### Post by nmccrina on 2010-04-08
> **juancarlospaco said:**
> The *"Normal"* position for you maybe is not the normal for all...

What I want to know is, how would buttons-on-the-left become *normal* for anyone? I've used Windows since Windows 95, OpenSolaris, and many flavours of Linux (never a Mac, though) and I don't recall ever seeing this before. I'm not saying you're wrong if you prefer it or anything, I'm just genuinely interested in where this came from. This isn't original GUI engineering from Ubuntu, is it?

---

### Post by mcduck on 2010-04-08
> **nmccrina said:**
> What I want to know is, how would buttons-on-the-left become *normal* for anyone? I've used Windows since Windows 95, OpenSolaris, and many flavours of Linux (never a Mac, though) and I don't recall ever seeing this before. I'm not saying you're wrong if you prefer it or anything, I'm just genuinely interested in where this came from. This isn't original GUI engineering from Ubuntu, is it?

well, perhaps the person in question would have used a Mac... or BeOS, RiscOS and many others, that all either have all the buttons on left, or some on left and some on right.

Actually even many Linux window managers have a bunch of buttons on the left side as well as on the right side.

edit: actually, now that I think about it, even Windows 3.11 had the close button on left side and minimize/maximize on right side... Windows 95 was the first version to have all the buttons on the right. ;)

---

### Post by Rasa1111 on 2010-04-08
> edit: actually, now that I think about it, even Windows 3.11 had the close button on left side and minimize/maximize on right side... Windows 95 was the first version to have all the buttons on the right. :wink:

 haha :lol:
surprise! 

again, window$ is the culprit. lol

good to know mcduck, thanks. :)

---

### Post by chris4585 on 2010-04-08
Yes, indeed there is a reason behind the movement of the controls.  I'm sure it will be interesting, but for now I will move my controls back on the right like probably a few thousand will do.  When the reason shows up I may keep it if its good enough.  I'm sure there will be people trying to revert back to the way it originally was too even then.

---

### Post by Penguin Guy on 2010-04-16
> **nmccrina said:**
> What I want to know is, how would buttons-on-the-left become *normal* for anyone? I've used Windows since Windows 95, OpenSolaris, and many flavours of Linux (never a Mac, though) and I don't recall ever seeing this before. I'm not saying you're wrong if you prefer it or anything, I'm just genuinely interested in where this came from. This isn't original GUI engineering from Ubuntu, is it?
It was introduced by Mac under the reasoning that most of it's target audience read from left to right. Therefore having the buttons on the leftmost part of the window would make them easier to use.

---

### Post by Penguin Guy on 2010-04-16
For those that don't want to go through the trouble of installing Ubuntu Tweak; I've made a post with info on various commands you can use to change the layout to whatever you want, I've also added a link to this post. The guide is [here]("http://ubuntuforums.org/showthread.php?p=9126578") if anyone is interested.

---

### Post by Rasa1111 on 2010-04-16
> **Penguin Guy said:**
> For those that don't want to go through the trouble of installing Ubuntu Tweak; I've made a post with info on various commands you can use to change the layout to whatever you want, I've also added a link to this post. The guide is [here]("http://ubuntuforums.org/showthread.php?p=9126578") if anyone is interested.

 really niice, thanks man! :KS

---

