---
title: "Having install problems after letting install run unattended"
date: 2013-06-19
forum: Ubuntu Studio
---

### Post by mcolquitt on 2013-06-19
Hi everyone,

This is my first post (obviously) and I hope it is not too whacky for you but here is my dilemma. I have been trying unsuccessfully to install Ubuntu Studio alongside windows 7 and having little patience to sit and watch a blue wheel spin around I decided to start the install up to the point where it offers the choices of running from disk, install and so on. Well I selected install and went to bed. Next morning it had gotten to a part where it was asking for my password and I never set one (obviously) so at first I just clicked like I wasn't going to install one but it would not move forward, it was determined for me to furnish it with this password I never configured. Well now I can't get it to go any further, attended or not!

Is this a ridiculous question, or can I still hold my head high? :)

Thanks for any help you may have, I am really liking what I have seen so far, I just want to be all installed and rolling along, as does everyone.

Thanks

Mark

---

### Post by zequence on 2013-06-19
Just reboot the computer, and redo the installation.

This might sound like a joke, but it is actually one way to safely shutdown and reboot your Linux OS. 
First press Shift+Ctrl+Alt+PrintScreen. Then, type the word "busier" backwards. R, E, I, S, U, B (each letter shuts something down, B reboots).

Another way that may work, is dropping into a shell. Use Ctrl+Alt+F1
then, type: 
```
shutdown -r now
```

or:
```
sudo shutdown -r now
```

---

