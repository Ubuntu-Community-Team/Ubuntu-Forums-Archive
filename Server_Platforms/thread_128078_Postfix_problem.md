---
title: "Postfix problem"
date: 2006-02-10
forum: Server Platforms
---

### Post by siefkencp on 2006-02-10
I have tried to install postfix several times and i now get this message any time i try to use it to send mail. I have completely removed it and reset it up but I still get the same error....

I'm out of options-- so I guess I need to reinstall from ground 0?

I dont want to but i'm at a loss...

warning: unable to look up public/pickup: No such file or directory

---

### Post by robert_pectol on 2006-02-13
Did you install Postfix from the Ubuntu repos?  I've installed it on several Ubuntu machines and have never seen that message.

---

### Post by MJN on 2006-02-13
What exactly do you mean by 'try to use it to send mail'?
 
What are you using to send your mail? Is Postfix actually running? (try a /etc/init.d/postfix start and watch for output - including the logs)
 
Mathew

---

### Post by siefkencp on 2006-02-13
Ok, I messed up in my installation some how during the set up process and some files were missing/confused/incorrectly permissioned. In any case i tried removing it and got myself in more trouble... fortunately this is a brand new set up so i simply re-installed the OS. I ran the desktop set up with out second guessing myself this time and it works correctly. Phase 2 will make this a full blown mail server but for now it's just sending mail and running a php/mysql app. 

I have officially moved from RHEL to Ubuntu - in production, and I am never gonna look back!

Thanks for the ideas... what do I have to do to land another bean around here??

---

