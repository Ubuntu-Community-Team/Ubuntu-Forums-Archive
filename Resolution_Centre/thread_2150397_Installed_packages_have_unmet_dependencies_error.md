---
title: "Installed packages have unmet dependencies error"
date: 2013-05-31
forum: Resolution Centre
---

### Post by nadarajan on 2013-05-31
Hi,
I have a 64bit machine running Ubuntu 12.04 LTS. For the past few weeks there is a red dot at the top of the window. When I click on it it shows "An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: "Error: BrokenCount>0". This usually means that your installed packages have unmet dependencies". I am unable to install anything. When I try, I get the following error message:

installArchives() failed: dpkg: dependency problems prevent configuration of mysql-client: 
 mysql-client-core-5.5 (5.5.31-0ubuntu0.12.04.1) breaks mysql-client (<< 5.5.31-0ubuntu0.12.04.1) and is installed. 
  Version of mysql-client to be configured is 5.5.29-0ubuntu0.12.04.2. 
dpkg: error processing mysql-client (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 mysql-client 
Error in function:  
dpkg: dependency problems prevent configuration of mysql-client: 
 mysql-client-core-5.5 (5.5.31-0ubuntu0.12.04.1) breaks mysql-client (<< 5.5.31-0ubuntu0.12.04.1) and is installed. 
  Version of mysql-client to be configured is 5.5.29-0ubuntu0.12.04.2. 
dpkg: error  processing mysql-client (--configure): 
 dependency problems - leaving unconfigured

Please let me know how to resolve it.

Thanks

---

### Post by cariboo on 2013-06-01
The Resolution Centre is a place where can voice your complaints against the Moderation Team, not for asking support questions. I will close this thread, and copy it to General Help, where you question should be answered fairly soon.

---

