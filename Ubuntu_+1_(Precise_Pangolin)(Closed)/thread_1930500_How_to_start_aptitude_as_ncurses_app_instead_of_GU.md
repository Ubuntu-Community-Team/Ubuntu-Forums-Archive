---
title: "How to start aptitude as ncurses app instead of GUI?"
date: 2012-02-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ratcheer on 2012-02-23
In 11.10, when I run "sudo aptitude" I get the familiar ncurses application. But in 12.04, I get a silly GUI interface where the buttons don't seem to work. How can I get it to start the old way?

I have searched this site and Googled, but so far, I haven't found an answer.

Thanks,
Tim

---

### Post by matt_symes on 2012-02-23
Hi

What's the result of

```
dpkg -l aptitude-gtk
```

Maybe you have that installed ?

Kind regards

---

### Post by PaulW2U on 2012-02-23
You've probably installed aptitude-gtk.

The ncurses version of aptitude exists in 12.04 just as it has done in previous releases.

---

### Post by ratcheer on 2012-02-23
All I told the Software Center was to install "aptitude". I don't know why I would have gotten something else.

But, I will try to uninstall whatever I install and install aptitude with apt-get.

Thanks,
Tim

---

### Post by ratcheer on 2012-02-23
Okay, both aptitude and aptitude-gtk were installed. I removed aptitude-gtk, and now the normal aptitude runs.

The removal also removed packages libglade2-0{u}, libglademm-2.4-1c2a{u}, and libgtkmm-2.4-1c2a{u}. I hope that's not going to hurt anything else.

Thanks again,
Tim

---

