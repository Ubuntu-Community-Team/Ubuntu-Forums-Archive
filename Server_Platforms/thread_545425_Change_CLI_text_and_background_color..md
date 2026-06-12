---
title: "Change CLI text and background color."
date: 2007-09-07
forum: Server Platforms
---

### Post by OldGaf on 2007-09-07
I have a several servers running and would like to be able to change the text and/or back ground color on them to make them easily identified.

I have changed the resolution with vga=791which makes them MUCH easier to work with, but as stated, changing fond & back ground colors would be great.

Can anyone help me with this?

---

### Post by robert_pectol on 2007-09-07
Paste this at the command line for a colorful treat:
```
pass=0; while [ $pass -lt "8" ]; do echo -e "\033[1;3${pass}m"; echo "hello"; pass=$(($pass + 1)); sleep 1; done; echo -e "\033[1;0m"
```
This at least demonstrates some of the basic colors available and how to specify them.  Enjoy!

---

### Post by OldGaf on 2007-09-11
Thank you for your reply.

Is there a list you can point me to of other colors I can use or it that all of them?

Also, is it possible to change the back ground?

Thanks again,

---

### Post by robert_pectol on 2007-09-11
Yes, and yes.  First of all, the best, "list" I can point you to is what google turns up with the simple search terms, "linux terminal colors."  There are many pages that go into a lot of detail so I won't do it here.  But yes, you can do all sorts of things like highlighting, reverse contrast, blinking,  bright, dim, underline, background colors, etc.  Good luck.

---

### Post by bodhi.zazen on 2007-09-11
This is an awesome link : [http://www.gentoo.org/doc/en/articles/prompt-magic.xml](http://www.gentoo.org/doc/en/articles/prompt-magic.xml)

As are these :

[http://www.linuxjournal.com/article/8603](http://www.linuxjournal.com/article/8603)

[http://tldp.org/LDP/abs/html/colorizing.html](http://tldp.org/LDP/abs/html/colorizing.html)


Enjoy !

---

### Post by OldGaf on 2007-09-11
> **robert_pectol said:**
> Yes, and yes.  First of all, the best, "list" I can point you to is what google turns up with the simple search terms, "linux terminal colors."  There are many pages that go into a lot of detail so I won't do it here.  But yes, you can do all sorts of things like highlighting, reverse contrast, blinking,  bright, dim, underline, background colors, etc.  Good luck.

Thanks a bunch......

I did actually spend a lot of time on google before posting, but they all seem to refer to virtual consoles...........

---

