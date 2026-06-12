---
title: "The sudo (password wrong) timeout - isn't it silly?"
date: 2013-06-16
forum: Security
---

### Post by hakermania on 2013-06-16
We've all done it.

We've given
```

sudo command

```
and then the wrong password. A timeout of approximately 3 seconds and then you are informed that you've typed the wrong password.

VERY annoying for us that want a strong password to have to retype it and have to wait this timeout so many times per day.

They say that it is a security measure: A brute force attack will take months if every password attempt lasts for 3 seconds.

But I find this wrong. A hacker would attempt passwords simultaneously through multiple instances of sudo so as to "guess" the right password. Nothing forbids you from having multiple instances of sudo asking for password.

Let's say that you have 1000 instances of sudo, and each of them allow you one guess per 3 seconds, so we have a total of 3000 guesses in 9 seconds, rather than 3.

That's why I believe that this won't work on a real brute force attack.

What do you think?

---

### Post by Hungry Man on 2013-06-17
You are correct, this wouldn't ever work because the assumption is that the attacker has local code execution anyways, so there's no way to enforce the 3 second time out.

It's a silly feature to make people think they're more secure than they really are. Many things are.

In reality Ubuntu should up its iteration count for the password hashing based on CPU speed. If it's a modern CPU give it 10,000 rounds of PBKDF2, give a weak one 1,000. No one can bypass that and it'll be a million times more effective.

---

### Post by hakermania on 2013-06-17
Hey hungry!

Can you elaborate a bit on the kind of security that you suggest?

---

### Post by Hungry Man on 2013-06-17
[https://en.wikipedia.org/wiki/PBKDF2](https://en.wikipedia.org/wiki/PBKDF2)

Basically when you use a password you hash it and you use that hash to decrypt some token or file or something. How long it takes to hash can be extended by iterating that hash over and over again with something like PBKDF2. You can't bypass that, you can only speed it up by attacking the algorithm or using faster hardware. It would be much more secure to just hash it a bunch of times to estimate a 3 second waiting period. Running simultaneous sessions would take more than 3 seconds becuase it would require more CPU per session. So instead of 1 session taking 10,000 rounds you'd have 2 seconds taking 20,000 rounds. Every new session would increase the work, and the time it would take to get that work done.

---

