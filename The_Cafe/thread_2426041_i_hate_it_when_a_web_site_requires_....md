---
title: "i hate it when a web site requires ..."
date: 2019-09-03
forum: The Cafe
---

### Post by Skaperen on 2019-09-03
i hate it when a web site requires your email address to get a forgotten password.  i have about 10 email addresses of which 5 allow using "+" to follow the user name to put email into specific mailboxes.  i know i used the user "skaperen" on this site, but i do not recall either the password nor which email address nor which "+" extension i used.  i can pick up mail at most of these email addresses and all i want is for that web site to just send the email with the password reset code to the email address they have on record.  then maybe i can get it.

---

### Post by VMC on 2019-09-04
Time for a password manager?

---

### Post by Skaperen on 2019-09-04
yeah, i have one, now.  still trying to scrape up all my old passwords to put in it.

---

### Post by uRock on 2019-09-04
I have a document listing all of my user IDs and passwords. A hacker can try to find it, but I wish them luck. It may or may not be on one of the many VMs on one of the computers I use. Most of my email addresses closed out ages ago.

---

### Post by TheFu on 2019-09-05
I use a password manager, but require positive action on my part for anything to be entered. I start with 55 character, random character, passwords. If a site refuses that, I'll cut back on the length, but keep the character complexity as much as possible. My ISP only allows 20 character passwords on their network equipment, which sucks.  One of my banks has way-to-short password length and next to zero complexity and doesn't support 2FA which I can use.  Instead, they ask those stupid 2nd questions, which I keep in the password manager.  All of them are long answers and lies. For example:
> Mother's maiden name:   asdkfjwe*^&*& %$& 23aefkkksyewu &2222sdfdss dkoerwejfdks
(but randomly generated).  I never tell the truth on those questions.  I hate that they ask "How old were you when" question.  100 guesses and an attacker is in. Stupid.

My brokerage account has even shorter passwords allowed, but they shipped me a security FOB with a number that changes every 60 seconds for the 2FA.  Also, I changed my userid to be random and long.  I couldn't guess that login under any situation.

For access I need BEFORE the password manager can be accessed, I'll write down part of the login and part of the password, so it is still long.  Then there is a part that I enter either before or after that longer part.  For some access, I'll use a yubikey long, static, entry for the part I don't remember, but still keep about 10 characters in my head.  That's how my full-disk encryption access works.  Of course, LUKS supports 8 passphrase slots, so there is another complex passphrase which can be used to unlock the disk, should that yubikey be lost.

I have no issue with parts of passwords being written down, just never have the entire password written. Always keep about 8-20 characters in your head.

Whenever possible, avoid using passwords, use keys for authentication.

---

### Post by Skaperen on 2019-09-05
i do use keys wherever i can.  but i have yet to see a web site that lets me do that (even over ssh).

HTUK18Rivi6?1BrIrMH?Q1f87dcmbYMH00ynRv%=4&u2z-4fENLPr2Oiohs?usDw

---

### Post by TheFu on 2019-09-06
Public websites are an issue, but many support U2F keys and other dynamic authentication methods.  
[https://www.dongleauth.info/](https://www.dongleauth.info/)

---

### Post by ryansenn on 2019-09-13
What would be the alternative?

---

### Post by Skaperen on 2019-09-14
i can still get email to any user name at each of 3 different domains.  2 of them get lots of spam.  i give out different addresses everywhere and kept a list of what i gave to where.  i can cross check which resulted in lots of spam.  i've even received other people's spam ... other peop[e entering fake email addresses and hitting one of my domains.  i even tracked on of the people who did that.

i once received email misaddressed to one of my domains that included a clear password of a bank's central file server.  a couple weeks later i got another email (to that same address) wanting me to ... and i quote ... "send it back".  yeah, right, as if that would secure it.

---

### Post by Skaperen on 2019-09-15
> **ryansenn said:**
> What would be the alternative?

link to the "forgot your email address and password" page.  many sites don't ask for the email address.  the only time when people forget their password is when they haven't been on the site for a while.  if their records confirm that, then it's not a case of someone trying tor trigger an email to them.  that and limit it to 3 per day, 1 per hour, to avoid floods.

---

