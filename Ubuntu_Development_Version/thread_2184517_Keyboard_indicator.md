---
title: "Keyboard indicator"
date: 2013-10-29
forum: Ubuntu Development Version
---

### Post by ikt on 2013-10-29
Hi all,

I think the current keyboard indicator sticks out like a sore thumb, and it does so because it goes against all the other indicators, they all have white icon or text and a grey background, compared to the new keyboard indicator which has a white background and grey text.

I understand black text on white background is easier to read, but it's the keyboard indicator, it shouldn't be stealing focus away from the rest of my screen.

I'm just wondering if anyone else thinks so as well?

I've done a quick mockup to compare the 2:

[IMG]https://ikt.id.au/blog/wp-content/uploads/2013/10/current.png[/IMG]

and inverted:

[IMG]https://ikt.id.au/blog/wp-content/uploads/2013/10/inverted.png[/IMG]

Which do you prefer?

---

### Post by xc3RnbFO8P on 2013-10-29
what if the panel is white?
(I prefer inverted)

---

### Post by grahammechanical on 2013-10-29
I accept the point that you are making but I will not vote in this poll for two reasons. 1) Democracy is not the way to change things in Ubuntu. 2) It does not upset me in the way that it upsets you.

I accept Ubuntu as a community gift. I am thankful for all the hard work done in my behalf. There are bigger injustices and much greater suffering happening on this planet to be upset over the development of a computer operating system.

---

### Post by ventrical on 2013-10-29
@Graham..

+1

---

### Post by VinDSL on 2013-10-29
Inverted, definitely...

Unless you feel like playing around with the css file.

That's what I would do, so don't do it.  ;)

---

### Post by VinDSL on 2013-10-29
> **ikt said:**
> I think the current keyboard indicator sticks out like a sore thumb, and it does so because it goes against all the other indicators[...]
That's my sentiment, exactly, about the workspace app indicator extension in GS Staging -- I love the extension, but hate the indicator.

Example (top-right, above conky)...

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-29-oct-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-29-oct-2013-2.png")[/INDENT]


I don't know if you've ever used GS, but the default workspace indicator is hideous, just like your 'current' indicator.

The way I 'fixed' it was to tweak the css file -- in my case '/usr/share/gnome-shell/extensions/workspace-indicator@gnome-shell-extensions.gcampax.github.com/stylesheet.css'.  Now it's tolerable, although hardly stylish (you should see the original).

I'm assuming the look n' feel of your app indicator is controlled by a style-sheet too... yes?

If so, you could make it look any way you want.  ;)

Personally, I'd put a grayish frame around the 'inverted' indicator, and call it a day...

---

### Post by xc3RnbFO8P on 2013-10-29
Aha screenshots  :)

[[img]http://farm4.staticflickr.com/3790/10563456375_5e391a5f8d_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/10563456375/)
[Screenshot from 2013-10-29 22:55:34](http://www.flickr.com/photos/96052779@N07/10563456375/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by VinDSL on 2013-10-29
> **Ringi said:**
> Aha screenshots  :)
Heh!  After voting, and taking the exit poll (so to speak) I didn't want to appear to be mocking the OP.

Sadly, sometimes a pic is worth 1000 words, you know?  Your 'tongue', on the other hand, is what sinks you.  Based on the comments, I think the OP was taken the wrong way.

Anyway, there are several app indicators I won't run, simply because I cannot stand the button -- and, it's not worth the effort to 'fix' them, every time there is a package upgrade -- so, I don't run them at all.

The ones that I deem paramount, I tweak.

I'm not trying to force change.  I can make Ubuntu look any way I want, and so can the OP.

The pic was to exemplify the concept -- that's all.    ;)

---

### Post by xc3RnbFO8P on 2013-10-29
> Unless you feel like playing around with the css file.
 icons are easier maybe ?
> Sadly, sometimes a pic is worth 1000 words, you know? Your 'tongue'
my point exactly :)

---

### Post by mc4man on 2013-10-29
Not sure if he was taken wrong or something else not worth mentioning
Any the OP is correct, looks out of place, certainly in a default install
Whether it's a big or little job to 'fix', no idea, there are 551 .svg's involved though again no clue as why so many are needed per lang. 
(Ex. there are 33 En ones, indicator-keyboard-En.svg being the one used by default here 
(I get rid of as no use anyway .

---

### Post by philinux on 2013-10-30
My personal preference is no keyboard indicator.

[http://ubuntuforums.org/showthread.php?t=2182038&p=12826792&viewfull=1#post12826792](http://ubuntuforums.org/showthread.php?t=2182038&p=12826792&viewfull=1#post12826792)

---

### Post by ikt on 2013-10-30
> **grahammechanical said:**
> I accept the point that you are making but I will not vote in this poll for two reasons. 1) Democracy is not the way to change things in Ubuntu. 2) It does not upset me in the way that it upsets you.

I understand it doesn't affect some people, hence the option 'meh'.

I work in design, I felt the button was misplaced amongst its colleagues and I'm checking to see if anyone else feels the same way before I redo the icon properly and submit a bug.

> **Ringi said:**
> Aha screenshots  :)

