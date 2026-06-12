---
title: "problem with write permissions..."
date: 2005-10-01
forum: Server Platforms
---

### Post by Simpel on 2005-10-01
Hello everyone!

First of all, I'm a stupid n00b!

I accidently wrote chmod -R 777 / as root and then pressed enter. after this my  little server when grumpy. So, now to the question, is there an easy way to recreate the default write permissions for my filestructure. One effect of my misstake is that the server won't allow access for my user via SSH, witch of course is a biig problem.

So, what to do??

---

### Post by Glut on 2005-10-04
First, check your system logs. I suspect that your system wont like your permissions on /etc/shadow or /etc/passwd. Possibly even your public keys, from memory in /etc/ssh

You could try changing these, but a better thing to do now would be a reinstall. It's simply safer.

---

### Post by deuce868 on 2005-10-04
[QUOTE=Simpel]Hello everyone!
First of all, I'm a stupid n00b!
I accidently wrote chmod -R 777 / as root and then pressed enter. after this my  little server when grumpy. So, now to the question, is there an easy way to recreate the default write permissions for my filestructure. One effect of my misstake is that the server won't allow access for my user via SSH, witch of course is a biig problem.
So, what to do??[/QUOTE]

Ouch! I think a reinstall is going to be the best way. Right now all your files are readable by everyone and that's a pretty bad bad thing. Knowing the proper permissions on so many files is really impracticle.

---

