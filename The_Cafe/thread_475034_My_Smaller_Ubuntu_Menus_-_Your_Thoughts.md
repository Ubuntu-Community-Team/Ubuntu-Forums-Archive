---
title: "My Smaller Ubuntu Menus - Your Thoughts?"
date: 2007-06-15
forum: The Cafe
---

### Post by Old Pink on 2007-06-15
[[IMG]http://www.mbhoy.com/wp-content/uploads/mfimg/neatersmall.jpg[/IMG]]("http://www.mbhoy.com/wp-content/uploads/mfimg/neater.jpg")
[LEFT]*Click to Enlarge*

[http://www.mbhoy.com/15-06-2007/smaller-neater-menus-in-ubuntu](http://www.mbhoy.com/15-06-2007/smaller-neater-menus-in-ubuntu) (how-to & info)

What do _you_ think? I personally really like it, and think it's a fair improvement, once your menus get cluttered, it literally halves the size of them without the need for sorting into confusing folders. 

I'm keeping them, for now. Certainly an improvement in my eyes. :) 

[Digg it!]("http://www.digg.com/linux_unix/HowTo_Smaller_neater_menus_in_Ubuntu") (please?) 
[/LEFT]

---

### Post by juxtaposed on 2007-06-15
Certainly a good idea if I ever get too many programs to fit.

---

### Post by diskotek on 2007-06-15
well, i can't see any difference, but i'll try it :D

---

### Post by zeeR on 2007-06-15
That's nice, can be really helpful for those with lots of Applications on the menu ;)

I dugg your article!

---

### Post by Tundro Walker on 2007-06-15
I don't notice any difference between your screenshot and the menu's I'm currently using.  What exactly did you do...reduce the height each takes up, or the width of the overall menus that pan out?

---

### Post by Old Pink on 2007-06-15
> **Tundro Walker said:**
> I don't notice any difference between your screenshot and the menu's I'm currently using.  What exactly did you do...reduce the height each takes up, or the width of the overall menus that pan out?

Half the icon size, from 32x32 to 16x16 px, and the text adjusts accordingly. :) 

[B]Original:
[/B][IMG]http://www.ubuntu.com/files/u3/helpmenu.png[/IMG]

[B]New:
[/B][IMG]http://img156.imageshack.us/img156/308/42286210wc8.png[/IMG]

You can't tell me there's not a significant size difference? ;)

---

### Post by Old Pink on 2007-06-16
I understand the modification wasn't working for some people, due to wordpress changing the " symbols. I've worked around this problem, and the modification should work for anyone now.

Regards & Apologies :)

---

### Post by zeeR on 2007-06-20
Your site is down... And by using the procedure on the Google cache, it doesn't work...Why don't you post it here??

---

### Post by BuffaloX on 2007-06-20
Looks cool

But the link doesn't work.

---

### Post by DC@DR on 2007-06-20
Yes, it looks promising, but the site is down atm :-s

---

### Post by dptxp on 2007-06-20
Here I have only reduced the font size.

---

### Post by BarfBag on 2007-06-20
I'd like to try this.  But your site is down.

---

### Post by zeeR on 2007-06-20
If someone knows how to do this, please help us!

---

### Post by Old Pink on 2007-06-20
Sorry guys, host went bust, spent time moving it around, back on track with GoDaddy now, all should be working on the big name? :)

---

### Post by picpak on 2007-06-20
Is there any reason you need to run sudo gedit, etc and whatnot? I mean, this guide can be reduced to one step:

```
wget http://www.mbhoy.com/wp-content/uploads/mfimg/gtkrc_mine.txt | mv gtkrc_mine.txt .gtkrc.mine
```

Other than that, looking good!

---

### Post by Old Pink on 2007-06-21
Thanks picpak, never thought of it like that, updated the guide. :) 

Anyone who tried the modification before 21/06/07 and saw it fail could try chmodding the file to 666, so it's used at log in, without root access, as explained here: [http://www.mbhoy.com/15-06-2007/smaller-neater-menus-in-ubuntu#comment-513](http://www.mbhoy.com/15-06-2007/smaller-neater-menus-in-ubuntu#comment-513)

---

### Post by BuffaloX on 2007-06-21
This is really cool

However I had to apply the changes to the file: 
**.gtkrc-2.0**
to make it work

---

### Post by Old Pink on 2007-06-21
> **BuffaloX said:**
> This is really cool

However I had to apply the changes to the file: 
**.gtkrc-2.0**
to make it work

[http://www.mbhoy.com/15-06-2007/smaller-neater-menus-in-ubuntu#comment-517](http://www.mbhoy.com/15-06-2007/smaller-neater-menus-in-ubuntu#comment-517)

Posted it in a comment, thanks BuffaloX. :)

---

### Post by matthinckley on 2007-06-21
awesome.. my System >> Preferences menu was too long for my screen.. this fixed it! thanks!

---

### Post by forrestcupp on 2007-06-21
The problem is that your screenshot isn't a full screen.  It's pretty hard to tell a difference in size when you don't have the reference of how big the complete screen is.  Just from looking at your screenshot, I had no idea what you did, until I read through the thread.

I suggest updating the screenshot with a picture that shows your full screen as a reference.

---

### Post by Old Pink on 2007-06-22
> **matthinckley said:**
> awesome.. my System >> Preferences menu was too long for my screen.. this fixed it! thanks!
Glad to see it worked well for someone. :) 
> **forrestcupp said:**
> The problem is that your screenshot isn't a full screen.  It's pretty hard to tell a difference in size when you don't have the reference of how big the complete screen is.  Just from looking at your screenshot, I had no idea what you did, until I read through the thread.

I suggest updating the screenshot with a picture that shows your full screen as a reference.
Interesting. I'll get a full screenshot up, but you're the only one to mention this, the other problems have been with applying the modification, not seeing the initial change.

Did the mod work for you? :)

---

### Post by Old Pink on 2007-06-24
The mod may need to be re-applied when switching themes, or applied to different files when switching themes, as mentioned in the comments section of that post, as I noticed today. :)

---

