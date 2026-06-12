---
title: "VI wont let me edit"
date: 2010-12-03
forum: Server Platforms
---

### Post by cbarron on 2010-12-03
I just did a fresh install of Ubuntu Server 10.10 on my FTP Server. When I try to press i to start editing it it does nothing. I have already run  sudo apt-get update and sudo apt-get upgrade. Yes I have permission to edit these files, my user is the only one on the server. Any Ideas?

---

### Post by SlugSlug on 2010-12-03
are you logging in as root?  if not then you may (depending on path) need to 
sudo vi /path/file

I use the insert key to edit,

---

### Post by karthick87 on 2010-12-03
You should press the insert key in your keyboard,after that you can able to edit.

---

### Post by cbarron on 2010-12-03
I did......sudo vi /etc/network/interfaces......entered my password,and the file opens, but the insert key does not allow me to edit either. This is real frusterating.....I can not edit any thing any where...ie terminal or via ssh....any more ideas?

---

### Post by SlugSlug on 2010-12-03
You could try nano instead of vi

---

### Post by I'mGeorge on 2010-12-03
you could consider using nano instead of vi, sudo nano /path_to_your_text_file

---

### Post by cbarron on 2010-12-03
Nano...huh? I will have to try that......but on another note I did get it fixed............I thought vi came installed with server....but it turns out it doesnt...so I installed it..........funny how you can view via vi without it installed but you have to install it to edit........this was purely newby mistake.......lol

---

### Post by dtfinch on 2010-12-03
I use "nano -w" because otherwise without the "-w" it hard wraps long lines, breaking them into separate lines on save, very destructive to most files. Or at least it did when I last checked, and according to [http://wiki.linuxquestions.org/wiki/Nano](http://wiki.linuxquestions.org/wiki/Nano).

Edit: I guess they finally fixed the default behavior last year by adding "set nowrap" to the default /etc/nanorc. [https://bugs.launchpad.net/debian/+source/nano/+bug/39866](https://bugs.launchpad.net/debian/+source/nano/+bug/39866) . So for 1 out of the ~7 years I've been using "-w" I didn't really need to.

---

### Post by cbarron on 2010-12-05
Thank You all for the input....I think I like nano better than vi. Thanks again....Im sure I will have more questions....lol  ;)

---

