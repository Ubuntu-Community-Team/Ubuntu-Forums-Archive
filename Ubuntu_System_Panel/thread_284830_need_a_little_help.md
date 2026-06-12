---
title: "need a little help"
date: 2006-10-26
forum: Ubuntu System Panel
---

### Post by zekopeko on 2006-10-26
hi,

i just downloaded USP and put it instead of my gnome menu. 

the problem is that i can't put plugins or rather i don't know how.

I tried with the USPconfig but it says (terminal example) "Plugin USPterm not found".

in gconf-editor there are folders for plugins but when i try some option it says "This key has no schema".

I extracted the plugins in .usp/plugins in their folder.

So what i'm i doing wrong?

---

### Post by Malac on 2006-10-26
Try running USP from a terminal window like this :
```
usp run-in-window
```
and then post the results from that.
Plugins should be fine in .usp/plugins in your home folder.
I may have misunderstood your post but they should not be in a sub-folder under .usp/plugins folder.

"Plugin USPterm not found" can show up if there is an error in the file and also if you haven't got libvte installed.

What OS are you running Edgy or Dapper?

---

### Post by zekopeko on 2006-10-26
i just installed edgy(was on dapper when i posted) so i have to setup my OS first but that shouldn't take to much time. will post back when i try that command

---

### Post by zekopeko on 2006-10-26
ok i managed to set USP without much problem. 
the only thing that bothers me is that in gconf-editor the 'panel size' is set to 24.
i tried to set the value to 0 but it resets.
when i try to set the value of 0 as default it says that i don't have a database or something.

---

### Post by chanders on 2006-10-27
Try setting it to 1, and it will work ;-)

---

