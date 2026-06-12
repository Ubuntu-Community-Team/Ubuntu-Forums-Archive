---
title: "Reformed windows user/Linux newb requests assistance"
date: 2014-05-21
forum: Ubuntu Studio
---

### Post by kenslaptopshop on 2014-05-21
I need a super basic tutorial as I am not able to figure out how to get my sound inputted from my edirol UA-25 into any of the programs like Ardour or SooperLooper.

WTF (where the frack) do I start?

I think there is some sort of JACK patching that needs to happen but again, I'm coming from Windows retardland and just spent an hour trying to get my wireless to connect.

If anyone has a minute to help the newb it's much appreciated!

Thanks in advance,

Ken McNamara

---

### Post by jejeman on 2014-05-21
First see if the UA-25 works
```
aplay -l
```

---

### Post by kenslaptopshop on 2014-05-21
Yep I can see the meter going when I open theInput Devices from the Volume Control panel

---

### Post by kenslaptopshop on 2014-05-21
THis is what I get from aplay:

card 2: UA25 [UA-25], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by jejeman on 2014-05-24
Good, card is working. Now, just setup JACK. Open Qjackctl and choose the UA card.
Whatch this, serach similar
[http://www.youtube.com/watch?v=fMz6fDGBnA4](http://www.youtube.com/watch?v=fMz6fDGBnA4)

---

