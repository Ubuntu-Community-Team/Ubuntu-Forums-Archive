---
title: "Does not execute bash command for .Xresources"
date: 2018-07-16
forum: Ubuntu Development Version
---

### Post by VMC on 2018-07-16
.xinitrc:
```
# exec openbox-session
[B]xrdb -merge -I$HOME ~/.Xresources
[/B][[ -f ~/.Xresources ]] && **xrdb -merge -I$HOME ~/.Xresources**
exec startlxqt
```

```
$ ls .Xresources
.Xresources
```

As you can see, the above files are in place, but "**xrdb -merge -I$HOME ~/.Xresources**" never gets executed. As shown, I needed to place it on a line by itself.
Xubuntu, Ubuntu, Debian, an a host of other linuxes all work correctly, without  "xrdb" on a separate line.. Lubuntu does not. The logic is correct.

---

### Post by VMC on 2018-07-17
Changing "[[" and ""]]" to a single "[" "]" fixes the problem, although everywhere I google it shows double braces, and they work on every distro except Lubuntu LXQT.
This only effects 'getty' auto login and not DM auto login. Too obscure to file a bug report.
I'll just make this solved for now.

If I use bash while online it works with either 1 or 2 braces.

---

