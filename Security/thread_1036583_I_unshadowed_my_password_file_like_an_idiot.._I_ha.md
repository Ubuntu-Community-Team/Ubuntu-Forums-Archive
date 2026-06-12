---
title: "I unshadowed my password file like an idiot.. I have a question"
date: 2009-01-11
forum: Security
---

### Post by Koori23 on 2009-01-11
Okay, I was playing with John the Ripper. Instead of creating a test user account or just some MD5 encoded password SIMILAR to mine.. I unshadowed /etc/shadow and allowed John to run.

My question is.. What exactly did I screw up doing that? John ran all day and didn't crack my password. I have since changed my password. 

Did my "experiment" compromise my system's password security with the unshadow command?

---

### Post by Dr Small on 2009-01-11
I've never unshadowed the /etc/shadow file, so I'm not real sure. But as long as any user can read this file (on a multi-user system) then you are at risk of some user attempting to crack your password hash.

---

### Post by Kinstonian on 2009-01-11
Exactly how did you unshadow it?  JtR provides a way to unshadow (combine) the /etc/passwd and /etc/shadow files into one file before cracking it.  There isn't anything wrong with doing that, as long as your original passwd and shadow file haven't been modified.  Check to see if /etc/passwd contains the encrypted hashes.  If it doesn't then you should be fine.

BTW, if you're into password cracking, check out this [Hak5](http://revision3.com/hak5/GPU-Brute-Force-MD5-and-Ophcrack/) episode on using your video card to crack passwords faster than with your regular CPU.

---

### Post by Koori23 on 2009-01-11
sudo unshadow /etc/shadow > mypasswd

sudo john mypasswd

that's the commands I ran

---

### Post by bodhi.zazen on 2009-01-12
That is not a problem.

Just delete the file  mypasswd when you are done.

---

### Post by scorp123 on 2009-01-12
> **Koori23 said:**
> sudo unshadow /etc/shadow > mypasswd While "unshadow" does create a "combined passwd + shadow" file it does not seem to modify /etc/shadow itself .... IMHO nothing bad has happened here. :D

---

