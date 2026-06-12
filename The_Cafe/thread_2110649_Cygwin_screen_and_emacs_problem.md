---
title: "Cygwin: screen and emacs problem"
date: 2013-01-30
forum: The Cafe
---

### Post by InkyDinky on 2013-01-30
I run cygwin at work. Inside cygwin, I run screen and emacs. 
I keep running into the problem where I hit C-a x or C-a C-x which brings up the lockscreen in screen. 
After I get rid of the lockscreen, C-x C-s (save buffer) in emacs no longer works in *new* instances of screen. If I had emacs running before I hit C-a x then C-x C-s still works.

More info on the lockscreen:
This lockscreen is different than what I experience on a linux box running screen. In cygwin, the first time you hit C-a x to invoke the lockscreen it prompts you for 
```
key:
```
 then 
```
again:
```
And then it prompts you for the password.

I'm curious as to why this is happening and how to fix it. 
The behavior is just bizarre to me since it occurs only in new xterm instances.
Changing the save key-bindings seems like a fix but I have become accustomed to C-x C-s. 

If anyone knows of a better place to post such a question I'd appreciate it.

Screen version 4.00.03 (FAU) 23-Oct-06
GNU Emacs 24.2.1

---

