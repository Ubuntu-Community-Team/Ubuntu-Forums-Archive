---
title: "JTR - more pw hashes than users, why?"
date: 2010-05-13
forum: Security
---

### Post by Dynatoz on 2010-05-13
Hello everyone. I'm currently running tests on my SAM file on my XP partition. Partly because I want a password that is hard to crack, and also out of curiosity.

While running John the Ripper (no options used) I'm noticing that there are 8 pasword hashes, yet only 4 users associated with WinXP. I know that JTR only does 7(?) characters when it check for a solution. Is the 8 hashes because it separates passwords longer than 7 into 2 hashes, and then cracks them individually as 2 parts?

Sorry for the noob question, I did try googling this, but google hasn't proved to be very helpful with this question.

---

### Post by Helkaluin on 2010-05-13
> **Dynatoz said:**
> While running John the Ripper (no options used) I'm noticing that there are 8 pasword hashes, yet only 4 users associated with WinXP. I know that JTR only does 7(?) characters when it check for a solution. Is the 8 hashes because it separates passwords longer than 7 into 2 hashes, and then cracks them individually as 2 parts?


Did you include the HelpAssistant, ASPNET, and SUPPORT_388945a0 accounts when you said 4 users?

EDIT: Also Guest?

---

### Post by cdenley on 2010-05-13
I believe XP stored 2 hashes for each password. The NT hash, and the NTLM hash for backwards compatibility with older windows systems. Perhaps JTR parses both of them.

---

