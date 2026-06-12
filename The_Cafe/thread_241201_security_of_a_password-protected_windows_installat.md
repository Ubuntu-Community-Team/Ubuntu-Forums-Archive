---
title: "security of a password-protected windows installation"
date: 2006-08-22
forum: The Cafe
---

### Post by user1397 on 2006-08-22
does it make a difference in security (from malware, not people that can physically steal your laptop) to have a user password in windows xp?  because once you've signed in, you're a full-fledged computer admin, unlesss of course you've made it a limited account.

???

---

### Post by Johan! on 2006-08-22
A blank password is very easy to guess.
When the attacker (malware or a hacker) knows you don't have a password, he is in full control.

---

### Post by mrgnash on 2006-08-22
Running as an admin in WinXP is essentially the same as running as root in Linux. That is to say, any programs you run or content you access which has malicious components, inherits your permissions. (I'm over-simplifying here, but you get the idea).

---

### Post by user1397 on 2006-08-22
i understand what everybody's saying already....i just want to know what the answer is to my first and only quesstion in the origianl post! :mad:

---

### Post by aysiu on 2006-08-22
It doesn't make a difference for internet security--since you'll never be prompted for your password--only local security, which is bypass-able anyway with a Knoppix CD.

So really if you're running Windows as administrator, there's no point in having a password at all, unless you're trying to protect yourself from your computer illiterate family members.

---

### Post by user1397 on 2006-08-22
> **aysiu said:**
> It doesn't make a difference for internet security--since you'll never be prompted for your password--only local security, which is bypass-able anyway with a Knoppix CD.

So really if you're running Windows as administrator, there's no point in having a password at all, unless you're trying to protect yourself from your computer illiterate family members.thank you, that's the answer i was looking for.

---

### Post by jdong on 2006-08-22
From a network standpoint, XP is **most** secure when none of the accounts have a password. Blank password accounts are automatically denied the opportunity for remote logins.


From a local standpoint, if you don't physically protect your computer, sure not having a password is gonna make your system more vulnerable, but having a password really doesn't help out much because of the number of ways to circumvent OS password protection (LiveCD, yanking out the HD, etc)

---

### Post by aysiu on 2006-08-22
> **jdong said:**
> From a network standpoint, XP is **most** secure when none of the accounts have a password. Blank password accounts are automatically denied the opportunity for remote logins. That's good to know, jdong. Thanks for that bit of info.

---

