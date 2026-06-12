---
title: "Snort Issues"
date: 2018-09-19
forum: Security
---

### Post by cal516 on 2018-09-19
I am attempting to print packet headers using snort in sniffer mode but I am receiving the following error:

bash: ./snort: no such file or directory

I have attached a screen shot for more detail. 

[ATTACH=CONFIG]281127[/ATTACH]

---

### Post by deadflowr on 2018-09-19
*Thread moved to **Security***

---

### Post by Claus7 on 2018-09-20
Hello,

> **cal516 said:**
> I am attempting to print packet headers using snort in sniffer mode but I am receiving the following error:

bash: ./snort: no such file or directory

I have attached a screen shot for more detail. 

[ATTACH=CONFIG]281127[/ATTACH]

since you are in the /etc directory there is no need to issue a command with ./ .
Are you sure that the installation of snort is the correct one?

In order to verify it yourself, if it is under your /etc folder then check the output of:
ls -l | grep snort

either you won't see any output, which means that snort is not there or you will see an alternative name for the snort executable. 

You can type also the command:
which snort

to verify the folder that the executable is located.

Welcome to the forums.
Regards!

---

