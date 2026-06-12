---
title: "SSH Root Login"
date: 2010-02-10
forum: Security
---

### Post by bbourdet on 2010-02-10
Hello,

Just a quick question. I have disabled root login in the sshd_config file, however, when checking my ```
//var/log/auth_log
``` I am seeing that people are trying to login with that account. So my question is, even if it is disabled it will let people attempt to log in?

Thanks for your time,

Tarken

---

### Post by FuturePilot on 2010-02-10
Disabling root logins will not stop people from trying it. But it will not allow them to login. However that's a moot point since by default the root account has no password so you can't login as root anyway.

---

### Post by The Cog on 2010-02-10
It has to let them enter a username before it can even begin to think to itself whether that username should be allowed in. So yes, it has to let them attempt to log in as root in order to know that's what they're trying to do.

---

### Post by FlaHAM on 2010-02-11
Yes, they may still _attempt_ to log on..
However, that is as far as they will get.
When I first enabled my SSh Server I also noticed many attempts to logon.
The first thing I did was to move the SSh Port off of the default (22) and added a stronger passwd.

Later I learned how to use Dual Key access and disabled passwd access.
Now the only way to log on is to have a valid RSA/DSA key.

FlaHAM

---

### Post by OpSecShellshock on 2010-02-13
You're probably logging both successes and failures, so as long as there are no successes (and there probably won't be, since it's not configured to accept them), then you're good. If the server is facing the web then it's getting port scanned--that's just a fact of life. If 22 is listening, then people know that the server accepts incoming ssh connections. The first thing they're going to try as far as logins go is root. In most cases they realize that it won't work and just move on.

---

### Post by HermanAB on 2010-02-13
Howdy,

There are automated scripts that attempt to log into SSH enabled machines.  Once in, they typically set up a Spam server.  These login attempts are like a continuous DOS attack on a server.  A simple way to stop it, is to change the port that SSHD is listening on in /etc/ssh/sshd_config tosomething non-standard like 2345 or whatever.

The brute force scripts are very simple things and changing the default port is quite sufficient to stop this nonsence.

---

### Post by bodhi.zazen on 2010-02-14
> **HermanAB said:**
> Howdy,

There are automated scripts that attempt to log into SSH enabled machines.  Once in, they typically set up a Spam server.  These login attempts are like a continuous DOS attack on a server.  A simple way to stop it, is to change the port that SSHD is listening on in /etc/ssh/sshd_config tosomething non-standard like 2345 or whatever.

The brute force scripts are very simple things and changing the default port is quite sufficient to stop this nonsence.

You can also either write a few rules for iptables, or install a service such as denyhosts or fail2ban.

---

