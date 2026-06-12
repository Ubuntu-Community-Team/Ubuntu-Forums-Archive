---
title: "Black screen"
date: 2015-01-28
forum: Ubuntu Development Version
---

### Post by cecilpierce on 2015-01-28
Just installed 15.04 32bit and 64bit before and all I get is black screen and mouse cursor.

I have nvidia-current and latest kernel installed.

I did manage to install gnome-shell from a tty and it logs in and works fine,

Any ideas whats wrong or what to try ?

Thanks,
Cecil

---

### Post by cecilpierce on 2015-01-30
Give up, staying with GS.

---

### Post by NunoLava1998 on 2015-02-08
Switch to terminal using Ctrl+Alt+T then type "startx"
Does it bring up the desktop after some time or instantly?

---

### Post by zika on 2015-02-08
> **NunoLava1998 said:**
> Switch to terminal using Ctrl+Alt+T then type "startx"
Does it bring up the desktop after some time or instantly?Startx from Terminal inside GS?
If all is well installed, the very existence of file ~/.Xauthority should not alow You that, not to mention deeper reasons...
Did You, by any chance, mean from tty?

---

### Post by NunoLava1998 on 2015-02-08
> **zika said:**
> Startx from Terminal inside GS?
If all is well installed, the very existence of file ~/.Xauthority should not alow You that, not to mention deeper reasons...
Did You, by any chance, mean from tty?

sudo -i
type password
done, you can now run startx lol

---

### Post by zika on 2015-02-08
> **NunoLava1998 said:**
> sudo -i
type password
done, you can now run startx lolYeap, that is the sure way to make trouble with startx. We've discussed that so many times... ;) Have fun. But be carefull when giving advices... Some people do use their machines for seriuos work... ;)

---

### Post by NunoLava1998 on 2015-02-08
> **zika said:**
> Yeap, that is the sure way to make trouble with startx. We've discussed that so many times... ;) Have fun. But be carefull when giving advices... Some people do use their machines for seriuos work... ;)


I never saw it made trouble with startx.
So gaining root and typing startx messes startx? hahahaha.

---

### Post by zika on 2015-02-08
> **NunoLava1998 said:**
> I never saw it made trouble with startx.
So gaining root and typing startx messes startx? hahahaha.To be precise, starting startx with sudo. OK, I've reread Your post and You did change home folder (&#8222;-i&#8220;) so I give You that. My warning still stands, without &#8222;-i&#8220; that would be call for some troubles.

---

### Post by NunoLava1998 on 2015-02-08
> **zika said:**
> To be precise, starting startx with sudo. OK, I've reread Your post and You did change home folder („-i“) so I give You that. My warning still stands, without „-i“ that would be call for some troubles.

sudo -i is just a command to get root permission in terminal-

---

### Post by zika on 2015-02-09
> **NunoLava1998 said:**
> sudo -i is just a command to get root permission in terminal-No, read about the difference between just ```
sudo
``` and one with „-i“... ;)

---

