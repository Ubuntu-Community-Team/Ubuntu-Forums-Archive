---
title: "shot in the dark, web design off topic question"
date: 2007-06-15
forum: The Cafe
---

### Post by silent1643 on 2007-06-15
figured i would try here since this community has such awesome users..

soo.. does anybody know how to embed sound in a webpage, on mouseover, that will work with firefox and IE? Apparently javascript crashes firefox, in my case at least, and IE tries to play it in quicktime lol... just wondering if there was another option other than flash.

---

### Post by ThinkBuntu on 2007-06-15
> **silent1643 said:**
> figured i would try here since this community has such awesome users..

soo.. does anybody know how to embed sound in a webpage, on mouseover, that will work with firefox and IE? Apparently javascript crashes firefox, in my case at least, and IE tries to play it in quicktime lol... just wondering if there was another option other than flash.
Why on earth would anyone need this? If you're building some little web toy that makes noises when a cursor hovers a button, you're better off using Flash.

---

### Post by Warpnow on 2007-06-15
Hrm, never done it on mouseover but I would think it could be done with simply html...

bleh, its 7:20 and I'm still up, haha, if I were less tired I'd hunt around for you...

---

### Post by Warpnow on 2007-06-15
> **ThinkBuntu said:**
> Why on earth would anyone need this? If you're building some little web toy that makes noises when a cursor hovers a button, you're better off using Flash.


Unless you'd prefer spend 15 minutes on it rather than 15 hours and want it to be easily updatable, maybe even by the users...

---

### Post by silent1643 on 2007-06-15
> **ThinkBuntu said:**
> Why on earth would anyone need this? If you're building some little web toy that makes noises when a cursor hovers a button, you're better off using Flash.

well to make a long story shot, i am basically fixing the current menu we have on our e-commerce site. It is flash right now, and if it were up to me i would get rid of the sounds and use a moo.fx style accordion menu but the sounds are part of the agreement when the website was contracted and from what i have been told they cannot be removed because they were already paid for and it might cause some problems. So in light of my discussions on trying to get rid of the sounds i am simply left with just trying to make the menu not overlap content as it does now. :D

---

### Post by ThinkBuntu on 2007-06-15
> **silent1643 said:**
> well to make a long story shot, i am basically fixing the current menu we have on our e-commerce site. It is flash right now, and if it were up to me i would get rid of the sounds and use a moo.fx style accordion menu but the sounds are part of the agreement when the website was contracted and from what i have been told they cannot be removed because they were already paid for and it might cause some problems. So in light of my discussions on trying to get rid of the sounds i am simply left with just trying to make the menu not overlap content as it does now. :D
Explain to them that adding sounds like this will in increase bandwidth and load times, and that it does nothing from the point of view of the end user who just wants to purchase the product, and most likely has sound turned off.

---

### Post by koenn on 2007-06-15
I agree that a menu that makes noise is a useless gimmick that will annoy most of the users, but I had a look around and found this : 

[http://www.phon.ucl.ac.uk/home/mark/audio/play.htm](http://www.phon.ucl.ac.uk/home/mark/audio/play.htm)

#3 sure looks useful for what you're trying to do

---

### Post by init1 on 2007-06-15
> **silent1643 said:**
> figured i would try here since this community has such awesome users..

soo.. does anybody know how to embed sound in a webpage, on mouseover, that will work with firefox and IE? Apparently javascript crashes firefox, in my case at least, and IE tries to play it in quicktime lol... just wondering if there was another option other than flash.

Javascript does not crash firefox. This page has javascript in it. Mouseovers are easy, 
```
<img scr="www.someurl.com" onmouseover="somecode">
```
But sound in FF is not. 
[http://www.scriptwell.net/howtoplaysound.htm]("http://www.scriptwell.net/howtoplaysound.htm")
I googled and found this. Try it.

---

