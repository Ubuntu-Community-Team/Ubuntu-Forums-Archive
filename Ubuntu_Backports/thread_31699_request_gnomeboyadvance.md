---
title: "request: gnomeboyadvance"
date: 2005-05-04
forum: Ubuntu Backports
---

### Post by McQuaid on 2005-05-04
This is a gnome front end to visualboyadvance.  I have it in debian sid, can't recall if it's official or not but I believe it is official on the debian side.

---

### Post by defkewl on 2005-05-04
So why don't you just download it from debian repo? :D

---

### Post by McQuaid on 2005-05-04
Your joking right?

---

### Post by Technoviking on 2005-05-04
I have made one and sent it to jdong.

Mike

---

### Post by jdong on 2005-05-04
I've added Mike's package to my local working copy, and it'll be uploaded with aDesklets once this 40MB monster (Adobe Acrobat Reader 7) finishes.

---

### Post by Technoviking on 2005-05-04
[QUOTE=defkewl]So why don't you just download it from debian repo? :D[/QUOTE]
The one from the debian repo has depenancy problem with python 2.4.1, my package fixes that.

Mike

---

### Post by McQuaid on 2005-05-08
thanks a lot.  I really have to learn how to package stuff.  Giving a glance over the deb maintainer's guide it assumes your starting from source.  Most of these backports are using the debian's src file correct? Is there a smaller guide going on the assumption you already have a src deb?  I'd like to give it a go.

Btw How did you fix the python 2.4.1 dependency problem?  I was about to install python 2.3 to satisfy the deb all pkg from the programs site but held off to see if someone would package it here.

---

### Post by obvious_ron on 2005-07-25
[QUOTE=Mike Basinger]The one from the debian repo has depenancy problem with python 2.4.1, my package fixes that.

Mike[/QUOTE]

What do I search for in Synaptic and where do I search for it?

---

### Post by kazuya on 2005-10-26
Does the joystick work for gnomeboyadvance? Where do you get it from? debian sid or universe? I seem to find gnuboy instead. And the deb for gnomeboy adavance I find, never install successfully?

Is there a required kernel, vga, gamepad, or repository? Is directX required? ogg splitter, etc?

I own a saitek pad.

---

### Post by Technoviking on 2005-10-27
New instructions for installing gnomeboyadvance under Breezy at:
[http://www.ubuntuforums.org/showthread.php?p=448163#post448163](http://www.ubuntuforums.org/showthread.php?p=448163#post448163)

I'm not adding it to the backports since it was not built from offical Ubuntu source files.

Mike

---

