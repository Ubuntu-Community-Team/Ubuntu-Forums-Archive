---
title: "SELinux - restricting root user"
date: 2013-02-24
forum: Security
---

### Post by su27 on 2013-02-24
Hi,

I'm totally new to SELinux but I need to know if it is possible to restrict root user to have full OS permissions except access to one executable file and the process that is run by that file (disable ability to kill that process)?
Maybe someone did something similar and have some tips/instructions how to do it?

TIA

Regards
su27

---

### Post by unspawn on 2013-02-24
> **su27 said:**
> I'm totally new to SELinux but 
...then learning about SELinux first would probably be the most efficient thing to do.


> **su27 said:**
> I need to know if it is possible to restrict root user to have full OS permissions except access to one executable file and the process that is run by that file (disable ability to kill that process)?
Two points here: first of all regard "root" as a set of privileges required to run a system in the UNIX tradition and not as some account. Secondly realize the default "targeted" SELinux policy is one of the "hard on the outside, chewy on the inside" kind: it's designed to protect the system against FOD while allowing local user convenience. The latter should lead to the conclusion that you will need to build a different policy yourself, probably MLS-type, and the first one should lead to questioning what you (think you) intend to do in the first place.

Maybe it would be better to explain in detail what you want to do and what you think you should protect against.

---

### Post by samiux on 2013-02-24
> **su27 said:**
> if it is possible to restrict [COLOR="RoyalBlue"]root[/COLOR] user to have full OS permissions except access to one executable file and the process that is run by that file ([COLOR="RoyalBlue"]disable ability to kill that process[/COLOR])?

As far as I know, "root" user is the highest privilege account in *nix system (such as Linux).  

What do you think if the highest privilege account is restricted to do something else (such as the ability to kill a process) in the system?  What will be the account can do that command or have this ability/rights?

It may be another "root" account namely "root the second"?  What if the "root the second" is restricted to do something else?  .... endless ....

I think SELinux cannot do that or similar.  I guess the most suitable solution is "sudoer" account.  It is because you can restrict the sudoer for doing something else.

Please do not touch "root" account, thanks.

Samiux

---

### Post by su27 on 2013-02-24
> **unspawn said:**
> 
Maybe it would be better to explain in detail what you want to do and what you think you should protect against.

I have to publish ami image in aws cloud so anyone who use it will have root access - but I need to keep a running agent on the instance and I don't want root user to kill it or change configuration.

> **samiux said:**
> 
It may be another "root" account namely "root the second"? 

That's exactly what I'm thinking of - "root" account with almost all privileges except access to one resource and "admin" with real root privileges.

---

### Post by su27 on 2013-02-25
In fact I don't need another root - all I need is to restrict unconfined users access to this one file/process. Then I can have one basic OS user with selinux admin rights and access to the file.

---

### Post by Hungry Man on 2013-02-25
Run that process as a separate user or store the file in a separate user account, and only root will be able to access it.

---

### Post by offgridguy on 2013-02-25
> **su27 said:**
> 
That's exactly what I'm thinking of - "root" account with almost all privileges except access to one resource and "admin" with real root privileges.
What you are describing here does not sound realistic. Root by
definition has all privileges, by default. Root in linux is the equivalent of Administrator in windows. Admin in linux does not
have Root privileges, hence the need for sudo .
edit; correction, I see that in Fedora 18, Administrator is Root.

---

### Post by bodhi.zazen on 2013-02-26
> **offgridguy said:**
> What you are describing here does not sound realistic. Root by
definition has all privileges, by default. Root in linux is the equivalent of Administrator in windows. Admin in linux does not
have Root privileges, hence the need for sudo .
edit; correction, I see that in Fedora 18, Administrator is Root.

You can restrict any user, including root, with either apparmor or selinux.

If you have questions on how to configure selinux, I HIGHLY suggest you start with the Fedora selinux guide:

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/index.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/index.html)

You will then need to explain exactly what you want. First you are asking about preventing the root user from killing a process, next you are talking about preventing access to a file.

These tasks can probably be done best with proper configuration of your users access to root power (ie proper configuration of sudo) and/or Linux permissions.

If you need selinux to confine root, I can not tell if you need to simply confine your users, confine root, or go to a different selinux policy.

If you wish more information on selinux you are best off asking on IRC (#fedora-selinux or #selinux) as, IMO, most people who use Ubuntu do not know much about selinux.

---

