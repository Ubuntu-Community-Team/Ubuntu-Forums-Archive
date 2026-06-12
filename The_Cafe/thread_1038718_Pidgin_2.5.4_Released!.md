---
title: "Pidgin 2.5.4 Released!"
date: 2009-01-13
forum: The Cafe
---

### Post by Kosimo on 2009-01-13
Pidgin team has just released a new version: **2.5.4** Which fixes a critical connection bug in MSN network, and has also more bugfixes.

Here the changelog:

libpurple:
· Fix a connection timeout with empty Gadu-Gady buddy lists. (Martin Rosinski)
· Don't ignore namespace information when parsing XMPP data. (Michal Witkowski)
· Fix a crash that occurred when retrieving certain Offline Messages on MSN.
· Extended purple-url-handler to handle "gtalk" URI's. (Paul Aurich)
· Fix the hang on exit in Network Location Awareness for Windows XP and Windows Vista. (Paul Aurich)

MSN:
· Change Contact Server to temporarily fix connection problems. (Thanks to Youness Alaoui)

XMPP:
· Support for XEP-0191 blocking. (Vijay Raghunathan)
· Don't put SASL PLAIN or IQ Auth passwords in debug logs. (Paul Aurich)
· Fix removal of avatars (both PEP and vCard), we weren't removing them correctly before. (Paul Aurich)

Pidgin:
· Fix a crash in the Add Account dialog when changing protocols under certain circumstances.

Finch:
· Redirect stderr outputs to the debug window.
· Fix rebinding actions with the arrow-keys and tab.


As always:

Download the source code.
Then
```
./configure
make
sudo make install
```


Or download an easy deb from [Getdeb]("http://www.getdeb.net/app/Pidgin")

---

### Post by binbash on 2009-01-14
I am glad they fixed the msn issue

---

### Post by Nevon on 2009-01-14
I got it yesterday, but for some reason MSN still wouldn't work. Msn-pecan did, but... It sucks. Regular MSN didn't give me the "cannot connect to address book" error message, but instead my contacts just never showed up.

---

### Post by airjaw on 2009-01-14
That "crash upon exit" bug in XP was really annoying.. I uninstalled 2.5.3 and reinstalled 2.5.2

I don't really see any point in upgrading to 2.5.4

---

### Post by kevdog on 2009-01-14
Here is further compile instructions -- haven't updated to 2.5.4 yet, but the process is exactly the same except for revision number.  I just compiled last night and all is working well:

[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

---

### Post by Kosimo on 2009-01-14
Guys... I don't know what's happening to you but... I couldn't connect to MSN network using 2.5.x (for the very known bug) And this particular bug has been fixed with 2.5.4. I've installed using getdeb .deb's and is working perfectly.

---

### Post by ithanium on 2009-01-14
updated, works good!

---

### Post by Polygon on 2009-01-14
the hang on exit was VERY annoying on windows. im glad they fixed it

---

### Post by stormtrooprdave on 2009-01-14
Is there a pidgin repository so I can get it through backports?

---

### Post by Polygon on 2009-01-14
no, you can get it through getdeb however

---

