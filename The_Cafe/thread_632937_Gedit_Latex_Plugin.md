---
title: "Gedit Latex Plugin"
date: 2007-12-06
forum: The Cafe
---

### Post by zadig on 2007-12-06
I've been using texmaker for a long time and decided to move to gedit for mainly code completion functionality. I'm using dapper as my main machine and downloaded the latex plugin for gedit. I've put the plugin under ~/.gnome2/gedit/plugins as described. When I open gedit, and go to edit/preferences/plugins I see the latex plugin. The problem is I cant activate it, the check box doesnt load it. I get the following error on my terminal when I open gedit and try to load the plugin. 

Traceback (most recent call last):
  File "/home/bilgic/.gnome2/gedit/plugins/LaTeXPlugin/__init__.py", line 25, in ?
    from PluginInstance import PluginInstance
  File "/home/bilgic/.gnome2/gedit/plugins/LaTeXPlugin/PluginInstance.py", line 21, in ?
    from gedit import encoding_get_utf8, tab_get_from_document
ImportError: cannot import name encoding_get_utf8

** (gedit:21109): WARNING **: Could not load python module LaTeXPlugin


** (gedit:21109): WARNING **: Error, impossible to activate plugin 'LaTeX Plugin 0.1.2'

I have gutsy installed on another computer. Followed the same steps and I just works.

---

### Post by zadig on 2007-12-06
I've installed libgtk2.0-dev and it works fine now. Installing libgtk2.0-dev was pain in the neck, as i was getting dependency problems in synaptic. One of the problematic packages was libcario I cant remember the other one now. I've  type sudo aptitude install libcairo2-dev, it asked to downgrade to solve the dependencies: 

Downgrade the following packages:
libcairo2 [1.2.2-0ubuntu1 (now) -> 1.0.4-0ubuntu1.1
I've accepted and then tried installing libgtk2.0-dev again and it worked. Then the plugin started working as well. Maybe not the best solution, but better than no solution i guess :)

---

### Post by Wnutt on 2007-12-06
Thanks, I was typing (a lot of) latex files in gEdit and I didn't know about this plugin. 

Your post was very helpful.

---

### Post by Malcolm on 2007-12-06
> **zadig said:**
> Downgrade the following packages:
libcairo2 [1.2.2-0ubuntu1 (now) -> 1.0.4-0ubuntu1.1
I've accepted and then tried installing libgtk2.0-dev again and it worked. Then the plugin started working as well.

Of those two packages, I have libgtk2-dev installed correctly, and the version of libcairo2 is 1.4.10-1ubuntu4.1. Looks newer than yours, so maybe we're using different versions of Ubuntu (I'm using 7.10).

The plugin worked right away for me as well. Gedit is becoming a great editor, I've decided to use it as my main editor and I love it. I like how it starts very simple and can be extended with plugins, depending on my needs. The snippets plugin is very useful as well.

---

### Post by zadig on 2007-12-06
Yes I have 6.06 installed on my laptop, i dont want to upgrade to feisty or gutsy as i am a newbie and really scared of messing things up. I try to keep my laptop pretty stable and dont mess it. My desktop has freshly installed gutsy where I dont keep any valuable information and try everything. It works just fine there, that's how i tried the plugin :) I dont care downgrading on my laptop to make it work. 

I like gedit latex plugin because of the auto-completion functionality, I'm kind of new and need to see whats out there as i'm typing. I didnt know snippits plugin, it rocks !

---

