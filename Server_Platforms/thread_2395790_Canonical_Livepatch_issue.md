---
title: "Canonical Livepatch issue"
date: 2018-07-06
forum: Server Platforms
---

### Post by barroncm on 2018-07-06
Fresh install of Ubuntu Server 18.04.

Ran [COLOR=#111111][FONT=&quot]sudo snap install canonical-livepatch
Then ran "[/FONT][/COLOR][COLOR=#111111][FONT=&quot]sudo canonical-livepatch enable (My KEY)"

Which returns:
[/FONT][/COLOR]Command 'canonical-livepatch' is available in '/snap/bin/canonical-livepatch'
The command could not be located because '/snap/bin' is not included in the PATH environment variable.
canonical-livepatch: command not found


Is this a bug or am I missing something else that's not obvious to me.

---

### Post by monkeybrain20122 on 2018-07-06
export PATH=$PATH:/snap/bin

---

### Post by barroncm on 2018-07-07
So now Im getting this error:

Last login: Fri Jul  6 23:18:13 2018 from 10.10.2.80
administrator@Server1:~$ sudo canonical-livepatch enable (My Key)
[sudo] password for administrator:
cannot change profile for the next exec call: No such file or directory
snap-update-ns failed with code 1
administrator@Server1:~$

I was hoping this would be easier than its proving to be.

Any Ideas?

---

### Post by barroncm on 2018-07-08
bump

---

