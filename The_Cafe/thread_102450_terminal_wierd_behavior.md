---
title: "terminal wierd behavior"
date: 2005-12-12
forum: The Cafe
---

### Post by vb7prog on 2005-12-12
DISCLAIMER--
First I would like to say this is actually a "unix" problem, but linux and unix share many attributes and I like to use the right tool for the job, in this case freebsd unix happens be the tool for my job. Also, I tried to post in a forum that shouldn't get ppl mad to see a unix qustion? My other _server_ that runs debian runs flawlessly. Please don't flame this thread.
END DISCLAIMER--

SUMMARY--
I believe my keys are somehow unbound and require setting a certain variable that is unknown to me in order to utilize all keys from my keyboard?
--


I have this wired terminal problem

I try hitting up arrow(to use the last command) and it prints "^]]A" to the screen
Pressing insert puts a tilda on the screen.

I try specifying the terminal type which is currently "cons25"

I just have a normal pc keyboard nothing fancy PS/2 is it the terminal setting, or the keyboard mapping, that does this?

also sometimes VI acts really funny to it wont let me insert characters after using the insert key or it capitalizes the character to the left when pressing insert, sometimes it deletes the current line, I don't think its vi I think its a mal configured terminal or keyboard.

here are some of the variables that are present(I don't know any other pertainent vars):
TERM=cons25
SHELL=/bin/sh

english is my first language but right now my sentences aren't very coherent and I apologize.

---

### Post by Jussi Kukkonen on 2005-12-12
Are you sure the shell you are using offers history-with-arrow-keys? I remember that it wasn't the case with at least one of the BSDs default shell...

---

