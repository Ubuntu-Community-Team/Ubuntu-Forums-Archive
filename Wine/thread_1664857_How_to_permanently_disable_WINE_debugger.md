---
title: "How to permanently disable WINE debugger"
date: 2011-01-11
forum: Wine
---

### Post by djevlen on 2011-01-11
Please tell me how to permanently disable debugger in wine.


Ubuntu 10.04 LTS - Lucid Lynx
Wine-1.2

---

### Post by Cadeyrn on 2011-01-13
Why would you want to do that? WINE doesn't even debug unless you tell it to.

---

### Post by cogadh on 2011-01-14
Are you talking about the very basic debug output you get when normally running programs through Wine in the terminal (the "fixme" errors and such)? If so, you can't disable that permanently, it can only be disabled on an app-by-app basis by simply prepending your Wine command with "WINEDEBUG=-all":
```
WINEDEBUG=-all wine foo.exe
```
You can actually do quite a few things with that command, some details here: [http://wiki.winehq.org/DebugChannels](http://wiki.winehq.org/DebugChannels)

---

### Post by djevlen on 2011-01-19
i want to disable debugger because i get this error when trying to run windows program in wine.

Program is called ACM MT4 (small program for currency trading)
size 4.4 mb
download link : [http://mt4.ac-markets.com/acm4setup.exe](http://mt4.ac-markets.com/acm4setup.exe)
I get this error after the program has updated itself from  v.4.00 build 225 to v.4.00 build 229

If you want to see some error output then please tell me step by step what to do . I am still an ubuntu beginner :)

---

### Post by djevlen on 2011-01-19
i want to disable debugger because i get this error when trying to run windows program in wine.

Program is called ACM MT4 (little program to trade currency markets)
Here is the download link :[http://mt4.ac-markets.com/acm4setup.exe](http://mt4.ac-markets.com/acm4setup.exe)
size:4,4 mb

If you want to see some error output then please tell me step by step what to do . I am still an ubuntu beginner :)

---

### Post by djevlen on 2011-01-19
sry..double-post..

---

