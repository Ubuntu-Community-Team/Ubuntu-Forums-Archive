---
title: "How do I move faster in the terminal?"
date: 2016-01-06
forum: Server Platforms
---

### Post by Higgins909 on 2016-01-06
When I'm trying to enter a long command and trying to troubleshoot at the same time... well it takes a long time.
I use mtputty for ssh. holding the left arrow key isn't cutting it.
Also when using nano is there a way to make the cursor go faster?

Thanks,
    Higgis909

---

### Post by MAFoElffen on 2016-01-06
You might not like my answer. I am sometimes brutally honest, to a fault.

Cursor is just slow in putty and MTputty in Windows. 

I do admin and dev in multi-platform environments. I do ssh from a Linux terminal, such as Byobu. No lag from that kind of terminal... over a putty type terminal emulation. My server management is Linux boxes. Even My own windows dev machines here have Ubuntu I can run in Hyper-V. My laptops have both Win10 and Ubuntu. My android phone has Ubuntu running as chroot, with a few terminal apps.

So a native terminal is faster than an emulation.

Just my preferences and what I am used to.

---

### Post by Higgins909 on 2016-01-06
So you're telling me, there is no way to go from "here" to "there" quickly?
```

Root@MyLittleServer:~$ there/dir/dir/dir/dir/asfafeeaawf/awefaewfawfaw/awefawfewaf/program.sh here

```
I was hoping there was a hotkey to make editing the command that you typed wrong, go by faster.
Same with nano, was hoping some hotkey like ctrl + uparrow or right arrow would make it travel x5 faster or something.

Quite the bummer if so.

---

### Post by lisati on 2016-01-06
Using tools like SSH and putty will usually incur some kind of overhead that can slow things down, and will never be quite the same as having hands-on access to a terminal on the box you want to control. 

The only keyboard shortcut that comes to my mind at the moment is the tab key to help auto completion.

---

### Post by sudodus on 2016-01-07
Try the HOME and END keys :-)

The manual page ```
man bash
``` contains a lot of information. The paragraph 'Searching', 'Commands for Moving', 'Commands for Manipulating the History', 'Commands for Changing Text' and 'Completing' can be useful.

But it is probably better to start with some easier to read tutorial, that you can find if you search the internet for **bash tutorial**.

---

### Post by sergio53 on 2016-01-07
How about grep commands?
or pg up, pg dn buttons

---

