---
title: "scanning in ubuntu"
date: 2010-02-09
forum: Wine
---

### Post by matifsyed on 2010-02-09
hi dear friends

i have hp scanjet g2410 scanner but it does not work on ubuntu, when i start the scan program the message no devices available appear pls help me
thanks a
ashah

---

### Post by OrangeCrate on 2010-02-09
Have you tried Xsane Image Scanner? (Go to Applications > Graphics...)

I have an HP Officejet J4550 all-in-one, and it recognizes the scanner.

---

### Post by hikaricore on 2010-02-09
Considering this is posted under wine i suspect the OP has tried to install windows based software for his scanner for use on linux. lol..
Try the suggestion above as you are currently doing it wrong.

---

### Post by OrangeCrate on 2010-02-09
> **hikaricore said:**
> **Considering this is posted under wine** i suspect the OP has tried to install windows based software for his scanner for use on linux. lol..
**Try the suggestion above as you are currently doing it wrong**.

Never even noticed it was in the Wine sub-forum, just picked it out of the New Posts...

I confirm hikaricore's advice to you, sorry for any confusion on my part. From Ubuntu, please follow my original suggestion, and you should be fine.

---

### Post by matifsyed on 2010-02-10
> **OrangeCrate said:**
> Have you tried Xsane Image Scanner? (Go to Applications > Graphics...)

I have an HP Officejet J4550 all-in-one, and it recognizes the scanner.
i have tried the xsane image scanner program but all in vain
pls help me

---

### Post by OrangeCrate on 2010-02-10
> **matifsyed said:**
> i have tried the xsane image scanner program but all in vain
pls help me

Not being an expert on printers/scanners, I don't know what to tell you to do next.

From 8.10 onwards, Ubuntu picks up pretty much anything HP (HP is very well supported for Linux). Without having my hands on your computer, I would only be making guesses here, as to what your problem might be.

If you happen to be using 8.04, it's a little more complicated to get Xsane to recognize the scanner. It's been a long time since I've thought about this, but here's some info to ponder. I remember using these instructions to install a scanner in Debian Lenny, and I assume it would be the same with Hardy.

At the terminal, using sudo:

```
apt-get install hpoj
```

Then:
 
```
/etc/init.d/hpoj setup
```

This gave you a dialog to setup the printer/scanner.

That's all I remember, and I'm sorry, but I don't have anything more to contribute to help you. Some kind soul might come along that knows more about scanners than I do, or you might try searching for additional information both here on the forums, and on the web.

Good luck...

---

