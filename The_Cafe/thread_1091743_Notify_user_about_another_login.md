---
title: "Notify user about another login"
date: 2009-03-09
forum: The Cafe
---

### Post by tuxcanfly on 2009-03-09
Here's a little python script I wrote which notifies the user through a popup about another (local or remote) login. Try it out by running it from the terminal.

> 
python notify-login-2.0.py


ssh into your own machine and check out the notification.  :) if you like it, add the above command to your list of autostarted programs.

[EDIT]: Depends on libnotify-bin

> sudo apt-get install libnotify-bin

[EDIT] --  Thanks to zekopeko
**Added notification on user logoff
**Added option to hide (that annoying) notification for current user :popcorn:

---

### Post by zekopeko on 2009-03-09
it's nice but would be better if it would keep track of logged user and also inform you if somebody has logged off. and make it ignore the user thats sitting in front of the computer.

---

