---
title: "Easytag Broken"
date: 2013-04-19
forum: Ubuntu Development Version
---

### Post by jlacroix on 2013-04-19
Easytag seems to be broken. When I go to open it, it never appears on screen. If I try to open it from a terminal, no output appears. It just doesn't open. I'm not sure if this is indicative of a bigger issue, but it seems to be the only program that won't open for me in 13.04. I have also tried purging it as well, and deleting the config file but it won't ever appear.

Anyone else notice this with Easytag or another program?

---

### Post by JMB74 on 2013-04-19
Easytag starts OK here on kubuntu.

---

### Post by jlacroix on 2013-04-19
> **JMB74 said:**
> Easytag starts OK here on kubuntu.
Very strange. On mine it won't start at all, but all other programs I use start fine...

---

### Post by jlacroix on 2013-04-19
If I run "kdesudo easytag" it will open, but not as my normal user. I would rathre not update my files as root, though.

---

### Post by Roasted on 2013-04-19
Just a thought - perhaps nuking whatever hidden folder there is for easytag and starting over would do the trick? aka, show hidden folders in your home directory, look for .easytag, and rename to something else so it auto creates a new config folder for it. Just thinking out loud, no idea if it would fly...

---

### Post by jlacroix on 2013-04-19
> **Roasted said:**
> Just a thought - perhaps nuking whatever hidden folder there is for easytag and starting over would do the trick? aka, show hidden folders in your home directory, look for .easytag, and rename to something else so it auto creates a new config folder for it. Just thinking out loud, no idea if it would fly...
That's a great idea, but unfortunately I've tried it. :(

---

### Post by Elfy on 2013-04-19
[http://www.spinics.net/linux/fedora/fedora-kde/msg12328.html](http://www.spinics.net/linux/fedora/fedora-kde/msg12328.html)

Might point in the right direction

Easytag not showing but has actually started

```
ps aux | grep easytag
```

> If I change "oxygen-gtk" to any other widget style (other than QtCurve) it 
starts up just fine.  It just looks ugly...

---

### Post by jlacroix on 2013-04-19
Thanks, I can confirm that it works if I change the GTK theme to something else.

---

### Post by Elfy on 2013-04-20
I'd report it.

---

### Post by jlacroix on 2013-04-20
> **Elfy said:**
> I'd report it.
It's reported. Hopefully it's fixed soon, I'm nervous that easytag may not be the only GTK program this may affect.

---

### Post by ufugu on 2013-04-22
Easytag seems to have been abandoned a few years ago.  Until your issue is fixed, you could give Puddletag a shot.  It's a great tagger and it's in the repos now.

---

### Post by jlacroix on 2013-04-22
> **ufugu said:**
> Easytag seems to have been abandoned a few years ago.  Until your issue is fixed, you could give Puddletag a shot.  It's a great tagger and it's in the repos now.
Right now, running "sudo easytag" seems to work. Your point about Easytag being abandoned is probably true, but I don't think the problem is Easytag. I think it is a Kubuntu 13.04 specific bug. It's been filed, but I would expect it to be low-priority. I just fear it may affect more than just Easytag.

---

