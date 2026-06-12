---
title: "Used tiger and I have a huge list for security warnings"
date: 2011-01-10
forum: Security
---

### Post by LetsMugSanta on 2011-01-10
Yeah so as the title says I used tiger which was in Bodhi.zazen's security thread in order to check for holes and I have this huge list. I just don't know where to start exactly, Im not really sure if it will let me attach this file because its html.

---

### Post by LetsMugSanta on 2011-01-10
bump

---

### Post by uRock on 2011-01-10
Please do not bump your thread more than once per 24 hours.

Thanks,
uRock

---

### Post by bodhi.zazen on 2011-01-10
> **LetsMugSanta said:**
> Yeah so as the title says I used tiger which was in Bodhi.zazen's security thread in order to check for holes and I have this huge list. I just don't know where to start exactly, Im not really sure if it will let me attach this file because its html.

Also in my sticky is how to obtain more information on the output.

If you are unwilling to read, do not run the tool.

Please do not post the long list here, but if you have questions about something you read, ask for clarification.

---

### Post by LetsMugSanta on 2011-01-10
***WARN*** [pass014w]Login (backup) is disabled, but has a valid shell.
There are a bunch of things like that. And all your thread said was to research them and I couldn't really find anything on a quick skim, all I wanted was a quick and short answer. There are also other ones that do not belong to certain packages or are symlinks. I'm not really familiar with these or what happens if I delete them or what risk they pose exactly.

---

### Post by bodhi.zazen on 2011-01-10
> **LetsMugSanta said:**
> ***WARN*** [pass014w]Login (backup) is disabled, but has a valid shell.
There are a bunch of things like that. And all your thread said was to research them and I couldn't really find anything on a quick skim, all I wanted was a quick and short answer. There are also other ones that do not belong to certain packages or are symlinks. I'm not really familiar with these or what happens if I delete them or what risk they pose exactly.

From the sticky on Tiger:

> bodhi@lucid:~$ tigexp pass014w

The listed login ID is disabled in some manner ('*' in passwd field, etc),
but the login shell for the login ID is a valid shell (from /etc/shells
or the system equivalent). A valid shell can potentially enable the
login ID to continue to be used. The login shell should be changed to
something that doesn't exist, or to something like /bin/false. 

If you are looking for the short answer, you do not need Tiger, relax and enjoy Ubuntu.

---

