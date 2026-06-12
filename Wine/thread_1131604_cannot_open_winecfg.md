---
title: "cannot open winecfg"
date: 2009-04-21
forum: Wine
---

### Post by bubuzzz on 2009-04-21
hi all, 

 After installing some games (warcraft 3, max payne) using Wine, i cannot open wincfg anymore, even though everything else is still fine (add/remove program, playing game...). This is the error message in my terminal

```

bubuzzz@dell-desktop:~$ wine --version
wine-1.1.19
bubuzzz@dell-desktop:~$ winecfg
err:seh:setup_exception_record stack overflow 816 bytes in thread 0009 eip b7d0df7e esp 00231000 stack 0x230000-0x231000-0x330000
bubuzzz@dell-desktop:~$
``` 

Can anyone suggest me some ways to solve it? I am using ubuntu 8.04 with GeForce 8400 GMS and the driver version is 173.14.02 

Thanks.

---

### Post by hikaricore on 2009-04-21
First try:

> sudo apt-get install --reinstall wine

If that doesn't work try downloading the previous release of WINE for your Ubuntu release here and installing it.
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
For example you're using 1.1.19 now, try 1.1.18.  Sometimes there are bugs in the new packages and they go unnoticed.

---

### Post by bubuzzz on 2009-04-21
well, the reinstallation didn't work. Maybe i just keep it there and continue updating the system until they fix all the bugs coz if i install the previous version, maybe all the games don't work anymore. Thank anyway.

---

### Post by NightMKoder on 2009-04-21
Thats not a wine bug. You probably added some override that you shouldn't have.

Open ~/.wine/user.reg in an editor (gedit, kate), find the line that looks like:
```

Software\\Wine\\DllOverrides

```
and erase the entries under it. Like, if you have:
```

[Software\\Wine\\DllOverrides] 1240202576
"msxml3"="native,builtin"
"riched20"="native,builtin"
"usp10"="native,builtin"

[Software\\Wine\\Drivers] 1231744680
"Audio"="alsa"

```

change it to
```

[Software\\Wine\\DllOverrides] 1240202576

[Software\\Wine\\Drivers] 1231744680
"Audio"="alsa"

```

---

### Post by bubuzzz on 2009-04-22
well, i didn't add any dll libs to wine. All the games work smoothly without configuring anthing after installations. So, I cannot find Software\\Wine\\DllOverrides

---

### Post by bubuzzz on 2009-04-22
one more thing, i want to open wineconfig because in max payne, i cannot play it in the full screen. The game covers almost the screen, except the top panel. So, is there any way to solve it ?

---

### Post by dubbelodub on 2010-09-12
> **NightMKoder said:**
> Thats not a wine bug. You probably added some override that you shouldn't have.

Open ~/.wine/user.reg in an editor (gedit, kate), find the line that looks like:
```

Software\\Wine\\DllOverrides

```
and erase the entries under it. Like, if you have:
```

[Software\\Wine\\DllOverrides] 1240202576
"msxml3"="native,builtin"
"riched20"="native,builtin"
"usp10"="native,builtin"

[Software\\Wine\\Drivers] 1231744680
"Audio"="alsa"

```

change it to
```

[Software\\Wine\\DllOverrides] 1240202576

[Software\\Wine\\Drivers] 1231744680
"Audio"="alsa"

```

Thank you soooooo much

---