Would you say the icon fits in with the rest of them? I'm not sure if it's because it's being pressed or because the whole theme is greyscale (which is awesome :D) but it doesn't look as thumbstickouty to me.

> **VinDSL said:**
> Heh!  After voting, and taking the exit poll (so to speak) I didn't want to appear to be mocking the OP.

It's depressing for me to read because [canonical hired Matthieu James (Faenza Icon set creator) to work on the icons]("http://www.omgubuntu.co.uk/2012/10/canonical-hire-faenza-designer-to-work-on-new-ubuntu-icon-set"), he's one of the best in the linux industry, so I don't know how this could happen.

> **mc4man said:**
> Not sure if he was taken wrong or something else not worth mentioning
Any the OP is correct, looks out of place, certainly in a default install

Yeah it does look out of place, glad I'm not the only one :)

I got rid of it, but I think if it was less out of place I'd be less inclined to get rid of it, for example I never use the mail/social media applet or the switch user applet, but I have no inclination to remove them as opposed to the keyboard one which I immediately noticed.

---

### Post by mc4man on 2013-10-30
> **ikt said:**
> I understand it doesn't affect some people, hence the option 'meh'.

I work in design, I felt the button was misplaced amongst its colleagues and I'm checking to see if anyone else feels the same way before I redo the icon properly and submit a bug.


It would be nice to see an example of a redone one, would also be curious how it would look if the panel opacity is lowered. 
To me the best would just show 2 letters with a trans background
For testing on En the one .svg I mentioned is used

---

### Post by xc3RnbFO8P on 2013-10-30
Looks so much better in Gnome Shell

[[img]http://farm8.staticflickr.com/7324/10578426385_603a49c3d8_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/10578426385/)
[Keyboard Indicator 01](http://www.flickr.com/photos/96052779@N07/10578426385/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by VinDSL on 2013-10-30
> **ikt said:**
> I work in design, I felt the button was misplaced amongst its colleagues and I'm checking to see if anyone else feels the same way before I redo the icon properly and submit a bug.[...]

It's depressing for me to read because [canonical hired Matthieu James (Faenza Icon set creator) to work on the icons]("http://www.omgubuntu.co.uk/2012/10/canonical-hire-faenza-designer-to-work-on-new-ubuntu-icon-set"), he's one of the best in the linux industry, so I don't know how this could happen.
Yes, his work is quite popular.  Following mc4man's lead, we'll leave it at that.

My favorite icon theme is 'Clarity-mono-light' -- been using it for several months, which is unheard of, for me.  I'm a restless creature.

Maybe you should contact Matthieu James directly...  ;)

---

### Post by mc4man on 2013-10-30
I was thinking more along the lines like this, shot from a guest session

---

### Post by ikt on 2013-10-31
> **mc4man said:**
> I was thinking more along the lines like this, shot from a guest session

That's it! That's what it should be. Spot on!

---

### Post by QDR06VV9 on 2013-10-31
> **grahammechanical said:**
> I accept the point that you are making but I will not vote in this poll for two reasons. 1) Democracy is not the way to change things in Ubuntu. 2) It does not upset me in the way that it upsets you.

I accept Ubuntu as a community gift. I am thankful for all the hard work done in my behalf. There are bigger injustices and much greater suffering happening on this planet to be upset over the development of a computer operating system.

Nicely Put 
Count me there also.(thankful for all the hard work done in my behalf)

---

### Post by ikt on 2013-10-31
> **runrickus said:**
> Nicely Put 
Count me there also.(thankful for all the hard work done in my behalf)

Yeah I agree.

---

### Post by mc4man on 2013-10-31
> **ikt said:**
> That's it! That's what it should be. Spot on!

What I know about svg's could fit on the head of a pin so likely below is not proper. I decided to open the svg in a text editor & it seemed fairly simple as there were only 3 colors 'defined'. 
So i changed this
```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<svg width="22" xmlns="http://www.w3.org/2000/svg" version="1.1" height="22">
 <defs>
  <mask id="m">
   <rect y="0" x="0" style="fill:#fff" height="22" width="22"/>
   <text y="15.5" x="4" style="font-size:12;font-family:Ubuntu;font-weight:500;fill:black">En</text>
  </mask>
 </defs>
 <rect style="fill:#dfdbd2" mask="url(#m)" rx="2" height="20" width="20" y="1" x="1"/>
</svg>
```
to this, no clue if "none" is proper, only that it logically  described  what I wanted...??

```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<svg width="22" xmlns="http://www.w3.org/2000/svg" version="1.1" height="22">
 <defs>
  <mask id="m">
   <rect y="0" x="0" style="fill:none" height="22" width="22"/>
   <text y="15.5" x="4" style="font-size:12;font-family:Ubuntu;font-weight:500;fill:white">En</text>
  </mask>
 </defs>
 <rect style="fill:white" mask="url(#m)" rx="2" height="20" width="20" y="1" x="1"/>
</svg>
```

---

