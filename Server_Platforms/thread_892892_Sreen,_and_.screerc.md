---
title: "Sreen, and .screerc"
date: 2008-08-17
forum: Server Platforms
---

### Post by path_mcgohenn on 2008-08-17
I am attempting to configure screen to use a .screenrc on my server. I was a little suprised when screen didn't generate at least a default rc file.

I have created a basic file. but it doesn't appear to be loading it during execution. Everytime I start screen I get the default GNU lisence message.

Any suggestions?

---

### Post by path_mcgohenn on 2008-08-17
I have gotten the program to register my .screenrc. Now how do I get it to accept the license and not show it every time i start a screen session?

---

### Post by littlegreiger on 2008-08-17
to get it to accept the license just add this to the file
```
startup_message off
```

---

