---
title: "A lot of warnings when I ran rkhunter"
date: 2013-10-31
forum: Security
---

### Post by Askel on 2013-10-31
Hi
I run rkhunter now and then, and before I've only gotten a couple of warnings and while checking google I found that it should be ok. But this time I had several warnings where the hashnumbers were incorrect. It was the following files:

```
[10:17:44] Warning: The file properties have changed:
[10:17:44]          File: /usr/sbin/rsyslogd
[10:17:44]          Current inode: 792236    Stored inode: 824344
[10:17:44]          Current file modification time: 1379621877 (19-sep-2013 22:17:57)
[10:17:44]          Stored file modification time : 1370461893 (05-jun-2013 21:51:33)
```
```
[10:17:46]   /usr/bin/curl                                   [ Warning ]
[10:17:46] Warning: The file properties have changed:
[10:17:46]          File: /usr/bin/curl
[10:17:46]          Current inode: 784979    Stored inode: 787693
[10:17:46]          Current file modification time: 1377888637 (30-aug-2013 20:50:37)
[10:17:46]          Stored file modification time : 1372362854 (27-jun-2013 21:54:14)
```
```
[10:17:46]   /usr/bin/dpkg                                   [ Warning ]
[10:17:46] Warning: The file properties have changed:
[10:17:46]          File: /usr/bin/dpkg
[10:17:46]          Current hash: 087d869e604b534801af80683a923d4be36db4b2
[10:17:47]          Stored hash : ff843a15faf57d0af0bbb01c8f47d5d4e94c9fad
[10:17:47]          Current inode: 806617    Stored inode: 785112
[10:17:47]          Current file modification time: 1381746044 (14-okt-2013 12:20:44)
[10:17:47]          Stored file modification time : 1357594277 (07-jan-2013 22:31:17)
[10:17:47]   /usr/bin/dpkg-query                             [ Warning ]
[10:17:47] Warning: The file properties have changed:
[10:17:47]          File: /usr/bin/dpkg-query
[10:17:47]          Current hash: 68d0282a8994a150a6d32e0a5587751b72c10667
[10:17:47]          Stored hash : b851ae9c460f7f9d4c200686cbc02788e4e6d4f5
[10:17:47]          Current inode: 880010    Stored inode: 785117
[10:17:47]          Current file modification time: 1381746044 (14-okt-2013 12:20:44)
[10:17:47]          Stored file modification time : 1357594277 (07-jan-2013 22:31:17)
```
```
[10:17:48]   /usr/bin/ldd                                    [ Warning ]
[10:17:48] Warning: The file properties have changed:
[10:17:48]          File: /usr/bin/ldd
[10:17:48]          Current hash: cd55795aa4e77bb3090ea0659faa1de7b9b55565
[10:17:48]          Stored hash : aa188957027d9376768af76c91e32276023a792d
[10:17:48]          Current inode: 793178    Stored inode: 786263
[10:17:48]          Current file modification time: 1380553430 (30-sep-2013 17:03:50)
[10:17:48]          Stored file modification time : 1359374262 (28-jan-2013 12:57:42)
[10:17:48] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
```
```
[10:17:50]   /usr/bin/pgrep                                  [ Warning ]
[10:17:50] Warning: The file properties have changed:
[10:17:50]          File: /usr/bin/pgrep
[10:17:50]          Current hash: 5059204da6ca92deb3349a1f01367b7016fdfcc3
[10:17:50]          Stored hash : 7bc85405c16a30af059dd7399b7e987f65ba69a0
[10:17:50]          Current inode: 791856    Stored inode: 785723
[10:17:50]          Current file modification time: 1382021414 (17-okt-2013 16:50:14)
[10:17:50]          Stored file modification time : 1323711758 (12-dec-2011 18:42:38)
```
```
[10:17:52]   /usr/bin/top                                    [ Warning ]
[10:17:52] Warning: The file properties have changed:
[10:17:52]          File: /usr/bin/top
[10:17:52]          Current hash: 954c1dfb62d12ae28b7ce6a8bc6d290fc9d3a5e4
[10:17:52]          Stored hash : 4998ec6cef8694ea13decb84f74199b4ff23e798
[10:17:52]          Current inode: 786543    Stored inode: 785990
[10:17:52]          Current file modification time: 1382021414 (17-okt-2013 16:50:14)
[10:17:52]          Stored file modification time : 1323711758 (12-dec-2011 18:42:38)
```
```
[10:17:53] Warning: The file properties have changed:
[10:17:53]          File: /usr/bin/vmstat
[10:17:53]          Current hash: 7c7473118705b232b53489d76b6e6226fd5457d8
[10:17:53]          Stored hash : 91a352cea3389ac87b9880fed378fe76478900e8
[10:17:53]          Current inode: 791874    Stored inode: 786071
[10:17:53]          Current file modification time: 1382021414 (17-okt-2013 16:50:14)
[10:17:53]          Stored file modification time : 1323711758 (12-dec-2011 18:42:38)
[10:17:53]   /usr/bin/w                                      [ Warning ]
[10:17:53] Warning: The file properties have changed:
[10:17:53]          File: /usr/bin/w
[10:17:53]          Current hash: 22f860fef16cb144b1ad260326e789464b2d19b5
[10:17:53]          Stored hash : e5136b844ed540d340f61c6ae264e6bdb9c717b4
[10:17:53]   /usr/bin/watch                                  [ Warning ]
[10:17:53] Warning: The file properties have changed:
[10:17:53]          File: /usr/bin/watch
[10:17:53]          Current hash: 910bea91547f95e83f496b5e350545ecda9afa71
[10:17:53]          Stored hash : 30bd80edbc88a894e79d55c3b4af54eea6cb20bf
[10:17:53]          Current inode: 791879    Stored inode: 786077
[10:17:53]          Current file modification time: 1382021414 (17-okt-2013 16:50:14)
[10:17:53]          Stored file modification time : 1323711758 (12-dec-2011 18:42:38)
```
```
[10:17:54]   /usr/bin/unhide.rb                              [ Warning ]
[10:17:55] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
```
```
[10:17:55]   /usr/bin/w.procps                               [ Warning ]
[10:17:55] Warning: The file properties have changed:
[10:17:55]          File: /usr/bin/w.procps
[10:17:55]          Current hash: 22f860fef16cb144b1ad260326e789464b2d19b5
[10:17:55]          Stored hash : e5136b844ed540d340f61c6ae264e6bdb9c717b4
[10:17:55]          Current inode: 791877    Stored inode: 786075
[10:17:55]          Current file modification time: 1382021414 (17-okt-2013 16:50:14)
[10:17:55]          Stored file modification time : 1323711758 (12-dec-2011 18:42:38)
```
```
[10:17:56] Warning: The file properties have changed:
[10:17:56]          File: /sbin/ifdown
[10:17:56]          Current hash: 088f06b8b2cc9cb210bc7b162a969cf53c126142
[10:17:57]          Stored hash : e3b2b298d3c697bcd631447a3342ffe16e89b3d3
[10:17:57]          Current inode: 1444115    Stored inode: 1439035
[10:17:57]          Current size: 53232    Stored size: 53168
[10:17:57]          Current file modification time: 1379620770 (19-sep-2013 21:59:30)
[10:17:57]          Stored file modification time : 1333603183 (05-apr-2012 07:19:43)
[10:17:57]   /sbin/ifup                                      [ Warning ]
[10:17:57] Warning: The file properties have changed:
[10:17:57]          File: /sbin/ifup
[10:17:57]          Current hash: 088f06b8b2cc9cb210bc7b162a969cf53c126142
[10:17:57]          Stored hash : e3b2b298d3c697bcd631447a3342ffe16e89b3d3
[10:17:57]          Current inode: 1444115    Stored inode: 1439037
[10:17:57]          Current size: 53232    Stored size: 53168
[10:17:57]          Current file modification time: 1379620770 (19-sep-2013 21:59:30)
[10:17:57]          Stored file modification time : 1333603183 (05-apr-2012 07:19:43)
```
```
[10:17:59]   /sbin/sysctl                                    [ Warning ]
[10:17:59] Warning: The file properties have changed:
[10:17:59]          File: /sbin/sysctl
[10:17:59]          Current hash: 2a38fce1c6454e264b7a4135c35a58e4b9c54ceb
[10:17:59]          Stored hash : f9d27af0455e041fd3056ff30c0d790990961a94
[10:17:59]          Current inode: 1444129    Stored inode: 1439148
[10:17:59]          Current file modification time: 1382021414 (17-okt-2013 16:50:14)
[10:17:59]          Stored file modification time : 1323711758 (12-dec-2011 18:42:38)
```
```
[10:18:02]   /bin/kill                                       [ Warning ]
[10:18:02] Warning: The file properties have changed:
[10:18:02]          File: /bin/kill
[10:18:02]          Current hash: cf65fb61f1c28e0b10194ba83124320230c7334e
[10:18:02]          Stored hash : c139270a9785b3739dbb9f1f0c42af0ee592165b
[10:18:02]          Current file modification time: 1382021414 (17-okt-2013 16:50:14)
[10:18:02]          Stored file modification time : 1323711758 (12-dec-2011 18:42:38)
```
```
[10:18:04]   /bin/ps                                         [ Warning ]
[10:18:04] Warning: The file properties have changed:
[10:18:04]          File: /bin/ps
[10:18:04]          Current hash: 63d0576f323163e8e633e4317eaa3aafffe6c4c1
[10:18:04]          Stored hash : ff0397d3ee3f033a87665a0a2c661217d9132669
[10:18:04]          Current file modification time: 1382021414 (17-okt-2013 16:50:14)
[10:18:04]          Stored file modification time : 1323711758 (12-dec-2011 18:42:38)
```

