---
title: "strip system of apache2/php/mysql? (newb)"
date: 2005-04-29
forum: Server Platforms
---

### Post by fiddy_k on 2005-04-29
Hello, thx for reading this. I just recently installed apache2, php, and mysql in the wrong order  :-|  and since I'm new and will learn from any situation, I'd like to strip my system of all three items so I can do a clean reinstall and do it right. I've done an apt-get remove for all three, but the directories associated with them still exist in /etc. I attempted to simply remove these directories, however it didn't seem to do anything. I know if a directory isn't empty it will automatically error, but I am under the impression --ignore-fail-on-non-empty would delete it regardless. I'm very aware I could be wrong.

Before I make a mistake I'll regret, does anyone have any suggestions on how to completely wipe a system of these packages/directories/whatever, short of wiping the system itself? Any advice is appreciated. Thanks.

---

### Post by flyinglizard on 2005-04-30
have you tried the --purge option to apt-get?

```
sudo apt-get remove --purge mysql-server apache2 php4
```

---

### Post by fiddy_k on 2005-04-30
Nope, didn't even know it existed. Thanks! I'll try that and post a reply with the results... if I don't totally murder my system  :-|

---

