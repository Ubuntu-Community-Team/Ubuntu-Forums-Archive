---
title: "Password hacking by bruteforce?"
date: 2010-01-04
forum: Security
---

### Post by shade5 on 2010-01-04
Hi,
I think it is very easy to hack passwords in Linux, but I did not try it yet. If you use sudo you get 3 attempts for the correct password. But if you get enough time it should be no problem to hack it by bruteforce. Imagine a script an attacker places on your machine which runs for a few hours or days. 

I think it is much more effective to delete the user out of the admin (or adm?) group so that user cannot be any danger anymore. You would have to login with root and readd the user then.

You now say: but if you login with root you got almost the same effect as with sudo. Of course it is the same. That is why I would use a system (not sure which yet) to create sub enviroments of your OS, which got the attribute that they can run without root, only got one account that can sudo and once sudo access is denied there is no other way to login as root. You just can repermit sudo access by the parent os layer. 

Maybe a virtual server could do that. Or maybe a kind of rootjail.

What do you think?

---

### Post by BkkBonanza on 2010-01-04
I think if you use an 8 letter/symbol password, that's,

26+26+10+12 = 74 

74^8 = 899194740203776 possible passwords.

At 3 seconds each (the default time between allowed tries) thats,

85539834 years of trying. Now even if you hit the right password at 50% through,

that's still 45 million years. So to paraphrase Clint Eastwood, "go ahead, brute force me". 

And hope I don't have a 9+ letter password.

No need for other weirdness. If someone is sitting at your machine then they have root access anyway. Encrypted home is some protection for that.

---

### Post by llawwehttam on 2010-01-04
haha my password is 27 characters long including letters, numbers and symbols so good luck hacking me. Also i have sendmail configured to email me when the 'root' gets mail in the log folder which I check quite often with ssh.

---

### Post by lisati on 2010-01-04
I can think of one or two ways of speeding up the process, but they only work under certain circumstances. Physical access to the machine is needed for one of them. Permission to access the machines is recommended.

---

### Post by shade5 on 2010-01-04
If you start multiple instances of sudo you might could increase the speed again by a high factor.

Also think of the next years. Computers will get much faster.

---

### Post by Sarmacid on 2010-01-04
The problem with having no sudo and enabling the root account is that you lose accountability. You no longer know who did what if that person is using the root acount.

---

### Post by BkkBonanza on 2010-01-04
The login process has a time delay set in PAM that prevents attempting login more than once in 3 seconds (default value as defined in /etc/pam.d/login). 

Being able to sudo assumes you have already logged in as a user.

Also I believe you can choose to alter the default pam authentication rules for sudo if you like, though I haven't tried that.

Starting lots of processes may help - you could get it in 45 years with a million processes running... :)

---

### Post by Shippou on 2010-01-04
I do think that if the 3-second time interval spent for wrong passwords is removed, this would somewhat be possible (though it would still take a very long time).

My best guess is that you use a dictionary-based brute force approach, not the naive brute force approach.

Better yet, use social engineering. Or a keylogger to make the task easier. Or maybe build a spoof login GUI.

Oh my. I think I am referring to Windows users/ (esp. the keylogger thing.)

---

### Post by dogdo on 2010-01-04
> **Shippou said:**
> I do think that if the 3-second time interval spent for wrong passwords is removed, this would somewhat be possible (though it would still take a very long time).

My best guess is that you use a dictionary-based brute force approach, not the naive brute force approach.

Better yet, use social engineering. Or a keylogger to make the task easier. Or maybe build a spoof login GUI.

Oh my. I think I am referring to Windows users/ (esp. the keylogger thing.)

Is Ubuntu vulnerable to keyloggers in the first place? Speaking of which ive heard that there are rootkits that can infect linux-could a rootkit allow for a privilege escalation attack?

---

### Post by BkkBonanza on 2010-01-04
Umm, what dictionary will help you with a random letter + symbol password? None.
And sure there's other ways to get passwords. At gun point is one. But that's not what we're talking about here.

---

### Post by Shippou on 2010-01-04
> **BkkBonaza said:**
> Umm, what dictionary will help you with a random letter + symbol password? None.


At least most users would be hacked. Of course, there are exceptional cases. But then, they are exceptions, not rules.

> **BkkBonaza said:**
> 
And sure there's other ways to get passwords. At gun point is one. But that's not what we're talking about here.

Nice statement. :p

---

### Post by BkkBonanza on 2010-01-04
Well, there is no denying that if you choose a weak password then you can get hacked.
And such users have only themselves to blame not sudo, linux or pam.

Rootkits are useful for maintaining root access once achieved but they don't help you get root access: you need to already be root to install a rootkit.

By default the sudo command fails after 3 tries but can be run again. The default pam modules don't enhance that much. If you want more security on sudo you could add other pam modules to the /etc/pam.d/sudo config file. Using pam_tally would allow restricting sudo so that it doesn't even start if more than some number of attempts is made. It has more options such as a timeout period when X tries made, or even permanent bans. It would be only a few moments change to add a "10 fails = 15 minute ban" to sudo. This would make more sense then other roundabout and questionable ad-hoc security ideas.

