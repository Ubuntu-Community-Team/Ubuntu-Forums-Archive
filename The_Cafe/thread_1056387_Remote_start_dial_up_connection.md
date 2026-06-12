---
title: "Remote start dial up connection"
date: 2009-01-31
forum: The Cafe
---

### Post by Odd_sam on 2009-01-31
This is probably the wrong forum for this but oh well kinda new here *points to post count*

Anyways. Here's my thoughts. See I am suck on dial up, however I am frequently in locations where if I had access to my computer's Hard drive I would be a little better off. I've got only one phone line but if I'm not home I don't need it. So I got to thinking is there a way to tell my computer to dial into my ISP on it's own and start say an ftp server so I can access files stored on my computer. 

My idea is using my cell phone I would call my house phone. I would have my modem set using something so that if a incoming call is detected it will pick up the line and listen in. I would punch a PIN into my cell phone and my modem would check it against a file, if correct it would hang up and start vwdial in the terminal.


My question is, how plausible is this as far as making it work? Can a generic hardware modem be programed to work in such a way?

---

### Post by Daveski on 2009-01-31
Simpler solution is to run a program that monitors the serial line. When the phone rings the modem sends the text string 'RING'. You could program it easily to count the rings, if only 1 is detected before the caller hangs up for example, that could trigger it to dial the ISP.

As a precaution, you could get it to automatically disconnect if the server is not accessed within a few minutes.

---

### Post by Odd_sam on 2009-01-31
epic that's almost exactly what I want to do. Can some one point me in the right direction to get started?

---

### Post by Daveski on 2009-02-01
Dunno if there are any good tools specifically designed for this sort of thing, but if you are comfortable coding scripts in bash or python, then it should be fairly easy.

Failing that, bolt some other tools together. Here is some a quick google turned up:

[http://www.ibiblio.org/pub/linux/system/serial/!INDEX.html](http://www.ibiblio.org/pub/linux/system/serial/!INDEX.html)

---

### Post by Odd_sam on 2009-02-01
I found a solution. xringd it takes a bit to get the right config file but it works amazingly.

---

### Post by Daveski on 2009-02-02
That sounds perfect. Excellent.

---

