---
title: "Ubuntu Server 12.04 LTS - &quot;Access Denied&quot; but still allowed in...?"
date: 2013-03-07
forum: Server Platforms
---

### Post by mister_doctor on 2013-03-07
Hello,

I recently rebuilt our small "sandbox" virtual machine to run 12.04 LTS at my workplace. We use as a general "sandbox", for pretty much anything from web development to shell scripting practice.

We have a couple of windows based network shares that I've mounted on this server. To do so, I joined it to the domain using the [powerbroker open]("http://www.powerbrokeropen.org/") package.

I'm experiencing strange behaviour when logging in with a local user ever since joining the domain, making me think I've misconfigured something somewhere. It allows me in, however what it echoes doesn't make sense:

```
login as: username
Access denied
Using keyboard-interactive authentication.
Password:
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-23-generic x86_64)

```

I checked the auth.log file and found nothing that indicates an authentication failure.

```
Mar  7 13:01:25 rpm-cvl03 sshd[50862]: Accepted keyboard-interactive/pam for username from 172.25.0.104 port 54191 ssh2
Mar  7 13:01:25 rpm-cvl03 sshd[50862]: pam_unix(sshd:session): session opened for user batch by (uid=0)

```

Any ideas? Not exactly a showstopper but I wouldn't mind if it went away. I can't remember for the life of me if or how this happened on the previous server.

Thanks in advance!

---

### Post by steeldriver on 2013-03-07
not sure I understand your setup, but is GSSAPI involved somewhere? that looks exactly like what happens sometimes with putty - when it attempts GSSAPI auth first, fails, and then drops through to password auth

---

### Post by mister_doctor on 2013-03-07
Yes that was exactly it.

I set it to No in sshd_config, restarted the service, logged back in, all good now.

Thanks for that!

---

