---
title: "Midi keyboard through Roland quad capture"
date: 2014-09-24
forum: Ubuntu Studio
---

### Post by davevr on 2014-09-24
Anyone know if it's possible to hook up an old Roland Midi keyboard (not USB) I have to my pc through my Quad Capture. 
and not midi in + out. I mean the following : {Midi Keyboard = Midi out}  to {quad capture = Midi in} and then via {quad capture = USB} to 
my pc. 

Seems it should do it, have not tried it yet, and have no plans in spending another night trying the impossible.....

---

### Post by jejeman on 2014-09-25
Plug in that Quad and give
```
amidi -l
```

---

