---
title: "Possibly infiltrated"
date: 2009-04-13
forum: Security
---

### Post by teaguecl on 2009-04-13
Yesterday my auth.log.0 shows that someone logged into my Ubuntu machine remotely over ssh using a user account which I no longer use, and haven't logged in with in months.  Not long after that, they were somehow able to su to root.
I've deleted the affected user account, and disabled root (passwd -l root) - but I'm not sure what all they did to my box.  One thing I picked out as unusual was that my sshd now points to sshd2.  Is this normal?

$ which sshd
/usr/local/sbin/sshd
$ ls -al /usr/local/sbin/sshd
lrwxrwxrwx 1 root root 5 2009-04-12 08:33 /usr/local/sbin/sshd -> sshd2

Oddly, the sshd2 executable was created yesterday (the day of the possible intrusion), and I don't think it really exists in any packages I have installed.  I say this because a "apt-file search sshd2" returns nothing.
I only started investigating because my attempts to ssh in remotely today failed, so I'm pretty worried about what may have gone on here.  Can anyone shed some light on the sshd2 situation?  Any other advice?  I've run rkhunter, but every item it complains about has many reports of false positives, so I'm unsure if it's helpful or not.

---

### Post by ktrnka on 2009-04-13
ssh should not be a symlink to anywhere else. Sounds like your system was infiltrated and rootkited. Did you remember to take care of the ssh key vulnerability last year? [http://www.debian.org/security/2008/dsa-1576]("http://www.debian.org/security/2008/dsa-1576")

What release are you using? Only surefire way is to do a clean install or restore your system from known good backups.

---

### Post by antikristian on 2009-04-13
Most likely they installed a rootkit on your machine.

There are programs to find and remove rootkits, but you can never be sure since a rootkit replaces commands that you would use to list files, delete files list processes and so on.

My advice: disconnect the computer from the network now!
Reinstall Linux

I try to harden ssh a bit on my computers by changing the default port, only allow protocol 2 and adding "AllowGroups ssh" in /etc/ssh/sshd_config to only allow people belonging to a certain group to have ssh access. (remember to add a user to that group)

Also, do not use simple passwords, disallow root access in ssh, and preferably, use keys with passfrases instead of passwords.

---

### Post by brian_p on 2009-04-14
> **teaguecl said:**
> 

Yesterday my auth.log.0 shows that someone logged into my Ubuntu machine remotely over ssh using a user account which I no longer use, and haven't logged in with in months.  Not long after that, they were somehow able to su to root.

The portion of the log showing this would be useful. Was the account open to anyone besides yourself? What was the password for it? (The account has been deleted; revealing it is of no consequence).

> $ which sshd
/usr/local/sbin/sshd
$ ls -al /usr/local/sbin/sshd
lrwxrwxrwx 1 root root 5 2009-04-12 08:33 /usr/local/sbin/sshd -> sshd2

Where does the package system think it put the files?

```
dpkg -L openssh-server
```

> I've run rkhunter, but every item it complains about has many reports of false positives, so I'm unsure if it's helpful or not.

I'd be very sure about the 'helpfulness' of rkhunter.

---

### Post by teaguecl on 2009-04-14
Thanks everyone for the advice, I'll be re-installing it looks like.  No big deal I guess, since I can just back up my /home and that's where everything important is anyway.  A little more background for those who asked.  I am running Intrepid 64 bit, and have all the updates.  My computer is pretty much single user - just one account I use and nobody else touches the machine locally or remotely.  I did create a account for my girlfriend, and like an idiot the username/pass was easy to guess - katrina/katrina.  That's how they got in.  You can see in the log below they are just hammering my machine, attempting to log in with a list of first names.  At 07:09:16 they get in.  At 08:22:34 they change the accounts password.  They begin trying to su to root unsuccessfully for a while, but then at 08:22:50 they do it - I'm still a little confused as to how.  I have a default install, I didn't even think there was a root account.  Who knows what all they've done - I only noticed because my ssh setup got messed up.
I really appreciate the help, and even though it's bad news I'll know a bit more for the next time :)
Chris

