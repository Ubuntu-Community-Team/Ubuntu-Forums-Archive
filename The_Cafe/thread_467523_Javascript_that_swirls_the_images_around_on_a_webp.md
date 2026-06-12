---
title: "Javascript that swirls the images around on a webpage"
date: 2007-06-07
forum: The Cafe
---

### Post by Clay_Banger on 2007-06-07
i have seen it around, its a bunch of JavaScript code that when added on the the end of the url, plays around with all of the images on the webpage. Ive had a google for it, but i cant seem to find it.
anyone know what im talking about and where i could find it?

---

### Post by FuturePilot on 2007-06-07
I know exactly what you're talking about. I'll be right back:p

---

### Post by FuturePilot on 2007-06-07
```
javascript:R=0; x1=.1; y1=.05; x2=.25; y2=.24; x3=1.6; y3=.24; x4=300; y4=200; x5=300; y5=200; DI=document.getElementsByTagName("img"); DIL=DI.length; function A(){for(i=0; i-DIL; i++){DIS=DI[ i ].style; DIS.position='absolute'; DIS.left=(Math.sin(R*x1+i*x2+x3)*x4+x5)+"px"; DIS.top=(Math.cos(R*y1+i*y2+y3)*y4+y5)+"px"}R++}setInterval('A()',50); void(0);
```
There you go. Go back to the Cafe and try it. It's kind of funny. All the envelopes go flying around:D

---

### Post by Clay_Banger on 2007-06-07
> **FuturePilot said:**
> I know exactly what you're talking about. I'll be right back:p
Swweeeeeeet!:D

---

### Post by Clay_Banger on 2007-06-07
> **FuturePilot said:**
> ```
javascript:R=0; x1=.1; y1=.05; x2=.25; y2=.24; x3=1.6; y3=.24; x4=300; y4=200; x5=300; y5=200; DI=document.getElementsByTagName("img"); DIL=DI.length; function A(){for(i=0; i-DIL; i++){DIS=DI[ i ].style; DIS.position='absolute'; DIS.left=(Math.sin(R*x1+i*x2+x3)*x4+x5)+"px"; DIS.top=(Math.cos(R*y1+i*y2+y3)*y4+y5)+"px"}R++}setInterval('A()',50); void(0);
```
There you go. Go back to the Cafe and try it. It's kind of funny. All the envelopes go flying around:D

Thats just what i wanted!! thanks!

---

### Post by FuturePilot on 2007-06-07
Watch out for the flying thumb tacks :lolflag:

---

### Post by Clay_Banger on 2007-06-07
nah, i think that paper cuts maybe more of a problem.. :smile:

---

### Post by knopper67 on 2007-06-07
This Sounds Interesting, How do I Make the Images fly around?

---

### Post by Clay_Banger on 2007-06-08
> **knopper67 said:**
> This Sounds Interesting, How do I Make the Images fly around?
you visit a webpage, preferably one with lots of pictures on it, then in the url bar you remove what is in there and  paste the javascript code above into it, and what the images swirl..

---

### Post by FuturePilot on 2007-06-08
Make sure you hit Enter. Clicking the go button doesn't work. Took me forever to figure that out:p

---

### Post by RAV TUX on 2007-06-08
Thanks this is really fun, know of any other java scripts?

screenshot:

---

### Post by RAV TUX on 2007-06-08
> **RAV TUX said:**
> Thanks this is really fun, know of any other java scripts?

screenshot:another screenshot

---

### Post by FuturePilot on 2007-06-08
ROFL. Try this one. It makes your browser window go crazy:D My avatar has gone flying around:lolflag:
```
javascript:function Shw(n) {if (self.moveBy) {for (i = 35; i > 0; i--) {for (j = n; j > 0; j--) {self.moveBy(1,i) ;self.moveBy(i,0);self.moveBy(0,-i);self.moveBy(-i,0); } } }} Shw(6)
```

---

### Post by RAV TUX on 2007-06-08
> **FuturePilot said:**
> ROFL. Try this one. It makes your browser window go crazy:D My avatar has gone flying around:lolflag:
```
javascript:function Shw(n) {if (self.moveBy) {for (i = 35; i > 0; i--) {for (j = n; j > 0; j--) {self.moveBy(1,i) ;self.moveBy(i,0);self.moveBy(0,-i);self.moveBy(-i,0); } } }} Shw(6)
```

funny thanks I need one of those every once in a while. ;)

---

### Post by Clay_Banger on 2007-06-08
> **FuturePilot said:**
> ROFL. Try this one. It makes your browser window go crazy:D My avatar has gone flying around:lolflag:
```
javascript:function Shw(n) {if (self.moveBy) {for (i = 35; i > 0; i--) {for (j = n; j > 0; j--) {self.moveBy(1,i) ;self.moveBy(i,0);self.moveBy(0,-i);self.moveBy(-i,0); } } }} Shw(6)
```
just moves the window to the right a small bit... is it supposed to do something else?

---

### Post by RAV TUX on 2007-06-08
> **Clay_Banger said:**
> just moves the window to the right a small bit... is it supposed to do something else?

should shake it up also

---

### Post by FuturePilot on 2007-06-08
It should also make it vibrate like crazy.

---

### Post by Clay_Banger on 2007-06-08
turned off beryl, it works now. :lolflag:

---

### Post by Dragonbite on 2007-06-08
Oh, these are funny!  Gotta see about fitting them into some of the websites I'm working one (for unsuspecting browsers ... ;) )

---

