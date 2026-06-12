---
title: "CIS Benchmark Fail - SSH Hardening"
date: 2021-08-27
forum: Security
---

### Post by seeptiim on 2021-08-27
Hello! I found that Ubuntu fails the following CIS Benchmarks:

3001 - SSH Hardening: Protocol should be set to 2 ___ _Why does Ubuntu allow the use of SSH 1 by default?_
3002 - SSH Hardening: Root account should not be able to log in ___ _Shouldn't this be disallowed by default?_
3005 - SSH Hardening: Empty passwords should not be allowed ___ _Shouldn't these be disallowed by default?_
3006 - SSH Hardening: Rhost or shost should not be used for authentication ___ _Is this necessary for Ubuntu?_
3007 - SSH Hardening: Grace Time should be one minute or less.
3008 - SSH Hardening: Wrong Maximum number of authentication attempts ___ _More than 4 should not be allowed_

Cheers

---

### Post by TheFu on 2021-08-27
> **seeptiim said:**
> Hello! I found that Ubuntu fails the following CIS Benchmarks:

3001 - SSH Hardening: Protocol should be set to 2 ___ _Why does Ubuntu allow the use of SSH 1 by default?_
3002 - SSH Hardening: Root account should not be able to log in ___ _Shouldn't this be disallowed by default?_
3005 - SSH Hardening: Empty passwords should not be allowed ___ _Shouldn't these be disallowed by default?_
3006 - SSH Hardening: Rhost or shost should not be used for authentication ___ _Is this necessary for Ubuntu?_
3007 - SSH Hardening: Grace Time should be one minute or less.
3008 - SSH Hardening: Wrong Maximum number of authentication attempts ___ _More than 4 should not be allowed_

Cheers
The last 3 seem valid, but the first 3 are not part of normal Ubuntu installs.
When reading the /etc/ssh/sshd_config file, the commented lines show the defaults.  To change them, remove the comment and change the value.

[LIST]
[*]3001: Using ssh v2 has been the default in Ubuntu for at least 12 yrs. If there isn't a specific setting, that what you get. I think v1 support was removed from ssh. [https://www.openssh.com/txt/release-7.6](https://www.openssh.com/txt/release-7.6) says v1 was completely removed in 2017. **Outdated tool./B] BTW, I'm positive that 12.04 had the [B]Protocol 2** setting.
[*]3002: root logins. Ubuntu doesn't allow root logins local or remote. I suspect some cloud/VPS image is the issue here. **Bad image.**
[*]3005: Empty passwords cannot be set, except by root. This is a non-issue or another bad image.  The default sshd setting is:
```
#PermitEmptyPasswords no
```
[*]3006: I haven't seen rhosts or shosts used anywhere since the 1990s.  The use of rhosts is meaningless in v2 ssh. It isn't possible. **Outdated tool.**  I just checked 20 systems here and none of them have any files named shosts or .shosts.  Seems like a non-issue. We always use ssh-keys.
[/LIST]
Always helpful to check the manpage for stuff.  For example:
```
     PermitEmptyPasswords
             When password authentication is allowed, it specifies whether
             the server allows login to accounts with empty password
             strings.  **The default is no.**
```

The last 2 in the list are matters of opinion. Change them if you want to be compliant with the specific stuff.
3007 - The default is 2m. Meh. We use key-based authentication, so this is really a non-issue.
3008 - Wrong Maximum number of authentication attempts.  Fail2ban defaults to 5, but that can be configured however you like. MaxAuthTries defaults to 6, which is what the OpenSSH team chose.



I think passwords for ssh should be prohibited 10 minutes after a new machine is installed and RSA-based keys shouldn't be allowed.  Let's get CIS to add those to their list.

My practical ssh "hardening" .... includes:
[LIST=1]
[*]```
sudo apt install ssh fail2ban
```
[*]Then modify the sshd_config this way, at the bottom of the file:
```
PasswordAuthentication no
Match Address 172.22.22.0/24,172.21.22.0/24,172.22.21.0/24
      PasswordAuthentication yes

```
This effectively prevents any passwords to be used outside the 3 internal LANs we have.  We have some other LANs on 10.x.x.x, but those have to use keys, never passwords, as if they were over the internet.

[*]Never using 22/tcp on the internet.  Moving to any other port - probably 60,000+ gets the attempted cracks reduced to about 0. This is something configured in the router.  Inside the LAN, 22/tcp is fine for our needs.
[/LIST]

---

### Post by seeptiim on 2021-08-30
Thank you very much for your detailed answer! I appreciate it.

---

