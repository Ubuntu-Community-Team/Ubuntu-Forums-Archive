---
title: "Risks of Internet-open SSH server"
date: 2008-10-09
forum: Security
---

### Post by ivze on 2008-10-09
Some days ago I got the ability to connect to my home computer from the workplace (got external IP), so I decided to set up an SSH server.

The first attempt to break in came in one day, the attacks repeat regularry (about one attack in two days). The attacks were mere password-guessing.

The following information might be just curious to know, it won't be anything new for the specialist. I have got it via experiment (and I am not a specialist ^^).

All the attacking computers were running linux. (thanks to "nmap -O attacker-address"). One of them was, probably, OpenSUSE. 

In order to learn the passwords, being tested on my computer (SSH server only writes usernames in auth.log system log file), I have created a modified version of openSSH server. The modification was adding some lines in source code, that dumped every connecting person usernames and passwords in a log file. When an attack starts, I shut down the original SSH server and start a patched one.

The username\tpassword pairs sent to me in one of such attacks are attached to my post. 

Read this log. Hope, your password can't be guessed this way:).

---

### Post by Dr Small on 2008-10-09
I run John the Ripper on my passwords first, so if that bruteforce can't crack it, then I doubt the scriptkiddie bots will never be able to.

---

### Post by jerome1232 on 2008-10-09
Even though you are probably the only user of your system I don't know if I would keep that patch on ssh, incorrect passwords are getting logged to a plain text file that any user of your system can see. So if you misstype your password by one character once, it's now there for all users of your system to see.

---

### Post by hyper_ch on 2008-10-10
install denyhosts or fail2ban

---

### Post by dperfors on 2008-10-10
Looks like they are just using a dictionary. From what I have seen they don't have a lot of complexity in the passwords at all. (only lower case and some numbers at the end.) As long as you use al kind of characters (or even better, public/privat key combination only) you should be safe.

---

### Post by mregister on 2008-10-10
where are the failed passwords logged? I don't see that in auth.log.

---

### Post by jerome1232 on 2008-10-10
> **mregister said:**
> where are the failed passwords logged? I don't see that in auth.log.

You have to patch and recompile ssh to do that, usually used for honeypots to log what usernames/passwords bots try and use.

---

### Post by Biochem on 2008-10-10
I find fascinating that nobody tried with "root" as a user.

---

### Post by cariboo on 2008-10-11
I usually get a dozen or so attempts using root every week,

here is a listing from /var/lib/denyhosts/users-invalid:

```
aaron:12:Tue Oct  7 19:18:55 2008
abuse:2:Thu Aug 28 11:06:37 2008
accept:2:Mon Sep  1 16:16:56 2008
adam:2:Thu Aug 28 11:06:37 2008
admin:56:Fri Oct 10 23:09:07 2008
ale:4:Mon Sep 15 20:59:57 2008
alias:14:Tue Oct  7 19:22:26 2008
andrew:2:Tue Sep  2 18:58:27 2008
anton:2:Tue Sep 16 10:06:57 2008
apple:2:Tue Sep  2 18:57:57 2008
apple1:2:Tue Sep 16 10:06:57 2008
brian:2:Tue Sep  2 18:57:57 2008
bruce:6:Tue Sep 16 10:06:57 2008
cead:4:Mon Sep 15 21:00:27 2008
chris:6:Tue Sep 16 10:06:57 2008
condor:2:Wed Sep 10 16:28:08 2008
dilli:4:Mon Sep 15 20:59:57 2008
fluffy:6:Mon Sep 29 11:05:34 2008
ftpuser:12:Fri Sep 26 10:50:52 2008
gt05:8:Tue Oct  7 19:19:26 2008
guest:22:Wed Oct  8 19:57:26 2008
hacker:2:Mon Sep  1 16:16:56 2008
honza:2:Fri Sep 26 10:50:52 2008
leo:2:Mon Sep  1 16:16:56 2008
library:2:Mon Sep 22 21:19:22 2008
lpa:2:Tue Sep 23 18:07:24 2008
lpd:2:Tue Sep 23 18:06:54 2008
mailer:2:Thu Sep 18 00:07:28 2008
office:14:Tue Oct  7 19:22:56 2008
oracle:4:Fri Sep 26 10:51:22 2008
plant:2:Thu Sep  4 11:36:06 2008
postgres:2:Mon Sep  1 16:16:56 2008
recruit:16:Tue Oct  7 19:22:26 2008
redhat:8:Fri Aug 29 19:29:46 2008
rfmngr:2:Tue Oct  7 19:22:26 2008
sales:16:Tue Oct  7 19:22:26 2008
samba:8:Sun Sep 28 12:14:34 2008
simoni:6:Sun Oct  5 10:17:23 2008
sleeper:2:Sun Sep 21 12:07:55 2008
spam:2:Mon Sep 22 19:38:52 2008
staff:14:Sun Sep 28 12:14:34 2008
stud:16:Fri Oct 10 23:09:07 2008
test:32:Sun Sep 28 22:57:34 2008
tomcat:6:Sun Sep 28 12:14:34 2008
trash:16:Fri Oct 10 23:09:38 2008
user:4:Fri Sep 26 10:50:52 2008
webadmin:4:Mon Sep 22 19:38:22 2008
webmaster:4:Mon Sep 22 21:18:52 2008
x:2:Fri Sep 26 10:50:52 2008
zeppelin:2:Mon Sep  1 16:16:56 2008
```

Of course I don't have any of the users listed on my system.

Jim

---

### Post by Dave_Connor on 2008-10-11
You can add to your sshd config of only allowing your account to access the system so alot of attackers just get booted right away from trying access your box.

---

### Post by cariboo on 2008-10-11
I have one of my computers setup so that you can only access it from certain computers on the network. It is fairly easy to setup. You configure hosts.deny to deny all connections, then configure hosts.allow to only allow certain ip addresses. You can use this type of setup if you are only accessing your computer from the same ip address all the time.

Jim

---

### Post by kevdog on 2008-10-11
Why someone would not want to take the time to learn about configuring iptables correctly, but settle for another solution such as hosts/allow/deny entirely is beyond me.  Your best defense is multiple strategies.

---

