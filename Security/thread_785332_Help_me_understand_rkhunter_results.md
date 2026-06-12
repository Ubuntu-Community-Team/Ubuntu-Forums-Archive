---
title: "Help me understand rkhunter results"
date: 2008-05-07
forum: Security
---

### Post by hito1 on 2008-05-07
I ran rkhunter and got several warning results stating that commands had been replaced by a script:

```
[10:00:04] /bin/egrep                                        [ Warning ]
[10:00:04] Warning: The command '/bin/egrep' has been replaced by a script: /bin/egrep: POSIX shell script text executable
[10:00:04] /bin/fgrep                                        [ Warning ]
[10:00:04] Warning: The command '/bin/fgrep' has been replaced by a script: /bin/fgrep: POSIX shell script text executable
[10:00:06] /bin/which                                        [ Warning ]
[10:00:06] Warning: The command '/bin/which' has been replaced by a script: /bin/which: POSIX shell script text executable
[10:00:08] /usr/bin/groups                                   [ Warning ]
[10:00:08] Warning: The command '/usr/bin/groups' has been replaced by a script: /usr/bin/groups: POSIX shell script text executable
[10:00:09] /usr/bin/ldd                                      [ Warning ]
[10:00:09] Warning: The command '/usr/bin/ldd' has been replaced by a script: /usr/bin/ldd: Bourne-Again shell script text executable
[10:00:13] /usr/bin/lwp-request                              [ Warning ]
[10:00:13] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: perl script text executable
[10:00:15] /usr/sbin/adduser                                 [ Warning ]
[10:00:15] Warning: The command '/usr/sbin/adduser' has been replaced by a script: /usr/sbin/adduser: perl script text executable
```

All the rest was normal. Is my ubuntu compromised?

---

### Post by brian_p on 2008-05-07
> **hito1 said:**
> I ran rkhunter and got several warning results stating that commands had been replaced by a script:

```
[10:00:04] /bin/egrep                                        [ Warning ]
[10:00:04] Warning: The command '/bin/egrep' has been replaced by a script: /bin/egrep: POSIX shell script text executable
[10:00:04] /bin/fgrep                                        [ Warning ]
[10:00:04] Warning: The command '/bin/fgrep' has been replaced by a script: /bin/fgrep: POSIX shell script text executable
[10:00:06] /bin/which                                        [ Warning ]
[10:00:06] Warning: The command '/bin/which' has been replaced by a script: /bin/which: POSIX shell script text executable
[10:00:08] /usr/bin/groups                                   [ Warning ]
[10:00:08] Warning: The command '/usr/bin/groups' has been replaced by a script: /usr/bin/groups: POSIX shell script text executable
[10:00:09] /usr/bin/ldd                                      [ Warning ]
[10:00:09] Warning: The command '/usr/bin/ldd' has been replaced by a script: /usr/bin/ldd: Bourne-Again shell script text executable
[10:00:13] /usr/bin/lwp-request                              [ Warning ]
[10:00:13] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: perl script text executable
[10:00:15] /usr/sbin/adduser                                 [ Warning ]
[10:00:15] Warning: The command '/usr/sbin/adduser' has been replaced by a script: /usr/sbin/adduser: perl script text executable
```

All the rest was normal. Is my ubuntu compromised?

I think there is enough at

[http://forum.slicehost.com/comments.php?DiscussionID=1306](http://forum.slicehost.com/comments.php?DiscussionID=1306)

for you to make a decision.

---

### Post by roderick on 2008-05-07
I read that site, and had a look at my /bin/egrep and it's a binary executable elf32 and not a script.

I wonder then what package would replace /bin/egrep on the system with a shell script, as it is apparent that I do not have any such package installed. I am running Hardy upgraded from Gutsy and it's the KDE version (Kubuntu).

My /bin/egrep is provided by package grep (dpkg -S egrep returns grep as the package owning the file).

Checking in the package database, I see a conflict with package rgrep. Can you see if you have package rgrep installed and if /bin/egrep is part of that package? It appears rgrep is no longer in the repo, and only grep. 

You got me curious now about the differences... :)

---

### Post by hito1 on 2008-05-07
Thank you. :)

---

### Post by brian_p on 2008-05-07
> **roderick said:**
> I read that site, and had a look at my /bin/egrep and it's a binary executable elf32 and not a script.

I wonder then what package would replace /bin/egrep on the system with a shell script, as it is apparent that I do not have any such package installed. I am running Hardy upgraded from Gutsy and it's the KDE version (Kubuntu).

My /bin/egrep is provided by package grep (dpkg -S egrep returns grep as the package owning the file).

Checking in the package database, I see a conflict with package rgrep. Can you see if you have package rgrep installed and if /bin/egrep is part of that package? It appears rgrep is no longer in the repo, and only grep. 

You got me curious now about the differences... :)

For Debian etch:

```
josie@laptop:~$ file /bin/egrep /bin/fgrep /bin/grep 
/bin/egrep: Bourne shell script text executable
/bin/fgrep: Bourne shell script text executable
/bin/grep:  ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.1, dynamically linked (uses shared libs), for GNU/Linux 2.4.1, stripped
```

For Hardy and Debian unstable:

```
josie@laptop:~$ file /media/cdrom0/bin/egrep /media/cdrom0/bin/fgrep /media/cdrom0/bin/grep 
/media/cdrom0/bin/egrep: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped
/media/cdrom0/bin/fgrep: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped
/media/cdrom0/bin/grep:  ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped
```

The changelog.gz reveals all.

---

### Post by OrangeCrate on 2008-05-07
@OP

Did you update the data files prior to running rkhunter? If not, here's the command to do that:

```
sudo apt-get rkhunter --update
```

Here are a list of commands for rkhunter. It would be good to bookmark them for future reference:

[http://zbww.tech.us.edu.pl/cgi-bin/man/man2html?rkhunter+8](http://zbww.tech.us.edu.pl/cgi-bin/man/man2html?rkhunter+8)

-----

I just ran a scan on Hardy, and everything was O.K.

---

### Post by hito1 on 2008-05-08
> **OrangeCrate said:**
> @OP

Did you update the data files prior to running rkhunter? If not, here's the command to do that:

```
sudo apt-get rkhunter --update
```

Here are a list of commands for rkhunter. It would be good to bookmark them for future reference:

[http://zbww.tech.us.edu.pl/cgi-bin/man/man2html?rkhunter+8](http://zbww.tech.us.edu.pl/cgi-bin/man/man2html?rkhunter+8)

-----

I just ran a scan on Hardy, and everything was O.K.
Yes, I updated. And thank you for the link.

---

### Post by moonpup on 2008-05-08
From one of my other rkhunter posts... try this...

Here's a tip when using rkhunter... use the pkgmgr flag. This will use the distribution's package manager for verification.

ubuntu example:

sudo rkhunter --check --pkgmgr dpkg

redhat example:

rkhunter --check --pkgmgr rpm

just run rkhunter with no flags to see all the options available.

---

