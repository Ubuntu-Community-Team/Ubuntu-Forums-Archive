---
title: "Server 11.04 bash_completion failure"
date: 2011-06-17
forum: Server Platforms
---

### Post by xoppaw on 2011-06-17
I have an Ubuntu box running server 11.04 that is displaying a weird behavior when logging into the CLI.  The message below will scroll for about 15-20 seconds when you first log in, but then it goes to the normal shell and everything seems to work fine.  has anyone else seen this before? any suggestions on how to fix this?


```

Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-server x86_64)

 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)
Last login: Thu Jun 16 15:23:14 2011 from dd-wrt
-bash: 1307890272: command not found
-bash: 1307890582: command not found
-bash: 1307890893: command not found
-bash: 1307891193: command not found
-bash: 1307891503: command not found
-bash: 1307891813: command not found
-bash: 1307892124: command not found
-bash: 1307892424: command not found
-bash: 1307892734: command not found
-bash: 1307893044: command not found
-bash: 1307893355: command not found
-bash: 1307893655: command not found
-bash: 1307893965: command not found
-bash: 1307894275: command not found
-bash: 1307894585: command not found
-bash: 1307894896: command not found
-bash: 1307895196: command not found
-bash: 1307895506: command not found
-bash: 1307895816: command not found
-bash: 1307896127: command not found
-bash: 1307896427: command not found
-bash: 1307896737: command not found
-bash: 1307897047: command not found
-bash: 1307897358: command not found
-bash: 1307897658: command not found
-bash: 1307897968: command not found
-bash: 1307898278: command not found
-bash: 1307898589: command not found
-bash: 1307898889: command not found
-bash: 1307899199: command not found
-bash: 1307899509: command not found
-bash: 1307899820: command not found
-bash: 1307900120: command not found
-bash: 1307900430: command not found
-bash: 1307900740: command not found
-bash: 1307901050: command not found
-bash: 1307901351: command not found
-bash: 1307901661: command not found
-bash: 1307901971: command not found
-bash: 1307902281: command not found
-bash: 1307902582: command not found
-bash: 1307902892: command not found
-bash: 1307903202: command not found
-bash: 1307903512: command not found
-bash: 1307903823: command not found
-bash: 1307904123: command not found
-bash: 1307904433: command not found
-bash: 1307904743: command not found
-bash: 1307905053: command not found
-bash: 1307905354: command not found
-bash: 1307905664: command not found
-bash: 1307905974: command not found
-bash: 1307906284: command not found
-bash: 1307906595: command not found
-bash: 1307906895: command not found
-bash: 1307907205: command not found
-bash: 1307907515: command not found
-bash: 1307907826: command not found
-bash: 1307908126: command not found
-bash: 1307908436: command not found
-bash: 1307908746: command not found
-bash: 1307909057: command not found
-bash: 1307909357: command not found
-bash: 1307909667: command not found
-bash: 1307909977: command not found
-bash: 1307910287: command not found
-bash: 1307910598: command not found
-bash: 1307910898: command not found
-bash: 1307911208: command not found
-bash: 1307911518: command not found
-bash: 1307911829: command not found
-bash: 1307912129: command not found
-bash: 1307912439: command not found
-bash: 1307912749: command not found
-bash: 1307913059: command not found
-bash: 1307913360: command not found
-bash: 1307913670: command not found
-bash: 1307913980: command not found
-bash: 1307914291: command not found
-bash: 1307914591: command not found
-bash: 1307914901: command not found
-bash: 1307915211: command not found
-bash: 1307915522: command not found
-bash: 1307915822: command not found
-bash: 1307916132: command not found
-bash: .: /etc/bash_completion.d/gpg: cannot execute binary file




1307890272: command not found
1307890582: command not found
1307890893: command not found
1307891193: command not found
1307891503: command not found
1307891813: command not found
1307892124: command not found
1307892424: command not found
1307892734: command not found
1307893044: command not found
1307893355: command not found
1307893655: command not found
1307893965: command not found
1307894275: command not found
1307894585: command not found
1307894896: command not found
1307895196: command not found
1307895506: command not found
1307895816: command not found
1307896127: command not found
1307896427: command not found
1307896737: command not found
1307897047: command not found
1307897358: command not found
1307897658: command not found
1307897968: command not found
1307898278: command not found
1307898589: command not found
1307898889: command not found
1307899199: command not found
1307899509: command not found
1307899820: command not found
1307900120: command not found
1307900430: command not found
1307900740: command not found
1307901050: command not found
1307901351: command not found
1307901661: command not found
1307901971: command not found
1307902281: command not found
1307902582: command not found
1307902892: command not found
1307903202: command not found
1307903512: command not found
1307903823: command not found
1307904123: command not found
1307904433: command not found
1307904743: command not found
1307905053: command not found
1307905354: command not found
1307905664: command not found
1307905974: command not found
1307906284: command not found
1307906595: command not found
1307906895: command not found
1307907205: command not found
1307907515: command not found
1307907826: command not found
1307908126: command not found
1307908436: command not found
1307908746: command not found
1307909057: command not found
1307909357: command not found
1307909667: command not found
1307909977: command not found
1307910287: command not found
1307910598: command not found
1307910898: command not found
1307911208: command not found
1307911518: command not found
1307911829: command not found
1307912129: command not found
1307912439: command not found
1307912749: command not found
1307913059: command not found
1307913360: command not found
1307913670: command not found
1307913980: command not found
1307914291: command not found
1307914591: command not found
1307914901: command not found
1307915211: command not found
1307915522: command not found
1307915822: command not found
1307916132: command not found
-bash: .: /etc/bash_completion.d/gpg: cannot execute binary file

```

