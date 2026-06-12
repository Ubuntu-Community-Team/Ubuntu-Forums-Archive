---
title: "Unwanted SSHD access attempts"
date: 2010-07-16
forum: Security
---

### Post by es20641 on 2010-07-16
Hello. I recently took a look in my /var/log/auth.log file and found a whole slew of remote SSH login attempts to my computer. Is there any way I can disable SSH so whoever is trying to access my computer won't be able to anymore?

If I can't disable SSH what steps should I take?
Thanks a lot in advance. I appreciate it.

Here is an example of a few lines from my log.

sshd[6727]: Failed password for invalid user gobernacion from 212.227.158.175 port 55926 ssh2
Failed password for invalid user el_diablo from 212.227.158.175 port 38891 ssh2

---

### Post by lykwydchykyn on 2010-07-16
You can uninstall it:
```

sudo apt-get remove openssh-server

```

Or if you want to keep it, you can install something like fail2ban to shut down brute force attacks.

---

### Post by es20641 on 2010-07-16
Fail2Ban seems like a really cool idea. I might give that a try. It is insane the number of SSH login attempts that occur in the course of 2 days according to my logs. Kinda scary.

---

### Post by Sanjeevtrip on 2010-07-16
You can list the IPs from which you would do ssh, in ssh_config

---

### Post by es20641 on 2010-07-16
That's a great idea too. Maybe I'll try both of those.
How difficult is it for someone to gain access to a computer with an ssh brute force attack. Is it something that I should really worry about, or is it a real stab in the dark.

---

### Post by bodhi.zazen on 2010-07-16
You can secure ssh in many ways.

IMO most important - Use keys and disable passwords.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

From there you can use the AllowUsers configuration option in sshd_config, TCP wrappers, a service such as fail2ban or denyhosts, or a few "simple" rules for iptables to drop brute force attacks.

IMO, all you need are keys and to disable password authentication.

---

