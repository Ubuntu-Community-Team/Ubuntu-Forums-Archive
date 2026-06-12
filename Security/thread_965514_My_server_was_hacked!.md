---
title: "My server was hacked!?"
date: 2008-10-31
forum: Security
---

### Post by linuxisevolution on 2008-10-31
I have a local ssh server setup. I never changed any configs or anything, but today, I go to login, and I get:

> ssh guest@192.168.1.125
guest@192.168.1.125's password: 
Permission denied, please try again.
guest@192.168.1.125's password: 
Permission denied, please try again.
guest@192.168.1.125's password: 
Permission denied (publickey,password).


I am able to login via root ( root@192.168.1.125 )

So, I checked the last logged in users and the ips that they came from. I am the only person that has access to this server, but, as you see, there are several ip addresses in there that are not on my static router. Before I delete all my personal files immediately and destroy the install, was this server really hacked?


I am winrid-desktop.

> debian:~# last
root     pts/0        winrid-desktop.h Wed Jan  5 00:28   still logged in   
reboot   system boot  2.6.18-6-686     Wed Jan  5 00:17 - 00:29  (00:12)    
guest    pts/2        ac9e1a6c.ipt.aol Tue Jan  4 17:25 - 17:25  (00:00)    
guest    pts/1        ac9e1a6c.ipt.aol Mon Jan  3 15:51 - 17:57  (02:06)    
guest    pts/1        212.1.97.86      Mon Jan  3 15:32 - 15:48  (00:16)    
guest    pts/1        winrid-desktop.h Mon Jan  3 05:22 - 05:27  (00:04)    
guest    pts/1        winrid-desktop.h Mon Jan  3 05:20 - 05:22  (00:02)    
guest    pts/1        winrid-desktop.h Mon Jan  3 05:12 - 05:19  (00:07)    
guest    pts/1        189.27.236.123.a Sun Jan  2 15:00 - 15:03  (00:03)    
guest    pts/0        winrid-desktop.h Sat Jan  1 21:44 - 22:06  (00:21)    
guest    pts/0        winrid-desktop.h Sat Jan  1 21:29 - 21:30  (00:00)    
reboot   system boot  2.6.18-6-686     Sat Jan  1 19:02 - 00:29 (3+05:27)   
guest    pts/0        winrid-desktop.h Wed Jan 19 17:05 - 17:29  (00:24)    
guest    pts/0        mail.zlhr.org.zw Tue Jan 18 22:56 - 22:57  (00:00)    
guest    pts/0        221.232.148.68   Tue Jan 18 11:22 - 11:22  (00:00)    
guest    pts/0        winrid-desktop.h Mon Jan 17 20:58 - 20:59  (00:00)    
guest    pts/0        winrid-desktop.h Mon Jan 17 20:46 - 20:47  (00:00)    
guest    pts/0        winrid-desktop.h Mon Jan 17 20:41 - 20:46  (00:05)    
guest    pts/0        winrid-desktop.h Mon Jan 17 20:24 - 20:40  (00:15)    
guest    pts/0        winrid-desktop.h Mon Jan 17 20:14 - 20:19  (00:05)    
guest    pts/0        winrid-desktop.h Mon Jan 17 19:21 - 19:22  (00:01)    
reboot   system boot  2.6.18-6-686     Mon Jan 17 19:20 - 00:29 (-12+-18:-50
guest    pts/0        winrid-desktop.h Mon Jan 17 19:17 - crash  (00:02)    
guest    pts/0        winrid-desktop.h Mon Jan 17 19:12 - 19:17  (00:05)    
guest    pts/0        winrid-desktop.h Mon Jan 17 18:12 - 18:32  (00:19)    
guest    pts/0        winrid-desktop.h Mon Jan 17 17:57 - 18:12  (00:14)    
guest    pts/0        winrid-desktop.h Mon Jan 17 14:53 - 14:54  (00:00)    
guest    pts/0        winrid-desktop.h Sun Jan 16 19:09 - 19:15  (00:06)    
guest    pts/0        winrid-desktop.h Sun Jan 16 14:30 - 14:30  (00:00)    
guest    pts/1        winrid-desktop.h Sat Jan 15 21:46 - 21:54  (00:07)    
guest    pts/0        winrid-desktop.h Sat Jan 15 21:39 - 21:54  (00:15)    
guest    pts/0        winrid-desktop.h Sat Jan 15 21:33 - 21:35  (00:02)    
guest    pts/0        winrid-desktop.h Sat Jan 15 21:24 - 21:24  (00:00)    
guest    pts/0        :0.0             Sat Jan 15 21:16 - 21:16  (00:00)    
guest    pts/3        winrid-desktop.h Sat Jan 15 21:06 - 21:14  (00:07)    
root     pts/0        localhost        Sat Jan 15 21:03 - 21:15  (00:11)    
root     pts/2        :0.0             Sat Jan 15 20:29 - 21:15  (00:45)    
guest    pts/1        :0.0             Sat Jan 15 20:28 - 20:29  (00:01)    
guest    pts/0        :0.0             Sat Jan 15 20:27 - 20:36  (00:08)    
guest    :0                            Sat Jan 15 20:25 - crash (1+22:55)   
reboot   system boot  2.6.18-6-686     Sat Jan  1 19:01 - 00:29 (3+05:28)   
guest    tty5                          Tue Jan  4 09:17 - crash (-2+-14:-16)
guest    tty4                          Tue Jan  4 09:16 - crash (-2+-14:-15)
reboot   system boot  2.6.18-6-686     Sat Jan  1 19:03 - 00:29 (3+05:26)   
root     pts/2        :0.0             Fri Jan 28 17:14 - 17:49  (00:34)    
guest    pts/0        :0.0             Fri Jan 28 17:11 - 17:14  (00:02)    
root     pts/1        :0.0             Fri Jan 28 17:03 - 17:11  (00:07)    
guest    :0                            Fri Jan 28 16:59 - 17:53  (00:53)    
reboot   system boot  2.6.18-6-686     Fri Jan 28 16:59 - 17:55  (00:56)    
root     pts/1        :0.0             Sat Jan 15 23:21 - 23:29  (00:07)    
guest    :0                            Sat Jan 15 23:01 - 15:38 (12+16:37)  
reboot   system boot  2.6.18-6-686     Sat Jan 15 23:00 - 15:39 (12+16:38)  
root     pts/1        :0.0             Sat Jan 15 19:48 - crash  (03:12)    
root     pts/2        :0.0             Fri Jan 14 17:36 - 18:15  (00:39)    
root     pts/3        :0.0             Fri Jan 14 17:26 - 19:10  (01:44)    
root     pts/2        :0.0             Fri Jan 14 17:19 - 17:26  (00:06)    
root     pts/3        :0.0             Mon Jan 10 11:07 - 13:39  (02:31)    
guest    :0                            Mon Jan 10 10:51 - crash (5+12:08)   
reboot   system boot  2.6.18-6-686     Mon Jan 10 10:51 - 15:39 (18+04:48)  
reboot   system boot  2.6.18-6-686     Mon Jan  3 13:50 - 15:28  (01:38)    
root     pts/1        :0.0             Sat Jan  1 20:55 - 21:10  (00:15)    
guest    pts/0        :0.0             Sat Jan  1 20:52 - 20:54  (00:01)    
guest    :0                            Sat Jan  1 20:51 - 21:12  (00:20)    
reboot   system boot  2.6.18-6-686     Sat Jan  1 20:51 - 21:13  (00:22)    

wtmp begins Sat Jan  1 20:51:01 2000


Thanks!

---

### Post by Kinstonian on 2008-10-31
Are there any suspicious processes or network connections?  You have the time the suspected incident took place, so use the find command to search for files modified at around that time.

In nearly every attack the attacker will place or modify files on your computer so that should turn up some suspicious results if you really were hacked, unless a rootkit is involved.  So use chkrootkit or similar to look for signs you've been infected with a rootkit.

If you really were hacked, don't forget to determine how it happened before you reformat (if that's what you chose to do).  You don't want to reformat and get hacked again the next day.

