---
title: "Trouble installing email server."
date: 2013-07-02
forum: Server Platforms
---

### Post by NuxNik on 2013-07-02
Hello,

I'm trying to follow the Ubuntu install Mail server menu
I have reached a point where there may be a mistake on the page
  ---[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

At the step where the instructions are:
..
  touch smtpd.key
  chmod 600 smtpd.key 
  openssl genrsa 1024 > smtpd.key

I get the error message permission denied
I am assuming that the touch smtpd.key is supposed to be in the same directory as
  [COLOR=#333333][FONT=monospace]/etc/postfix/sasl/smtpd.conf
[/FONT][/COLOR]
I also tried 
  sudo [COLOR=#333333][FONT=UbuntuMono]openssl genrsa 1024 > smtpd.key
but no joy..

Can anyone tell me what happened, why I'm blocked, and how to continue ?

============================================================

Addendum

After going through the guide a couple of times, I realized that I was supposed to create the file in my own directory and move it over after the keys have been created...



[/FONT][/COLOR]

---

### Post by Bucky Ball on 2013-07-02
***Post moved to own thread.***

Please do not hijack threads. It reduces your chances of getting help, dilutes community effort, is confusing and unfair to the original poster. Change the title of this thread to sumothing more appropriate if you want (you have half hour to do so otherwise let me know). Thanks and good luck.

---

### Post by NuxNik on 2013-07-03
> **Bucky Ball said:**
> ***Post moved to own thread.***

Please do not hijack threads. It reduces your chances of getting help, dilutes community effort, is confusing and unfair to the original poster. Change the title of this thread to sumothing more appropriate if you want (you have half hour to do so otherwise let me know). Thanks and good luck.


My apologies.

Won't happen again..

---

