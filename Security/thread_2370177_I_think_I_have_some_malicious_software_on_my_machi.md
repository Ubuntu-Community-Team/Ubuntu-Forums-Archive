---
title: "I think I have some malicious software on my machines"
date: 2017-08-30
forum: Security
---

### Post by rsteinmetz70112 on 2017-08-30
Recently I have found some odd processes running on one of my machines They seem to be disguised and somewhat related to Apache.

```
scanner   4574     1  0 10:32 ?        00:00:00 [sync_supers]
scanner   4576     1  0 10:32 ?        00:00:00 /bin/bash ./s
scanner  14036  4576  0 13:04 ?        00:00:05 /usr/sbin/http    0
```

Then there are dozens of these.

```
scanner   8750 14036  0 13:31 ?        00:00:00 /usr/sbin/http    0
scanner   9022 14036  0 13:31 ?        00:00:00 /usr/sbin/http    0
scanner   9026 14036  0 13:31 ?        00:00:00 /usr/sbin/http    0
scanner   9027 14036  0 13:31 ?        00:00:00 /usr/sbin/http    0
scanner   9047 14036  0 13:31 ?        00:00:00 /usr/sbin/http    0
scanner   9051 14036  0 13:31 ?        00:00:00 /usr/sbin/http    0
scanner   9052 14036  0 13:31 ?        00:00:00 /usr/sbin/http    0
scanner   9056 14036  0 13:31 ?        00:00:00 /usr/sbin/http    0
```

Of course there is no file /usr/sbin/http 
The user scanner was created by our copier company to allow scans to be placed directly on our server.
I have changed the shell to /bin/false, hopefully that will stop whatever from running again.

I found the scripts in /tmp/.b22z but I'm not sure I got all of it.

Does any of this look familiar to anyone?
Is [sync_supers] a legit process ? If so where is it located.
What else should I look for.

---

### Post by Perfect Storm on 2017-08-31
Moved to Security.

---

### Post by Habitual on 2017-08-31
in a terminal, issue
```
lsof -p 4576 | less
```  and look for the suspect.

in a terminal: 
```
top -u scanner
``` and inside the top UI, press "c" to show the command-line{s}

scanner on my Ubuntu 14.04-equivalent workstation is
```
scanner:x:109:saned
```

Do you have a scanner?

---

### Post by rsteinmetz70112 on 2017-09-01
Thanks for the help. I deleted the scripts I found. So I can't look further much further. 

On my system in /etc/passwd is now:

s```
canner:x:1054:109::/home/scanner:/bin/false

```
In /etc/groups

```
scanner:x:109:rob,cupsys,hplip,saned
```

those are all longstanding, legit users.

I don't have a scanner directly connected but I do have a document center copy/scan/fax/print on the network.

I'm watching for any return of these processes.

---

### Post by Habitual on 2017-09-01
Glad you got a handle on it. 
```
ps aux | grep <keyword>
``` is another. ;)

and a little digg'ier 
```
lsof +D /path/to/directory
``` That will look for open process{,es} in said /path/
Don't be in it, when you run it ;)

---

### Post by SeijiSensei on 2017-09-02
There may be no malicious intent at all.

Is this the machine to which clients send fax files?  Does the faxing client software use HTTP to upload/download the files?  If so, all of this may be software that was installed by the copier company.  Did you call them before deleting whatever you removed?

---

