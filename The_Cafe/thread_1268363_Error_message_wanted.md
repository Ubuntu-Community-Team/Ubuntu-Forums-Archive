---
title: "Error message wanted"
date: 2009-09-16
forum: The Cafe
---

### Post by Student1 on 2009-09-16
Thats right I'm actually looking how to find an error promt that reads "[B]I'm sorry dave, I can't let you do that".
[/B]
Its for extra credit for a project of mine.  can anyone tell me how to get this error prompt message.

---

### Post by Sealbhach on 2009-09-16
[IMG]http://imgur.com/DjW4j.png[/IMG]

.

---

### Post by dragos240 on 2009-09-16
Maybe by running an application that needs root access on an unprivalegeded user?

---

### Post by tjwoosta on 2009-09-16
Im pretty sure this falls under homework which would make it against the rules to ask for help here but you can just google how to make a fake error prompt and you will find tons of links that will teach you. There are even youtube videos on the subject.

---

### Post by t0p on 2009-09-16
> **tjwoosta said:**
> Im pretty sure this falls under homework which would make it against the rules to ask for help here but you can just google how to make a fake error prompt and you will find tons of links that will teach you. There are even youtube videos on the subject.

And if you use a program like **espeak** you'll be able to make your computer actually *say* the immortal words.  Just like the real Hal.

Dunno how to make it sing "Daisy" though.  :p

---

### Post by jeromey on 2009-09-16
for linux ?

gnome
```
gdialog --msgbox "I'm sorry dave, I can't let you do that" --title "Error"
```

kde
```
kdialog --msgbox "I'm sorry dave, I can't let you do that" --title "Error"
```

---

### Post by Student1 on 2009-09-16
k Wow, I was told Linux Ubuntu had a strong community but damn.  I didn't think I would get a resopose that fast.

I should have specified GNOME, but the 
gdialog --msgbox "I'm sorry dave, I can't let you do that" --title "Error"

 code worked like a charm.

ty all

---

