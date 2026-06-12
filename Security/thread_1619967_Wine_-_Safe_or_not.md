---
title: "Wine - Safe or not?"
date: 2010-11-12
forum: Security
---

### Post by Ranger_Joe on 2010-11-12
I've never used Wine. However, I'm wondering if it's safe to use. What are the security risks of porting in Windows programs? 

Here's my thought: Porting in Windows programs doesn't change the Linux infrastructure. These programs still would not have root access... or would they? Am I wrong? What are your thoughts?

---

### Post by uRock on 2010-11-12
Moved to Security Discussions.

---

### Post by syntr on 2010-11-12
That is correct. Progams running under Wine still do not have root access.

They are just as safe as anything else you would run on your system. :)

---

### Post by Ranger_Joe on 2010-11-13
Anyone else want to weigh in on this? Someone play Devil's advocate please :)

---

### Post by WeAreLinux on 2010-11-13
I have no experience with Wine, so I can't really comment. The Security Sticky does have some important precautions when using Wine. Worth a look.

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by RiceReaper on 2010-11-13
I'm not the most experienced Linux user, but coming 100% from windows I know that the security issues involved with the windows OS are a result of its design. Any problems or infections you COULD get using a windows program, I would imagine stay within that program.

---

### Post by CharlesA on 2010-11-13
> **RiceReaper said:**
> I'm not the most experienced Linux user, but coming 100% from windows I know that the security issues involved with the windows OS are a result of its design. Any problems or infections you COULD get using a windows program, I would imagine stay within that program.

They would be confined to WINE in that at most, the ~/.wine folder would get corrupted.

---

### Post by Ranger_Joe on 2010-11-13
Ok, this is good to know. It kind of confirmed what I was already thinking but I am SO new to Linux that I thought I would check. 

Thanks everyone! I'm marking this one solved.

---

### Post by movieman on 2010-11-13
Note that, by default, Wine typically has access to all files in your home directory. I would suggest creating a new directory for shared files and only allowing access to that; if it does need access to some of your documents folders you can create symbolic links to them.

---

### Post by Ranger_Joe on 2010-11-13
That's good to keep in mind movieman. Thanks!

---

