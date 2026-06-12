---
title: "Wine sound troubles"
date: 2009-08-26
forum: Wine
---

### Post by Piro24 on 2009-08-26
Hello everyone.

I'm having a problem with sound in Wine. Basically, I cannot play a game (cs 1.6 non steam) with sound if I have rhythmbox open, or any other program that is using sound. I know it's possible to do this, because I was able to do this outofthebox on another installation, but I had to reformat and reinstall.

Now, I can either have the mp3 playing, and no sound in the game, or the no mp3, but sound in the game. Thanks for any suggestions.

---

### Post by ajgreeny on 2009-08-26
Have you changed your sound configuration to stop pulse?  Try changing the choices in System > Preferences > Sound and see if it helps.

---

### Post by Piro24 on 2009-08-26
It doesnt have any effect, my mp3's still play, but no in game sounds will play.

---

### Post by eriktheblu on 2009-08-26
Is the program set to OSS audio in your Wine configuration?

I've read on occasion that the alsa-oss package can be helpful in similar situations.

[https://help.ubuntu.com/community/alsa-oss]("https://help.ubuntu.com/community/alsa-oss")

---

