---
title: "Auditing in Ubuntu"
date: 2008-04-22
forum: Security
---

### Post by wiz561 on 2008-04-22
Hi!

I'll probably have a number of questions relating to securing ubuntu in the near future.  I'm hoping to be able to setup a wiki page on how to make ubuntu confirm to nist-like standards.  

In order to do this though, I have a few questions relating to auditing.  I've been monkeying around with a few settings but can't seem to get them right.  I'm going through the auditing section of 800-53 and need to accomplish the following...

----
* Start-up and shutdown of the audit functions.
* Successful use of the user security attribute administration functions
* All attempted uses of the user security attribute administration functions 
&#131;
* Identification of which user security attributes have been modified 
&#131;* Successful and unsuccessful logons and logoffs 
&#131;* Unsuccessful access to security relevant files including creating, opening, closing, modifying, and deleting those files 
&#131;* Changes in user authenticators 
&#131;* Blocking or blacklisting user Ids, terminals, or access ports  
&#131;* Denial of access for excessive logon attempts 
&#131;* System accesses by privileged users 
&#131;* Privileged activities at the system console (either physical or logical consoles) and other system- level accesses by privileged users 
* Starting and ending times for each access to the system 

------

I've been able to get a couple of them correct, but is there an easy way to implement these?  Additionally, is there a nice interface to access the logs?


Thanks!

---

### Post by cbobb@alinean.com on 2008-04-24
Hi there,

I had to perform almost the same criteria for PCI compliance, and what I did was take the CIS benchmark for Linux (Red Hat) and modify to apply to Ubuntu, as those were the servers we were using.  The Benchmark covers quite a few of the topics that you listed below. Probably want to look into something that can monitor the logs being written and alert you to various triggers.  Also probably want to look into something like AIDE or Samhain for File integrity monitoring.  Good Luck.

cb


* Start-up and shutdown of the audit functions.
* Successful use of the user security attribute administration functions
* All attempted uses of the user security attribute administration functions 
ƒ
* Identification of which user security attributes have been modified 
ƒ* Successful and unsuccessful logons and logoffs 
ƒ* Unsuccessful access to security relevant files including creating, opening, closing, modifying, and deleting those files 
ƒ* Changes in user authenticators 
ƒ* Blocking or blacklisting user Ids, terminals, or access ports  
ƒ* Denial of access for excessive logon attempts 
ƒ* System accesses by privileged users 
ƒ* Privileged activities at the system console (either physical or logical consoles) and other system- level accesses by privileged users 
* Starting and ending times for each access to the system 

------

I've been able to get a couple of them correct, but is there an easy way to implement these?  Additionally, is there a nice interface to access the logs?


Thanks![/QUOTE]

---

