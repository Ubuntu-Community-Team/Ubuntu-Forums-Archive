---
title: "Problem with bind19 and Postfix"
date: 2013-10-12
forum: Server Platforms
---

### Post by Qr4cl3 on 2013-10-12
When I try to install bind9 i found following problems

>   You might want to run 'apt-get -f install' to correct these:The following packages have unmet dependencies:
 bind9 : Depends: libbind9-80 (= 1:9.8.1.dfsg.P1-4ubuntu0.7) but 1:9.8.1.dfsg.P1-4ubuntu0.4 is to be installed
         Depends: libdns81 (= 1:9.8.1.dfsg.P1-4ubuntu0.7) but 1:9.8.1.dfsg.P1-4ubuntu0.4 is to be installed
         Depends: libisc83 (= 1:9.8.1.dfsg.P1-4ubuntu0.7) but 1:9.8.1.dfsg.P1-4ubuntu0.4 is to be installed
         Depends: libisccc80 (= 1:9.8.1.dfsg.P1-4ubuntu0.7) but 1:9.8.1.dfsg.P1-4ubuntu0.4 is to be installed
         Depends: libisccfg82 (= 1:9.8.1.dfsg.P1-4ubuntu0.7) but 1:9.8.1.dfsg.P1-4ubuntu0.4 is to be installed
         Depends: liblwres80 (= 1:9.8.1.dfsg.P1-4ubuntu0.7) but 1:9.8.1.dfsg.P1-4ubuntu0.4 is to be installed
         Depends: bind9utils (= 1:9.8.1.dfsg.P1-4ubuntu0.7) but 1:9.8.1.dfsg.P1-4ubuntu0.4 is to be installed
 postfix-ldap : Depends: postfix (= 2.9.3-2~12.04.4) but 2.9.6-1~12.04.1 is to be installed
 postfix-pcre : Depends: postfix (= 2.9.3-2~12.04.4) but 2.9.6-1~12.04.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So, i have following questions
 1. Are there any ways to solve such problems
 2. Are there any effect to this server and postfix ?  If i try to update **postfix-ldap** and **postfix-pcre.**
thank you.

---

### Post by Habitual on 2013-10-12
Try 'apt-get -f install' with no packages?

---

### Post by Qr4cl3 on 2013-10-12
I've already try this, result still the same 
> [COLOR=#000000]*postfix-ldap : Depends: postfix (= 2.9.3-2~12.04.4) but 2.9.6-1~12.04.1 is to be installed*[/COLOR]
[COLOR=#000000]*postfix-pcre : Depends: postfix (= 2.9.3-2~12.04.4) but 2.9.6-1~12.04.1 is to be installed*[/COLOR]

---

### Post by SeijiSensei on 2013-10-14
Did you run "sudo apt-get update" first?  Your package lists may be out of date.

---

### Post by Qr4cl3 on 2013-10-17
Yep, I've already done that.

---

