---
title: "Default file permissions secure enough?"
date: 2010-08-20
forum: Security
---

### Post by dogdo on 2010-08-20
Im not that literate with linux but are the default file permissions on a new ubuntu 10.04 install secure enough for the desktop? How do the file permissions compare to a new windows 7 install?

---

### Post by sharathcshekhar on 2010-08-20
Depends on how you use your system. Whether multiple users use the system, do you use it to log in from a remote network, or planning to host a server?
For normal, single user usages, the default permissions are more than secure.
Default permission are decided by the value of umask, which is 022. Which means the permission is 644 for all files, and 755 for directories which translates to Read/Write to the owner of the file and Read permissions for all user belonging to your group and to all other users as well.

--
Sharath C

---

### Post by bodhi.zazen on 2010-08-20
In general Linux permissions are sufficient for the vast majority of both desktops and servers.

If for some reason you want more then the defaults you can use acl, selinux, or apparmor.

If for some reason you are a high profile target (beyond paranoia, ie you are a financial institution for example), I would add selinux or apparmor.

---

### Post by wacky_sung on 2010-08-20
> **bodhi.zazen said:**
> In general Linux permissions are sufficient for the vast majority of both desktops and servers.

If for some reason you want more then the defaults you can use acl, selinux, or apparmor.

If for some reason you are a high profile target (beyond paranoia, ie you are a financial institution for example), I would add selinux or apparmor.

I do not really understand by sentences below.May be anybody can explained it in details or due to my lowly IQ.:lolflag:

```
Default permission are decided by the value of umask, which is 022. Which means the permission is 644 for all files, and 755 for directories which translates to Read/Write to the owner of the file and Read permissions for all user belonging to your group and to all other users as well.
```

As i have switch from Window to Ubuntu lately and i used to download movie from IRC.Usually what those files contain are bind to botnet in which anybody download the file and extracted it out of the zip.The botnet script will auto seize admin right over your folder and then they start to steal all your data turning your system into a zombie.

Does it gonna affected Ubuntu system as well?

---

### Post by CharlesA on 2010-08-20
Don't download pirated stuff then.

---

### Post by wacky_sung on 2010-08-20
> **CharlesA said:**
> Don't download pirated stuff then.

Actually i do not support Pirated stuff but i love to learn about security.I did it just to have a better understanding how those botnet are widely used in IRC.

---

### Post by Bachstelze on 2010-08-20
> **wacky_sung said:**
> Actually i do not support Pirated stuff but i love to learn about security.

People are amazing.  "I download movies from IRC, but actually I do not support pirated stuff."  Awesome. =D>

"I love to learn about security", especially the kind of security that gives me free movies, right?

---

### Post by CharlesA on 2010-08-20
Ah ok. If it works on Windows, it probably won't work on Linux.

---

### Post by wacky_sung on 2010-08-20
> **Bachstelze said:**
> People are amazing.  "I download movies from IRC, but actually I do not support pirated stuff."  Awesome. =D>

Don't be Amazed by what you see because i am trying to find ways to disassemble the zip file and find the source code which lead to botnet server.

---

### Post by OpSecShellshock on 2010-08-20
> **wacky_sung said:**
> I do not really understand by sentences below.May be anybody can explained it in details or due to my lowly IQ.:lolflag:

```
Default permission are decided by the value of umask, which is 022. Which means the permission is 644 for all files, and 755 for directories which translates to Read/Write to the owner of the file and Read permissions for all user belonging to your group and to all other users as well.
```As i have switch from Window to Ubuntu lately and i used to download movie from IRC.Usually what those files contain are bind to botnet in which anybody download the file and extracted it out of the zip.The botnet script will auto seize admin right over your folder and then they start to steal all your data turning your system into a zombie.

Does it gonna affected Ubuntu system as well?

I've never heard of (nor could I conceive of, but then I usually don't try) a cross-platform botnet. As such it would have to be written for the OS it's meant to run on. Also, it would have to work. What you've described above is a trojan, and as far as I know that form would be the most effective way of getting malicious code onto a Linux desktop (as it is with any other, since it's basically physical access by proxy).

---

### Post by wacky_sung on 2010-08-20
> **OpSecShellshock said:**
> I've never heard of (nor could I conceive of, but then I usually don't try) a cross-platform botnet. As such it would have to be written for the OS it's meant to run on. Also, it would have to work. What you've described above is a trojan, and as far as I know that form would be the most effective way of getting malicious code onto a Linux desktop (as it is with any other, since it's basically physical access by proxy).

Probably i will test it myself to verify it.

What do you meant by [COLOR="Red"]What you've described above is a trojan, and as far as I know that form would be the most effective way of getting malicious code onto a Linux desktop (as it is with any other, since it's basically physical access by proxy)[/COLOR]. Thank

