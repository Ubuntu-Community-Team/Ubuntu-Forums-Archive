---
title: "how can I edit text files stored on the server?"
date: 2011-12-12
forum: Server Platforms
---

### Post by sirspazzolot on 2011-12-12
I have a web server being chill and stuff and it's got some text files on it and I can look at them but I want to be able to edit them through a browser. how would I go about doing this? I don't want to use google docs or any equivalent service like that, because I'm too cool. thanks pals!

---

### Post by nothingspecial on 2011-12-12
You ssh into it and use a console text editor.

```
ssh user@host
nano textfile
```

Although nano may not be cool enough so you might like to use vi

:D

---

### Post by lolium on 2011-12-12
> **nothingspecial said:**
> You ssh into it and use a console text editor.

```
ssh user@host
nano textfile
```Although nano may not be cool enough so you might like to use vi

:D

Although vi is the way to go :D he's asked to be cool and do it through a web browser to be leet :)

The best thing to do would be to look for some php scripts which will let you edit them via a browser i would guess be the easiest way as there are plenty of scripts online that you can use :)

---

### Post by sirspazzolot on 2011-12-12
Alrighty, thanks! yeah, I could ssh in, but if I'm on somebody else's computer, or a school computer, that isn't the best option.

---

### Post by RealityMaster on 2011-12-12
Perhaps something like this?

[http://ubuntu.online02.com/node/6](http://ubuntu.online02.com/node/6)

---

### Post by sirspazzolot on 2011-12-12
Hm. I'll look into that as well. thanks!

---

