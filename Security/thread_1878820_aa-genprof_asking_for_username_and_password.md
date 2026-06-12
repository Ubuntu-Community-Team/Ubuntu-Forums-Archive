---
title: "aa-genprof asking for username and password"
date: 2011-11-10
forum: Security
---

### Post by newhere_m on 2011-11-10
This is regarding apparmor-profile creation for a program. Suppose I try this command:
```
sudo aa-genprof totem 
```It first asks for running th program in another window and after that asks for system scan. Next it asks if new user is to be created etc. I do not understand what this means. Can anybody please help. The response is here:
```

Please start the application to be profiled in 
another window and exercise its functionality now.

Once completed, select the "Scan" button below in 
order to scan the system logs for AppArmor events.  

For each AppArmor event, you will be given the  
opportunity to choose whether the access should be  
allowed or denied.

Profiling: /usr/bin/totem

[(S)can system log for SubDomain events] / (F)inish
Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.

Create New User?

(Y)es / [(N)o]
Username: 
Password: 

Save Configuration? 

[(Y)es] / (N)o



```The prompt for username appears even if I give "n". This ends with
```

Login Error
RPC::XML::Client::send_request: HTTP server error: Not Found

```However this query for user name and password is repeated until I try ctrl+z to come out of this sequence. My doubt is this prompt for this creation of new user is not indicated in usual apparmor-literature. I am not able to proceed beyond this step. Am I doing something wrong? (I use ubuntu 10.04LTS) (A funny thing happens when I give ctrl+z; the characters in the terminal all become boldface. Why does that happen and what does that indicate?)

---

