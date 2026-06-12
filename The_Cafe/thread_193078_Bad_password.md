---
title: "Bad password"
date: 2006-06-09
forum: The Cafe
---

### Post by wmcbrine on 2006-06-09
Hey, check out what happens in Dapper when the screen is locked and you enter the wrong password. It's cute.

---

### Post by Stormy Eyes on 2006-06-09
[QUOTE=wmcbrine]Hey, check out what happens in Dapper when the screen is locked and you enter the wrong password. It's cute.[/QUOTE]

I've rigged mine to cry out, "Help! Help! I'm being repressed!" if you put in a bad password.

---

### Post by mostwanted on 2006-06-09
It would be cooler if it also said "uh-uh!".

---

### Post by Klaidas on 2006-06-09
[QUOTE=Stormy Eyes]I've rigged mine to cry out, "Help! Help! I'm being repressed!" if you put in a bad password.[/QUOTE]

How did you change that?

---

### Post by Stormy Eyes on 2006-06-09
[QUOTE=Klaidas]How did you change that?[/QUOTE]

Use these two options in /etc/X11/gdm/gdm.conf:

For failed login: ```

SoundOnLoginFailure=true
SoundOnLoginFailureFile=/path/to/sound.wav

```

For successful login: ```

SoundOnLoginSuccess=true
SoundOnLoginSuccessFile=/path/to/sound.wav

```

---

### Post by Klaidas on 2006-06-09
Thank you Stormy Eyes.

---

### Post by Stormy Eyes on 2006-06-09
[QUOTE=Klaidas]Thank you Stormy Eyes.[/QUOTE]

No problem. :) I rigged my success to be the first few minutes of "Good Enough" by Van Halen, where Sammy Hagar yells out, "Hello, baby!" It makes my wife giggle every time she logs in.

---

### Post by mostwanted on 2006-06-09
Lol, awesome mini-howto. I'm bookmarking this topic.

---

### Post by ????? on 2006-06-09
Is it possible to change the text on the lock screen logon?

(ex. change Bad password to something else)

---

### Post by wmcbrine on 2006-06-09
...and just now I discovered that, like so many things, the effect is copied from Mac OS X. (Yes, it's a bad day for me mistyping my password.)

---

### Post by Maupertus on 2006-06-09
[QUOTE=Stormy Eyes]No problem. :) I rigged my success to be the first few minutes of "Good Enough" by Van Halen, where Sammy Hagar yells out, "Hello, baby!" It makes my wife giggle every time she logs in.[/QUOTE]

Thanks Stormy Eyes, thanks to that little titbit of info, James Hetfield now shouts "So F*cking What!" when I make a typo in my PW.:D


Scares the hell out of my dog.

---

### Post by Stormy Eyes on 2006-06-09
[QUOTE=Maupertus]Thanks Stormy Eyes, thanks to that little titbit of info, James Hetfield now shouts "So F*cking What!" when I make a typo in my PW.:D[/QUOTE]

Congratulatons, you made my wife laugh.

---

### Post by Maupertus on 2006-06-09
If she wasn't married, my next step would be to buy her a drink ;)

---

