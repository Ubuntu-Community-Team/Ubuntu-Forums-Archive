---
title: "Someone got unauthorized access..."
date: 2009-08-11
forum: Security
---

### Post by mjwalfredo on 2009-08-11
Oh no...  I never took security seriously until now.  Mostly because I started using Linux while living out in the country where I was rarely connected to the Internet.  Now, I have cable and I have experienced the dangers being on the Internet 24/7 first hand.

So, I did something really stupid.  I installed DB2 on my machine and set the database user db2inst1's password the same as the user id.  I found out when I tried to start the database after rebooting and the weak password wouldn't work anymore.

It looks like someone from a .ro domain logged in through SSH as db2inst1 last friday night.  The good news is that my database didn't have anything sensitive on it and the db2inst1 doesn't have any other privleges that it doesn't need. (No sudo authority)

I have changed all my weak passwords for the DB2 related users.
What else should I do to make sure the hacker didn't do anything malicious?

Also, I am trying to turn off SSH access for all users but my main user id but I can't figure that out.  The user and groups settings reports that none of my users are in the ssh group (??).:confused:

Thanks for any help.

---

### Post by mjwalfredo on 2009-08-11
Well, I am a little bit safer now.  I updated /etc/ssh/sshd_config to allow only users belonging to the ssh group.  I also turned off root login.  I go the info from this thread [http://ubuntuforums.org/showthread.php?t=292057]("http://ubuntuforums.org/showthread.php?t=292057")

I've heard that Ubuntu does not allow root login by default anyway. Is that true?  I don't remember ever setting a password for the root account but it looks like I have a root account when I go into the users and groups applet.

---

### Post by cariboo on 2009-08-11
The root account is disabled by default, you will still see root listed, but there is no password. another way to check is to open a terminal and type:

```
sudo cat /etc/shadow
```

you will get a listing that looks something like this:

```
root:!:14364:0:99999:7:::
daemon:*:14364:0:99999:7:::
bin:*:14364:0:99999:7:::
sys:*:14364:0:99999:7:::
sync:*:14364:0:99999:7:::
games:*:14364:0:99999:7:::
man:*:14364:0:99999:7:::
lp:*:14364:0:99999:7:::
```

As you can see root has an ! instead of an encryted password.

---

### Post by mjwalfredo on 2009-08-11
Oh Cool!

Is there any practical difference between ! and * in the shadow file?

---

### Post by cariboo on 2009-08-11
The * means that nobody can login with that account even if there is a password for it, and ! means that the account is disabled.

---

### Post by bear24rw on 2009-08-11
also install fail2ban, it watches for authentification attempts and blacklists an IP if it fails to login to many times. i've been using it very successfully to stop brute force logins

```
sudo aptitude install fail2ban
```

and you should be good to go, it runs as a daemon in the background

```
sudo jail2ban-client status ssh
```

i think that is the command to see the current blacklist dont quote me on that though

---

### Post by mjwalfredo on 2009-08-11
> **bear24rw said:**
> also install fail2ban, it watches for authentification attempts and blacklists an IP if it fails to login to many times. i've been using it very successfully to stop brute force logins

```
sudo aptitude install fail2ban
```

and you should be good to go, it runs as a daemon in the background

```
sudo jail2ban-client status ssh
```

i think that is the command to see the current blacklist dont quote me on that though

Did you mean fail2ban-client instead of jail2ban-client in the second command?  And thanks for the tip, that will be getting installed promptly.

And ughhh, spam in my post!:mad:

---

### Post by bear24rw on 2009-08-11
hah yeah its fail2ban-client i beleive idk why i keep thinking its called jail.. also google fail2ban tutorial or something there are some great reads that show you how you can easily change the rules for banning

---

### Post by bodhi.zazen on 2009-08-12
I suggest you read [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

Then learn how to use your firewall ;)

---

### Post by mjwalfredo on 2009-08-12
Thanks for the link to the security thread.  I may be confused but I just don't see how a firewall would help at all.  I mean, if my machine is not listening for connections, it's just going to refuse any connection attempts anyway, right?

If I need my machine to listen for connections, on port 22 for example, I can't block that with a firewall either becuase then nobody can connect from the WAN...

---

### Post by bodhi.zazen on 2009-08-13
Look on the iptables tutorial I gave you. iptables can log as well as dynamically block ports.

So you may block port 22 after say 8 attempts (or less).

Learning to use iptables is a bit of an uphill battle, but in the end itis easier then installing and learning numerous "replacement" apps such as a graphical configuration tool or something like denyhosts or fail2ban.

---

### Post by bear24rw on 2009-08-13
> **bodhi.zazen said:**
> 
So you may block port 22 after say 8 attempts (or less).

how would you do that with just iptable rules?

fail2ban uses iptables to block intruders

---

### Post by bodhi.zazen on 2009-08-14
I posted that here : [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

I know it is a long page, go to this section

[http://bodhizazen.net/Tutorials/iptables/#Additional_Tips](http://bodhizazen.net/Tutorials/iptables/#Additional_Tips)

ans scroll down just a bit.

---

### Post by Drone022 on 2009-08-14
Also, change SSH so it uses a non-standard port, this will greatly reduce the number of unauthorized access attempts.

---

