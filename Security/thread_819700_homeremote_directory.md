---
title: "/home/remote/ directory?"
date: 2008-06-05
forum: Security
---

### Post by richeepoo on 2008-06-05
Hi

First of all, Hello,  I'm new on here and this'll be my first posting.  Forgive me for jumping straight in, but no amount of googling has helped, so here I am.

I just need to know if it's normal to find a /home/remote directory and a user named remote in users.  I've never seen this before and never set this up and I think it's probably meant to be there for some reason, but being a little scared the system may have been compromised I thought it a good idea to ask. So, is it supposed to be there?  If so, why and what's it for? 

Cheers 


Rich

---

### Post by HalPomeranz on 2008-06-06
I'm not sure why that directory would exist.  Do an "ls -ld /home/remote" and see what user owns the directory.  You might also try "grep /home/remote /etc/passwd" to see if any user in the password file has that directory set as their homedir.

If you fear your system may have been compromised, try running rkhunter and/or chkrootkit (both available via Synaptic or apt-get) and see if they detect any signs of a break-in on your machine.

Good luck!

---

### Post by richeepoo on 2008-06-08
cat> **HalPomeranz said:**
> I'm not sure why that directory would exist.  Do an "ls -ld /home/remote" and see what user owns the directory.  You might also try "grep /home/remote /etc/passwd" to see if any user in the password file has that directory set as their homedir.

If you fear your system may have been compromised, try running rkhunter and/or chkrootkit (both available via Synaptic or apt-get) and see if they detect any signs of a break-in on your machine.

Good luck!

I did all this.   The user "remote" owns the directory.  I can't login to the "remote account" as a normal user as it appears to have a password.

I did,  less /etc/passwd | grep remote  and got
remote:x:1001:1002:,,,,:/home/remote:/bin/bash

chkrookit reports all ok but rkhunter has some warnings. Here's the relevant output.

Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /bin/bash                                                [ OK ]
.......................................cut
    /usr/bin/dpkg                                            [ Warning ]
    /usr/bin/dpkg-query                                      [ Warning ]
.......................................cut

Performing trojan specific checks
    Checking for enabled inetd services                      [ OK ]
    Checking for enabled xinetd services                     [ Warning ]
    Checking for Apache backdoor                             [ Not found ]

Performing system configuration file checks
    Checking for SSH configuration file                      [ Found ]
    Checking if SSH root access is allowed                   [ Warning ]

Performing filesystem checks

    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

Even though their is a warning about ssh root access I am unable to log in as root to this machine.

I checked the rkhunter log file, it didn't give me anything more than the output.  Other than this "remote" user and "/home/remote" directory appearing all looks fine.  Does anyone know if some process could legitimately cause this in the same way I have an ftp user, group and "/home/ftp" directory?

Cheers

Rich

---

### Post by richeepoo on 2008-06-08
cat> **HalPomeranz said:**
> I'm not sure why that directory would exist.  Do an "ls -ld /home/remote" and see what user owns the directory.  You might also try "grep /home/remote /etc/passwd" to see if any user in the password file has that directory set as their homedir.

If you fear your system may have been compromised, try running rkhunter and/or chkrootkit (both available via Synaptic or apt-get) and see if they detect any signs of a break-in on your machine.

Good luck!

I did all this.   The user "remote" owns the directory.  I can't login to the "remote account" as a normal user as it appears to have a password.

I did,  less /etc/passwd | grep remote  and got
remote: x :1001:1002:,,,,:/home/remote:/bin/bash

chkrookit reports all ok but rkhunter has some warnings. Here's the relevant output.

Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /bin/bash                                                [ OK ]
.......................................cut
    /usr/bin/dpkg                                            [ Warning ]
    /usr/bin/dpkg-query                                      [ Warning ]
.......................................cut

Performing trojan specific checks
    Checking for enabled inetd services                      [ OK ]
    Checking for enabled xinetd services                     [ Warning ]
    Checking for Apache backdoor                             [ Not found ]

Performing system configuration file checks
    Checking for SSH configuration file                      [ Found ]
    Checking if SSH root access is allowed                   [ Warning ]

Performing filesystem checks

    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

Even though their is a warning about ssh root access I am unable to log in as root to this machine.

I checked the rkhunter log file, it didn't give me anything more than the output.  Other than this "remote" user and "/home/remote" directory appearing all looks fine.  Does anyone know if some process could legitimately cause this in the same way I have an ftp user, group and "/home/ftp" directory?

Cheers

Rich

---

### Post by brian_p on 2008-06-08
> **richeepoo said:**
> I just need to know if it's normal to find a /home/remote directory and a user named remote in users.  I've never seen this before and never set this up  . . . . .

I've never seen it before either so is the faulty memory tack worth following? It's what I'd pursue first. The rkhunter log doesn't look abnormal.

What are the directory contents? Do the dates on the directory and its contents give any clues? What do you get for

```
sudo cat /etc/group | grep remote
```

and how does the date on /etc/group compare with dates on other files in /etc and /home/remote?

Have you installed ftp or ssh servers?

---

### Post by richeepoo on 2008-06-08
Thanks for your help.

I've become totaly paranoid about the whole thing.  I've decided to re-install the whole system and change my passwords.  Luckily there's nothing too important that hasn't been backed up so I'll lose nothing but time.

Cheers

Rich

---

### Post by brian_p on 2008-06-08
> **richeepoo said:**
> Thanks for your help.

I've become totaly paranoid about the whole thing.  I've decided to re-install the whole system and change my passwords.  Luckily there's nothing too important that hasn't been backed up so I'll lose nothing but time.

Cheers

Rich

I was going to point you to

[http://ohioloco.ubuntuforums.org/showthread.php?t=596917&page=2](http://ohioloco.ubuntuforums.org/showthread.php?t=596917&page=2)

Post #18 is the relevant one. It's the only reference I've seen to /home/remote. Ring any bells?

Good luck with the reinstall.

---

