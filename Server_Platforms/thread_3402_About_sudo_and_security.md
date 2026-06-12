---
title: "About sudo and security"
date: 2004-11-05
forum: Server Platforms
---

### Post by Burgundavia on 2004-11-05
I was wondering about sudo and the timestamp option. By default, if you run a command that requires sudo with the timestamp, you don;t have to reinput the password. With this in mind, could I not write a script to replace one of the menu items with a script that would run the program as normal, thus prompting for a password, but also run some sort of malware?

Corey

---

### Post by mr_ed on 2004-11-11
Yes.  Next question.  :)

That person would need to hack archives or security.ubuntulinux.org, or be an insider.
I'm sure that it would be found out fairly quickly.

Or, you could tell everyone that you have some packages in a third-party repository.
Once somebody finds out that there's malware, I'm sure someone will post big warnings about your site.  Plus, it would be trivial to find out your ISP, etc...

So in the end, I wouldn't lose sleep over it.

---

### Post by bomanizer on 2008-01-20
Good to see that this issue has been covered. How about the current state of this issue? Does anybody have input? I was about to make a new post, 'cause the matter just popped into my mind, good to see that this has been addressed...

Regards

-B

---

### Post by cprofitt on 2008-01-20
> **Burgundavia said:**
> I was wondering about sudo and the timestamp option. By default, if you run a command that requires sudo with the timestamp, you don;t have to reinput the password. With this in mind, could I not write a script to replace one of the menu items with a script that would run the program as normal, thus prompting for a password, but also run some sort of malware?

Corey

I think it would make more sense for a 'cracker' to exploit a know buffer overflow and take root control that way.

---

