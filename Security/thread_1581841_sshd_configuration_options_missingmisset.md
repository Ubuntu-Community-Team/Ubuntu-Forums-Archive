---
title: "sshd configuration options missing/misset"
date: 2010-09-25
forum: Security
---

### Post by louis_carole on 2010-09-25
Dear All,

In the time I've had to find a solution to this problem, I didn't.

```

me@this-computer:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server sshd
/etc/ssh/sshd_config: line 15: Bad configuration option: Host
/etc/ssh/sshd_config: line 16: Bad configuration option: ForwardX11
/etc/ssh/sshd_config: terminating, 2 bad configuration options

```Until last night this-computer's ssh server daemon was running OK.  After a remote reboot command was received from a known user w/ sudo privileges (and the computer did reboot), sshd has been unable to start, and the etc ssh script yields the error message above.

ForwardX11 is #'ed out in ssh_config, with would-be value 'no'.  Host does not appear at all in ssh_config.

What other on-my-own info should I be looking for?  Thanks!

- Louis

-----

Linux - because I like banging my head against walls.

---

### Post by CharlesA on 2010-09-25
Can you post the contents of /etc/ssh/sshd_config please.

---

### Post by BkkBonanza on 2010-09-25
You seem to be mixing up ssh_config and sshd_config. They both potentially exist and are different. 

Host is not valid in sshd_config but is valid in ssh_config. Maybe someone meant to add that line to ssh_config and mistakenly put it in sshd_config? It appears to now be stopping sshd from starting. Same regarding ForwardX11.

---

