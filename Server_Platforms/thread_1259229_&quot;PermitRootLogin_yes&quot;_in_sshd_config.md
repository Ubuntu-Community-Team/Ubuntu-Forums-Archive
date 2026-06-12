---
title: "&quot;PermitRootLogin yes&quot; in sshd_config?"
date: 2009-09-06
forum: Server Platforms
---

### Post by tr333 on 2009-09-06
If Ubuntu has the root account locked by default, why does /etc/ssh/sshd_config have "PermitRootLogin yes" in the default config?  Isn't that a security risk allowing the root account to login by default?  If Ubuntu users have to specifically enable the root account then I don't think its too much extra effort to allow root ssh login if they really require it.

---

### Post by Bachstelze on 2009-09-06
> **tr333 said:**
> If Ubuntu has the root account locked by default

Not exactly. By default, Ubuntu gives the root user a password which is impossible to get right (i.e. you could try every possible password, it would never work). However, you can very well login as root via SSH in other ways, for example using key-based or host-based authentication instead of password-based.

---

### Post by tr333 on 2009-09-07
That would mean someone could use ssh keys to get a root shell without having to reset the password?

---

### Post by nandemonai on 2009-09-07
> **tr333 said:**
> That would mean someone could use ssh keys to get a root shell without having to reset the password?

In theory, yes.. I think...

Stupid default if you ask me. Ubuntu promotes use of sudo over root account so why does that not follow through to ssh access?

:confused:

---

### Post by Xipher on 2009-09-07
Yes, and this can also be achived by setting PermitRootLogin to without-password. Setting it to without-password is what we often do where I work when we want automated root logins with out actually enabling the password. Don't forget you keep your keys safe and password protected.

> **nandemonai said:**
> In theory, yes.. I think...

Stupid default if you ask me. Ubuntu promotes use of sudo over root account so why does that not follow through to ssh access?

:confused:
It really does. In a default state login to root over SSH won't work with out some external method of authentication be it ssh keys or gssapi/kerberos and the addition of such takes the system out of the default state. Leaving it enabled though allows those you wish to enable root in their preseed file with out the headache of also having to follow up and enable direct root post OpenSSH install via script.

---

### Post by Bachstelze on 2009-09-07
> **nandemonai said:**
> 
Stupid default if you ask me. Ubuntu promotes use of sudo over root account so why does that not follow through to ssh access

Because if you know how to setup alternate SSH authentication methost, you probably know your stuff well enough and don't need your hand held about root and sudo. ;)

---

### Post by SoftwareExplorer on 2009-09-07
I doesn't seem hurt to turn it off. I've always disabled it and it hasn't given me problems yet.

---

