---
title: "Search Box + Transparency"
date: 2006-08-20
forum: Ubuntu System Panel
---

### Post by Eman64 on 2006-08-20
2 quick questions guys

1. Ok when I tried to get rid of the Search box all that happened was the box went away but the space where it was originally is just blank. How do I change this?

2. Ok I've looked at the HOWTO and the directions still make no sense to me. How do you make the USP transparent? Do you need a certain program? And what's up with the Brute Force thing? I tried holding down alt and scrolling and got nothing.

---

### Post by bulldog on 2006-08-20
To get your panel in your own colours hit in gconf-editor 'custom colours'and change the numbers of your colours to what you want.

To get transparacy you must have gset-compiz installed.
Go to tab plugins-> state and select opacity and menu and add it to your list with the desired transparacy.

The clock-plugin is to big for my panel.
When you look at it, you will see movement in the panel next to it.
Not a big issue though.:cool:

---

### Post by delfick on 2006-08-20
> **bulldog said:**
> 
To get transparacy you must have gset-compiz installed.
Go to tab plugins-> state and select opacity and menu and add it to your list with the desired transparacy.

actually, you need xgl and compiz (or aiglx and compiz) first
also gset-compiz is getting outdated......gconf-editor works better...

---

### Post by cptnapalm on 2006-08-20
I hate gconf-editor...  Anything which requires me to use it, will almost certainly result in me either sticking to whatever the current configuration is or not using it at all.

As Windows Registry is to assembler, gconf-editor is to C (with some assembler).

My unasked for .02.

---

### Post by spockrock on 2006-08-20
is there a way to make it wobble, I dunno what window type I should have in my window types to make it wobble??

---

### Post by chanders on 2006-08-21
> **cptnapalm said:**
> I hate gconf-editor...  Anything which requires me to use it, will almost certainly result in me either sticking to whatever the current configuration is or not using it at all.

As Windows Registry is to assembler, gconf-editor is to C (with some assembler).

My unasked for .02.

I agree, that is why there will be a configuration window as soon as time and resources permits...

> **spockrock said:**
> is there a way to make it wobble, I dunno what window type I should have in my window types to make it wobble??

USP is of type Menu, so just add Menu to you list of window types under wobbly and watch it wobble ;-)

---

### Post by spockrock on 2006-08-21
thanks chanders I was about to come in here edit my post, but yes adding Menu as a window type in the wobbly plugin it wobbles again.

---

### Post by Uncle Spellbinder on 2006-08-21
> **spockrock said:**
> thanks chanders I was about to come in here edit my post, but yes adding Menu as a window type in the wobbly plugin it wobbles again.

Sweet!

---

### Post by SlugO on 2006-09-05
So has anyone figured out what the syntax is for setting USP to transparent in this new usability nightmare called CSM? ](*,) 

I think the correct tab is Set Window Attribs by various criteria -> String Lists. I just haven't guessed the right string format yet...

---

### Post by _simon_ on 2006-09-06
In CSM

Set Window Attribs by various criteria -> String Lists

Top box - Window Opacity

Click Add
Set the value to c:Usp:80 (or whatever opacity value you want)

---

### Post by SlugO on 2006-09-06
I also noticed that you can change the application's position from that same tab.

It's a bit annoying that USP doesn't stick to the panel when you start it from a panel that's on top of the screen. It's always separated from it.

If you want it to start itself so that it does stick just add c:Usp:7 to the Position box that's in the same tab as the previously mentioned one.

Although it does move them so that you notice it every time. Atleast if your menus aren't wobbly :)

---

