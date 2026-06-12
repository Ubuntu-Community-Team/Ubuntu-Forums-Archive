---
title: "SSHD broke aftyer upgrading from 14.04 to 16.04"
date: 2018-01-30
forum: Security
---

### Post by oregonbob on 2018-01-30
I upgraded my PC from 14.04 to 16.04 which is working OK, however it now appears that the new openssh sets up so none of my SSH applications now function.

An excellent terminal emulator on Windows called Anzio does not connect but appears stuck in a loop trying to connect.

Even trying to ssh from an older, but not ancient Linux fails with message "no matching cipher". I tried adding a line to /etc/ssh/sshd_config for additional ciphers but that made sshd fail to run.

Is there any simple way to make SSHD work like it used to in say...14.04 with password logins?

---

### Post by #&amp;thj^% on 2018-01-30
This is always the first thing I do before messing with the .conf files:


Prior to editing the configuration file, you should make a copy of the original file and protect it from writing so you will have the original settings as a reference and to reuse as necessary.

Copy the /etc/ssh/sshd_config file and protect it from writing with the following commands, issued at a terminal prompt:

```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.original
sudo chmod a-w /etc/ssh/sshd_config.original
```

Remember 16.04 use's systemd now.
Good place to brush up a bit: [https://help.ubuntu.com/lts/serverguide/openssh-server.html](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
And a good way to restart SSHD:
```
sudo systemctl restart sshd.service
```
Good luck :)

---

### Post by oregonbob on 2018-01-30
So you are saying if I make a backup copy of the sshd_config file and then restart the sshd service that will make it all work again?

I don't think that will help.

---

### Post by #&amp;thj^% on 2018-01-30
> **oregonbob said:**
> So you are saying if I make a backup copy of the sshd_config file and then restart the sshd service that will make it all work again?

I don't think that will help.
No I'm not saying that.;) the link provided should get you going though.
Copying the files is just good common sense to help you with the original settings as a reference and to reuse as necessary.

---

### Post by HermanAB on 2018-02-01
Howdy,

Note that there was a change to SSHD which now doesn't allow older insecure login handshakes by default anymore.  For example, an older Diffie Hellman type now need to be enabled in the config file.

You need to look on the OpenSSH web site for details, but it is best to upgrade your older insecure SSH clients.

Run ssh with verbose error messages to see what is happening: ssh -vvv user@server

---

