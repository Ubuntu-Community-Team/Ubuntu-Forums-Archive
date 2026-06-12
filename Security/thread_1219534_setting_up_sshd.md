---
title: "setting up sshd"
date: 2009-07-21
forum: Security
---

### Post by pokeyThePenguin on 2009-07-21
I just installed openssh-server. How can I make SSH remote access as secure as possible? I'm using the default settings right now since I'm unfamiliar with them and how to change them.

I noticed that to establish a connection, you need to provide your root password. I'm definitely not comfortable with that. Is there a way to change the SSH password?

I'm using:
Jaunty Jackalope
GNOME 2.26.1

---

### Post by TuckLive on 2009-07-21
1.  Do not use weak passwords.
2.  Change default port to a non-standard port.
3.  This will help you with changing the default port and allowing certain users  [https://help.ubuntu.com/SSH]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

---

### Post by TuckLive on 2009-07-21
This will help show you how to disable root access.

[http://www.howtogeek.com/howto/linux/security-tip-disable-root-ssh-login-on-linux/]("http://www.howtogeek.com/howto/linux/security-tip-disable-root-ssh-login-on-linux/")

---

### Post by bodhi.zazen on 2009-07-22
Well by default root can not log in with a password, to you do not need to do anything. People who claim this is a security hole in Ubuntu do not understand that or have set a root password.

There are very very few reasons you need to log in as root and if you do I highly advise you use keys.

---

