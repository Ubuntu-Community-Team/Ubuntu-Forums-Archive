---
title: "Gazpro6, updated this morning and now can't log in"
date: 2016-11-10
forum: System76 Support
---

### Post by sviginak on 2016-11-10
Type in my password and press enter, after a brief pause screen goes black, then appears to be blank and backlit?, then goes back to my login screen. It does not say my PW is wrong and I know it is right. After I try three times screen goes black.

---

### Post by sviginak on 2016-11-11
Thinking it might be a security issue. I am at a B&B with no wifi password. Before I log in to computer I do not connect to wifi automatically, and when I try it says insufficient privileges. Usual suspect .Xauthority owner is not the problem.

---

### Post by sviginak on 2016-11-13
sudo apt-get purge nvidia* worked, but in the meantime I had loaded Lubuntu which someone suggested earlier (but that didn't work). Now I would like to get rid of Lubuntu. Also, how do you mark a question as Solved?

---

### Post by philinux on 2016-11-13
Yes I had to purge nvidia too. 
Just below the thread title click on thread tools to mark solved.

---

### Post by sviginak on 2016-12-17
philinux - I still have the Lubuntu log in screen to get rid of. Also, I followed the link to remove old kernels, I am wondering if I should do that. I have a long list of stuff when I step through your six step process, below is after step 4;
```
linux-base
linux-firmware
linux-generic
linux-headers-3.13.0-36
linux-headers-3.13.0-36-generic
linux-headers-3.13.0-37
linux-headers-3.13.0-37-generic
linux-headers-3.13.0-43
linux-headers-3.13.0-43-generic
linux-headers-3.13.0-44
linux-headers-3.13.0-45
linux-headers-3.13.0-46
linux-headers-3.13.0-46-generic
linux-headers-3.13.0-48
linux-headers-3.13.0-48-generic
linux-headers-3.13.0-52
linux-headers-3.13.0-53
linux-headers-3.13.0-53-generic
linux-headers-3.13.0-54
linux-headers-3.13.0-54-generic
linux-headers-3.13.0-58
linux-headers-3.13.0-58-generic
linux-headers-3.13.0-62
linux-headers-3.13.0-62-generic
linux-headers-3.13.0-63
linux-headers-3.13.0-63-generic
linux-headers-3.13.0-65
linux-headers-3.13.0-65-generic
linux-headers-3.13.0-66
linux-headers-3.13.0-66-generic
linux-headers-3.13.0-67
linux-headers-3.13.0-68
linux-headers-3.13.0-70
linux-headers-3.13.0-70-generic
linux-headers-3.13.0-73
linux-headers-3.13.0-73-generic
linux-headers-3.13.0-74
linux-headers-3.13.0-77
linux-headers-3.13.0-79
linux-headers-3.13.0-79-generic
linux-headers-3.13.0-83
linux-headers-3.13.0-83-generic
linux-headers-3.13.0-85
linux-headers-3.13.0-85-generic
linux-headers-3.13.0-88
linux-headers-3.13.0-88-generic
linux-headers-3.13.0-92
linux-headers-3.13.0-92-generic
linux-headers-4.4.0-45
linux-headers-4.4.0-45-generic
linux-headers-4.4.0-47
linux-headers-4.4.0-47-generic
linux-headers-4.4.0-51
linux-headers-4.4.0-51-generic
linux-headers-generic
linux-image-2.6.38-15-generic
linux-image-3.0.0-21-generic
linux-image-3.13.0-36-generic
linux-image-3.13.0-37-generic
linux-image-3.13.0-39-generic
linux-image-3.13.0-40-generic
linux-image-3.13.0-43-generic
linux-image-3.13.0-44-generic
linux-image-3.13.0-48-generic
linux-image-3.13.0-49-generic
linux-image-3.13.0-52-generic
linux-image-3.13.0-53-generic
linux-image-3.13.0-54-generic
linux-image-3.13.0-57-generic
linux-image-3.13.0-58-generic
linux-image-3.13.0-59-generic
linux-image-3.13.0-62-generic
linux-image-3.13.0-63-generic
linux-image-3.13.0-65-generic
linux-image-3.13.0-66-generic
linux-image-3.13.0-67-generic
linux-image-3.13.0-68-generic
linux-image-3.13.0-70-generic
linux-image-3.13.0-73-generic
linux-image-3.13.0-76-generic
linux-image-3.13.0-77-generic
linux-image-3.13.0-79-generic
linux-image-3.13.0-85-generic
linux-image-3.13.0-88-generic
linux-image-3.13.0-92-generic
linux-image-3.13.0-93-generic
linux-image-3.13.0-95-generic
linux-image-3.2.0-67-generic
linux-image-4.4.0-45-generic
linux-image-4.4.0-47-generic
linux-image-4.4.0-51-generic
linux-image-extra-3.13.0-37-generic
linux-image-extra-3.13.0-39-generic
linux-image-extra-3.13.0-43-generic
linux-image-extra-3.13.0-44-generic
linux-image-extra-3.13.0-49-generic
linux-image-extra-3.13.0-53-generic
linux-image-extra-3.13.0-54-generic
linux-image-extra-3.13.0-58-generic
linux-image-extra-3.13.0-59-generic
linux-image-extra-3.13.0-62-generic
linux-image-extra-3.13.0-63-generic
linux-image-extra-3.13.0-65-generic
linux-image-extra-3.13.0-66-generic
linux-image-extra-3.13.0-68-generic
linux-image-extra-3.13.0-70-generic
linux-image-extra-3.13.0-73-generic
linux-image-extra-3.13.0-77-generic
linux-image-extra-3.13.0-85-generic
linux-image-extra-3.13.0-92-generic
linux-image-extra-3.13.0-93-generic
linux-image-extra-3.13.0-95-generic
linux-image-extra-4.4.0-45-generic
linux-image-extra-4.4.0-47-generic
linux-image-extra-4.4.0-51-generic
linux-image-generic

```

---

