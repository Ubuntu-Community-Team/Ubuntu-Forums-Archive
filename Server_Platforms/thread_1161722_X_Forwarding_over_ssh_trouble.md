---
title: "X Forwarding over ssh trouble"
date: 2009-05-17
forum: Server Platforms
---

### Post by Tactical Fart on 2009-05-17
I looked around the internet to figure out how to get "X Forwarding over ssh" working. I eventually got to the point where I could 
```
firefox &
```
and a window would pop up and allow me to use firefox from my remote machine. (I even got vlc working perfectly... slow framerate, but it still worked and I counted that as a victory) But after a reboot, I'm getting
```
Error: cannot open display: localhost:10.0
```
again. I don't know what I did right the first time around. I configured my /etc/ssh/sshd_config so that it has "X11Forwarding yes" (no quotes). Like I said, I had it running nice at first, but after a reboot, the same error I've always been getting. The client I'm using is Bitvice Tunneler. Anyone know what I did right/wrong?

---

### Post by drave on 2009-05-17
try "xhost +"

its an X windows permission thing.

---

### Post by Tactical Fart on 2009-05-17
I get
```
xhost: unable to open display "localhost:10.0"
```

---

