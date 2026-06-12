---
title: "Problems Runing Wine"
date: 2009-02-19
forum: Wine
---

### Post by bobmatino17 on 2009-02-19
I tried installing Wine on my computer and it "installed" sucessfully. I tried running Notepad as a test run for it from Applications > Wine > Programs > Notepad, and nothing, no red light blinking to signal my hard drive is doing anything no window. So i try running it from the terminal...

```
tuxiscool@tuxiscool-desktop:~$ wine
wine: error while loading shared libraries: /usr/bin/../lib/libc.so.6: cannot read file data: Error 21
tuxiscool@tuxiscool-desktop:~$ 

```

Ive never used Wine much except playing a few games but i was wondering if i could get any help...

---

### Post by Valok on 2009-02-19
IIRC, you have to run winecfg before wine will function.  SO type that into a terminal, a WINE settings window will pop up, and then you should be good to go.

---

### Post by cogadh on 2009-02-19
Just typing "wine" won't do anything, you need to tell it what to "wine", like this:
```
wine notepad.exe
```

---

### Post by bobmatino17 on 2009-02-19
ty for the info.

---

### Post by NightMKoder on 2009-02-20
> **bobmatino17 said:**
> I tried installing Wine on my computer and it "installed" sucessfully. I tried running Notepad as a test run for it from Applications > Wine > Programs > Notepad, and nothing, no red light blinking to signal my hard drive is doing anything no window. So i try running it from the terminal...

```
tuxiscool@tuxiscool-desktop:~$ wine
wine: error while loading shared libraries: /usr/bin/../lib/libc.so.6: cannot read file data: Error 21
tuxiscool@tuxiscool-desktop:~$ 

```

Ive never used Wine much except playing a few games but i was wondering if i could get any help...

Actually this is a serious error. Just typing wine should give you the usage:
```

$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit

```

[http://ubuntuforums.org/showthread.php?t=607766](http://ubuntuforums.org/showthread.php?t=607766) has something regarding libc.so.6, so I would try:
```

sudo apt-get --reinstall install libc6

```

---

### Post by bobmatino17 on 2009-02-20
well i wont be trying anything for i while. I had this great idea to upgrade from hardy to jaunty alpha after modifying apt's repositories. It didnt go well:(

---

