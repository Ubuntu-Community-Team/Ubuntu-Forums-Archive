---
title: "Set unity/compiz back to default"
date: 2012-09-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by stinkeye on 2012-09-13
How do you set unity/compiz back to default in Quantal?

---

### Post by mc4man on 2012-09-13
This will take care of a lot of it
[http://ubuntuforums.org/showpost.php?p=12222839&postcount=9](http://ubuntuforums.org/showpost.php?p=12222839&postcount=9)

---

### Post by stinkeye on 2012-09-13
Ok thanks.

Running in terminal... 
```
dconf reset -f /org/compiz/
```

followed by 
```
compiz --replace & disown

```

works for me.

I tried
```
dconf reset -f /org/compiz/ && compiz --replace
```
but got errors.
```
[COLOR="Olive"]glen@Quantal:~$[/COLOR] dconf reset -f /org/compiz/ && compiz --replace
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - **Error: Another window manager is already running on screen: 0**
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core
```

---

