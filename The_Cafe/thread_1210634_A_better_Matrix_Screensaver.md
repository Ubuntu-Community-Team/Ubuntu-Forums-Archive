---
title: "A better Matrix Screensaver"
date: 2009-07-11
forum: The Cafe
---

### Post by racerraul on 2009-07-11
I use [[COLOR="YellowGreen"]this screensaver[/COLOR]]("http://www.geocities.com/matrixscr1/") in my Xp laptop that I use for work (I know I am working on it, unfortunately there is lots ActiveX BS on Co's the intranet, cry me a river!!!)

Anyways, I tried to use that windows .scr file in Ubuntu and failed miserably as a screensaver...

Wondering if there is anyone on board looking for a pet project for an xscreensaver equivalent.

I already have all the Matrix screensavers I could find for xscreensaver... IMO they all pale in comparison to that .scr file... you must see it to understand how much diff it is...

At the moment I am using xMatrix and it does not compare...

---

### Post by bodyharvester on 2009-07-11
that would make THE most amazing desktop

if anyone does discover something like that, do tell me, thanks

---

### Post by racerraul on 2009-07-11
Didn't even think about that... that would indeed roxxor.

---

### Post by CJ Master on 2009-07-11
I tried it... Imo the 3D matrix one included in ubuntu is much better.

---

### Post by Wiebelhaus on 2009-07-11
> **CJ Master said:**
> I tried it... Imo the 3D matrix one included in ubuntu is much better.

I agree!

---

### Post by jrusso2 on 2009-07-11
GL Matrix is about the best one, I think its also called matrixview GL

---

### Post by racerraul on 2009-07-11
> **CJ Master said:**
> I tried it... Imo the 3D matrix one included in ubuntu is much better.

I think that's GLMatrix... I have that too.

Too each its own... I think it sucks.  I't be ok if I could get it to stop zooming in.  Can only get the tilt to stop.

---

### Post by ghindo on 2009-07-11
> **racerraul said:**
> I think that's GLMatrix... I have that too.

Too each its own... I think it sucks.  I't be ok if I could get it to stop zooming in.  Can only get the tilt to stop.How do you configure it to stop the tilt?

---

### Post by racerraul on 2009-07-11
> **ghindo said:**
> How do you configure it to stop the tilt?

I have waves & panning disabled... don't remember which stops the tilt.

---

### Post by Yownanymous on 2009-07-11
Dunno about screensavers, but this should work cross-platform: [http://dissoluteproductions.com/desktops.php](http://dissoluteproductions.com/desktops.php)

---

### Post by racerraul on 2009-07-11
> **Yownanymous said:**
> Dunno about screensavers, but this should work cross-platform: [http://dissoluteproductions.com/desktops.php](http://dissoluteproductions.com/desktops.php)

cool concept... but 800x600 only support? :(

---

### Post by CJ Master on 2009-07-11
> **racerraul said:**
> I think that's GLMatrix... I have that too.

Too each its own... I think it sucks.  I't be ok if I could get it to stop zooming in.  Can only get the tilt to stop.

If you don't like the 3d aspect of it, there's also a 2d matrix screensaver included?

---

### Post by ghindo on 2009-07-11
> **racerraul said:**
> I have waves & panning disabled... don't remember which stops the tilt.How do you configure the screensaver?  I checked Gconf editor and the GNOME Screensaver dialogue and neither seemed to let me configure the screensaver.

---

### Post by ArtF10 on 2009-07-11
Now......I'm goina eat this chicken-salad sandwich, even though I know it's not real.  My brain is telling me that it's juicy and delicious.

---

### Post by racerraul on 2009-07-12
> **CJ Master said:**
> If you don't like the 3d aspect of it, there's also a 2d matrix screensaver included?

I think I have that too... xMatrix.  if you compare that to the one I posted you will the a huge difference.  The one I posted is more like the one in the movie and why I think visually is much better.

> **ghindo said:**
> How do you configure the screensaver?  I checked Gconf editor and the GNOME Screensaver dialogue and neither seemed to let me configure the screensaver.

I am using xscreensaver... is that what you are using?

---

### Post by djhypnotixx on 2010-09-09
SYSTEM/PREFERENCES/SCREENSAVER.. There is an awesome one out of the box in Ubuntu 10.04 and I think 9+

> **racerraul said:**
> I use [[COLOR="YellowGreen"]this screensaver[/COLOR]]("http://www.geocities.com/matrixscr1/") in my Xp laptop that I use for work (I know I am working on it, unfortunately there is lots ActiveX BS on Co's the intranet, cry me a river!!!)

Anyways, I tried to use that windows .scr file in Ubuntu and failed miserably as a screensaver...

Wondering if there is anyone on board looking for a pet project for an xscreensaver equivalent.

I already have all the Matrix screensavers I could find for xscreensaver... IMO they all pale in comparison to that .scr file... you must see it to understand how much diff it is...

At the moment I am using xMatrix and it does not compare...

---

### Post by juancarlospaco on 2010-09-09
Here comes Python the to save the day *(?)*:

```
import os, time, random, sys

class message(str):
    def __new__(cls, text, speed):
        self = super(message, cls).__new__(cls, text)
        self.speed = speed
        self.y = -1*len(text)
        self.x = random.randint(0, display().width)
        self.skip = 0
        return self
   
    def move(self):
        if self.speed > self.skip:
            self.skip += 1
        else:
            self.skip = 0
            self.y += 1

class display(list):
    def __init__(self):
        self.height, self.width = [int(x) for x in os.popen('stty size', 'r').read().split()]
        self[:] = [' ' for y in xrange(self.height) for x in xrange(self.width)]
   
    def set_vertical(self, x, y, string):
        string = string[::-1]
        if x < 0:
            x = 80 + x
        if x >= self.width:
            x = self.width-1
        if y < 0:
            string = string[abs(y):]
            y = 0
        if y + len(string) > self.height:
            string = string[0:self.height - y]
        if y >= self.height:
            return
        start = y*self.width+x
        length = self.width*(y+len(string))
        step = self.width
       
        self[start:length:step] = string
   
    def __str__(self):
        return ''.join(self)

i_message = raw_input("Input a message: ")
messages = [message(i_message, random.randint(1, 5))]
for t in xrange(1000):
    messages.append(message(i_message, random.randint(1, 5)))
    d = display()
    for text in messages:
        d.set_vertical(text.x, text.y, text)
        text.move()
    sys.stdout.write(str(d))
    sys.stdout.flush()
    del d
    time.sleep(0.1)
```

```
python matrix.py
```

Not too much 3D, but it can say your name or customize it as you want :lolflag:

---

### Post by VCoolio on 2010-09-12
or [this one](http://www.asty.org/cmatrix/) for console.

---

### Post by Giant Speck on 2010-09-12
Don't just stand there! THE ZOMBIES ARE COMING!

---

