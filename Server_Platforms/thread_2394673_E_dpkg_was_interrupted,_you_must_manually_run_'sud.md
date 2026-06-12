---
title: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a"
date: 2018-06-19
forum: Server Platforms
---

### Post by eightpock on 2018-06-19
Hello. 
I am attempting to update an Ubuntu server (Ubuntu 16.04.3 LTS) and I've encountered a problem I have not seen before. Refer below. 

root@host:~# sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
root@host:~# sudo dpkg --configure -a
dpkg: error processing package php7.0-mysql (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Processing triggers for libapache2-mod-php7.0 (7.0.28-0ubuntu0.16.04.1) ...
Errors were encountered while processing:
 php7.0-mysql


Has anyone had this error before? If I reinstall php7.0-mysql do I risk any data loss?

---

### Post by QIII on 2018-06-19
First let me make a couple of points:

1. Using the root account is very dangerous. By default, Ubuntu's root account is disabled/locked and we don't recommend enabling it.  Please see [this]("https://help.ubuntu.com/community/RootSudo") for the Forums Staff "official" position.  However, it is your system and you are free to mangle it as you wish.

2. Root does not require sudo.  sudo (***s**ubstitue **u**ser and **do*** -- or -- ***s**witch **u**ser and **do***) defaults to root's privileges if no other user is specified (i.e.: sudo billybob), so using sudo while root is at best superfluous.

3. It is far safer to operate as an admin user and use sudo to temporarily elevate your privileges.  This is not unique to Ubuntu.  I don't run as root on other distros, either.

To your question:  Do you risk data loss?  Not specifically due to that operation -- but I recommend backing up important data regularly in any case and before making substantive changes to your system.  Any change can lead to disaster and an inoperable system.  That notwithstanding, you do risk running into the same issue.  Just let us know.

---

### Post by #&amp;thj^% on 2018-06-19
Nicely said QIII ^^^^^
*The Golden Rule*
1st and formost You should always have good back-up's in place. ;)
Lets see if we lucky with:
```
sudo apt-get install -f --reinstall php7.0-mysql
```

---

### Post by LHammonds on 2018-06-19
To add onto what QIII said, your original problem might have come from a full drive.  Make sure you have free space before making further changes.

```
df -h
```

If you did not run out of space and you have plenty free, then go ahead and remove php and re-install it...but only after you have a good backup like QIII said.  Re-installing PHP and/or Apache and various libraries should not lose your data/websites.  But depending on how you remove/install, you might lose your configurations that point to your website(s).  Having a backup of your configs will help if that becomes an issue.

Since you are not going from one version of PHP to another, it will likely be no problem...but that is just my opinion (and might be incorrect)

LHammonds

---

