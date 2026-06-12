---
title: "Simple Home File Server-need help please"
date: 2008-03-02
forum: Server Platforms
---

### Post by wolfwatcher51 on 2008-03-02
I am trying to take an old computer and make a "Simple Home File Server" out of it using the Howto Forge.com tutorial.

I was doing pretty good until top of page 3.

It says to run sudo passvd root and give it a password. I typed sudo passvd root at the chris@server1tilde)$ prompt. It came back with [sudo] password for chris: I typed my password for new user password that we established earlier in the install. It came back with sudo: passvd: command not found. I guess I was supposed to enter a new, different, password? Now when I entersudo passvd root, it keeps coming back with sudo: passvd: command not found and not letting me try again to put in a password.

Please help, what do I do now? Thanks in advance, Chris.

---

### Post by faulkes on 2008-03-02
> **wolfwatcher51 said:**
>  password for chris: I typed my password for new user password that we established earlier in the install. It came back with sudo: **passvd**: command not found.

Please help, what do I do now? Thanks in advance, Chris.

The bolded text should be passwd (p a s s w d).

Faulkes

---

### Post by wolfwatcher51 on 2008-03-04
Oh such a beginner. Yes I see now what looked like a v is a w. I hate doing without understanding, but hoped I could get started by easy instructions and then try to learn more once up and running. I think the problem with the tutorial was that the author assumed the people following it alreaady had linux experience and knew what else you had to enter besides what he showed in the tutorial. Like he wrote edit, took me awhile to fall across you needed to use -e, etc. Thanks again for your help, Chris.

---

