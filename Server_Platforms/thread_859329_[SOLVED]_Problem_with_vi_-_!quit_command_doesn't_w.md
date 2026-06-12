---
title: "[SOLVED] Problem with vi - !quit command doesn't work"
date: 2008-07-14
forum: Server Platforms
---

### Post by Tomas123 on 2008-07-14
Yesterday I installed Ubuntu Server 8.04.1 and noticed interesting problem with vi:

after making some changes I tried to quit vi with the command !quit in order to override all changes. This is what I would get an the screen:

:!quit
[No write since last change]
/bin/bash: quit: command not found
shell returned 127
Press ENTER or type command to continue
--------------------------------------------

after pressing ENTER I would be forwarded back to the editing screen. If I would try to quit with just :q command, I would get this error:

E37: No write since last change (add ! to override)

The only way to escape from that situation was with :wq command, which of course will save the changes...

Is this a bug?

---

### Post by Simon2006 on 2008-07-14
No bug, you need to put the ! after the 'quit' (or just use 'q!')

Putting an exclamation mark before the command tries to execute a bash command. For example, try !ls and it will list the contents of the current directory.

---

### Post by Tomas123 on 2008-07-14
Thanks Simon! Really that was a dumb mistake from my side... Sorry :) just 2nd month with linux...

---

### Post by bilgee0629 on 2010-05-06
thanks anyway... for me study more with vim:lolflag:

---

