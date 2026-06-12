---
title: "No more Gconf-Editor? How to get my &lt;CTRL-C&gt; back?"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by emarkay on 2012-04-15
and to disable thumbnailers, and more...

I may learn to live with the buttons on the wrong side, but I am not giving up my <Ctrl-V> and <Ctrl-C>!

---

### Post by treesurf on 2012-04-15
```
sudo apt-get install dconf-tools
```

Then do Alt+F2 and run dconf-editor.

---

### Post by eco2geek on 2012-04-16
> **emarkay said:**
> I may learn to live with the buttons on the wrong side, but I am not giving up my <Ctrl-V> and <Ctrl-C>!

Not sure what you mean. The keyboard shortcuts for cut, copy and paste never went away.

Anyway, if it's truly gconf-editor you want, then "sudo apt-get update && sudo apt-get install gconf-editor" from the command line.

---

### Post by ubuntu27 on 2012-04-16
The clasic keyboard shortcuts such as Ctrl+C for Copy and Ctrl+V for paste works in Ubuntu Precise perfectly.

If you mean that it does not work in Empathy Messenger (my guess is that you are referring to this app).. I hear you. It is the only app that does not support keyboard shortcuts (yet).

---

### Post by emarkay on 2012-04-16
Yes, surprise surprise, no more "control-alt-shift-c colon backslash space" just to grab some text.

It works again  as it did in 1990!  Hooray!

---

### Post by ubuntu27 on 2012-04-17
> **emarkay said:**
> Yes, surprise surprise, no more "control-alt-shift-c colon backslash space" just to grab some text.

It works again  as it did in 1990!  Hooray!

?? :confused:

Did you get it to work? What programs were you using?

---

