---
title: "Is apparmor needed for good security?"
date: 2010-01-06
forum: Security
---

### Post by dogdo on 2010-01-06
Hi

Ive already read that closed sticky thread on configuring apparmor but i still cant pin down my firefox profile right for my pc...that said if someone was able via a zero day exploit able to get to my pc would they first have to bypass sudo to install malware or would they be able to trash my home directory immediately?

---

### Post by cdenley on 2010-01-06
The only protection from a 0-day exploit is something such as apparmor. If there is an exploit that allows the attacker to execute arbitrary code, and it isn't restricted by something like apparmor, then the attacker can do anything which the user the process is running as (yourself) can do. Of course, they would need the sudo password to get root (unless they know a local privilege escalation vulnerability), but your user has permission to create scripts or binaries in your own home directory, read sensitive data which may be on your home directory, or use network tools to attack other systems (possibly on your LAN).

Of course noscript prevents most 0-day expoits in firefox. Also, ubuntu 9.10 already includes a firefox apparmor profile.

---

### Post by bodhi.zazen on 2010-01-06
> **cdenley said:**
> Of course noscript prevents most 0-day expoits in firefox. Also, ubuntu 9.10 already includes a firefox apparmor profile.

This is the best reason to upgrade to 9.10

Firefox has a ton of vulnerabilities, I counted 50 or so on[ USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn")

---

### Post by running_rabbit07 on 2010-01-06
> **bodhi.zazen said:**
> This is the best reason to upgrade to 9.10

Firefox has a ton of vulnerabilities, I counted 50 or so on[ USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn")

How does the upgrade effect this? Does Karmic have different AA settings or is the upgrading of FF that makes the difference? Or both?:)

---

### Post by bodhi.zazen on 2010-01-06
Upgrading what exactly ?

If you upgrade to Ubuntu 9.10, the firefox profile is in the package apparmor-profiles, and if you have that package installed (apparmor-profiles) it (the firefox profile) will be included when you upgrade (to 9.10).

The firefox profile is fairly generic (as you might imagine for firefox), and you may wish to review it. I modified it to restrict access to files in $HOME a tad =)

If you are asking about upgrading firefox, yes the firefox profile is fairly generic, so the upgrade to a new version of ff works.

From time to time the firefox profile is updated.

---

### Post by running_rabbit07 on 2010-01-06
> **bodhi.zazen said:**
> Upgrading what exactly ?

If you upgrade to Ubuntu 9.10, the firefox profile is in the package apparmor-profiles, and if you have that package installed (apparmor-profiles) it (the firefox profile) will be included when you upgrade (to 9.10).

The firefox profile is fairly generic (as you might imagine for firefox), and you may wish to review it. I modified it to restrict access to files in $HOME a tad =)

If you are asking about upgrading firefox, yes the firefox profile is fairly generic, so the upgrade to a new version of ff works.

From time to time the firefox profile is updated.

I was asking which aspect of the upgrade to karmic added security to FF. I guess it is the AppArmor that makes it better. I have just recently started reading your thread on aparmor and it has me motivated to learn more about it. I have Karmic and I added the ```
sudo apt-get install apparmor-profiles
``` package, but I haven't started tweaking it yet. I do plan on copying your configurations that you linked in the thread, once I feel more confident in how AA works.

---

### Post by bodhi.zazen on 2010-01-06
AWESOME =)

Just keep in mind, by default aa profiles are not active, you need to enable them.

---

### Post by running_rabbit07 on 2010-01-06
> **bodhi.zazen said:**
> AWESOME =)

Just keep in mind, by default aa profiles are not active, you need to enable them.

