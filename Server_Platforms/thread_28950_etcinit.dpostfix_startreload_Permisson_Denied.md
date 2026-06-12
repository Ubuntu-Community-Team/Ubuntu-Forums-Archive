---
title: "/etc/init.d/postfix start/reload Permisson Denied?"
date: 2005-04-22
forum: Server Platforms
---

### Post by crmanski on 2005-04-22
Hello,
On boot of when manually running as root...
/etc/init.d/postfix reload
or 
/etc/init.d/postfix start
 I get the error...
bash: /etc/init.d/postfix: Permission denied

Strangely enough I can start the postfix server with the Postfix webmin interface under servers.

Could someone suggest how to diagnose what I am being denied here?

Another oddity is that I see a file called postfix.locked in the /etc/init.d directory.

Thanks
Craig

---

### Post by andvaranaut on 2005-04-22
Seems to me like the postfix script is not executable.  The 'permission denied' error means that Bash (the shell you type on in terminals) is not able to read the file contents.

Try **sudo chmod a+rx /etc/init.d/postfix** and see if it fixes things.

Cheers

---

### Post by crmanski on 2005-04-22
Thanks!
That did it.  I like easy solutions...

---

