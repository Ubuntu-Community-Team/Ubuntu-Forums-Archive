---
title: "Tiger unix security"
date: 2008-05-29
forum: Security
---

### Post by grewolf on 2008-05-29
I was wondering how to read the tiger unix security log files.  I have run man tiger in the command line and found where the files are located but when I double click on them I get the error [COLOR=Red]"No application suitable for automatic installation is available for handling this kind of file."  [COLOR=Black]I have run tiger -H in command line and don't understand what it is telling me here is one of the outputs

[/COLOR][/COLOR][COLOR=Red]**Code [acc001w]**[/COLOR]
 [COLOR=Red]The listed login ID is disabled in some manner ('*' in passwd field, etc), but the login shell for the login ID is a valid shell (from /etc/shells or the system equivalent). A valid shell can potentially enable the login ID to continue to be used. The login shell should be changed to something that doesn't exist, or to something like /bin/false. [/COLOR]

please help

---

### Post by HalPomeranz on 2008-05-30
The tiger output files are just text files, so you can open them with a text editor like gedit or view them from the command line using a tool like "less" or "more".

Whenever you want more information about a specific error message you can feed its code number into the tigexp program, for example:

```

tigexp acc001w

```

The specific error message you cite in your original posting is trying to warn you about accounts that have been blocked by putting an invalid entry in the password field in /etc/shadow but which have a valid default login shell in /etc/passwd.  The danger is that somebody either (a) manages to set a valid password on the account in the /etc/shadow file, or (b) manages to set up an SSH authorized_keys entry in the account's home directory.  This would cause the account to become a potential back-door onto your system.  That being said, there are a huge number of accounts in the default Ubuntu passwd/shadow files that will get flagged by this warning, but it's pretty low on the list of things I'd worry about when it comes to securing my systems.

This is the problem with auditing tools like tiger.  They have some basic rules defined in their auditing scripts but they don't have a lot of intelligence or contextual discrimination and so end up generating a lot of noise about fairly trivial issues.  It takes some amount of computer security knowledge plus experience with the tools to be able to distinguish the truly serious warnings from the noise.

---

### Post by grewolf on 2008-06-05
> **HalPomeranz said:**
> The tiger output files are just text files, so you can open them with a text editor like gedit or view them from the command line using a tool like "less" or "more".

Whenever you want more information about a specific error message you can feed its code number into the tigexp program, for example:

```

tigexp acc001w

```

The specific error message you cite in your original posting is trying to warn you about accounts that have been blocked by putting an invalid entry in the password field in /etc/shadow but which have a valid default login shell in /etc/passwd.  The danger is that somebody either (a) manages to set a valid password on the account in the /etc/shadow file, or (b) manages to set up an SSH authorized_keys entry in the account's home directory.  This would cause the account to become a potential back-door onto your system.  That being said, there are a huge number of accounts in the default Ubuntu passwd/shadow files that will get flagged by this warning, but it's pretty low on the list of things I'd worry about when it comes to securing my systems.

This is the problem with auditing tools like tiger.  They have some basic rules defined in their auditing scripts but they don't have a lot of intelligence or contextual discrimination and so end up generating a lot of noise about fairly trivial issues.  It takes some amount of computer security knowledge plus experience with the tools to be able to distinguish the truly serious warnings from the noise.



[COLOR="Blue"]Thank you is there any info out there where I can find how to distinguish the real security threats from the noise so far I've just been reading the tiger manual by doing man tiger in the terminal [/COLOR]

---

### Post by HalPomeranz on 2008-06-06
You might benefit from a good general book on Unix Security like the Garfinkle and Spafford book published by O'Reilly:

[http://oreilly.com/catalog/9780596003234/](http://oreilly.com/catalog/9780596003234/)

I'm also a big fan of David Curry's book on Unix System Security.  It's quite an old book (circa 1992) but still surprisingly useful and quite readable:

[http://www.amazon.com/UNIX-System-Security-Guide-Administrators/dp/0201563274/ref=pd_bbs_4?ie=UTF8&s=books&qid=1212725266&sr=8-4](http://www.amazon.com/UNIX-System-Security-Guide-Administrators/dp/0201563274/ref=pd_bbs_4?ie=UTF8&s=books&qid=1212725266&sr=8-4)

---

### Post by grewolf on 2008-06-23
Thank you for your reply.  I will try and pick that book up.

---

### Post by Nullack on 2008-06-23
Whats on my mind is that Tiger has come back with a bunch of issues on a default Hardy install :(

Some of these are easy to fix but it does beg the question why they arent default to begin with, There doesnt seem to be any user impact to what Tiger has identified.

Good to see though that Ubuntu had the latest tiger package in the repos.

---

