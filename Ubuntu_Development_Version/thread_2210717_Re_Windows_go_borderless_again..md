---
title: "Re: Windows go borderless again."
date: 2014-03-11
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-03-11
> **philinux said:**
> [http://www.omgubuntu.co.uk/2014/03/ubuntu-14-04-introduces-borderless-windows?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2014/03/ubuntu-14-04-introduces-borderless-windows?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

Scroll bar pop up? I was wondering about scrolling and seen this in the comments. The comment would imply that you have a pause before the scroll bar pops up.
Interesting! :) I like normal scrolling and always have to fix that. I wonder if this will be customizable.

---

### Post by mc4man on 2014-03-12
> **Cavsfan said:**
> Scroll bar pop up? I was wondering about scrolling and seen this in the comments. The comment would imply that you have a pause before the scroll bar pops up.
Interesting! :) I like normal scrolling and always have to fix that. I wonder if this will be customizable.
Don't know what that comment is referring to, if 'thumb' it pops up immediately here
When window edge is approached from inside you get thumb 1st., resize 2nd, from outside resize 1st.,  thumb 2nd.
(same 'should' hold true for things like scroll-able sidebars though on occasion the thumb can get in the way..

Overall very pleased 0px borders  returned, was pleasantly surprised when my request went thru Design & implementation so smoothly.

---

### Post by Cavsfan on 2014-03-12
> **mc4man said:**
> Don't know what that comment is referring to, if 'thumb' it pops up immediately here
When window edge is approached from inside you get thumb 1st., resize 2nd, from outside resize 1st.,  thumb 2nd.
(same 'should' hold true for things like scroll-able sidebars though on occasion the thumb can get in the way..

Overall very pleased 0px borders  returned, was pleasantly surprised when my request went thru Design & implementation so smoothly.

I haven't a clue! Thumb must be used on laptops I take it. I've never had a laptop. That might change eventually.
I seen this though:
"As with that older implementation, the change does not affect resizing windows as the “grab area” remains unchanged.

While subtle, the change does improve the appearance of certain applications, such as the GNOME Terminal."

---

### Post by mc4man on 2014-03-12
> **Cavsfan said:**
> I haven't a clue! Thumb must be used on laptops "
No 'thumb' is on overlay scrollbars, see screen for example

---

### Post by Cavsfan on 2014-03-12
> **Cavsfan said:**
> I haven't a clue! Thumb must be used on laptops.

> **mc4man said:**
> No 'thumb' is on overlay scrollbars, see screen for example

Oh thanks for the explanation. That is what I get rid of as soon as I can. :) I prefer normal scrollbars.
Can you still press Cntl+Home to go to the top and Cntl+End to scroll to the bottom using that mode?
I use that feature a lot and it's immediate.

(Of topic but I use Cntl+Page Down a lot to move from tab to tab in browsers.)

[ATTACH=CONFIG]251073[/ATTACH]

---

### Post by mc4man on 2014-03-13
As part of going with 0px borders it seems the shadow radius was also increased, (though not to extent MS once wanted of 54px.

Myself hate large shadows, if wanting to adjust seems to be simple enough in unity.css, for example ambiance - 
/usr/share/themes/Ambiance/gtk-3.0/apps/unity.css
Here have gone pretty small with 8px for active, 5px for inactive - ex.

/```
* Decorations */

UnityDecoration {
    -UnityDecoration-extents: 28px 0 0 0;
    -UnityDecoration-input-extents: 10px;

    -UnityDecoration-shadow-offset-x: 1px;
    -UnityDecoration-shadow-offset-y: 5px;
    -UnityDecoration-active-shadow-color: rgba (0, 0, 0, 0.75);
    -UnityDecoration-active-shadow-radius:[COLOR="#0000CD"] 8px[/COLOR];
    -UnityDecoration-inactive-shadow-color: rgba (0, 0, 0, 0.3);
    -UnityDecoration-inactive-shadow-radius:[COLOR="#0000CD"] 5px[/COLOR];

    -UnityDecoration-glow-size: 10px;
    -UnityDecoration-glow-color: rgb (221, 72, 20);
.....
.....
```

Will have to fool around with some other lines to see what they do, ect.


"Can you still press Cntl+Home to go to the top and Cntl+End to scroll to the bottom using that mode?"
yes

---

### Post by Cavsfan on 2014-03-13
Interesting! You must have forgotten more than I know about this stuff! 
I'm battling a cataract in one eye and reading glasses that are about 8+ years old, but I could be doing worse.

I'll have to check that out one of these days.

Thanks for the info.

---

### Post by mc4man on 2014-03-13
> **Cavsfan said:**
> Interesting! You must have forgotten more than I know about this stuff! 
I'm battling a cataract in one eye and reading glasses that are about 8+ years old, but I could be doing worse.

I'll have to check that out one of these days.

Thanks for the info.
In this regard don't know jack but that's no reason not to experiment. 
I wanted "borderless" back in general but particularly for minimal players like cvlc, mplayer, mpv so that change was a good deal but *for me*  then adding a big shadow sorta killed the clean effect.
So while the above mentioned line toned down the shadows I was still getting a 'drop shadow' at the bottom. That seems to be affected by  the line - 
-UnityDecoration-shadow-offset-y: 5px;
So here I made it 1px & am fairly happy for the moment..

---

### Post by startas on 2014-03-13
Well, there is a problem with it :
1) even if ubuntu has now borderless windows, windows 7 with its massive aero window borders still looks like it has more space, so its not about having more space, its about minimizing linux theming problems. Its like driving a big car in a city with very small parking spots and not caring about it vs being in space without mask and trying to catch every possible molecule of oxygen and never having enough.
2) Having border is great - it looks great, plus you can bind window resize to it, because now window resizing in ubuntu is a mess, in some situations you cant do it...

