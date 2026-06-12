---
title: "How to use a &quot;BAD PASSWORD: it is based on a dictionary word&quot;"
date: 2008-04-18
forum: Security Discussions
---

### Post by tuathan on 2008-04-18
When you change your user password from cmd line (using "passwd") is there a way to ignore the BAD PASSWORD error?

I want to set my password to a dictionary word with some integers at the end....

---

### Post by Dr Small on 2008-04-18
Do you have permissions to edit /etc/shadow ?
If not, no.

---

### Post by Chayak on 2008-04-20
> **tuathan said:**
> When you change your user password from cmd line (using "passwd") is there a way to ignore the BAD PASSWORD error?

I want to set my password to a dictionary word with some integers at the end....

You are aware that most dictionary based password attacks now will add integers and special characters to the beginning and end of words if the first pass doesn't get anything.

It's telling you you're password is weak for a reason.

Instead of:   password123 (cracked in less than a minute with John)
Try something like:  $Str0ngP@22w0rd#1 (have a long time to wait to crack this...)
Or even something like :  $1StrongPassword23# (not as strong as the second but still way more time than people will want to waste.

Most brute force attacks on machines just tries dictionary attacks and then moves on.

---

