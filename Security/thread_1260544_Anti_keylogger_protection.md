---
title: "Anti keylogger protection"
date: 2009-09-07
forum: Security
---

### Post by colonelmustard on 2009-09-07
hi! i recently moved to ubuntu from windows. i am looking for protection against keyloggers, screen capture software, clipboard capture software, and similar surveillance software. i am looking for behavior based protection (doesn't rely on signature based detection like many antivirus programs) that alerts me to such behavior and gives me the option of blocking it or allowing it.

i understand that many people consider linux a safer operating system than windows. nevertheless, there are still many easily found examples of such threats in linux. therefore, i have looked long and hard for such protection, but i have been unable to find such anti surveillance software in linux. please help!

---

### Post by cariboo on 2009-09-07
Someone would have to be able to install a keylogger for it to be useful. As you have found out, you as a user can only install programs in your owwn home directory. in order to install porgrams system wide you have to be root.

The biggest security problem is the user, surf safely and use strong passwords. Use something like [this]("http://ubuntuforums.org/showthread.php?t=208449") to create a password, instead of using dictionary words for passwords.

---

### Post by colonelmustard on 2009-09-07
> **cariboo907 said:**
> Someone would have to be able to install a keylogger for it to be useful. As you have found out, you as a user can only install programs in your owwn home directory. in order to install porgrams system wide you have to be root.

The biggest security problem is the user, surf safely and use strong passwords. Use something like [this]("http://ubuntuforums.org/showthread.php?t=208449") to create a password, instead of using dictionary words for passwords.
so if a keylogger gets installed, is it over? or are there still behavior based measures i can take to stop it?

---

### Post by MC707 on 2009-09-07
> **colonelmustard said:**
> so if a keylogger gets installed, is it over? or are there still behavior based measures i can take to stop it?

Its pretty easy NOT to install the keylogger in the first place. You should NEVER use root account, while using sudo only gives root rights for the specific command/application and for that specific terminal session. When inputting passwords in terminal (like sudo), no characters will be shown, to protect you from keyloggers (IIRC)

Just use common sense, it is worse to have a linux computer jam packed with antivirus, firewall, and antirootkit + a dumb user than to have a windows xp box without antivirus, firewall and antirootkit + a common sense user. analogy: As a rule of thumb, if it smells bad, it is rotten.

---

### Post by bodhi.zazen on 2009-09-08
> **colonelmustard said:**
> hi! i recently moved to ubuntu from windows. i am looking for protection against keyloggers, screen capture software, clipboard capture software, and similar surveillance software. i am looking for behavior based protection (doesn't rely on signature based detection like many antivirus programs) that alerts me to such behavior and gives me the option of blocking it or allowing it.

i understand that many people consider linux a safer operating system than windows. nevertheless, there are still many easily found examples of such threats in linux. therefore, i have looked long and hard for such protection, but i have been unable to find such anti surveillance software in linux. please help!

There are 2 questions here.

First - How to keep your system secure ?

Start with **[B]Sticky:**[/B] 			                          			 			[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

There is no way for you to have a key logger unless your system has already been cracked or you install it yourself. Best keep your system from being cracked in the first place.


2. What to do if your system is cracked ? If somebody has unauthorized access to your computer and has the ability to install unauthorized applications, key logger or otherwise, ...

A. Image the hard drive for forensics. Try to determine how such access was obtained.

B. Reinstall your operating system.

The only potential tools you might have in this area would be SELinux or appparmor, but I would not rely on those tools to completely contain unauthorized access.

---

### Post by Soul-Sing on 2010-02-11
That is a lot of text. It is for free I assume, but is not opensource, and not in the repositories of Ubuntu.
So i don't know what I am going to install.
And the linkage doesn't pass WOT.(on my system)

---

### Post by wojox on 2010-02-11
> **leoquant said:**
> That is a lot of text. It is for free I assume, but is not opensource, and not in the repositories of Ubuntu.
So i don't know what I am going to install.
And the linkage doesn't pass WOT.(on my system)

I think we just got spammed. ;)

---

### Post by mkvnmtr on 2010-02-11
The post above offering anti keylogger software is the perfect example of how to infect your system with a keylogger or malware. Never install from unknown sources . Never never. We have repositories for a reason. When somebody with one post recomends something it is a suere thing I will not install it or even go the the page it links to. That is if IPblock lets me go t o the page.

---

### Post by CharlesA on 2010-02-11
> **mikebenjamin97 said:**
> "Hi There! CoDefender by Encassa will be the best solution for you....

Owait, it's for Windows only? Norly!

This is my 666th post. Like gasp. :popcorn:

---

