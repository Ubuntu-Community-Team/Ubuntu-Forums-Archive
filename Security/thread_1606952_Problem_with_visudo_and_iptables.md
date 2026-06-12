---
title: "Problem with visudo and iptables"
date: 2010-10-27
forum: Security
---

### Post by raz3r_ on 2010-10-27
Hi everyone, I am developing a Mono application with C# who actually runs iptables commands. Ofcourse those commmands requires sudo and password so I decided to modify the sudoers file in order to don't need password anymore.

My sudoers looks like that right now:

> ...
# User privilege specification
user ALL=(ALL) NOPASSWD: /sbin/iptables, /sbin/iptables-save, /sbin/iptables-restore
root    ALL=(ALL) ALL
...

The problem is that my program stucks at the first iptables command asking for sudo password. Even if I open a Terminal and execute "sudo iptables -L" for example Ubuntu asks me for password. What's wrong in my sudoers? Wrong syntax?

---

### Post by cariboo on 2010-10-27
Have you logged and back in again?

---

### Post by sisco311 on 2010-10-27
> **raz3r_ said:**
> Hi everyone, I am developing a Mono application with C# who actually runs iptables commands. Ofcourse those commmands requires sudo and password so I decided to modify the sudoers file in order to don't need password anymore.

My sudoers looks like that right now:



The problem is that my program stucks at the first iptables command asking for sudo password. Even if I open a Terminal and execute "sudo iptables -L" for example Ubuntu asks me for password. What's wrong in my sudoers? Wrong syntax?

sudo reads the sudoers file and applies permissions in order from top to bottom. You have to put your entry after **%admin ...** line, otherwise it will be overwritten. See:  

[thread=1132821]HowTO: Sudoers Configuration[/thread]

---

