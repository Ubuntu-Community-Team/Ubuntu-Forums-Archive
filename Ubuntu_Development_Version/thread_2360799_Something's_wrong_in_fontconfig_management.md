---
title: "Something's wrong in fontconfig management"
date: 2017-05-08
forum: Ubuntu Development Version
---

### Post by fthx on 2017-05-08
Hi,

I remember a thread where I asked for Jeremy Bicha about missing fonts in Thunderbird in Zesty (if my memory is not wrong).
The solution I found was to reinstall fontconfig package to regenerate fonts cache (there is another way to do that, but simply reinstall is quick).

Today in Firefox a lot of letters were missing in :
[http://www.omgubuntu.co.uk/2017/05/get-the-look-ubuntu-dash-to-panel](http://www.omgubuntu.co.uk/2017/05/get-the-look-ubuntu-dash-to-panel)
so I had to activate the emergency plan with fontconfig...

What's wrong ? It *seems* to me that it should miss this regeneration of fonts cache after upgrading some packages, but I reached the limits of my knowledge/intuition here... ^_^

---

### Post by #&amp;thj^% on 2017-05-08
rebuild the font cache with 
```
fc-cache -f -v
```

---

