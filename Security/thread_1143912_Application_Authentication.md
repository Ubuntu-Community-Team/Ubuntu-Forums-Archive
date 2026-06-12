---
title: "Application Authentication"
date: 2009-04-30
forum: Security
---

### Post by tituspurdin on 2009-04-30
How does Ubuntu (Hardy) construct (encrypt) passwords.  I am, of
course, used to crypt().  I want to do application level authentication;
but cannot puzzle out how to do what I have done using crypt() in
the past.  I think it is using MD5 with salt, but I cannot reconstruct
the way in which the salt is being added or determine if there is a
system tool that will do the job for me.  Thanks.

---

### Post by bodhi.zazen on 2009-04-30
That is a very broad question. passwords for what ? login ? what type of authentication ?

Passwords for ecryptfs ? LUKS ? seahorse ?

---

### Post by tituspurdin on 2009-05-01
You are correct.  It is a broad question.  I was a bit frustrated
when I posted it.  What I want to do is emulate login(),  For
example, like a screen saver that wants the user's password to
unlock the screen.  User types in their password and I need to
convert it to an appropriate encrypted string to compare it to
the user's password as stored in /etc/shadow.

---

