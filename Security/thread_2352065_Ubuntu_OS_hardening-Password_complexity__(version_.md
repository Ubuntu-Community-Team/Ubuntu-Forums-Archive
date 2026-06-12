---
title: "Ubuntu OS hardening-Password complexity  (version 14.0.4.3)"
date: 2017-02-09
forum: Security
---

### Post by makauser on 2017-02-09
Dear Concern,

We want to implement following OS hardening feature in below version in Ubuntu. Request to share us necessary plan.

amirislam@blnidapp03:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty

1. Password complexity (Min Length=8, upper-case=1, lower-case=1, digit=1, non-alphanumeric=1).
2. Password history (remember last 5 passwords).

With Best Regards,
Md. Abdullah-Al Kauser

---

### Post by TheFu on 2017-02-09
[https://askubuntu.com/questions/244115/how-do-i-enforce-a-password-complexity-policy](https://askubuntu.com/questions/244115/how-do-i-enforce-a-password-complexity-policy)

14.04.3 is not supported. THAT is the biggest security issue. Move to 14.04.5 ASAP.

---

### Post by gordintoronto on 2017-02-10
It has been proven that forcing users to change their passwords after a certain amount of time, makes a network LESS secure. The only time you should force them to change is if there has been a breach.

(I can't remember my new password, so I will write it on a sticky-note and paste it on my monitor.)

---

### Post by Mopar1973Man on 2017-02-13
For my thought on passwords, I've been using an app called "KeePassX" to do all my password generation and keeping. It's a protected database and can create some serious stout passwords. I typically create passwords in excess of 16 characters to prevent dictionary type attacks from working. Most of my server passwords are exceeding 32 characters making logging in very difficult for hackers. 

[https://www.keepassx.org/](https://www.keepassx.org/)

---

### Post by ynota on 2017-02-13
I hope you have a strong password for KeePassX and change it often, if they crack that then they have all your other passwords for free :)

---

### Post by TheFu on 2017-02-13
> **ynota said:**
> I hope you have a strong password for KeePassX and change it often, if they crack that then they have all your other passwords for free :)

That goes without saying. 

KeePassX supports both keyfiles AND passwords, so it can't be opened by someone without both, if you choose that option.  This is handy when traveling. Pick an image file from a URL somewhere (that you control) as the keyfile.  Don't bring it with you; download it from the internet after arrival. Then you don't have it at border crossings.  Or use a Yubikey with the static part AND a passphrase. Put some characters before and after the yubikey entry. That will get you to 40+ characters easy. Hard to crack when they don't know the length of the pre/post parts.  Or just leave the yuubikey/2FA-device at home.

All the goodness of a password manager vastly overshadows any issues. Having to remember 3 different passwords is much better than trying to remember/build 150.  3 is manageable, but all those online accounts deserve long, random, complex, unique, passwords too.  What is the alternative?  There isn't one.

---

### Post by gordintoronto on 2017-02-14
Software can fail, software publishers can go out of business, software can be hacked. I remember half a dozen passwords, the others are on paper, which is as secure as my wallet.

My stock broker limits logon passwords to six characters. To enter a transaction is a different story. I'm struggling with how to get them to fix this problem.

---

### Post by TheFu on 2017-02-14
> **gordintoronto said:**
> Software can fail, software publishers can go out of business, software can be hacked. I remember half a dozen passwords, the others are on paper, which is as secure as my wallet.

My stock broker limits logon passwords to six characters. To enter a transaction is a different story. I'm struggling with how to get them to fix this problem.

KeePassX is F/LOSS - I have the source code AND the ability to rebuild it.

My broker gave me a securID fob when I asked for it - but they don't force it to be used, always.  But I figure if I use it always and don't let anyone see the serial number on it (like Chinese hackers), then I'm safer. No replay attacks.  Plus I do all financial banking/brokerage stuff on a special system - not my daily use systems.  NEVER, EVER, on a smart phone or tablet. NEVER.

They have a mainframe running things on the back end, so the 8 character limitation is from the 1970s. I was a mainframe programmer very early in my career.  They should disconnect all direct authentication from the MF and force a Unix system to handle it all via LDAP.  That's what it is for.  I suspect the real issue they don't is that their 40 yr old telephone order system is directly connected to the MF and someone decided that moving it elsewhere wasn't worth the effort until more people died who have been using it all their lives.  Of course, I don't really know - haven't physically been in any of their offices in a few decades.

The only way to get any company it fix issues like this is to take your money elsewhere.

---

### Post by KenUBF on 2017-04-09
[COLOR=#000000]makauser,
[/COLOR]
I agree that upgrading your system is a good idea. That, plus keeping current on all patches is also a good idea. I also use KeePass. It's a great program. If you want help with passwords I like to use GRC's Perfect Passwords generator: [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm) Just mix and match the strings in whichever way you want, with passwords that are as long as you want. The longer, the more random, the better.

---

