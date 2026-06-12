---
title: "CLI input problem - need help"
date: 2010-05-23
forum: Server Platforms
---

### Post by nejkica on 2010-05-23
Hey guys!

I'm quite new to this server stuff and I have a problem, that I cannot find a solution to.

If I login via putty everything looks normal and works. Also server works, the web pages are OK.
When I login directly to cli (tried usb and ps/2 keyboard) everything works OK untill I start one of the "graphics" program, such as nano, mc, htop ... The keypresses start acting weird, display shows strange stuf. When I press up, down arrows some command get executed as if I pressed something else. Cannot exit, F10 doesnt work. it starts to display output in the top middle of the screen - it's hard to describe.

Oh, I have Ubuntu server 9.10 installed and it worked fine for 6 months and I don't know exactly when this started to happen, because I use putty and there everything works perfectly fine.

Please help, it's very frustrating.

thanks.

---

### Post by mstjohn1974 on 2010-05-27
I don't know ...probably sounds stupid but did you swapped the keyboard?

---

### Post by arrrghhh on 2010-05-27
Do you _need_ to access the server locally?  I always thought most accessed them remotely.

I don't have any explanation for that however, my server is just fine with a physical keyboard.  I only have USB, but it looks like you tried a different keyboard correct?  You didn't just put a converter plug on the keyboard did you?

---

### Post by hictio on 2010-05-28
I might be wrong, but it sounds to me like you have a problem with ncurses libraries.
After executing any of those programs, if you are able to get back to the prompt, have you tried typing 'reset' and ENTER.
(It won reset the server ;) only the Terminal values, check the man page on another box:

```

man reset ENTER

```

---