---

### Post by ruffEdgz on 2011-06-17
Have some questions:
---
Is this an upgrade to 11.04 or a clean install?

Have you updated anything related to GPG in the past?

Updated or touched anything in the /etc/bash_completion.d/ directory?
---
If you don't know, that directory helps with the [TAB] completion for applications on your server/machine (documentation here): [http://www.debian-administration.org/articles/316](http://www.debian-administration.org/articles/316)

Cheers!

---

### Post by xoppaw on 2011-06-17
> **ruffEdgz said:**
> Have some questions:
---
Is this an upgrade to 11.04 or a clean install?

Have you updated anything related to GPG in the past?

Updated or touched anything in the /etc/bash_completion.d/ directory?
---
If you don't know, that directory helps with the [TAB] completion for applications on your server/machine (documentation here): [http://www.debian-administration.org/articles/316](http://www.debian-administration.org/articles/316)

Cheers!

this was an upgrade, not a clean install.  I did the upgrade about 2 weeks ago and didn't have any trouble until yesterday afternoon.   That being said, this server doesn't get logged into on a daily basis and can go a week or more with out having me on the console.      

to the best of my knowledge i haven't updated anything with GPG unless it was an official update via apt-get 

again, like above, i haven't updated/messed with anything in the bash_completion.d directory unless it came from the official apt-get repos.   

i assumed that this bash_completion.d  directory was something to do with the TAB completion, but when i test TAB completion in the CLI it still works properly.

---

### Post by Toz on 2011-06-17
Any chance you could post the contents of your ~/.bashrc and /etc/bash.bashrc files? Maybe there is something in there that is causing this.

---

### Post by xoppaw on 2011-06-17
> **Toz said:**
> Any chance you could post the contents of your ~/.bashrc and /etc/bash.bashrc files? Maybe there is something in there that is causing this.

the contained file has both

---

### Post by Toz on 2011-06-17
Those files look fine. 

It looks like a config/rc file somewhere is trying to execute those numbers as commands. If you can find them, you can fix them. You might want to try the rgrep command (recursive grep) in both your home dir and /etc (note: rgrep may take some time to complete):
```
rgrep 1307890272 ~
rgrep 1307890272 /etc
```

See what it spits out - might point us to the right location.

---

### Post by Toz on 2011-06-17
And as for the last message in that string, can you post the contents of /etc/bash_completion.d/gpg?

EDIT: Wait. Maybe gpg is the problem. What does:```
file /etc/bash_completion.d/gpg
``` return? It should be ascii text. If it's not, try moving it out of that directory to see if its the culprit.

---

### Post by ruffEdgz on 2011-06-17
> **Toz said:**
> 
EDIT: Wait. Maybe gpg is the problem. What does:```
file /etc/bash_completion.d/gpg
``` return? It should be ascii text. If it's not, try moving it out of that directory to see if its the culprit.

+1 on this suggestion. I asked those questions to make sure if you did/didn't do anything, we could move on from there but it doesn't hurt to remove some of those bash_completion scripts to make sure it does or doesn't help.

---

### Post by xoppaw on 2011-06-17
> **Toz said:**
> Those files look fine. 

It looks like a config/rc file somewhere is trying to execute those numbers as commands. If you can find them, you can fix them. You might want to try the rgrep command (recursive grep) in both your home dir and /etc (note: rgrep may take some time to complete):
```
rgrep 1307890272 ~
rgrep 1307890272 /etc
```

See what it spits out - might point us to the right location.
When I rgrep against /etc, it spits out this:
```
root@NERDY:/home/maddox# rgrep 1307890272 /etc
grep: /etc/alternatives/pluginappletviewer: No such file or directory
grep: /etc/blkid.tab: No such file or directory
grep: /etc/fonts/conf.d/30-defoma.conf: No such file or directory
/etc/bash_completion.d/getent:1307890272 0.05
/etc/webmin/system-status/history/cpuuser:1307890272 0
/etc/webmin/system-status/history/cpuidle:1307890272 100
/etc/webmin/system-status/history/bout:1307890272 0
/etc/webmin/system-status/history/diskused:1307890272 2214774169600
/etc/webmin/system-status/history/cpukernel:1307890272 1
/etc/webmin/system-status/history/swapused:1307890272 10342400
/etc/webmin/system-status/history/bin:131307890272 0.01
/etc/webmin/system-status/history/cpuio:1307890272 0
/etc/webmin/system-status/history/procs:1307890272 121
/etc/webmin/system-status/history/load:1307890272 0.00
/etc/webmin/system-status/history/memused:1307890272 1111482368
root@NERDY:/home/maddox#
```

