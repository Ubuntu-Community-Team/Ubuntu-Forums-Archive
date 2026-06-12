---
title: "Computer fully booted batch file"
date: 2012-05-19
forum: Server Platforms
---

### Post by JasonMarquez on 2012-05-19
I have my server set to start from my Windows 7 computer when I use by a batch file that uses WOL. In my batch file, I would like it to do some kind of while statement that will wait until the server is absolutely booted up completely. Then the batch file will tell me that the server is started up. I would like this so I know that my server has started up, even when I'm not around to actually see that it has.

Can someone help me write the code for that? It is for a batch file.

So to make it easier to understand:

-First runs the wol to turn it on (already taken care of)
-Then has something that will continuesly check if the server is fully booted up into Ubuntu 10.04
-When it confirms it's fully booted up, it will then let me know from my Windows computer batch file

---

### Post by koenn on 2012-05-20
```


:REPEAT
ping server
if not %errorlevel% == 0 GOTO REPEAT

echo server appears up


```

---

### Post by JasonMarquez on 2012-05-20
> **koenn said:**
> ```


:REPEAT
ping server
if not %errorlevel% == 0 GOTO REPEAT

echo server appears up


```

Thanks! Works great! Is there a way to not display the pinging process?

---

### Post by JasonMarquez on 2012-05-20
Nevermind got it

---

