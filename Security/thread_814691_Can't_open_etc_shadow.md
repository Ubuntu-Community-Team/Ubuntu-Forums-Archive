---
title: "Can't open etc shadow"
date: 2008-05-31
forum: Security
---

### Post by zaedi_ahmed on 2008-05-31
Can't open etc shadow 


I have also faced the same problem.

useradd: Cannot open /etc/shadow file.

and the ls -ali shows

read write permission for root but couldn't open.

Can any one help me.....

And 

ls -l /etc/shadow 

shows : -rw-r--r-- for shadow

lsattr /etc/shadow

shows : ---------- for shadow
Thanks in advance

---

### Post by p_quarles on 2008-05-31
Moved to Security Discussions.

First, that's not a file that's supposed to be manually edited (in any circumstance I can think of). What are you trying to do?

---

### Post by HalPomeranz on 2008-06-01
> **zaedi_ahmed said:**
> 
useradd: Cannot open /etc/shadow file.


Are you running the useradd command with "sudo useradd"?  You must be root to add users.

> **zaedi_ahmed said:**
> 
ls -l /etc/shadow 
shows : -rw-r--r-- for shadow


Those are not the correct permissions for /etc/shadow-- the file should NOT be world-readable!  On my 8.04 system, the file is mode 640 (-rw-r-----) owned by root:shadow.

You should fix the permissions on this file.  If /etc/shadow is world-readable then it's trivial for any user on the system to run a password cracker on your passwords.

---

### Post by Dr Small on 2008-06-01
> **p_quarles said:**
> Moved to Security Discussions.

First, that's not a file that's supposed to be manually edited (in any circumstance I can think of). What are you trying to do?
I have manually edited /etc/shadow before.

---

### Post by scorp123 on 2008-06-03
> **Dr Small said:**
> I have manually edited /etc/shadow before. Yes, e.g. for password recovery on a system where you locked yourself out (let's be honest here: it can happen :D ) you have to do that.

But under normal circumstances .... hmmmm, nope. You usually don't touch it manually. Ever.

---

### Post by zaedi_ahmed on 2008-06-08
Thanks to "HalPomeranz" for his comments.

> "Those are not the correct permissions for /etc/shadow-- the file should NOT be world-readable! On my 8.04 system, the file is mode 640 (-rw-r-----) owned by root:shadow.

You should fix the permissions on this file. If /etc/shadow is world-readable then it's trivial for any user on the system to run a password cracker on your passwords."

Well I have chnaged it (/etc/shadow) to 640 -rw-r-----

And I was not using "su" rather than using root to issue the:

"useradd" command

The problem is not about whether /etc/shadow file can be manually edited or not.

The problem is when I am issuing "useradd" command to create a user the command replies an error and I have got a snapshot of that hope someone could give solution of the problem.

There is an attachment with this to view the problem.

Thanks in advance.

---

### Post by Monicker on 2008-06-08
Take a look at this thread post.  Different distro but same error.

[http://www.linuxquestions.org/questions/showthread.php?p=3042231#post3042231](http://www.linuxquestions.org/questions/showthread.php?p=3042231#post3042231)

---