---

### Post by OpSecShellshock on 2010-08-20
> **wacky_sung said:**
> Don't be Amazed by what you see because i am trying to find ways to disassemble the zip file and find the source code which lead to botnet server.

Side note: trying to track down the command infrastructure of botnets is a waste of time. There is rarely a single server, since by nature its workload is distributed among already-compromised machines. Even if it's hard-coded (and in the new ones it's not) you won't find much useful information. That's if you can undo the packing and encryption. They also employ the most robust disaster recovery and business continuity infrastructure in the world. Efforts to disconnect the best-known ones from their upstream providers have lately resulted in maybe half-day interruptions of service.

---

### Post by OpSecShellshock on 2010-08-20
> **wacky_sung said:**
> Probably i will test it myself to verify it.

What do you meant by [COLOR=Red]What you've described above is a trojan, and as far as I know that form would be the most effective way of getting malicious code onto a Linux desktop (as it is with any other, since it's basically physical access by proxy)[/COLOR]. Thank

What I mean by that is that, since trojans are installed by the users themselves, it's essentially the same thing as having physical access--all you're doing is getting existing local users to voluntarily do what you would be doing if you were sitting at the keyboard.

---

### Post by wacky_sung on 2010-08-20
> **OpSecShellshock said:**
> What I mean by that is that, since trojans are installed by the users themselves, it's essentially the same thing as having physical access--all you're doing is getting existing local users to voluntarily do what you would be doing if you were sitting at the keyboard.

May be let me rephrase it.The botnet zip will auto execute the script while the user just extract out the file without knowing that the file inside the zip is bind to a botnet.Then their folders / system get compromised.The users did not do it voluntarily but without realize it.

Example, a movie file zombie.avi inside the zip and the user just extract out the zombie.avi to watch it.

---

### Post by bodhi.zazen on 2010-08-20
If you wish to know more about permissions, see :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

If you wish to learn more about Linux security, start with the stickies at the top of the security section.

Linux has vulnerabilities, but they are not the same as Windows.

---

### Post by uRock on 2010-08-20
> **wacky_sung said:**
> May be let me rephrase it.The botnet zip will auto execute the script while the user just extract out the file without knowing that the file inside the zip is bind to a botnet.Then their folders / system get compromised.The users did not do it voluntarily but without realize it.

Example, a movie file zombie.avi inside the zip and the user just extract out the zombie.avi to watch it.
If someone is using botnet, then he/she is voluntarily compromising their system. If you want movies, music, or software, then rent, buy or borrow them. All of this talk of downloading illegal stuff is wrong whether you are doing it for learning or pleasure or learning pleasure;), then you are still breaking the law. Stealing a candy bar just to see how a store's security works is still stealing a candy bar, even if you didn't mean to eat it.

Why did Dogdo's thread get hijacked?

---

### Post by wacky_sung on 2010-08-20
> **uRock said:**
> If someone is using botnet, then he/she is voluntarily compromising their system. If you want movies, music, or software, then rent, buy or borrow them. All of this talk of downloading illegal stuff is wrong whether you are doing it for learning or pleasure or learning pleasure;), then you are still breaking the law. Stealing a candy bar just to see how a store's security works is still stealing a candy bar, even if you didn't mean to eat it.

Why did Dogdo's thread get hijacked?

I think you got the whole issue thinking of downloading illegal stuffs.I am sticking to the same point of file permission of  a folder and not even went of tropic.What i am trying to stress is that how does file permission work in Linux.It is better to be wise than being ignorance which lead to your system getting compromised.

Thank Bodhi for the link.

---

### Post by cariboo on 2010-08-20
Have a look [here]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html") for a linux file permission explanation.

You may also want to bookmark [The Linux Documentation Project]("http://tldp.org/"), there is a lot of documentation on Linux basics.

---

### Post by wacky_sung on 2010-08-21
> **cariboo907 said:**
> Have a look [here]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html") for a linux file permission explanation.

You may also want to bookmark [The Linux Documentation Project]("http://tldp.org/"), there is a lot of documentation on Linux basics.

Thank you.I will bookmark it.):P

---

### Post by Morbius1 on 2010-08-21
I wonder what happened to dogdo. Anybody remember him/her? He/She was the one that started his thread. :p

---

