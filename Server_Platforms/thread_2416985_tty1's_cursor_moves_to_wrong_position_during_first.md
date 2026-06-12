---
title: "tty1's cursor moves to wrong position during first login"
date: 2019-04-18
forum: Server Platforms
---

### Post by cleaf on 2019-04-18
OS: ubuntu 18.04.1
server: Dell PowerEdge T640

When ubuntu is started, it goes to tty1, and the screen appears like this:

  *<server-name>* login: |
where | represents the cursor.  After a few seconds my cursor shifts to the beginning of line like this:

  |*<server-name>* login:  

I can login "normally", but when I type my username, the new text overwrites all text to the right of the cursor (i.e., the login prompt).


  When I use Ctrl+Alt+F2 to switch to tty2, this problem has not happened.

How to fixed the problem?

---

