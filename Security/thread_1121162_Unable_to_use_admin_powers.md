---
title: "Unable to use admin powers?"
date: 2009-04-09
forum: Security
---

### Post by lelandstrott on 2009-04-09
Hi,

It seem to have locked myself out of administrator privileges on my computer. After installing the program VirtualBox OSE on my Ubuntu 8.04 computer, it prompted me to change the group my user was in. 
I followed it's instructions without thinking and I am now unable to do anything that requires admin powers or a "sudo" command. 
I have also never enabled the root user. 

Is there anything I can do?

Your help would be appreciated.

---

### Post by bodhi.zazen on 2009-04-09
Boot to recovery mode. You will be at a command line only.

You need to add your user to the admin group.

So, from the command line, run

```
usermod -a -G <user> admin
```

then reboot.

---