---

### Post by Cavsfan on 2014-03-14
> **mc4man said:**
> In this regard don't know jack but that's no reason not to experiment. 
I wanted "borderless" back in general but particularly for minimal players like cvlc, mplayer, mpv so that change was a good deal but *for me*  then adding a big shadow sorta killed the clean effect.
So while the above mentioned line toned down the shadows I was still getting a 'drop shadow' at the bottom. That seems to be affected by  the line - 
-UnityDecoration-shadow-offset-y: 5px;
So here I made it 1px & am fairly happy for the moment..

You might not know jack about that but knowing where and how to experiment is a big plus. Maybe one day I'll get there learning from you and others.
I'm glad you got it where you're happy with it. My experience with Trusty keeps getting better all the time. It seems to be working pretty well. :)

> **startas said:**
> Well, there is a problem with it :
1) even if ubuntu has now borderless windows, windows 7 with its massive aero window borders still looks like it has more space, so its not about having more space, its about minimizing linux theming problems. Its like driving a big car in a city with very small parking spots and not caring about it vs being in space without mask and trying to catch every possible molecule of oxygen and never having enough.
2) Having border is great - it looks great, plus you can bind window resize to it, because now window resizing in ubuntu is a mess, in some situations you cant do it...

I haven't had any problem resizing windows since the recent updates. I pretty much live in Flashback w/compiz and it is working impressively.
I just resized terminal and no problem occurred. There is a bit of a black area around the borders while resizing it but that goes away when completed.

It used to choke and I got an apport popup.

I installed Emerald window decorator and here is my terminal:

[ATTACH=CONFIG]251135[/ATTACH]

---

### Post by mc4man on 2014-03-14
> **startas said:**
> Well, there is a problem with it :
.
2) Having border is great - it looks great, plus you can bind window resize to it, because now window resizing in ubuntu is a mess, in some situations you cant do it...
In *Ubuntu* 'border' has nothing to do with resizing. (light-themes
 There is an invisible 10px resize area so resizing has & continues to be quite easy. 
In sessions other than a ubuntu one there may be issues though it's  that session's problem & for  whoever is maintaining it
(sessions that use metacity come to mind

---

