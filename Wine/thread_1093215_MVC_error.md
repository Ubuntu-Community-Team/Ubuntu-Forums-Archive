---
title: "MVC error"
date: 2009-03-11
forum: Wine
---

### Post by Whisper45 on 2009-03-11
> **Whisper45 said:**
> (Almost) Every time I try and open a .exe with 'Wine Windows Program Loader', nothing works and I get this error:

```
Runtime Error!

Program: C:\windows\Microsoft.NET\Framework\v2.0.50727\mscorsvw.exe

R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the application's support team for more information.
```

I first got this problem when...:

I was trying to install Sony Vegas 7.0, so I look on these forums to see if it is possible to have .NET Framework 2.0 on Ubuntu. I find out: it is, using Winetricks.
So I follow the instructions, and load winetricks.
Out of the list I choose .NET framework 2.0 (or something similar) click install and voila. So I go back to the Vegas setup, launch it again and...

I get that error.

How can I fix this?
Thanks.

Original thread (I thought I might get more help if I post this here):
[http://ubuntuforums.org/newreply.php?do=newreply&p=6872600](http://ubuntuforums.org/newreply.php?do=newreply&p=6872600)

---

### Post by cogadh on 2009-03-11
Run the application from the terminal and post Wine's output here. When run from the terminal, Wine outputs its own error and information messages that may explain what is happening.

---

