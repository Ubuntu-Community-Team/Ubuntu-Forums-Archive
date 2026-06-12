---
title: "viruses &amp; linux"
date: 2011-01-30
forum: Security
---

### Post by vat with tux on 2011-01-30
"Ubuntu (linux) has less risk from viruses then windows.". Is this true? If yes then why? 

Thanking in advance.

---

### Post by HermanAB on 2011-01-30
Linux has a superior security architecture.  The result is that there simply aren't any Linux viruses.  On Linux, viruses are a non issue.  So, relax and enjoy your Ubuntu system.

---

### Post by vat with tux on 2011-01-30
what kind of security architecture? I want to understand it in deep. So can u suggest any external link from where i can understand this architecture.  

And also i'm using wine. So is there any risk from windows viruses?

---

### Post by |{urse on 2011-01-30
Behold! A wiki link..
[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by lisati on 2011-01-30
> **vat with tux said:**
> what kind of security architecture? I want to understand it in deep. So can u suggest any external link from where i can understand this architecture.  

And also i'm using wine. So is there any risk from windows viruses?

Have a read here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by dirghrabadia on 2011-01-30
> **vat with tux said:**
>  So is there any risk from windows viruses?

Its better to have an anti-virus anyways, as it prevents the spread of virus/trojan if you're going to transfer files from Windows->Linux->Windows.

---

### Post by clasificados on 2011-01-30
Linux uses a different architecture, most viruses are designed for windows, but that doesn't mean that linux viruses don't exist (root kits), or that you can't transfer a virus over to windows users, just to play it safe look up clamav

---

### Post by tekkidd on 2011-01-30
Linux has no viruses because of how the permissions system is set up. On a windows computer, notice that if you are an admin, you can go into the C: drive and delete files. That is because you are given the equivalent of "root" permissions. That means that you own and have power over all the files on the hard drive, not just the ones in your home directory. This makes it easy for viruses to get in, because if someone writes a script that you accidentally execute, that script can get into the C: without having the user grant it permission. In linux, even if you are an admin you are not given rights to the entire HDD, all you are given is permission to ask for those rights temporarily. So in that case, if a virus did try to run it would be given a big PERMISSION DENIED error. With that said, their are very few viruses out for linux just because writing one would be so complex, instead of going right in like in windows, a linux virus would have to use some sort of exploit in order to gain elevated privileges.  And usually if a loophole is found that does allow for an exploit, by the time that hackers would have written a virus for it, the hole would have been patched.

---

### Post by rvchari on 2011-01-30
> **tekkidd said:**
> Linux has no viruses because of how the permissions system is set up. On a windows computer, notice that if you are an admin, you can go into the C: drive and delete files. That is because you are given the equivalent of "root" permissions. That means that you own and have power over all the files on the hard drive, not just the ones in your home directory. This makes it easy for viruses to get in, because if someone writes a script that you accidentally execute, that script can get into the C: without having the user grant it permission. In linux, even if you are an admin you are not given rights to the entire HDD, all you are given is permission to ask for those rights temporarily. So in that case, if a virus did try to run it would be given a big PERMISSION DENIED error. With that said, their are very few viruses out for linux just because writing one would be so complex, instead of going right in like in windows, a linux virus would have to use some sort of exploit in order to gain elevated privileges.  And usually if a loophole is found that does allow for an exploit, by the time that hackers would have written a virus for it, the hole would have been patched.


i would link to add on and above the above mentioned quote.
linux is a free OS and i dont think guys will like to play around with virii...
there r so much more constructive things to learn..

---

### Post by deconstrained on 2011-01-30
Sorry, this beats everything else as an explanation for why there are no viruses in Linux:

[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

---

### Post by Rubi1200 on 2011-01-30
If you read the security stickies, keep to the official repositories, stay current with updates etc, you will likely never have a problem.

The only need for anti-virus would be if you have a mail server and/or you are sharing files with Windows users (as pointed out above).

---

### Post by rvchari on 2011-01-30
i hope using wine as user from installed windows based programs under wine wont give a gate way for the trojans to enter !!!
(.exe files will be ignored if not executed thru wine, right ?)

---

### Post by cascade9 on 2011-01-30
> **rvchari said:**
> i would link to add on and above the above mentioned quote.
linux is a free OS and i dont think guys will like to play around with virii...
there r so much more constructive things to learn..

Yes, and there are probably more constructive things to learn than the plural of 'virus' is 'viruses', not 'virii'.

[http://www.ofb.net/~jlm/virus.html](http://www.ofb.net/~jlm/virus.html)

BTW, "i dont think guys will like to play around with virii" is really funny. Not that 'virii' exists, but the closest thing in latin is 'viri', meaning (basicly) ''man, manliness, masculine". So what you really said was closest to "i dont think guys will like to play around with men". :lolflag:

---

### Post by rvchari on 2011-01-30
thanx for enlightening my english....
aussies and brits... apart from pronounciation, english is perfect, hats off... (let me not swing away from the basic purpose of this thread :P

---

### Post by rookcifer on 2011-01-30
[This guy]("http://linuxmafia.com/~rick/faq/index.php?page=virus") explains in detail why Linux has not been plagued by viruses as MS products have.  Of course, since Vista and 7, Windows has become better, but it's still not all that great.

---

