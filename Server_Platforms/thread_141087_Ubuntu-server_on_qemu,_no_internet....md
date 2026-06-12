---
title: "Ubuntu-server on qemu, no internet..."
date: 2006-03-07
forum: Server Platforms
---

### Post by danf_1979 on 2006-03-07
Hi,

I'm having some trouble to get internet on an ubuntu-server installed on qemu. I have installed Windows XP and with this qemu command line I DO get internet:
```

/usr/bin/qemu -hda image.img -m 240 -user-net

```
This works OK on Windows, but no internet on ubuntu-server. Any one knows why? :(
On ubuntu I get only "lo" interface when doing a ifconfig command...

Thanks

---

### Post by Glut on 2006-03-08
> On ubuntu I get only "lo" interface when doing a ifconfig command...
It means that there are no other NICs. Which then asks the question, do you have a network card? if so, what type?

---

### Post by danf_1979 on 2006-03-24
I am posting from ubuntu desktop. I have no trouble with my network. The problem is on ubuntu-server in qemu.... :(
Any ideas?

---

