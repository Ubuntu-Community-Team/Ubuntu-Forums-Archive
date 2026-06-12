---
title: "Question about etc/passwd"
date: 2007-12-27
forum: Server Platforms
---

### Post by TreeFinger on 2007-12-27
I have a question about the etc/passwd file located on unix/linux machines.

I am seeing a Login ID called 'nobody'.

Where would this Login come from? 

Also, why are there 2 locations containing the same data?

"/etc/passwd" and "/etc/passwd-"

same thing here:
"/etc/shadow" and "/etc/"shadow-"



I don't feel comfortable having this account called 'nobody'. I am thinking of removing it. Should I?

---

### Post by p_quarles on 2007-12-27
Nothing to worry about with nobody:
[http://www.unix.com/unix-dummies-questions-answers/32480-how-do-i-become-user-nobody.html](http://www.unix.com/unix-dummies-questions-answers/32480-how-do-i-become-user-nobody.html)

/etc/passwd contains account information, but despite the name, modern *nix systems do not use it to store passwords.

/etc/shadow contains some duplicate account information, but also contains encrypted hashes of any passwords that you may have. This is to avoid having to store your password in plain text anywhere on the system. Instead, it checks your password against the encrypted hash, and if they match, you are authenticated. This is a security precaution, and a good one.

---

### Post by TreeFinger on 2007-12-27
Well I know what the files do, well what he ones without the '-'s do. Why are is there an extra file with a dash on the end? Is it a back-up? So that other forum question didn't really answer my question. They just wanted to know how to login as that user.



"What would happen if I removed the user 'nobody'?", is my actual question.

---

### Post by p_quarles on 2007-12-27
The second post did answer that question, though: nobody is a service account, has very limited privileges, and is locked by default. If you remove it, you could wind up compromising whatever nobody does for your system. You can scan your recent auth.log files to find out what it does, specifically. 

And, yes, the files ending with '-' are backups.

---

### Post by TreeFinger on 2007-12-27
OK, thanks. I have another question.

Does any application that uses an internet connection (maybe the right word is ethernet protocol?) have a user account on my system?

---

### Post by p_quarles on 2007-12-27
No one can make an account on your system without root access, so not unless you've made a habit of giving out your administrative password to strangers. :D

It is possible for people to access any public services running on your system, though. For instance, if you run a web server, other users can access those pages -- but they're not actually logged in. They're just being sent that information by the daemon that's responsible for running the web site. Is that what you were asking? If not, feel free to clarify.

---

### Post by TreeFinger on 2007-12-27
What type of information could someone receive from applications like a webserver?

---

### Post by p_quarles on 2007-12-27
> **TreeFinger said:**
> What type of information could someone receive from applications like a webserver?
If it's working correctly and properly secured, the only information anyone could get is the code for the web site itself. The daemon shouldn't even be able to access anything that it doesn't need specifically for running the site.

---

### Post by rsw686 on 2007-12-28
> **TreeFinger said:**
> What type of information could someone receive from applications like a webserver?

Apache2 runs under the www-data user. It can access files readable by www-data and files that are other readable.

---

