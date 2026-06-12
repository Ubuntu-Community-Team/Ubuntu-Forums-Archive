---
title: "Security problem?"
date: 2014-09-30
forum: Security
---

### Post by alvaro4 on 2014-09-30
Good Morning, 


I just got a undelivered emails, which I have not written. These emails contain this information: 
Subject: 


TESTING - 2012 
from: 
  ***** 
Date: 
30/09/2014 10:57 
to: 
***** 


############################# info #################### ######### 
############################# FOR YOU ################### ########## 
. 
. 
. 


SSH ############################# info ################### ########## 
############################# FOR YOU ################### ########## 
. 
. 
. 
############################# SHADOWFILE #################### ######### 
############################# SHADOWFILE #################### ######### 
. 
. 
. 
############################# iPS #################### ######### 
############################# iPS #################### #########
.
.
.
USERS WITH SHELL ############################# ################## ########### 
USERS WITH SHELL ############################# ################## ########### 
. 
. 
. 


In this information I can see all the users and groups on the system. So I think I have hacked the server, I changed the root password, but I do not know if I can do something else. 


A greeting and I hope your help

---

### Post by John_Ten on 2014-09-30
Well, you should check quickly from where you got the email! If you got it from inside the server then it's a problem, for example someone compromised it and was trying to read /etc/passwd and /etc/shadow, ifconfig and shell users in /etc/passwd.Basically you need to check the email headers and take action, maybe run chkrootkit or rkhunter, inspect logs, changing the root password won't solve much if the attacker is already in the machine.

---

