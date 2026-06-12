---
title: "rkhunter warnings"
date: 2010-08-05
forum: Security
---

### Post by skaramanger on 2010-08-05
Greetings,

I am running:

 ```
[myuserprompt$ uname -a
Linux my-desktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
 [myuserprompt]$ 
```

When rkhunter runs I get a message (in separate emails):


> Please inspect this machine, because it may be infected.

and

> Warning: Hidden file found: /dev/.blkid.tab: ASCII text
Warning: Hidden file found: /dev/.blkid.tab.old: ASCII text

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

I checked for this file and it exists, but should be linked to a file in the /etc folder, but it is broken. I was able to do a cat of the files in question, but now they are not found:

[myprompt]$ ls -la /dev/.blkid.tab
ls: cannot access /dev/.blkid.tab: No such file or directory
[myprompt]$ 

tried sudo as well files are no longer there.  So what to do now? Any suggestions?

Tia,

Skaramanger

---

### Post by Bachstelze on 2010-08-05
> **skaramanger said:**
> 
So what to do now?

Nothing.  Those files are harmless.

---

### Post by Rubi1200 on 2010-08-05
Have you read this?
 
[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)
 
Have you run this?
 
```
 
rkhunter --update

```

---

### Post by skaramanger on 2010-08-05
> **Rubi1200 said:**
> Have you read this?
 
[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)
 
Have you run this?
 
```
 
rkhunter --update

```

No, but I did just now look.  I did look at the log file and when I ran rkhunter from the command line it did comeback clean.  However, I just want to reiterate that the .blkid.tab file did exist on the /dev folder. I could read it using cat or less.  Then I the files were no long there?  The link is still there though.

Thanks for your reply,

Skaramanger



I played around with blkid command. I'm satisified.:>

---

