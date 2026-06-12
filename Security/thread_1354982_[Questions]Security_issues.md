---
title: "[Questions]Security issues"
date: 2009-12-14
forum: Security
---

### Post by JoeDaFlow on 2009-12-14
Hello guys, i am very happy of being a part of this forum and generally the ubuntu community. I am pretty new to this OS, and i have some questions.
My first questions is about viruses. I have heard that linux doesnt need any antivirus
cause they are not valuable to viruses. Is this true?
The second question is how i can disable the password authentication. Every single thing i do it asks me for a passowrd, and if it is wrong about my computers security, i dont mean from my house but remotely from hackers or such things.
And finally you can read about the commands of terminal somewhere or you learn them by time.
Thank you very much ; )
-JoeDaFlow

---

### Post by Rob_H on 2009-12-14
Generally, you don't need an anti-virus program for desktop Linux. Linux is mostly virus-free through a combination of its good security model and the fact that it is not an attractive target for virus authors because of its small market share. They can be much more effective by targeting Windows boxes because there are so many of them.

Regarding passwords: You'll have to be more specific. When are you getting prompted for passwords?

There are several good references for Linux command line tools. Some of my favorite online ones are [UNIX Toolbox]("http://cb.vu/unixtoolbox.xhtml"), [Linux Cheat Sheets]("http://www.nixtutor.com/linux/all-the-best-linux-cheat-sheets/"), and the [Advanced Bash Scripting Guide]("http://tldp.org/LDP/abs/html/index.html"). Have fun.

---

### Post by cdenley on 2009-12-14
Any actions which could potentially break your system requires privilege escalation which requires you to enter your password. Your password is required to verify you are in fact performing this action and your system (or yourself) isn't being tricked into performing it by someone or something with malicious intent. In other words, if your system is accessed remotely, the password requirement will limit the damage.

---

### Post by cariboo on 2009-12-14
As far as terminal commands go download [this]("http://www.ubuntupocketguide.com/index_main.html"),it should help.

---

### Post by Lars Noodén on 2009-12-15
In addition to 2 Rob_H's links, I would strongly suggest approaching the shell as a scripting or programming exercise rather than an arbitrary mass of 'commands' to be memorized.  These are a bunch of tools that you string together to solve a task.

---

### Post by bodhi.zazen on 2009-12-15
For linux security, please start with the stickies at the top of the forum.

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

In terms of viruses, there are currently no known active linux viruses, so nothing to scan for with antivirus.

---

