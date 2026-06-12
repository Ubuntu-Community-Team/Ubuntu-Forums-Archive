---
title: "Disable Wine Debugging: Oblivion GOTY"
date: 2009-11-26
forum: Wine
---

### Post by robertneville777 on 2009-11-26
Hey guys I've been following the instructions from [http://www.uesp.net/wiki/oblivion:linux]("http://www.uesp.net/wiki/oblivion:linux") and I now have Oblivion installed. It "runs," but the VIDEO runs slow. Now, the AUDIO comes in fine: there's no lag there. I'm sure it's the Wine debugging that's slowing the game down. I've tried following their intructions on making the script that disbales wine debugging, but, honestly, I have no idea on how to build the script (what exactly to put in and in what order). Please, can somebody help me in making the script to disable the wine debug for Oblivion? I want to play Oblivion really bad ;) 

Thanks! :D

--robertneville777

---

### Post by hikaricore on 2009-11-26
```
WINEDEBUG=fixme-all,err-all,warn+cursor,-all wine program.exe
```

Should do the trick.

---

### Post by robertneville777 on 2009-11-28
Dude thanks! With that and a tad more of tweaking added, Oblivion runs nice! Thank you very much man! And God bless you! ...Hopefully you're not atheist, hahah, nah, just kiddin, but really thanks!

--robertneville777

---

