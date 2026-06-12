---
title: "OTR -- encrypted garbage displayed"
date: 2008-11-26
forum: Security
---

### Post by Jav13r on 2008-11-26
I have this problem with OTR. It's displaying the encrypted garbage. Other then that it works, the recipient receives a plain text message.
How could I fix this?
Note: I'm using OTR plugin for Pidgin under Vista.

Screenshot:
[img]http://i36.tinypic.com/69gjk3.png[/img]

---

### Post by kevdog on 2008-11-26
Hmmm

That's very interesting -- glad to know the program actually encrypts.  I've used the OTR plugin with WinXP and pidgin and it doesn't function like that.  Never tried with Vista.

---

### Post by Jav13r on 2008-11-29
Problem solved.
The cause of this error was the "Message Splitter" plugin I've used for pidign, after I disabled the splitter, there was no more garbage displayed in my chat window, but plain text.

---

### Post by kevdog on 2008-11-29
Where did you obtain that plugin?

---

### Post by Jav13r on 2008-11-30
> **kevdog said:**
> Where did you obtain that plugin?

I got it many months ago, after a long search, I think it was a german website. I'm sure you can find it somewhere on the internet if you search long enough.

Anyway, I've also uploaded the one I have, just in case:
```
http://rapidshare.de/files/41029537/splitter.dll.html
```

---

### Post by kevdog on 2008-11-30
I compiled pidgin from source, and in at least one of the plugin packs I compiled Ive noticed this plugin to be already installed -- it called
message splitter 2.40.  Maybe its in the default install?  Why did you need to install it in the first place?

---

