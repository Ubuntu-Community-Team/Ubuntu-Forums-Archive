---
title: "/etc/services, ufw, and overriding default ports"
date: 2010-06-09
forum: Security
---

### Post by davemc01 on 2010-06-09
Hello Ubuntu community, I have a question regarding ufw and service names.

I understand that ufw uses the /etc/services file to map a service name to a port, when you use ufw syntax like: [FONT=Courier New]sudo ufw allow ssh[/FONT] rather than [FONT=Courier New]sudo ufw allow 22[/FONT]

However, in this particular case of ssh, I've changed my ssh port to something else in the /etc/ssh/sshd_config file.

If I run [FONT=Courier New]sudo ufw allow ssh[/FONT] will ufw know to allow the port that in actuality is tied to ssh, or will it simply go by what's in the /etc/services file.

Thanks in advance :)

Dave

---

### Post by bodhi.zazen on 2010-06-09
Neither and no, no, no =)

ufw uses config files in /etc/ufw/applications.d

in the case of ssh, /etc/ufw/applications.d/openssh-server

Here are the contents ...

> [OpenSSH]
title=Secure shell server, an rshd replacement
description=OpenSSH is a free implementation of the Secure Shell protocol.
ports=22/tcp

So, delete your current rule

```
sudo ufw delete allow ssh
```

Edit /etc/ufw/applications.d/openssh-server , change the ports line to the port you use, and then add the rule

```
sudo ufw allow ssh
```

If you do not wish to edit config files, simply

```
sudo ufw allow port/tcp
``` will do where "port" is the port you use for ssh.

Along those lines - I suggest you use denyhosts and ssh keys, both more effective then changing the port.

---

