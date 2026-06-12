---
title: "Laptop's mic does not seems to work"
date: 2012-10-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-10-01
external mic works just fine, but the built in one not so much
[FONT=Courier New]~$ lspci | grep Audio
00:07.0 Audio device: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)[/FONT]
it shows up, ut will not detect any sound (tap on plastic near it does nothing)

---

### Post by cariboo on 2012-10-01
Check:

```
alsamixer
```

to make sure the internal mic isn't muted.

Once you've made your changes, press esc to exit, then to save the changes you've made, use the following command:

```
sudo alsactl store
```

See the screenshot of alsamixer on my system.

---

### Post by pqwoerituytrueiwoq on 2012-10-01
it is not muted in alsamizer

---