I'm a rookie on these securityissues even though I try to read in on it. What does this mean? 

//Askel

---

### Post by Shrek01 on 2013-10-31
3 options
1- You upgraded to 13.10
2- You updated for the first time in months
3- Your machine has been compromised

If it's 1 or 2 then you need to tell rkhunter:
sudo rkhunter --propupd

rkhunter checks if any of those programs have been changed.  After an upgrade, it is normal for rkhunter to throw all these warnings.  It will keep doing it until you use the command mentioned before.  
Use the command only if you are sure that it is case 1 or 2.  If you use it and the machine has been compromised, then rkhunter becomes useless.

---

### Post by Askel on 2013-10-31
I still have 12.04. I havn't upgraded, and I do updates on a regular basis. I only use rkhunter like once every two months or so. 
A couple of weeks ago thou I updated and the update first frose. From the swedish supportforum I got the info that I had gotten the wrong kernel. I now have Kernel Linux 3.5.0-42-generic and I was supposed to have 3.2.0-54-generic. dpkg, grep, kill etc is programs tightly connected to the kernel right?
Two days ago I also added ppa:kubuntu-ppa/backports to install the latest version of Krita. That ppa made 120 packeges to update. I don't know if that may have anything to do with the rkhunterresaults.

---

### Post by Shrek01 on 2013-10-31
I don't think you understand how rkhunter works. 
It needs to run regularly (daily for example as a cron job) to be effective.
It detects changes to specific programs, modules, hidden files, etc. used by rootkits. If configured correctly it will only warn you via email when a changed has been made. 
Then you decide if it was a change made by you via an upgrade, or that your machine has been compromised.
If it was you, then you upgrade your rkhunter database using the command mentioned before.

