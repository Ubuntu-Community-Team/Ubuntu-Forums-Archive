---
title: "Executable from Samba?"
date: 2010-08-09
forum: Server Platforms
---

### Post by aguerrette on 2010-08-09
Hi everyone,

We currently have a problem with an executable from Samba. The file itself is an accounting system executable which use to run from basically a shared drive on windows. Upon the purchase of a server, we moved everything there. But now the problem is, that once in a while when we have several users in the system, the program (executable) freezes and causes the users to shut it down and start again. This file reads and writes to database files.
Now I've played around with the oplocks and fake oplocks settings for the share and it didn't fix the problem. And now I have set the force unix user to 1 specific user. Which up to now seems to be ok, but yet I still get some write errors...
Also, I know it's not the network, because we have 15 other users loading documents from different shares with different user rights without any problems.
Now am I overlooking something, or am I just dreaming of the fact that I can run an executable from the server itself?
Any help of suggestions would be greatly appreciated, I have basically ran out of ideas on what to do.

Thanks,
Andre

---

### Post by clrg on 2010-08-09
I'm no expert in this, but I guess the program does not like being executed from several users on several workstations. 

Do you also have problems if only one person uses the program (starting it from samba)?

---

### Post by aguerrette on 2010-08-09
Thing is, the program is designed to be used by several users at the same time. And the force Unix user didn't work as well so basically I'm back to square one.
After contacting the manufacturer, they know nothing except that they have other companies using their software off a Unix box without any problems (they say)...
The program will still cause some problems even with only 1 user in it. It almost looks like Samba is locking the database files and when a Write attempt is made, and then it freezes the application. 
So if you compare when a Excel document is in read only mode because a user is already in the document, you get a warning, but in this case, the application would just freeze because of the Write attempt on that praticular file, does this make any sense? Is there anyting I can do to prevent files from being frozen maybe for this particular share?

---

### Post by clrg on 2010-08-09
I guess your program doesn't contain any data by itself (rather stores it in a database), so there is no need to write to it. Have you tried chmoding it to 550? 

Concerning the file locking mechanisms, I don't know why this shouldn't work. I don't think its Linux/Samba's fault. Imagine 200 users on a Linux server, and every single one wants to run cat on some file at the same time. Linux wouldn't even try to lock /bin/cat for a single user, since it makes no sense. Maybe the Faildows clients are trying to lock the file?

---

### Post by aguerrette on 2010-08-09
clrg, I think you just woke me up! I looked at the users/groups assigned and they both were my username because I was the one that had initially transfered all the file, thus making me the owner (right?) so the folder containing all the db info was owned myusername:myusername. So I changed it to the group that has access to this share, and everything seems (SEEMS) to be working fine now... I'll just have to wait and see tommorow morning to find out if this fixed it.

---

