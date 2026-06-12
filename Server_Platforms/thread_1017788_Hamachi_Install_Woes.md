---
title: "Hamachi Install Woes"
date: 2008-12-21
forum: Server Platforms
---

### Post by spynappels on 2008-12-21
Hi guys,

   I have another question for you great people.

   i am trying to install hamachi on the latest Server edition. I ran the "make install" command and get the following error message. Can anyone just tell me what this means and what I need to do?
> Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Copying tuncfg into /sbin ..
install: cannot run strip: No such file or directory
install: strip process terminated abnormally
make: *** [install] Error 1
maha@imeddocserver:~/hamachi-0.9.9.9-20-lnx$

I'd really appreciate some help with this one please.

   Thanks, Stefan.

---

### Post by spynappels on 2008-12-22
bump.

---

### Post by Zebra_ on 2009-01-05
Alright I just did this:

Once you download the file, extract it into home/*user name*.
Then enter into the terminal:
cd ~/hamachi-0.9.9.9-20-lnx
sudo make install

Hope that helps

---

### Post by Zebra_ on 2009-01-05
Then after you have to 
cd ~/hamachi-0.9.9.9-20-lnx/tuncfg
sudo tuncfg

---

### Post by murchball on 2009-07-08
I just ran into this myself on a minimal Jaunty install. Installing gcc before running make install seemed to fix it.

---

