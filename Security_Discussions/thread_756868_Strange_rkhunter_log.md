---
title: "Strange rkhunter log"
date: 2008-04-16
forum: Security Discussions
---

### Post by olsmithy on 2008-04-16
Hey everyone just wanted to congratulate you on a very helpful forum in the last couple of days it has been really useful and a very much an asset to me. Just a few things I am concerned about my rkhunter reports a few odd changes mainly these...

[15:23:14] Warning: The file properties have changed:
[15:23:14]          File: /bin/su
[15:23:14]          Current gid: 110    Stored gid: 0

[15:23:16]          File: /usr/bin/awk
[15:23:16]          Current hash: 7bd14d67ff98ae633f95ef985fa944c1a9904bf5
[15:23:17]          Stored hash : 1a77edf9273da7a55843f941002f480fbada42de

[15:23:22] /usr/bin/ldd                                      [ OK ]
[15:23:22] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script r$

[15:23:38] /usr/sbin/adduser                                 [ OK ]
[15:23:38] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script $

[15:23:32] /usr/bin/gawk                                     [ Warning ]
[15:23:32] Warning: The file '/usr/bin/gawk' exists on the system, but it is no$ is not present in the rkhunter.dat file.

[15:23:32] /usr/bin/lwp-request                              [ OK ]
[15:23:32] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the '

[15:23:38] /usr/sbin/adduser                                 [ OK ]
[15:23:38] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'scr$e 'script replacement' check.

How much of a problem is this as I am very concerned over that new stack smash attack exploit floating around. 
Could some one confirm the awk hashes for me please too? 

All i have done since the new installation is install snort with oinkmaster ,BASE , php5 with mysql and apache. all services are locked down behind a firestarter firewall. Big ups to all those that reply on how I may fix this issue

---

