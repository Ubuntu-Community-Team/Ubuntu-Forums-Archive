---
title: "Oh wow precise tells you the keyboard shortcuts now!"
date: 2012-04-18
forum: The Cafe
---

### Post by Primefalcon on 2012-04-18
check out what pops up when you hold down the super key now.....

[[img]http://dl.dropbox.com/u/1212637/2012/04%20April/Screenshot%20from%202012-04-18%2018%3A08%3A40%7Ethumbnail.jpg[/img]](http://dl.dropbox.com/u/1212637/2012/04%20April/Screenshot%20from%202012-04-18%2018%3A08%3A40.png)
Click for a bigger pic

---

### Post by Ghil on 2012-04-18
...Wow, that's awesome!

Also look, I'm in the screenshot! I'm going to be famous naow! :)

---

### Post by wojox on 2012-04-18
That is cool. Been that way for a while.

Could you fix your sceen shot Primefalcon, it's a little big.

---

### Post by Primefalcon on 2012-04-18
> **wojox said:**
> That is cool. Been that way for a while.

Could you fix your sceen shot Primefalcon, it's a little big.
Easily done I have a script in my nautilus scripts tat I wrote that allows me to right click to create a thumbnail...

btw if anyone wants the same ability. Take the following script (make it executable) and dump it in ~/.gnome2/nautilus-scripts (surpised its still using .gnome2 but oh well)

```
#!/bin/bash
StrippedName=${1%.*}; convert "$1" -resize x150 -strip "$StrippedName~thumbnail.jpg"
```
note: you'll need to install imagemagick

---

### Post by Copper Bezel on 2012-04-18
Dude, awesome. That's ridiculously convenient.

Edit for clarity: I meant Primefalcon's script. Saves me opening Shotwell.

---

### Post by Penguinnerd on 2012-04-18
Even I'll admit that's pretty nice.

---

### Post by sffvba[e0rt on 2012-04-19
Expect a lot of awesome with 12.04...


404

---