---

### Post by cariboo on 2008-11-01
Who is the guest that is looging in all the time? Or did you just obfuscate the real user name. I get quite a few ssh request using guest as a user name that get denied by denyhosts.

```
 cat users-invalid | grep guest
guest:24:Fri Oct 24 15:04:22 2008
```

As you can see from the above output of /var/lib/denyhosts/users-invalid so far 24 tries with the name guest have been denied.

BTW fix your clock it's October 2008, not January 2000 :)

Jim

---

### Post by brian_p on 2008-11-01
> **linuxisevolution said:**
> 

guest pts/2 ac9e1a6c.ipt.aol Tue Jan 4 17:25 - 17:25 (00:00)
guest pts/1 ac9e1a6c.ipt.aol Mon Jan 3 15:51 - 17:57 (02:06)

guest pts/1 212.1.97.86 Mon Jan 3 15:32 - 15:48 (00:16)

guest pts/1 189.27.236.123.a Sun Jan 2 15:00 - 15:03 (00:03)

guest pts/0 mail.zlhr.org.zw Tue Jan 18 22:56 - 22:57 (00:00)

guest pts/0 221.232.148.68 Tue Jan 18 11:22 - 11:22 (00:00)

What is reported by sshd in /var/log/auth.log at these times?

---

### Post by amac777 on 2008-11-01
Was the password on the guest account something in the dictionary? Was it "guest"? :)

