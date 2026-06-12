---
title: "Sending Main from the Command Line"
date: 2011-03-28
forum: Server Platforms
---

### Post by ScatterBrain on 2011-03-28
I'm installing a 10.04 server remotely - it's basically an RSYNC host for backups. I've got one minor issue - it's really more of an annoyance, but I would like to have it solved.
 
When sending e-mails, the messages come in addressed to three destinations - when it's only supposed to be sent to one. What's worse is that the two additional addresses are based on the hostname of the machine.
 
Let me explain: I use this command:
 
```
mail -s Testing email@somedomain.com
```
 
I then compose the e-mail and send it. The mail arrive a few seconds later but addresed to the following:
 
```
from@hostname.domain.com; email@somedomain.com; hostname@hostname.domain.com
```
 
The "from@hostname.domain.com" has the actual word "from" in the address.
 
I've installed many, many servers like this in the past and this is the first time that anything wonky with email has happened that I couldn't fix or explain. The machine is running postfix and I installed the bsd-mailx package to get the command line "mail" command (I used to install "mailx", but this seems to work just like the old package).
 
Anyone seen this before and if so have a clue as to how I can fix this?

---

### Post by ScatterBrain on 2011-03-28
Nevermind. I found the cause.
 
When I was using the mail command I was actually doing this:
 
```
mail -s testing from hostname email@somedomain.com
```
 
Notice that I didn't put quotes around the subject? Well, appearently the mail command was only using the first word for the subject and thinking the rest of the words on the line were e-mail addresses. Where is couldn't find domain names, it appended it's own hostname.
 
Smack me for not noticing it sooner.

---

