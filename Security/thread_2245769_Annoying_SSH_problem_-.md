---
title: "Annoying SSH problem -"
date: 2014-09-25
forum: Security
---

### Post by scojopa on 2014-09-25
I connect to my ssh server - and can reconnect as long as I keep the terminal open. Once I close the terminal on my machine I can no longer connect - permission denied (public key)

I run eval "$(ssh-agent -s)" 

ssh-add

and I can connect again. 

Whats the problem here? Why do I have to keep reloading my keys. 

Thanks.

---

### Post by Lars Noodén on 2014-09-28
Depending on which desktop you are using, you should already have an agent running.  When you open a fresh terminal what related variables are set?

```

set | grep SSH

```

If there is nothing, then your system is not properly setting up an agent before starting your graphical session.  
If it lists SSH_AGENT_LAUNCHER, SSH_AGENT_PID, and SSH_AUTH_SOCK then the question is what is killing the agent.  How are you exiting your ssh session?

---

### Post by tgalati4 on 2014-09-28
It might look like:
> 
tgalati4@Mint14-Extensa ~ $ set | grep SSH
SSH_AGENT_PID=1899
SSH_AUTH_SOCK=/tmp/keyring-aKb9i7/ssh
SSH_CLIENT='XX.121.XX.173 61475 22'
SSH_CONNECTION='XX.121.XX.173 61475 10.XX.11.30 22'
SSH_TTY=/dev/pts/2


When not connected, you only get the first 2 lines.

Check that the *ssh-agent* is running:

> tgalati4@Mint14-Extensa ~/Desktop $ ps aux | grep ssh
root       493  0.0  0.0  50052   560 ?        Ss   Sep18   0:00 /usr/sbin/sshd -D
tgalati4  1821  0.0  0.0  13588   932 pts/2    R+   08:33   0:00 grep --colour=auto ssh
tgalati4  **1899 ** 0.0  0.0  12572    32 ?        Ss   Sep18   0:00 **/usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager**

---

