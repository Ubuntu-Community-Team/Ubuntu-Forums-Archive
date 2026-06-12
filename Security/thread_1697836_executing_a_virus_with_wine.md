---
title: "executing a virus with wine"
date: 2011-03-01
forum: Security
---

### Post by Jonker on 2011-03-01
Hi there, I was wondering what would happen, if I executed a Windows Virus in the program "Wine" in Ubuntu.

---

### Post by FoxEWolf on 2011-03-01
I am wondering the same thing.

I even posted the same thing just 5 minutes ago. 

[http://ubuntuforums.org/showpost.php?p=10508856&postcount=6](http://ubuntuforums.org/showpost.php?p=10508856&postcount=6)

---

### Post by kn0w-b1nary on 2011-03-01
depends on the virus, I would assume.

---

### Post by kaspar_silas on 2011-03-01
Your not the only ones to ponder such things.
[http://serverfault.com/questions/134319/wine-and-windows-virus]("http://serverfault.com/questions/134319/wine-and-windows-virus")

I would also say it depends on the virus. However Wine is not sandboxed so dont run them as a test. See:
[http://ubuntuforums.org/showthread.php?t=72598]("http://ubuntuforums.org/showthread.php?t=72598")

I guess you could make a virtual machine and run in that thou if you are really curious.

---

### Post by cariboo on 2011-03-01
This question has been asked and answered several time before, I would say often enough to almost make it a recurring discussion See here:

[http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

[http://ubuntuforums.org/showthread.php?t=1491008](http://ubuntuforums.org/showthread.php?t=1491008)

[http://ubuntuforums.org/showthread.php?t=1083222](http://ubuntuforums.org/showthread.php?t=1083222)

[http://ubuntuforums.org/showthread.php?t=471499](http://ubuntuforums.org/showthread.php?t=471499)

---

### Post by doas777 on 2011-03-01
asked? yes. answered? only in the most generic way.

as others have said, it depends entirely on how the malware functions. I've read interviews with ad/spyware crafters who have gotten their payloads to run flawlessly in wine. [http://philosecurity.org/2009/01/12/interview-with-an-adware-author](http://philosecurity.org/2009/01/12/interview-with-an-adware-author)

not saying you are wrong, just that being blasse about it is as bad as running around proclaiming for all to hear that the sky is falling. the topic deserves neither denials nor hysteria.

---

### Post by Jonker on 2011-03-02
Could one not try running Ubuntu in a sandbox and extecute a "funny virus" there?

---

### Post by doas777 on 2011-03-02
> **Jonker said:**
> Could one not try running Ubuntu in a sandbox and extecute a "funny virus" there?
one could certainly try. in all likelhood it will do nothing, or nothing dangerous, but you can never be sure. 

also be careful about the word "virus". it means somthing far more specific than most people realize. There are very few "viruses" for any platform. most everything focuses on trojans and worms now a days.

---

### Post by Jonker on 2011-03-02
but would the virus do generaly, the same harm to the computer like to a windows?

---

### Post by doas777 on 2011-03-02
> **Jonker said:**
> but would the virus do generaly, the same harm to the computer like to a windows?
no probably not, but it depends on what it is trying to do. a peice of javascript-based ad/spyware will generally function just as well in ubuntu as in windows, since all it needs is firefox to perform its evil. if that same malware tried to delete the system root however, it would seriously fail.

---

