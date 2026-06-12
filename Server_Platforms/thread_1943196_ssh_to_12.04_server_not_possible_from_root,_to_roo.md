---
title: "ssh to 12.04 server not possible from root, to root."
date: 2012-03-19
forum: Server Platforms
---

### Post by pnunn on 2012-03-19
Hi Guys,

I'm struggling to get a virt-manager connection to a new kvm server I've just set up and think I've discovered why. For some reason I can't ssh from my 12.04 kubuntu laptop as root, to root on the server, but I can ssh from the laptop user account to root on the server!! What tha??

Any ideas why I can't ssh root to root?  Virt-manager simply isn't connecting either (on other machines 10.04 no problems).

Ta

Peter.

---

### Post by ajgreeny on 2012-03-19
> **pnunn said:**
> Hi Guys,

I'm struggling to get a virt-manager connection to a new kvm server I've just set up and think I've discovered why. For some reason I can't ssh from my 12.04 kubuntu laptop as root, to root on the server, but I can ssh from the laptop user account to root on the server!! What tha??

Any ideas why I can't ssh root to root?  Virt-manager simply isn't connecting either (on other machines 10.04 no problems).

Ta

Peter.
Check the /etc/ssh/sshd_config to see if it is disabling root logins like this:-
```
# Authentication:
LoginGraceTime 20
[COLOR=Red]PermitRootLogin no[/COLOR]
StrictModes yes
MaxAuthTries 3
```
However, be very careful logging in as root.

---

### Post by pnunn on 2012-03-19
Thanks for the reply. I have rootlogin enabled, the odd thing is that I can login as root from a user account on the client, but not from root to root.

Peter.

---

### Post by hawkmage on 2012-03-19
Is there an error or any message when you try to ssh as root to the root account?

What about if you use the ssh option -vvv for verbose output?

---

### Post by pnunn on 2012-03-20
Sigh.. today its working fine.. rebooted last night so must have been some configuration it wasn't happy with.

Thanks so much for the help anyway.

Peter.

---

