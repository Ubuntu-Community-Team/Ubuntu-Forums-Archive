---
title: "Photoshop and WINE"
date: 2007-11-24
forum: Virtualisation
---

### Post by jmagick07 on 2007-11-24
When I try to install Photoshop using WINE, it says I don't have "JScript" (or something like that).

I've seen online tutorials on getting Photoshop on Ubuntu, but all the ones I've seen just talk about pushing Photoshop from your Windows partition to your Linux partition.

I don't have Windows at all, just Ubuntu Linux on this computer. I can't do what I've seen in those tutorials.

How can I install Photoshop on Linux?  What is this "JScript" thing it keeps complaining about?  How can I get this "JScript" thing?  What do I do?  Help? :confused:

---

### Post by SonicSteve on 2007-11-24
I know you can install java on Ubuntu, I would guess that it is asking for Java script. I don't know if that will help but it's a start.

---

### Post by cooljdude on 2007-11-24
Yeah, JScript means Javascript.

---

### Post by jmagick07 on 2007-11-24
Why would Photoshop complain about no JavaScript when trying to install?
JavaScript is scripting for browsers, not applications (I think).

---

### Post by SonicSteve on 2007-11-24
Did you try it? Who knows why it needs it, but it sure seems to. The real question is whether or not installing the Java environment in Ubuntu will have any effect on wine. I'm no wine expert so I don't know if Ubuntu's environment will have any effect on the virtual wine environment. Either way it's worth trying as a first step.

---

### Post by dpj23 on 2007-11-25
Running Photoshop using wine may not be a good thing:

[http://bugs.winehq.org/buglist.cgi?quicksearch=photoshop](http://bugs.winehq.org/buglist.cgi?quicksearch=photoshop)

check out the bugs listed for this program...

---

### Post by FrankVdb on 2007-11-26
Wine is no virtualisation software. If your PC is powerful enough, try VirtualBox or VMWare.

---

### Post by SunnyRabbiera on 2007-11-26
yeh give installing java a shot...
I have no idea why you got that error but installing photoshop is relatively fair in wine.

---

### Post by koenn on 2007-11-26
javascript is a scripting language which, apart from some syntax and vocabulary similarities to Java, has nothing to do with Java itself. Nothing. jscript is yet another scripting language that looks a lot like javascript, but isn't identical to it. You can think of jscript as Microsofts Incompatible Javascript. 

just a hunch : maybe photoshop expects to find Windows Scripting Host - a multi-language script parser/interpreter/engine that's present on every Windows system since win98.
Why Photoshop would want that, or jscript, is beyound me.

---

### Post by eagledrc on 2008-01-03
I have this same problem.  It has a simple solution: install jscript on ubuntu.  Can it be installed through wine or regardless of wine?  We should be able to install jscript on ubuntu.  Someone has gotta know how...

---

### Post by eagledrc on 2008-01-04
I have a breakthrough.
[http://kb.adobe.com/selfservice/viewContent.do?externalId=kb401521&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb401521&sliceId=1)
That is the exact same problem that we are having.  The only thing is, how does that apply to linux?

---

### Post by eagledrc on 2008-01-04
Okay...
I registered jscript.dll on the wine part of drive c just like adobe said for vista.
It did something, because when I click to install CS3, the dialog disappears instead of giving me the error message..but we are still stuck.

---

### Post by UbuWu on 2008-01-05
CS2 works better under wine.

---

### Post by newbie2 on 2008-02-18
> **dpj23 said:**
> Running Photoshop using wine may not be a good thing:

[http://bugs.winehq.org/buglist.cgi?quicksearch=photoshop](http://bugs.winehq.org/buglist.cgi?quicksearch=photoshop)

check out the bugs listed for this program...
[http://google-opensource.blogspot.com/2008/02/google-sponsors-wine-improvements.html](http://google-opensource.blogspot.com/2008/02/google-sponsors-wine-improvements.html)
:rolleyes:;)

---

