---
title: "/etc/sudoers after chmod +w"
date: 2011-02-28
forum: Security
---

### Post by cmujoy on 2011-02-28
Sorry if this question has been asked/answered before. I searched the archive but was not able to find the answer.

I was a sudoer on a Ubuntu 9.10 system. I made a mistake by 'sudo chmod +w /etc/sudoers' when I tried to add other users in. Now the system complains that /etc/sudoers is in invalid mode:
"sudo: /etc/sudoers is mode 0640, should be 0440"

As ubuntu does not have root. Am I just doomed?

---

### Post by cariboo on 2011-02-28
You can boot into recovery mode to fix your problem, once at the menu select drop to netroot, where you will be dropped to a root prompt.

---

### Post by cmujoy on 2011-02-28
Thanks a lot cariboo907 for your quick response. I will try that.

---

### Post by sisco311 on 2011-02-28
Welcome to the forums!

As cariboo907 pointed it out, you can reset the file's permissions from the single user mode (a.k.a. Recovery Mode).  

If you need more help, please check out:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

You probably know, but if you don't mind, I would like to clarify some things.

In Ubuntu, just like in almost all Unix/Linux distributions, the `root' account exists and it's fully functional. The root account password is locked because, by default, Ubuntu uses sudo instead of su; see:  
[uhelp]community/RootSudo[/uhelp]
and (of course) the man page:```
man sudo_root
```

In general, you shouldn't change the permissions or owner/group of the system files. In this particular case, you should have to use visudo to edit the file; check out:
[thread=1132821]HowTO: Sudoers Configuration[/thread]
and
```
man sudoers
man visudo
```

HTH

---

