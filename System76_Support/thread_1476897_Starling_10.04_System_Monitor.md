---
title: "Starling 10.04 System Monitor"
date: 2010-05-08
forum: System76 Support
---

### Post by Tart on 2010-05-08
I'm experiencing some weird problem on my Starling. Every time I click on System Monitor it hangs. This happens on my wife's Starling as well. I think this is network related. I like having system monitor on top panel, so when I add it it works fine for CPU but as soon as I added Network Starling hangs.

Any ideas on how to resolve this issue?

Thanks

UPDATE. Never mind, I found Tom's post [http://ubuntuforums.org/showpost.php?p=8982022&postcount=5]("http://ubuntuforums.org/showpost.php?p=8982022&postcount=5") Problem is known from 9 version and it was not resolved ;-(

---

### Post by Tart on 2010-05-08
So if I'm traveling and I need to get info about my wireless card (MAC) how do I do it without iwconfig?

---

### Post by Flyers2391 on 2010-05-09
> **Tart said:**
> So if I'm traveling and I need to get info about my wireless card (MAC) how do I do it without iwconfig?

are you able to right click on the network icon (I'm not sure where it would be with UNR) and select "connection information" that should show you MAC, IP, DNS, Default Gateway and more

---

### Post by Tart on 2010-05-10
Thank you Flyers

---

### Post by dlavi1976 on 2010-05-11
I have the same issue on my Starling.  Clicking on the system monitor freezes the machine and crashes everything.  I did a clean install of 10.04

---

### Post by thomasaaron on 2010-05-12
This is a bug with the wireless driver. Whenever you start System Monitor or run iwconfig, you will have a kernel panic. So, don't do it.

We tried to get the best driver included in Lucid, but it didn't happen. For now, there is no fix on this, and there is a limited amount we can do, as we can't really create wireless drivers.

But this issue is definitely on our radar, and we'll continue to try to figure it out.

---

### Post by dlavi1976 on 2010-05-12
I am a bit of a novice user.  I use System Monitor to force quit when a program becomes unresponsive.  If I can't use system monitor what is the best way to force quit an unresponsive program?

---

### Post by isantop on 2010-05-12
There are other system monitors and process listers out there. One that I know for sure will do what you need it to is the KDE system monitor, KSysguard. You can install it from Software Center by searching for "ksysguard" or through the terminal.

Alternatively, if you know the name of the problem application's process, you can open a terminal (Applications > Accessories > Terminal or Accessories > Terminal from UNR) and enter ```
killall {insert process name here}
```

If you don't know the name, you can find it. From a terminal, run ```
ps -A | grep {insert application name here}
```

which will spit out a number and the name. The number will usually be four digits long, but may be five. After this, just run ```
kill {insert number}
```

For example, if I want to kill an unresponsive Firefox, I could use:
```
system76@system76-pc:~$ killall firefox
```
or
```
system76@system76-pc:~$ ps -A | grep firefox
 2628 ?        00:00:00 firefox
 2637 ?        00:03:24 firefox-bin
system76@system76-pc:~$ kill 2628
```

---

### Post by superfrogman94 on 2010-07-29
you also can Press Alt - F2 and type xkill and click on the window and it will close. :)

---

