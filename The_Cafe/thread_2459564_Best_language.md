---
title: "Best language"
date: 2021-03-21
forum: The Cafe
---

### Post by orion20k on 2021-03-21
Ive been wrighting a bash script for a few days and its getting quite sprawled out with menus etc.

Ive been thinking that a gui would help convey the nessasery information and relovent options.

Now bash does have a gui but its rather obscure so it got me thinking.

Should i switch to a different language such as python, my bash script uses some terminal commands such as apt-get and mysql.

So my question is what language would you recommend?

---

### Post by TheFu on 2021-03-21
Tk and perhaps tcl for GUI stuff.

Anytime bash scripts are over 1 pg, I stop and rewrite them in a better language that supports complex data structures  and advanced programming methods. 

**Update:**
Before adding a GUI, please fully implement the cli solution so automation without any point-n-click is possible. In storage architecture, it is very common to keep the GUI separate from the code that does the work. By having the CLI version call a library that does all the work,
a) moving to a GUI will be easier
b) automatic testing of functionality will be easier
c) less manual testing for GUI issues will be needed.

Just saw this: [https://www.theregister.com/2021/03/22/canonical_flutter/](https://www.theregister.com/2021/03/22/canonical_flutter/)  
> Canonical: Flutter now 'the default choice for future desktop and mobile apps'
Cross-platform appeal outweighs performance penalty, argues Linux flinger

So, if having a GUI on Ubuntu is the goal, then, this year, Canonical wants to push Flutter. Find a language that has binding or works with Flutter.  3 yrs ago, Canonical was pushing a different GUI tool. 10 yrs ago, it was a different tool.  This is the nature of GUI stuff - there is always some new tool that is supposed to make things faster and easier.  I haven't seen that myself in 25+ yrs.  The Gui is just different, not better.
 If it was me and this was more than a little hacked together tool for just my needs, I'd use GTK+ which has been around 20 yrs now. Most of the programs you use all the time are built using it.  Gnome-everything is based on it and there are bindings for 10+ languages, I'd guess.

---

### Post by werner123 on 2021-04-08
Python - great language, it suits a lot of people.

---

