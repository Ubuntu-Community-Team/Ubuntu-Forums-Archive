---
title: "[SOLVED] Firewall for Ubuntu"
date: 2008-09-02
forum: Security
---

### Post by abhishek.malhotra35 on 2008-09-02
I want to use a firewall so as to control my applications connecting to net. I should be able to configure which application should connect to net or deny. In windows I used norton firewall for the same purpose. Is there any firewall of same kind in ubuntu?

---

### Post by tuxxy on 2008-09-02
I use the inbuilt Ubuntu firewall,

Open a terminal and type **ufw** for a list of commands, 

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by rogeriopvl on 2008-09-02
You have also a graphical interface for ufw, called Gufw: [http://gufw.tuxfamily.org](http://gufw.tuxfamily.org)

It's easy to configure. Although just like ufw, it doesn't operate by applications, but by ports.

---

### Post by cdenley on 2008-09-02
This is the only tool I know of that filters outgoing traffic based on the application initializing the connection.
[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)
The "owner" module for iptables should provide this functionality, but I think some options won't work on the default kernel.

While it would be nice to have this functionality, it isn't necessary in ubuntu as it is in windows because you should be aware of what applications do before you install them, and there shouldn't be any unwanted traffic if you install software from the repos.

---

### Post by abhishek.malhotra35 on 2008-09-02
Thanks for all your help. TuxGuardian is the kind of firewall I was looking for. I first tried firestarter and then shorewall. But wasn't able to get the desired functionality.

---

### Post by hyper_ch on 2008-09-02
I don't think you need to alter the default configuration of iptables for what you want to do.

---

### Post by cdenley on 2008-09-02
> **abhishek.malhotra35 said:**
> Thanks for all your help. TuxGuardian is the kind of firewall I was looking for. I first tried firestarter and then shorewall. But wasn't able to get the desired functionality.

Good luck getting it to work. I tried and failed
```

[23849.526567] tuxg: Unknown symbol register_security
[23849.526638] tuxg: Unknown symbol cap_ptrace
[23849.526704] tuxg: Unknown symbol cap_capget
[23849.526772] tuxg: Unknown symbol cap_task_reparent_to_init
[23849.526832] tuxg: Unknown symbol cap_task_post_setuid
[23849.526879] tuxg: Unknown symbol cap_bprm_set_security
[23849.526926] tuxg: Unknown symbol cap_capset_check
[23849.526972] tuxg: Unknown symbol cap_bprm_apply_creds
[23849.527019] tuxg: Unknown symbol cap_capable
[23849.527098] tuxg: Unknown symbol cap_capset_set
[23849.527159] tuxg: Unknown symbol mod_reg_security

```
I think it's just old and deprecated. It hasn't been updated since April 2006. I guess there isn't enough demand to keep a project like that going since it is so unnecessary.

---