If the answer is yes (to either of those questions), I think there is a good chance that you were hacked because some script kiddie guessed your easy password.

I have people continually trying to hack into my ssh sever and one of the most common usernames they try is guest.

EDIT: maybe use root to reset the password on the "guest" account to something you know again. Then login as guest and use the command "history" to see if you can see what recent commands have been run on that account. If history doesn't show anything interesting, this proves nothing because it's easy to clear. But if it shows some activity that wasn't you, that's pretty good proof you were hacked.

---

### Post by FakeOutdoorsman on 2008-11-02
This is a good read:
[Dead Linux Machines Do Tell Tales]("http://www.giac.org/practical/GCFA/James_Fung_GCFA.pdf") [link to PDF]

Once you wipe and reinstall:
[Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/")

---

### Post by linuxisevolution on 2008-11-03
haha. I never noticed. My server was made in 2000.

---

### Post by linuxisevolution on 2008-11-03
This is what it get:

debian:~# /var/log/auth.log
-bash: /var/log/auth.log: Permission denied

---

### Post by linuxisevolution on 2008-11-03
I would like to let everyone know that I fixed it. I'll leave this post as unsolved so users can still ask questions. After a month or so I'll mark it as solved. I fixed it by changing the password with root ( thanks amac777 ) and changed it to a bunch of random numbers. Now I just have to find out what this guy did....

---

### Post by HermanAB on 2008-11-04
There are SSH and FTP brute forcers out there that are always looking for Linux machines to set up spam sending shops.

This is why you have to use a proper password with more than 8 characters, since common brute force dictionaries go up to 8 characters.

I fix one or two compromised Linux servers per year and it is usually due to some dumkopf who thought that a 4 character password was 'cool'.

---

### Post by brian_p on 2008-11-04
> **linuxisevolution said:**
> This is what it get:

debian:~# /var/log/auth.log
-bash: /var/log/auth.log: Permission denied

You'll have more success with

```
less /var/log/auth.log
```

```
less /var/log/auth.log.0
```

```
less /var/log/auth.log.1.gz
```

etc.

---

### Post by brian_p on 2008-11-04
> **linuxisevolution said:**
> 

I fixed it by changing the password with root . . . . 

What was the original password?

---

### Post by brian_p on 2008-11-04
> **linuxisevolution said:**
> 

Now I just have to find out what this guy did....

You don't yet know whether anyone broke in but, if you are intending to go with assuming they did, changing the password is insufficient. You need to do a complete reinstall.

---

### Post by Marvindreyer on 2008-11-04
I just went through these links I must say these links are awesome! thanks for sharing.

---

### Post by robgr85 on 2008-11-04
> **linuxisevolution said:**
> I would like to let everyone know that I fixed it. I'll leave this post as unsolved so users can still ask questions. After a month or so I'll mark it as solved. I fixed it by changing the password with root ( thanks amac777 ) and changed it to a bunch of random numbers. Now I just have to find out what this guy did....

If there was really some serious attack on Your server, You should consider using **chrootkit** form some alien system (for example some fresh livecd linux distro). Changing the acutal password can be not enough if there is rootkit installed at Your server. If there is one, reinstall and cleverly configure Your server from scratch.
 
For the future, I would suggest learning the usage of TCT (**the coroner's toolkit**) package.

Hope that helps to someone.

Cheers,
Robert

---

### Post by TyTiger on 2008-11-04
> **HermanAB said:**
> There are SSH and FTP brute forcers out there that are always looking for Linux machines to set up spam sending shops.

This is why you have to use a proper password with more than 8 characters, since common brute force dictionaries go up to 8 characters.

I fix one or two compromised Linux servers per year and it is usually due to some dumkopf who thought that a 4 character password was 'cool'.

Another tip is not to forward your ssh port to yoru server, or if you abalutely must, make the externel port something random like 7289 for example. this helps a bit.

---

