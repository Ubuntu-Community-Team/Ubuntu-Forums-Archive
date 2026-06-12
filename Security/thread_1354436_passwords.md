---
title: "passwords"
date: 2009-12-13
forum: Security
---

### Post by ChadBJX on 2009-12-13
[SIZE=5]Hi,
I mostly type mostly by using Virtual Keyboard and the mouse. No one but me has (unsupervised) access to this computer. For me it is very difficult to use the keyboard. 

I haven't found any way to use the Virtual Keyboard to enter the passwords. 

Is it possible to/How can I - disable the ''Sign in to Ubuntu'' password prompt, and the Admin. password prompt when installing or removing software.

I really like Ubuntu, but this problem may cause me to have to return to Windows. This is a home computer, not on a network, I just don't need this.

FYI, I just upgraded to Ubuntu  9.10 Karmic Koala.

Thanks,
Chad
[/SIZE]

---

### Post by bodhi.zazen on 2009-12-13
First, please use the default font settings when posting. I understand you may be visually impaired, but if so please change the defaults for your browser ;)

You can enable auto login and you can configure sudo so that a password is not required, but I advise you simply use

sudo -i

gksu 

gksu nautilus

---

