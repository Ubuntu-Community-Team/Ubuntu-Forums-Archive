---
title: "Ubuntu 9.04 not restarting"
date: 2009-11-17
forum: Server Platforms
---

### Post by hankinator on 2009-11-17
I tried restarting the server and it doesn't seem to be working.
I tried 
```
reboot
```
```
shutdown -r
```
```
shutdown -f
```
It doesn't seem to work and this is the error it gives me, can anyone help?

```
The system is going down for reboot NOW!
shutdown: timeout opening/writing control channel /dev/initctl
init: timeout opening/writing control channel /dev/initctl

```

---

### Post by Aubergines on 2009-11-17
try

```
sudo reboot -f
```

---

### Post by hankinator on 2009-11-17
Hey thanks :) that did the trick! Thank you. :)

---

