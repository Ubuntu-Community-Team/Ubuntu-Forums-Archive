---
title: "IE4Linux and Juanty"
date: 2009-06-08
forum: Wine
---

### Post by lsutiger on 2009-06-08
Has anyone been able to install IE4Linux successfully in Juanty? I keep getting errors of corrupt files at installation or it downloads files at 130+%.

Odd...

---

### Post by ChaiTan on 2009-06-09
Instead of using IE4sLinux, use winetricks to install IE6
```
wget http://www.kegel.com/wine/winetricks
chmod +x winetricks
./winetricks ie6
```

you could use a different wineprefix if you don't wish to disturb the default one.
```
env WINEPREFIX=~/.wineie6 ./winetricks ie6
```

---

### Post by aysiu on 2009-06-09
Yes, I have successfully installed it in Jaunty. I know that doesn't help you.

---

