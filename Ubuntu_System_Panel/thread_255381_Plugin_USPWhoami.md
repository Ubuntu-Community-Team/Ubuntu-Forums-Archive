---
title: "Plugin: USPWhoami"
date: 2006-09-11
forum: Ubuntu System Panel
---

### Post by mucha on 2006-09-11
Saw in the plugin development thread a wish about a panel that shows user avatar and name. I hope it works fine! :)

---

### Post by chanders on 2006-09-11
Screenie? :D

---

### Post by mucha on 2006-09-11
Simple but anyway: :)

[img]http://img145.imageshack.us/img145/2823/uspwhoamigw2.png[/img]

---

### Post by chanders on 2006-09-11
> **mucha said:**
> Simple but anyway: :)

Beau-t-ful!! Check your PM ;-)

---

### Post by spockrock on 2006-09-12
how does one use this plugin??

edit never mind.

extract to 
~/.usp/plugins/


and then Add USPWhoami in gconf, works like a charm.

[IMG]http://img.photobucket.com/albums/v605/redemma/xgl/Screenshot-SystemPanel.png[/IMG]

one small thing I think I would like is if it read 'Who Am I?'  Or perhaps 'User' instead of 'Who am i', as the title above the Avitar.  Thanks!  I love this plugin.

---

### Post by chanders on 2006-09-12
Try changing self.heading in USPWhoami.py to whatever you like as the heading.. and reload the plugin..

---

### Post by spockrock on 2006-09-12
> **chanders said:**
> Try changing self.heading in USPWhoami.py to whatever you like as the heading.. and reload the plugin..


thanks thats easy enough

---

### Post by fantan on 2006-09-12
Hi people,

Today I've downloaded the USPWhoami plugin. I've extracted it, putted the two file firstly to ~/.usp/plugins/ directory and some time later I tried to put them to /usr/python2.4/site-packages/usp/plugins directory. In both case in gconf I've added USPWhoami to the plugins_list, but I got the following error message: "The Who am I plugin isn't found" and nothing else.
What should I do with it?
My second question is: how and where to set up my avatar, and what kind of type (jpg, png or what) should it be?

Thank you for the answer in advance.     

Best regards, fantan people

---

### Post by mucha on 2006-09-12
> **fantan said:**
> Hi people,

Today I've downloaded the USPWhoami plugin. I've extracted it, putted the two file firstly to ~/.usp/plugins/ directory and some time later I tried to put them to /usr/python2.4/site-packages/usp/plugins directory. In both case in gconf I've added USPWhoami to the plugins_list, but I got the following error message: "The Who am I plugin isn't found" and nothing else.
What should I do with it?
My second question is: how and where to set up my avatar, and what kind of type (jpg, png or what) should it be?

Thank you for the answer in advance.     

Best regards, fantan people

This might work:
- Remove the plugin from plugins_list in gconf
- Then delete the plugin in /usr/python2.4/site-packages/usp/plugins
- Change chmod on the plugin
```
$ cd ~/.usp/plugins
$ chmod 755 USPWhoami.py
$ chmod 755 USPWhoami.glade
```
- And add it to plugins_list again

To change your avatar you can just click on the avatar in the plugin or run gdmphotosetup

---

### Post by Uncle Spellbinder on 2006-09-13
Absolutely EXCELLENT!!!!

---

### Post by fantan on 2006-09-13
Hi mucha,

I did what you've proposed but no success!
When I did all you proposed, a window, named Window1 skipped up and when I clicked on the icon, my photo which I configured before in the "Login photo panel" appeared in this Window1. And when I clicked on the USP icon on the bottom panel, the error message appeared again: >>Plugin "USPWhoami" not found!<<

Now on my system the two file are in the ~/.usp/plugins directory, they permissions are 755. But no any results!
What is exactly the name which I must put in gconf to the plugins_list variable: USPWhoami, whoami, Whoami or what? And where can I put my name? In the file USPWhoami.py I found a variable: self.set.Name(). Maybe there?

What should be the next step?

fantan

---

### Post by LordMau on 2006-09-13
Excellent.

---

### Post by fantan on 2006-09-13
Hi for All,

Because I didn't got any answer I will answer to own questions now:

I don't know exactly what I did, but after several reboots of (firstly just the X, and after the all system), at last I've got all I wanted.
In any case, my congratulations for this excellent job. Now I have all: the avatar, the name of the user (that is me) etc.

Thank all you again,

fantan

---

### Post by bulldog on 2006-09-13
When you got troubles again fantan,just remove USP from your panel and add it again.

Most of the time is this the only fast way to put new plugins or whatever in your USP.

---

### Post by fantan on 2006-09-13
Thanks a lot, next time when an error appears I'll try what you provide.

fantan

---

