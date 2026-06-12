---
title: "securing an internet kiosk"
date: 2006-05-02
forum: Server Platforms
---

### Post by ashrack on 2006-05-02
Just did a fresh dapper install. And created 2 user account. 
One with full priviligies which has a very strong password ofcourse. This account will be used for doing administrative tasks on this computer if something goes fubar.
ANd the other account which will be used for those using the computer. And this account has the following priviligies:
```
id tom
uid=1002(tom) gid=1002(tom) groups=1002(tom),24(cdrom),25(floppy),29(audio),46(plugdev)

```
and so far it looks like this:
[ATTACH]8952[/ATTACH]
As U might have noticed I changed the permission on the .Desktop folder so ppl can only execute those icons but they  cant change or delete or create anything on the desktop.
But the thing that still bugs me is the home directory. Which they will still be able to change. How do I also secure that??

ps. gnome panels I've secured with "pessulus"

---

### Post by ashrack on 2006-05-03
anyone? How can I also secure the other hidden files in the user home dir  so they will not be able to change it!!

---

### Post by aysiu on 2006-05-03
[QUOTE=ashrack]anyone? How can I also secure the other hidden files in the user home dir  so they will not be able to change it!![/QUOTE] Change ownership on them...?

---

### Post by ashrack on 2006-05-03
[QUOTE=aysiu]Change ownership on them...?[/QUOTE]
that was also my first thought. But I dont know which ones I can change? I mean arent there also files that would need to be modified in order for gnoem to function? Or is it safe to just change the ownership of all file under home dir??

---

### Post by ashrack on 2006-05-04
[QUOTE=ashrack]that was also my first thought. But I dont know which ones I can change? I mean arent there also files that would need to be modified in order for gnoem to function? Or is it safe to just change the ownership of all file under home dir??[/QUOTE]
anyone

---

### Post by aysiu on 2006-05-04
I think trial and error might be your best bet.
Create a new user and *chown* all the hidden folders (not the hidden *files*, though) and see if the new user can function.

---

### Post by ashrack on 2006-05-04
[QUOTE=aysiu]I think trial and error might be your best bet.
Create a new user and *chown* all the hidden folders (not the hidden *files*, though) and see if the new user can function.[/QUOTE]
crap! I thought there was an easier sollution:(

ps. What about this kind of method that some1 described to me, can it be achieved:
> Originally Posted by IYY
You could just set it up so when a user logs out, his home directory gets restored to its original status (copied from some location in /usr/share/......). I think this is better than just locking access to config files, or at least it's what I'd prefer as a user.

---

### Post by aysiu on 2006-05-04
[QUOTE=ashrack]crap! I thought there was an easier sollution:(

ps. What about this kind of method that some1 described to me, can it be achieved:[/QUOTE] It can be achieved, but you'd have to write some kind of script to be executed at logout. The script would be easy to write. Getting it to execute at logout might be a bit more tricky.

---

### Post by ashrack on 2006-05-05
[QUOTE=aysiu]It can be achieved, but you'd have to write some kind of script to be executed at logout. The script would be easy to write. Getting it to execute at logout might be a bit more tricky.[/QUOTE]
the script I could probably manage. Theres a web site which teaches U of scripting. B
ut placing it at the GNOME LOG OUT now this could be tricky! Anyone has any ideas?

---

### Post by ashrack on 2006-05-08
anyone

---

### Post by ashrack on 2006-05-10
[QUOTE=BigDaddy]
I should set it up so when a user STUDENT logs out, his home directory gets restored to its original status (copied from some location in /usr/share/......).
[/QUOTE]
this is how I achieved this:
I tarred the STUDENT folder to /home/qhome.tar.gz. And chown it to TEACHER and gave executable permission to all.
So then I put this script into GNOME->SESSIONS->STARTUP PROGRAMS:
[ATTACH]9278[/ATTACH]

tell me what do U think?

---