Apr 12 07:09:05 teaguecl-desktop sshd[9740]: Failed password for invalid user karina from 82.165.235.170 port 48563 ssh2
Apr 12 07:09:06 teaguecl-desktop sshd[9742]: Invalid user katana from 82.165.235.170
Apr 12 07:09:06 teaguecl-desktop sshd[9742]: pam_unix(sshd:auth): check pass; user unknown
Apr 12 07:09:06 teaguecl-desktop sshd[9742]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=u15181460.onlinehome-server.com 
Apr 12 07:09:08 teaguecl-desktop sshd[9742]: Failed password for invalid user katana from 82.165.235.170 port 49544 ssh2
Apr 12 07:09:09 teaguecl-desktop sshd[9747]: Invalid user kathleen from 82.165.235.170
Apr 12 07:09:09 teaguecl-desktop sshd[9747]: pam_unix(sshd:auth): check pass; user unknown
Apr 12 07:09:09 teaguecl-desktop sshd[9747]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=u15181460.onlinehome-server.com 
Apr 12 07:09:11 teaguecl-desktop sshd[9747]: Failed password for invalid user kathleen from 82.165.235.170 port 50960 ssh2
Apr 12 07:09:12 teaguecl-desktop sshd[9749]: Invalid user kathrine from 82.165.235.170
Apr 12 07:09:12 teaguecl-desktop sshd[9749]: pam_unix(sshd:auth): check pass; user unknown
Apr 12 07:09:12 teaguecl-desktop sshd[9749]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=u15181460.onlinehome-server.com 
Apr 12 07:09:15 teaguecl-desktop sshd[9749]: Failed password for invalid user kathrine from 82.165.235.170 port 52165 ssh2
Apr 12 07:09:16 teaguecl-desktop sshd[9752]: Accepted password for katrina from 82.165.235.170 port 53444 ssh2
Apr 12 07:09:16 teaguecl-desktop sshd[9752]: pam_unix(sshd:session): session opened for user katrina by (uid=0)
Apr 12 07:09:23 teaguecl-desktop sshd[9805]: Invalid user kernel from 82.165.235.170
...
Apr 12 08:22:34 teaguecl-desktop passwd[14043]: pam_unix(passwd:chauthtok): password changed for katrina
...
Apr 12 08:22:46 teaguecl-desktop su[14062]: FAILED su for root by katrina
Apr 12 08:22:46 teaguecl-desktop su[14062]: - pts/7 katrina:root
Apr 12 08:22:48 teaguecl-desktop sshd[14066]: Failed password for root from 82.165.235.170 port 49747 ssh2
Apr 12 08:22:49 teaguecl-desktop sshd[14070]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=u15181460.onlinehome-server.com  user=root
Apr 12 08:22:50 teaguecl-desktop sudo:  katrina : TTY=pts/7 ; PWD=/home/katrina ; USER=root ; COMMAND=/bin/su
Apr 12 08:22:50 teaguecl-desktop su[14069]: Successful su for root by root
Apr 12 08:22:50 teaguecl-desktop su[14069]: + pts/7 root:root
Apr 12 08:22:50 teaguecl-desktop su[14069]: pam_unix(su:session): session opened for user root by katrina(uid=0)
Apr 12 08:22:51 teaguecl-desktop sshd[14070]: Failed password for root from 82.165.235.170 port 50725 ssh2

---

### Post by antikristian on 2009-04-14
you could log into the katrina account by running 
```
sudo su -
su katrina
```

and then you might see what they have done by running the history command

---

### Post by brian_p on 2009-04-14
> **teaguecl said:**
> 

Thanks everyone for the advice, I'll be re-installing it looks like.
  
Apr 12 07:09:16 teaguecl-desktop sshd[9752]: Accepted password for katrina from 82.165.235.170 port 53444 ssh2
Apr 12 07:09:16 teaguecl-desktop sshd[9752]: pam_unix(sshd:session): session opened for user katrina by (uid=0)


Looks like it. You haven't much choice unless you want to track down what happened after access was obtained.

Anyway, well-spotted and diagnosed. Just think how much safer the account would have been if only the password had been katrinaisthemostbeautifulgirlintheworld.

---

### Post by teaguecl on 2009-04-14
On a very related note... is there a way to ban an IP address automatically for attempting to login unsuccessfully many times?  They were doing it on different usernames, so it was never more than 1 unsuccessful attempt per account - but it was thousands of unsuccessful attempts in a row from the same IP.

---

### Post by brian_p on 2009-04-14
> **teaguecl said:**
> On a very related note... is there a way to ban an IP address automatically for attempting to login unsuccessfully many times?  They were doing it on different usernames, so it was never more than 1 unsuccessful attempt per account - but it was thousands of unsuccessful attempts in a row from the same IP.

```
sudo apt-get denyhosts
```

removes the annoyance but, as you are well aware, it was the weak password which allowed access, so don't let it give you a false sense of security.  With a strong password they could try every second of the day and not get in.

---

### Post by ktrnka on 2009-04-14
Was your girlfriend's account in the sudoers group? To prevent these sshbot attacks you can use fail2ban or sshguard. Another option that I have done is a geolocation ban. It drops packets for anyone attempting to ssh to my server outside of the US. I very rarely see any failed login attempts and sshguard takes care of the rest. Good Luck!

---

### Post by Peasantoid on 2009-04-14
Looks like you've been rk'ed.
Once that happens, there's very little you can do about it other than reinstall your system, preferably from a clean backup (you keep backups, right?).

---

