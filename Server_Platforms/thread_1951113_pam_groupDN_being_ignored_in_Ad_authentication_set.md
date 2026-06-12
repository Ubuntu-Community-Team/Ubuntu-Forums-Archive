---
title: "pam_groupDN being ignored in Ad authentication setup"
date: 2012-04-01
forum: Server Platforms
---

### Post by jihlava on 2012-04-01
Hello

I'm trying to get 11.10 oneiric to authenticate against Active DIrectory and enforce user access by membership of an AD group.  I cannot get it to work.  The setup is essentially the same as this thread [http://ubuntuforums.org/showthread.php?t=1857385](http://ubuntuforums.org/showthread.php?t=1857385)  though I'm not sure if they pertains to 11.10 oneiric.  Perhaps its not as the solution posted there to modify /etc/pam.d/common-account does not work in my case.

I have joined the server to the domain and have the appropriate keytab entries.  I also use kerberos (GSSAPI) to authenticate for the ldap queries. All this works at the command line using ldapsearch.  The other method of providing a bind user and password to AD also works.

The problem is any AD user can login.  pam_groupDN in /etc/ldap.conf seems simply to be ignored.  I have traced the execution of the client process as it attempts to authenticate and at no stage does it appear that a search is made for the group specified to pam_groupDN.  I see this also with ldap debugging enabled. 

I've noted that elsewhere that 11.10 oneiric has introduced the preferred method of doing this to be the sssd software package.  I've tried that and appear to have uncovered a bug that prevents my use of it (bugreport is raised).

So does anyone know if the use of pam_groupDN is simply ignored in 11.10 or should it work?

many thanks

r.

---

