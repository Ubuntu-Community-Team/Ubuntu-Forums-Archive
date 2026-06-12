---
title: "Why is there no GTK theming tool with a GUI?"
date: 2010-02-24
forum: The Cafe
---

### Post by Woolio1 on 2010-02-24
I've noticed that there is no GTK Theming tool with a GUI. There's just the text editor. Why is this? It certainly can't be that difficult to make a GUI frontend for this kind of thing, and it'd help immensely. I know a lot of people who do mock ups and things, but have no idea how to program, so they never realize their designs. This is one of the things, I believe, that keeps Linux a primarily "Geek" OS. It's still mainly "If you want to get anything done, you have to know some code." 

Nothing too fancy, just a basic toolkit, a way to choose patterns and colors and images for the theme. Let it give you a preview or something, so you don't waste time editing, checking, editing, checking, correcting, etc. 

Something like this could be very helpful to many people. It could also help to increase the capabilities of the GTK Window Decorator.

I'm just not sure if it's possible. I assume it is, but I'm not entirely sure. Maybe I should just get my butt in gear and learn how to code... Oh well, something to think about.

---

### Post by deanhopkins on 2010-02-24
Its not exactly what you want, but I feel it could help you, check out gnome-color-chooser (i think its in the repos).

---

### Post by Woolio1 on 2010-02-24
> **deanhopkins said:**
> Its not exactly what you want, but I feel it could help you, check out gnome-color-chooser (i think its in the repos).

Not entirely, but it's a start. Hey, we're dealing with Open Source Software here, why not add a few features, hmm? :D

---

### Post by Islington on 2010-02-24
Uh... editing a text file is easier. After all, it what most web designers do anyways.

Its too bad that the css theme engine is on hiatus; although I see that gnome shell is using css themeing.

---

### Post by Tibuda on 2010-02-24
there's the murrine configurator, i don't really know how it works

---

### Post by Woolio1 on 2010-02-24
> **Islington said:**
> Uh... editing a text file is easier. After all, it what most web designers do anyways.

Its too bad that the css theme engine is on hiatus; although I see that gnome shell is using css themeing.

So you're saying just because somebody doesn't know how to program, they shouldn't be able to do something? 

FOSS is about choice, accessibility, and freedom. If I want to do something, then I should be able to do that. If someone doesn't know how to code, there should be an alternative.

Just like everything else. It seems silly to even consider there is no alternative to Text Editing in this scenario.

---

### Post by Post Monkeh on 2010-02-24
> **Woolio1 said:**
> So you're saying just because somebody doesn't know how to program, they shouldn't be able to do something? 

**FOSS** is about choice, accessibility, and freedom. If I want to do something, then I should be able to do that. If someone doesn't know how to code, there should be an alternative.

Just like everything else. It seems silly to even consider there is no alternative to Text Editing in this scenario.

if you want everything free, sometimes you have to do it yourself

---

### Post by Tibuda on 2010-02-24
Tweak gtkrc (or css) file is not programming.

---

### Post by the yawner on 2010-02-24
Because gtk theme engines have subtle differences, a single tool could not possibly work with each and everyone of them. Murrine did have a configuration tool. Not sure of its current status though.

---

### Post by Gallahhad on 2010-02-24
Something for Metacity would be nice; an Icon Theme Packager would be sweet as well.

---

### Post by Islington on 2010-02-24
> **Woolio1 said:**
> So you're saying just because somebody doesn't know how to program, they shouldn't be able to do something? 

FOSS is about choice, accessibility, and freedom. If I want to do something, then I should be able to do that. If someone doesn't know how to code, there should be an alternative.

Just like everything else. It seems silly to even consider there is no alternative to Text Editing in this scenario.

:popcorn: I cant really say editing a gtk file involves programming. Even so, a text rc file allows the most amount of choice accessibility and freedom. There are plenty of ways to learn how to edit gtkrc files. Its like this: on the one hand you have a powerful tool like the commandline; which has a slight learning curve but in turn makes you independent. Or you could rely on a GUI tool which is easier to learn but makes you reliant on makers of that tool.

Its the difference between a .SVG file and a .AI file.

---

### Post by handy on 2010-02-25
> **Woolio1 said:**
> 
I've noticed that there is no GTK Theming tool with a GUI. There's just the text editor. Why is this? It certainly can't be that difficult to make a GUI frontend for this kind of thing, and it'd help immensely. I know a lot of people who do mock ups and things, but have no idea how to program, so they never realize their designs. This is one of the things, I believe, that keeps Linux a primarily "Geek" OS. It's still mainly "If you want to get anything done, you have to know some code." 

I agree with you completely, almost. ;)

The only thing I disagree with is your statement saying that you need to know some code. As I have found that you can fiddle around in the "gtkrc" file, & get the results you need. (with a little bit of blind luck) Though you do need to know that it exists & where to find it, to start with. 

Messing with the gtkrc is so VERY time consuming & for the vast majority of us, so incredibly tedious.

Most people who have done this would also agree with you. In that we ask the question; why hasn't someone made a GUI that works for ALL GTK front ends?

> **Woolio1 said:**
> 
Nothing too fancy, just a basic toolkit, a way to choose patterns and colors and images for the theme. Let it give you a preview or something, so you don't waste time editing, checking, editing, checking, correcting, etc. 

Yep.

> **Woolio1 said:**
> 
Something like this could be very helpful to many people. It could also help to increase the capabilities of the GTK Window Decorator.

I'm just not sure if it's possible. I assume it is, but I'm not entirely sure. Maybe I should just get my butt in gear and learn how to code... Oh well, something to think about.

I too wonder about the reasons that are stopping programmers from creating this most sought after tool; so many Linux/BSD + users are hanging out for this one? 

Is the reason that this useful & desired tool has not been created due to the fact that there exist a vast array of complications that put developers off?

Perhaps someone who does have a clue about the technicalities of this subject would be so kind as to inform us?  Because so many of us really do need to be informed on this one.

---

### Post by Andreas1 on 2010-02-25
use thewidgetfactory to simultaneously monitor your progress editing the gtkrc file. that's the easiest way i think.

---

