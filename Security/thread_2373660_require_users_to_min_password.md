---
title: "require users to min password"
date: 2017-10-08
forum: Security
---

### Post by micahpage on 2017-10-08
Ive been trying to tighten up my server against hacks. However in the process i somehow messed up passwd for password changes.

before i was able to use passwd to change passwords but now i get module unknown
```
metulburr ~ $ passwd
Changing password for metulburr.
(current) UNIX password: 
passwd: Module is unknown
passwd: password unchanged

```

I havent changed anything in config files, only looked at them..even though i used vim and sudo to look at them. 

EDIT: the one listed i did change was hosts.allow

```
 1986  cat /etc/passwd | awk -F':' '{ print $1}' | xargs -n1 groups 
 1987  chage -d 0 user1
 1988  sudo chage -d 0 user1
 1989  sudo chage -d 0 user2
 1990  sudo chage -d 0 user3
 1991  sudo chage -d 0 user4
 1992  sudo chage -d 0 user5
 1993  sudo chage -d 0 user6
 1994  pwscore
 1995  sudo apt-get install pwscore
 1996  sudo apt-get install libpwquality-tools
 1997  pwscore
 1998  sudo vim /etc/hosts.allow
 1999  cat /etc/hosts.allow
 2000  sudo reboot now
 2001  sudo vim  /etc/security/pwquality.conf
 2002  sudo vim /etc/pam.d/sshd
 2003  sudo vim /etc/pam.d/common-password 
 2004  pwscore
 2005  /etc/pam.d/system-auth
 2006  pwscore
 2007  /etc/pam.d/common-password
 2008  sudo /etc/pam.d/common-password
 2009  sudo grep password /etc/pam.d/common-password
 2010  sudo vim /etc/login.defs
 2011  sudo vim /etc/pam.d/common-password 
 2012  passwd
 2013  history



```

EDIT:
whoops sorry, i did edit a file.
/etc/pam.d/common-password 
and i added 
> password requisite pam_cracklib.so try_first_pass retry=3 minlength=12 lcredit=1 ucredit=1 dcredit=1     ocredit=1 difok=4



and with that addition passwd no longer works. I am trying to force a min password

---

### Post by Andreyshel on 2017-10-08
Do you have package libpam-cracklib installed?

---

### Post by untrustytahr on 2017-10-08
When it comes to working on PAM stuff, it is really important to understand what you are doing before doing it.  You would be wise to make a copy of whatever file(s) you are working on so you can revert back if necessary.  If you copied the line


> password requisite pam_cracklib.so try_first_pass retry=3 minlength=12 lcredit=1 ucredit=1 dcredit=1 ocredit=1 difok=4from the internet, I am willing to bet it does not do what you you think it does.  Most people think it requires a password of 12 characters with one upper,lower,digit,and other character in it.  It **doesn't**.  That line will pass its check with an 8 character password as long as it had all 4 character groups.  You would need to set the length to 16 and each character class to -1 to require a password of at least 12 characters with each class (upper,lower,digit,other).


Your initial post stated that you wanted a minimum length and nothing about complexity.  That doesn't require cracklib at all, but since you have probably already installed it by now, if you set each character class to 0, then the minimum length would be the number of characters that you entered for your password.  However, it would not force you to have each character class, but that's alright since you did not have that as an original requirement.

---

### Post by micahpage on 2017-10-09
thank you.

---

### Post by HermanAB on 2017-10-10
PAM is a very sensitive gal.  You got to handle her with the utmost care, or you may not be able to log into your machine at all.

---

