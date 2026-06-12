---
title: "broke xfce"
date: 2005-12-12
forum: The Cafe
---

### Post by doc_holiday on 2005-12-12
I was looking for a file manager in xfce, couldn't immideately find one. So I did run program Nautilus. This messed up my look and the ability to right click on the desktop.
Any way to restore this?

---

### Post by IYY on 2005-12-12
Well, the easiest thing you could do is log out and then log back in. If you don't want to, you could ***ps -aux | grep nautilus***, and then kill whatever process it finds.

---

### Post by doc_holiday on 2005-12-12
I already rebooted, the same problem. Even the selected desktop is not shown.

---

### Post by BatsotO on 2005-12-12
Click on menu, run aplication : xfdesktop
That should bring back your xfce desktop.
The reason why this happen is that nautilus conflict with xfdesktop (xfce desktop app) since nautilus it self run the desktop on gnome.
AFAIK the file manager for xfce is rox and xffm, and thunar if you just want to try it (find post by sapo). You can dig more of this xfce by searching thread about xubuntu.

---

### Post by doc_holiday on 2005-12-12
My hero ;)

Thanks!!

---

### Post by BatsotO on 2005-12-12
you're welcome :) 
i'm no hero.. :p

---

### Post by Luke on 2005-12-14
cool. that solved my problem too. i hadn't "messed" with anything but i still got the same problem. 
was running gnome.
installed xfce, logged off gnome session
started xfce session, everything was fine
turned off computer
came back later and the problem appeared

now that i know how to fix it..... here's comes the mega-newb question
where can i put that command so it does it automatically every time i start xfce?

thanks very much

---

