---
title: "ProFTPd is BROKEN after upgrade!"
date: 2007-02-07
forum: Server Platforms
---

### Post by hostile on 2007-02-07
I have had ProFTPd running smoothly for many years (long before Ubuntu came along).

Synaptic has been telling me for a few months now that ProFTPd would not be upgraded in the usual manner, and I had to do an "apt-get dist-upgrade" in order to resolve the issue.

Well, I did as I was told, and now logins to the server are broken.

The daemon starts just fine, but if any user tries to login, they are denied.

I don't even know where to start looking to resolve this... 

Anyone have any ideas at all?

All users are getting bounced with "login incorrect", even though they are all using the correct user/pass.

---

### Post by JimTDI on 2007-02-08
can you logon as one of those users at a terminal window?

if you:  sudo getent passwd | less

do you see the users listed?

---

### Post by hostile on 2007-02-08
As a safety precaution, all of my ftp users have /bin/false as their shell, so they cannot login any way other than FTP...

:(

---

### Post by hostile on 2007-02-09
I figured it out.

Ubuntu sets account aging at 60 days, with a 30 day password change grace period before it disables the account.

By going into /etc/shadow and changing the 60 day period to 99999 (which is basically "never expires"), everything works again.

FYI for anyone else stabbed by Ubuntu's short user account lifetime.

---