If you update the system regularly but you manually launch it once every two months, it doesn't make sense to use rkhunter, since you won't know who made the change: you or a "hacker".

---

### Post by sam_baker2 on 2013-10-31
I am following this thread also:
I just ran rkhunter on my machine ( first time in months ), and I got 
about a dozen messages like this, something similar to Askel:
```

[12:03:08] Warning: The file properties have changed:
[12:03:08]          File: /bin/ps
[12:03:08]          Current hash: 63d0576f323163e8e633e4317eaa3aafffe6c4c1
[12:03:08]          Stored hash : ff0397d3ee3f033a87665a0a2c661217d9132669
[12:03:08]          Current inode: 8650783    Stored inode: 8650879
[12:03:08]          Current file modification time: 1382021414 (17-Oct-2013 09:50:14)
[12:03:08]          Stored file modification time : 1323711758 (12-Dec-2011 11:42:38)

```

All of these files show a change on my system:
```
/usr/sbin/rsyslogd
/usr/bin/dpkg
/usr/bin/dpkg-query
/usr/bin/ldd
/usr/bin/pgrep
/usr/bin/rpm
/usr/bin/size
/usr/bin/strings
/usr/bin/top
/usr/bin/vmstat
/usr/bin/w
/usr/bin/watch
/usr/bin/w.procps
/sbin/ifdown
/sbin/ifup
/sbin/sysctl
/bin/kill
/bin/ps
```


I am using 12.04 LTS ( since May/2012 ) and now have kernel 3.2.0-55-generic
I run my updates once or twice a week and, of course, 
new kernels come in regularly.

---

### Post by Askel on 2013-10-31
allright. I guess I've learned something about rkhunter today then :-) So your assesement is that it's nothing to worry about then?

---

### Post by Shrek01 on 2013-10-31
Nope.  My assesement is that you haven't used rkhunter correctly so there is no way to know who changed those things that rkhunter is warning you.  Could be you, could be someone else.  
Good luck :)

---

