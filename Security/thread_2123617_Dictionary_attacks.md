---
title: "Dictionary attacks"
date: 2013-03-08
forum: Security
---

### Post by 3v3rgr33n on 2013-03-08
Hi

I have a simple question with regards to dictionary attacks.
Most systems give the user only three tries with the password, how are dictionary attacks possible then?

Regards,

Adeeb

---

### Post by Cheesemill on 2013-03-08
Dictionary attacks aren't really aimed at that type of password hacking.

They are usually used when you manage to get hold of the file containing the password hashes for a system (whether it's the /etc/shadow file, a database containing the password hashes, or the SAM file for Windows machines).

When you are cracking against a file of password hashes you don't have the 3 tries limitation, you can attempt as many passwords as you have time for.

---

### Post by dodo3773 on 2013-03-08
> **3v3rgr33n said:**
> Hi

I have a simple question with regards to dictionary attacks.
Most systems give the user only three tries with the password, how are dictionary attacks possible then?

Regards,

Adeeb

Can you be more specific? Three tries with what password? Login? SSH? FTP? What are we talking about here?

---

### Post by 3v3rgr33n on 2013-03-08
> **dodo3773 said:**
> Can you be more specific? Three tries with what password? Login? SSH? FTP? What are we talking about here?

I was trying to be general, but to my knowledge (I've just tried ssh) : ssh allows three login tries before discontinuing the login prompt. I'm not sure abt the others.
That wasn't the point though. Cheesemill seems to have answered me!

---

### Post by Stonecold1995 on 2013-03-11
Imagine you wanted to steal a safe from a bank.  How long do you think they'll let you stand giving them repeated fake identies before you're kicked out?  You wouldn't have that limitation if you had the actual bank vault present to try guessing the combination.  It's the same with a computer.  It can be set to wait an arbitrary amount of time after an arbitrary amount of failed attempts if it's between the attacker and the encrypted data.  If the attacker has actual physical access to the data (or a copy), he can guess passwords as fast as his computer's hardware allows.

---

### Post by 3v3rgr33n on 2013-03-11
I can't mark this thread as solved, the option is not available under Thread Tools. Have things changed with the new interface?

---

### Post by BlinkinCat on 2013-03-11
> **3v3rgr33n said:**
> I can't mark this thread as solved, the option is not available under Thread Tools. Have things changed with the new interface?

Yes -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