By activating, do you mean changing from complain to enforce? Such as,
```
rabbit@rabbit-desktop:~$ sudo enforce firefox
[sudo] password for rabbit: 
Setting /etc/apparmor.d/usr.bin.firefox-3.5 to enforce mode.
```I was able to get all of the profiles except these three changed to enforce.```
/usr/sbin/dovecot (complain)
/usr/lib/dovecot/pop3 (complain)
/usr/lib/dovecot/imap (complain)
```
When I enter the command to change them I get this ```
root@rabbit-desktop:/home/rabbit# enforce pop3
Can't find pop3 in the system path list.  If the name of the application is correct, please run 'which pop3' as a user with the correct PATH environment set up in order to find the fully-qualified path.
root@rabbit-desktop:/home/rabbit# enforce imap
Can't find imap in the system path list.  If the name of the application is correct, please run 'which imap' as a user with the correct PATH environment set up in order to find the fully-qualified path.
root@rabbit-desktop:/home/rabbit# enforce dovecot
Can't find dovecot in the system path list.  If the name of the application is correct, please run 'which dovecot' as a user with the correct PATH environment set up in order to find the fully-qualified path.
root@rabbit-desktop:/home/rabbit#
```

---

### Post by bodhi.zazen on 2010-01-06
> **running_rabbit07 said:**
> By activating, do you mean changing from complain to enforce? Such as,
```
rabbit@rabbit-desktop:~$ sudo enforce firefox
[sudo] password for rabbit: 
Setting /etc/apparmor.d/usr.bin.firefox-3.5 to enforce mode.
```I was able to get all of the profiles except these three changed to enforce.```
/usr/sbin/dovecot (complain)
/usr/lib/dovecot/pop3 (complain)
/usr/lib/dovecot/imap (complain)
```When I enter the command to change them I get this ```
root@rabbit-desktop:/home/rabbit# enforce pop3
Can't find pop3 in the system path list.  If the name of the application is correct, please run 'which pop3' as a user with the correct PATH environment set up in order to find the fully-qualified path.
root@rabbit-desktop:/home/rabbit# enforce imap
Can't find imap in the system path list.  If the name of the application is correct, please run 'which imap' as a user with the correct PATH environment set up in order to find the fully-qualified path.
root@rabbit-desktop:/home/rabbit# enforce dovecot
Can't find dovecot in the system path list.  If the name of the application is correct, please run 'which dovecot' as a user with the correct PATH environment set up in order to find the fully-qualified path.
root@rabbit-desktop:/home/rabbit#
```

When you have problems, specify the path to the aa profile (or cheat and use wildcards)

```
root@zenix:~#aa-enforce /etc/apparmor.d/usr.sbin.dovecot 
Setting /etc/apparmor.d/usr.sbin.dovecot to enforce mode.

root@zenix:~#aa-enforce /etc/apparmor.d/usr.lib.dovecot.*
Setting /etc/apparmor.d/usr.lib.dovecot.deliver to enforce mode.
Setting /etc/apparmor.d/usr.lib.dovecot.dovecot-auth to enforce mode.
Setting /etc/apparmor.d/usr.lib.dovecot.imap to enforce mode.
Setting /etc/apparmor.d/usr.lib.dovecot.imap-login to enforce mode.
Setting /etc/apparmor.d/usr.lib.dovecot.managesieve-login to enforce mode.
Setting /etc/apparmor.d/usr.lib.dovecot.pop3 to enforce mode.
Setting /etc/apparmor.d/usr.lib.dovecot.pop3-login to enforce mode.
root@zenix:~#
```

---

### Post by running_rabbit07 on 2010-01-06
Sweet! Thanx!

---

### Post by running_rabbit07 on 2010-01-06
Here is the stupid question of the day from me. Would this wildcard work? ```
aa-enforce /etc/apparmor.d/*
```Edit: Tested it in VBox. I guess it wouldn't be recommended if one has profiles that haven't been tested in complain mode first.

Now to move on to creating AppArmor profiles.

---

### Post by rookcifer on 2010-01-07
> **running_rabbit07 said:**
> Here is the stupid question of the day from me. Would this wildcard work? ```
aa-enforce /etc/apparmor.d/*
```Edit: Tested it in VBox. I guess it wouldn't be recommended if one has profiles that haven't been tested in complain mode first.

Now to move on to creating AppArmor profiles.

Yes, that works, and it is even a technique shown in the AppArmor sticky.  It's a good way to switch everything on or off if you have a problem.

Creating the profiles are fairly easy, given that you understand what the application you are creating the profile for does and why it does it.

---

