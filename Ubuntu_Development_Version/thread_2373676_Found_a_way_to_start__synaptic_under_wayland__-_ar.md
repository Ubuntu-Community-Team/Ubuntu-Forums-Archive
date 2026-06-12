---
title: "Found a way to start  synaptic under wayland  - are there security risks ?"
date: 2017-10-08
forum: Ubuntu Development Version
---

### Post by meijer.o on 2017-10-08
I found a very easy way to start synaptic under Wayland. Only two steps are needed.

Step 1
Open /etc/bash.bashrc and add the line:
```
xhost +SI:localuser:root
```

Step 2
Open /usr/share/applications/synaptic.desktop

And change the line 
```
Terminal=false
``` 
into
```
Terminal=true
```

Now synapic will work like it does under Xorg.

But are there any security risks, can someone give an explanation?

Thanks for replying.

Otto

---

### Post by dino99 on 2017-10-09
What's the need to open a new thread for copying/pasting an already existing one ?;)

---

