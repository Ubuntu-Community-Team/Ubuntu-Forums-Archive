---
title: "Multiple passwords"
date: 2010-01-07
forum: Security
---

### Post by warfacegod on 2010-01-07
I wonder if it is possible to have two passwords for one user account in 9.10. I have a long login password (5 words about 45 characters with spaces caps). I would like to set a shorter password for Authentication, sudo, etc. While retaining the original for logging in.

In short:

Have long password to login to computer.

Have short password for everything *after* login.

Thanks in advance.

---

### Post by warfacegod on 2010-01-07
What, if any, would be the security ramifications of doing what I am proposing?

---

### Post by cdenley on 2010-01-07
I'm pretty sure that is not possible. /etc/shadow can only contain 1 password hash per-line, and I think having multiple lines containing the same user would be problematic. Also, do not set a root password, and do not instruct how to set a root password on this forum. Sudo can be configured to ask for the root password, but I wouldn't recommend setting one, and policykit would still ask for your user password. If you want two passwords, then you need two users.

---

### Post by unmole on 2010-01-07
> **cdenley said:**
> I'm pretty sure that is not possible. /etc/shadow can only contain 1 password hash per-line, and I think having multiple lines containing the same user would be problematic. Also, do not set a root password, and do not instruct how to set a root password on this forum. Sudo can be configured to ask for the root password, but I wouldn't recommend setting one, and policykit would still ask for your user password. If you want two passwords, then you need two users.


My bad. Sorry.

---

### Post by warfacegod on 2010-01-07
So, in essence, I need to consider the pros and cons of shortening my password versus leaving it long.

---

### Post by BkkBonanza on 2010-01-07
Making your password more random is better than just making it long.
Consider some numbers,

truly random chars/symbols, say 72 symbols
length 7 = 72^7 =  10,030,613,004,288 = 10 trillion
length 8 = 72^8 = 722,204,136,308,736 = 722 trillion

or 5 simple dictionary words, say 1,000 word dictionary,
1000^5 = 1,000,000,000,000,000 = 1000 trillion

They are all really big numbers. Probably all beyond any real brute force attempts due to the time required to cycle the re-tries. If you allowed 1 year for someone to crack you then 10 trillion would mean 318,000 attempts per second. Even if they could access the /etc/shadow encrypted file (which they can't without already being root) then it's still practically speaking impossible.

What's important is randomness. As soon as you make up something that isn't random you cut down the search space by a huge factor, whether words or just letters. 

And the question arises: at what point would they just steal your computer rather than spending years brute forcing it, and just how valuable is the data?

I think you're likely safe enough with a shorter password as long as it's truly random. And especially not something made up of values related to you, like birth dates, names, and special meanings.

---

### Post by warfacegod on 2010-01-07
I'm considering shortening it for ease of using my laptop. Entering a password this long huy45 S6mklkln drrrjh )(*&vcxnbvc Killgfd for instance, is a hassle. I know about random password security.

Thanks for all of the replies.

---