---

### Post by __p1n__ on 2010-01-04
> **BkkBonaza said:**
> The login process has a time delay set in PAM that prevents attempting login more than once in 3 seconds (default value as defined in /etc/pam.d/login). 

Being able to sudo assumes you have already logged in as a user.

Also I believe you can choose to alter the default pam authentication rules for sudo if you like, though I haven't tried that.

Starting lots of processes may help - you could get it in 45 years with a million processes running... :)

You don't need to attempt to login or sudo.  A tool like john-the-ripper will generate and compare hashes against /etc/passwd using either dictionary or bruteforce mode.  PAM doesn't play any role whatsoever.

You should counter-measure this threat by using shadow passwords.

---

### Post by BkkBonanza on 2010-01-04
I thought shadow passwords was the default in Ubuntu? 
You would need to be root to get to them.

---

### Post by K.J. on 2010-01-04
The best way to eliminate these threats is running "chmod 755 /etc/passwd". Just kidding, don't do it. The point is what p1n pointed out, protect your /etc/passwd file or that 3 second time out means jack.

---

### Post by BkkBonanza on 2010-01-04
I just checked here and on my system (which must be default I think) the passwords are stored in /etc/shadow not in /etc/passwd. So shadow passwords are used by default. Only root can get access to the passwords (and they are encrypted too, of course).

Used to be, and maybe still on some distros, that passwords were stored in /etc/passwd.

And according to my reading PAM is definitely hooked into both logins and sudo now. Also ssh of course. Just check your logs. Everytime you authenticate, whether using sudo, login or ssh, you see PAM issues the log messages. The whole point of PAM is to modularize the authentication system in linux so of course it has a role.

---

### Post by rookcifer on 2010-01-04
> **shade5 said:**
> Hi,
I think it is very easy to hack passwords in Linux,

Not as easy as it is in Windows XP with its crappy [LM hash.]("http://en.wikipedia.org/wiki/LM_hash")

> **__p1n__ said:**
> You don't need to attempt to login or sudo.  A tool like john-the-ripper will generate and compare hashes against /etc/passwd using either dictionary or bruteforce mode.  PAM doesn't play any role whatsoever.

You should counter-measure this threat by using shadow passwords.

Shadow passwords have been the default in Linux for, what, 10 years?

---

### Post by __p1n__ on 2010-01-04
> **rookcifer said:**
> 
Shadow passwords have been the default in Linux for, what, 10 years?

Depends on the distro but probably the default now.  I installed a vanilla lenny a few weeks ago and was prompted to confirm shadow passwords.

---

### Post by BkkBonanza on 2010-01-04
> **rookcifer said:**
> Not as easy as it is in Windows XP with its crappy [LM hash.]("http://en.wikipedia.org/wiki/LM_hash")


There is a pam_unix module option to use blowfish encryption for passwords. I don't think it's set by default, at least not on my system. But it could be added in /etc/pam.d/common-account and (apparently) any password changed after that will be encrypted that way.

---

### Post by bodhi.zazen on 2010-01-04
> **__p1n__ said:**
> You don't need to attempt to login or sudo.  A tool like john-the-ripper will generate and compare hashes against /etc/passwd using either dictionary or bruteforce mode.  PAM doesn't play any role whatsoever.

You should counter-measure this threat by using shadow passwords.

I understand you point, but you have obviously not tried to hack an Ubuntu system with John any time in the last year or so, will not work ;)

> root@home:~#unshadow /etc/passwd /etc/shadow > crack.passwd

[COLOR=red]root@home:~#john crack.passwd[/COLOR]

[COLOR=#00eed0][/color][color=green]No password hashes loaded[/COLOR]

---

### Post by __p1n__ on 2010-01-04
> **bodhi.zazen said:**
> I understand you point, but you have obviously not tried to hack an Ubuntu system with John any time in the last year or so, will not work ;)

It depends upon which hash function that you've configured.  John (1.7.4) only supports: DES, BSDI, MD5, BF, AFS, LM.

I tried version 1.7.4 against a 8.10 kubuntu test installation and it correctly detected the lame MD5 password hashing function in the unshadow'ed passwd and shadow files and got to work bruteforcing.

---

### Post by jrusso2 on 2010-01-04
If you have physical access to the system there are other methods much easier then brute force you can use.

---

### Post by bodhi.zazen on 2010-01-05
> **__p1n__ said:**
> I tried version 1.7.4 against a 8.10 kubuntu test installation and it correctly detected the lame MD5 password hashing function in the unshadow'ed passwd and shadow files and got to work bruteforcing.

That is my point exactly, John will not work with a default installation of Ubuntu 9.04 or 9.10 (8.10 is over a year "old").

---

