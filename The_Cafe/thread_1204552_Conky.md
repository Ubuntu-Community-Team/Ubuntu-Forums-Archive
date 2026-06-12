---
title: "Conky?"
date: 2009-07-04
forum: The Cafe
---

### Post by Cam42 on 2009-07-04
so what is this Conky thing that I hear so much about? What is it and how would I install it on Ubuntu Jaunty?

---

### Post by dragos240 on 2009-07-04
Well conky is a nice little app that runs on your desktop background, it can be daemonized, and it's very usefull for many things such as "fortunes" weather, etc. And if your using ubuntu, sudo apt-get install conky, and download some conky conf files.

---

### Post by .Maleficus. on 2009-07-04
[This thread ought to help]("http://ubuntuforums.org/showthread.php?t=281865").

.conkyrc is the file that goes in your user's directory that tells Conky how and what to display on the desktop.  Copy/paste any of those .conkyrc's (or mix and match) to /home/*user*/.conkyrc.

---

### Post by CharmyBee on 2009-07-04
Conky is a robot that issues you the secret word for the day.

---

### Post by Cam42 on 2009-07-05
Would it be possible to display a working terminal in conky?

---

### Post by heyyy on 2009-07-05
i might be wrong but i think conky must be ran as a root.
is this true?

---

### Post by Sealbhach on 2009-07-05
> **heyyy said:**
> i might be wrong but i think conky must be ran as a root.
is this true?

No. Why would you need to?

.

---

### Post by Cam42 on 2009-07-05
how do I get Conky to start?

---

### Post by Tibuda on 2009-07-05
> **Cam42 said:**
> how do I get Conky to start?

```
conky
```

---

### Post by Cam42 on 2009-07-05
I figured that out. Turns out that conky wouldn't start because I copy/pasted a .conkyrc that monitored multiple processors, and I only have one. heh.

---

### Post by p0cky84 on 2009-07-05
> **Cam42 said:**
> so what is this Conky thing that I hear so much about? What is it and how would I install it on Ubuntu Jaunty?
Well, conky is this annoying thing that keeps posting in forums without checking the man page/project page/infos page, before posting a silly thread actually asking what it is... wait, OH SHI-

---