When I rgrep my home dir I this below, but it never actually completes.  I let it run for 20 min and finally just did a CTRL+C to kill it.

```

maddox@NERDY:~$ sudo rgrep 1307890272 ~
[sudo] password for maddox: 
grep: warning: /home/maddox/svn/xmlrpc-c/src/blddir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/src/srcdir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/lib/abyss/src/blddir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/lib/abyss/src/srcdir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/lib/curl_transport/blddir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/lib/curl_transport/srcdir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/lib/libutil/blddir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/lib/libutil/srcdir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/lib/expat/xmlparse/srcdir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/lib/expat/xmltok/blddir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/lib/expat/xmltok/srcdir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/lib/util/blddir: recursive directory loop

grep: warning: /home/maddox/svn/xmlrpc-c/lib/util/srcdir: recursive directory loop

```


> **Toz said:**
> And as for the last message in that string, can you post the contents of /etc/bash_completion.d/gpg?

EDIT: Wait. Maybe gpg is the problem. What does:```
file /etc/bash_completion.d/gpg
``` return? It should be ascii text. If it's not, try moving it out of that directory to see if its the culprit.

When i do the above command, i get: 
```

maddox@NERDY:~$ file /etc/bash_completion.d/gpg
/etc/bash_completion.d/gpg: data

```

When I move that gpg file to a different location, i get the original error message except that it doesn't have this part in it 
```
-bash: .: /etc/bash_completion.d/gpg: cannot execute binary file
```
Just the string of numbers.

---

### Post by Toz on 2011-06-17
Can you post back the contents of **/etc/bash_completion.d/getent**?

---

### Post by xoppaw on 2011-06-17
> **Toz said:**
> Can you post back the contents of **/etc/bash_completion.d/getent**?

Looks familiar...
```

maddox@NERDY:~$ cat /etc/bash_completion.d/getent
1307890272 0.05
1307890582 0.05
1307890893 0.05
1307891193 0.05
1307891503 0.05
1307891813 0.05
1307892124 0.05
1307892424 0.05
1307892734 0.06
1307893044 0.05
1307893355 0.05
1307893655 0.05
1307893965 0.05
1307894275 0.05
1307894585 0.05
1307894896 0.06
1307895196 0.05
1307895506 0.05
1307895816 0.05
1307896127 0.05
1307896427 0.07
1307896737 0.06
1307897047 0.06
1307897358 0.05
1307897658 0.05
1307897968 0.05
1307898278 0.05
1307898589 0.05
1307898889 0.05
1307899199 0.05
1307899509 0.05
1307899820 0.05
1307900120 0.05
1307900430 0.05
1307900740 0.06
1307901050 0.05
1307901351 0.05
1307901661 0.05
1307901971 0.05
1307902281 0.05
1307902582 0.05
1307902892 0.05
1307903202 0.07
1307903512 0.10
1307903823 0.08
1307904123 0.05
1307904433 0.05
1307904743 0.05
1307905053 0.05
1307905354 0.05
1307905664 0.05
1307905974 0.05
1307906284 0.05
1307906595 0.05
1307906895 0.05
1307907205 0.05
1307907515 0.05
1307907826 0.08
1307908126 0.06
1307908436 0.05
1307908746 0.05
1307909057 0.05
1307909357 0.05
1307909667 0.05
1307909977 0.05
1307910287 0.05
1307910598 0.05
1307910898 0.08
1307911208 0.07
1307911518 0.06
1307911829 0.05
1307912129 0.05
1307912439 0.05
1307912749 0.05
1307913059 0.05
1307913360 0.05
1307913670 0.05
1307913980 0.05
1307914291 0.10
1307914591 0.08
1307914901 0.05
1307915211 0.06
1307915522 0.06
1307915822 0.05
1307916132 

```

---

### Post by Toz on 2011-06-17
And there is your problem. I don't know what has happened to the scripts in your /etc/bash_completion.d directory - they have somehow been corrupted. To fix your current problem, I would suggest you delete the getent file. 

You might also want to try to re-install bash-completion:
```
sudo apt-get --reinstall install bash-completion
```

See if that helps.

---

### Post by xoppaw on 2011-06-18
> **Toz said:**
> And there is your problem. I don't know what has happened to the scripts in your /etc/bash_completion.d directory - they have somehow been corrupted. To fix your current problem, I would suggest you delete the getent file. 

You might also want to try to re-install bash-completion:
```
sudo apt-get --reinstall install bash-completion
```

See if that helps.

Getting rid of the getent file solved the problem, and I went ahead and re-installed bash-completion to be safe.  Everything is working the way it should.
Thanks for everyones help.

---

### Post by Toz on 2011-06-18
Glad to hear. If you don't mind, can you flag this thread as solved from the Thread Tools link above?

---

