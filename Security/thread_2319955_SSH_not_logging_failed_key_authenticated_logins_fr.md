---
title: "SSH not logging failed key authenticated logins from valid users"
date: 2016-04-08
forum: Security
---

### Post by puenteadrian on 2016-04-08
SSH not logging failed key authenticated logins from valid users


Hello Everyone!


For some reason OpenSSH is not logging the failed logins in /var/log/btmp (lastb) of valid users when I am authenticating with an SSH Key but it does when I am using an invalid user. On the other hand It logs failed and successful logins from valid and invalid users when I am using password authentication. 


I know that by adding/changing *LogLevel VERBOSE* in */etc/ssh/sshd_config* I will be able to see all logging activities in* /var/log/secure* but I need it to be logged in */var/log/btmp* so I can list the failed logins with *lastb*. The same behavior was found in CentOS 7.2. Any useful help or advice is highly appreciated.


**Environment**



[LIST]
[*]Version: Ubuntu 14.04.4 LTS
[*]Kernel: 3.13.0-85-generic
[*]OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.6, OpenSSL 1.0.1f 6 Jan 2014
[/LIST]


Greets
-- 
Adrián Puente Z.
@ch0ks
[http://www.hackarandas.com](http://www.hackarandas.com)

---

### Post by papibe on 2016-04-08
Hi puenteadrian. Welcome to the forums ):P

I didn't know anything about this when I read your thread, so it got me interested...

This is what I found out.

According to [this]("http://linux-training.be/sysadmin/ch17.html#idp66532736") documentation:
> Failed logins via ssh, rlogin or su are not registered in /var/log/btmp. Failed logins via tty are.
However since you have experienced, and I can confirm, it does some logging of ssh connections. So I went to see the source code at [github]("https://github.com/openssh/openssh-portable").

The function the creates entries in /var/log/btmp is:
```
void record_failed_login(const char *, const char *, const char *);
```
located in [loginrec.c]("https://github.com/openssh/openssh-portable/blob/0235a5fa67fcac51adb564cba69011a535f86f6b/loginrec.c")

The file that calls the function is [auth.c]("https://github.com/openssh/openssh-portable/blob/0235a5fa67fcac51adb564cba69011a535f86f6b/auth.c"). This would be the 2 calls that I found:
```
#ifdef CUSTOM_FAILED_LOGIN
	if (authenticated == 0 && !authctxt->postponed &&
	    (strcmp(method, "password") == 0 ||
	    strncmp(method, "keyboard-interactive", 20) == 0 ||
	    strcmp(method, "challenge-response") == 0))
		record_failed_login(authctxt->user,
		    auth_get_canonical_hostname(ssh, options.use_dns), "ssh");
```
and
```

	if (pw == NULL) {
		logit("Invalid user %.100s from %.100s port %d",
		    user, ssh_remote_ipaddr(ssh), ssh_remote_port(ssh));
#ifdef CUSTOM_FAILED_LOGIN
		record_failed_login(user,
		    auth_get_canonical_hostname(ssh, options.use_dns), "ssh");
#endif
```
My conclusions:
[LIST]
[*](from the first call) if there's a password asked (keyboard interactive?), it's logged into /var/log/btmp
[*](from second call) if the user is invalid, it's also logged there.
[/LIST]
Hope it helps. Let us know how that goes.
Come here often and have fun.
Regards.

---

