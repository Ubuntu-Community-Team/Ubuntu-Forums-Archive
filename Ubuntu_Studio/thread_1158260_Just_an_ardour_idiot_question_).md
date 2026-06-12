---
title: "Just an ardour idiot question :)"
date: 2009-05-13
forum: Ubuntu Studio
---

### Post by B4RR13N705 on 2009-05-13
Hi, i am trying to record some stuff i made with Virtual keyboard, trough Hexter and jack-rack, all under jack. 
I opened ardour and in jack connections, i found that ardour have:
Master-in an audio-in. What is the one that i have to connect to? master-in or audio-in??

---

### Post by thorgal on 2009-05-13
in ardour, you create an audio track to record audio material to your HD.
The master is a bus, and does not connect to any disk stream (as opposed to a track).

Master only collects all other tracks and busses outputs so you have a final stereo bus from which you can apply overall stuff (thus the name master).

In general, it is better to do the track port connection from ardour:
if you only have the track editor window opened (i.e. the mixer window is hidden), left-click on the track header and then make the mixer strip show up with Shift+E.
Left click on the "Input" button (about the top of the strip) and you will see a connection dialog. Each jack client is a tab in this dialog. Select the one you want. Connection is easy: click on a client port listed in the tab and it will be assigned to track-input1, do the same for the next port if it's a stereo track. That's all :)

---

### Post by B4RR13N705 on 2009-05-13
Thanx! it now records :popcorn:

---

### Post by markbuntu on 2009-05-22
There is an excellent ardour tutorial here

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

---

