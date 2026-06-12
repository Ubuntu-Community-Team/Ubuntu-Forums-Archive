---
title: "Help me to release mouse capture in virtualBox"
date: 2011-02-24
forum: Virtualisation
---

### Post by hoboy on 2011-02-24
i have install virtualBox OSE, then install windows 7.
but when the mouse is captured inside I press on pil-down-Right Ctrl to release the mouse, but nothing happen.
what key shall be use to release the mouse capture in virtualBox ?

---

### Post by CharlesA on 2011-02-24
That's the "host" key, by default it's right control. Shouldn't need to use any other keys in combination with the host key.

---

### Post by Hedgehog1 on 2011-02-25
This stumped me too at first.

They want you to press one key by itself:

  *The [CTRL] key on the right hand side of the keyboard.

Then the mouse gets release back to you (well, to the host OS).

:KS

---

### Post by hoboy on 2011-02-25
> **Hedgehog1 said:**
> This stumped me too at first.

They want you to press one key by itself:

  *The [CTRL] key on the right hand side of the keyboard.

Then the mouse gets release back to you (well, to the host OS).

:KS

Thanks a lots I will try that..
what an annoying think.

---

### Post by howefield on 2011-02-25
If you haven't already installed Guest Additions, doing so will give you a better set of drivers for your guest, including non capture of the mouse.

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

---

### Post by linuxbasiccommand on 2011-02-25
> **hoboy said:**
> i have install virtualBox OSE, then install windows 7.
but when the mouse is captured inside I press on pil-down-Right Ctrl to release the mouse, but nothing happen.
what key shall be use to release the mouse capture in virtualBox ?
  You select "CTRL+F"

---

### Post by kachilda on 2012-11-02
Open up Vitrualbox, go to settings, scroll down to usb and uncheck the virtualbox usb mouse port; that should free up your mouse to be used by your host operating system.:guitar:

---

