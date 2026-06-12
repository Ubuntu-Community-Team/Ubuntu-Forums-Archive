---
title: "Edgy Cups usb dection issue after normal updates on 8 March 2007"
date: 2007-03-08
forum: Repositories &amp; Backports
---

### Post by ccm7800 on 2007-03-08
Lost usb detection in cups after updates today.

Solved (after trying for 12 hours) with this fix:

sudo chmod a+rw /dev/usblp0 

Hope it helps anyone.

---

### Post by sancheztavo on 2007-03-08
I was experiencing the same problem here since today (although I didn't use the printer since a month ago or so), I did what you say and it got working again. 
Thank you!

---

### Post by ashleycrue on 2007-03-08
I had the same problem with both ubuntu and kubuntu but didn't see this before trying to reinstall now I'm stuck.

---

### Post by amelyst on 2007-03-09
see here for a possible solution

[http://ubuntuforums.org/showthread.php?p=2270082#post2270082]("http://ubuntuforums.org/showthread.php?p=2270082#post2270082")

cheers

---

### Post by digby280 on 2007-03-09
> **ccm7800 said:**
> Lost usb detection in cups after updates today.

Solved (after trying for 12 hours) with this fix:

sudo chmod a+rw /dev/usblp0 

Hope it helps anyone.

thanks you're a life saver!

Pete

---

### Post by Knudson on 2007-03-09
thanks, i was going nuts, same problem with samsung ml 1520 , tried to reinstall cups, booted with liveCD, tried almost everything and the fix was just a stupid chmod !

thanks again!

---

### Post by amelyst on 2007-03-09
doing a chmod on the device file does not solve the issue permanently, since the devce file is deleted as soon as the usb printer detaches (power off).

After attaching again, the wrong ownerchip/permissions will be back.

So have a look at my post 
[http://ubuntuforums.org/showthread.php?p=2270082#post2270082]("http://ubuntuforums.org/showthread.php?p=2270082#post2270082")

which suggests a more permanent solution to the problem

cheers

---

### Post by francesco44 on 2007-03-09
I have the same problem since a longer time. I tried sudo chmod a+rw/dev/usblp0 but it ask for a missing operand or argument? Does anybody have a solution? I think may be the right syntax is something like usblXX isnt'it?

---

### Post by amelyst on 2007-03-09
you are missing a blank ' ' in your command

i exaggerate now 

```
sudo chmod a+rw      /dev/usblp0
```

cheers

---

### Post by francesco44 on 2007-03-09
Thank you Amelyst,

as my view is bad I also tried what you suggest but rhe return was there is no such file or directory as "/dev/usblp0"

---

### Post by amelyst on 2007-03-09
> **francesco44 said:**
> 
as my view is bad I also tried what you suggest but rhe return was there is no such file or directory as "/dev/usblp0"

Well then it seems in the end your problem may be not related at all, but ...

... just a few more ideas:

- the file /dev/usblp0 is only existent as long as there is a usb printer connected an turned on
- if the command ```
ls -l /dev/usblp*
``` does not show any files although your printer is connected, you may have a deeper problem regarding usb device detection

hth
cheers

---

