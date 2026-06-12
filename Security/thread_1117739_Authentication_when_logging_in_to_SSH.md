---
title: "Authentication when logging in to SSH"
date: 2009-04-06
forum: Security
---

### Post by Superdude_123 on 2009-04-06
So my question is, how do I make sure that their is no man in the middle when I log in to my SSH server? I have my system setup with passwords and no keys (will be used next month), but for now, how do have my server confirm that it is who it is, and not someone else in the middle pretending to be my server?

---

### Post by cdenley on 2009-04-06
That's what the public key is used for. The first time you connect, you will see a message like
```

The authenticity of host 'hostname (xxx.xxx.xxx.xxx)' can't be established.
RSA key fingerprint is xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx.
Are you sure you want to continue connecting (yes/no)?

```
There is no way for the client to verify it isn't being spoofed the first time you connect automatically. You can verify this manually by viewing the correct RSA key fingerprint locally on the server, and comparing it
```

ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key

```
After you connect, the public key for the server will be stored in ~/.ssh/known_hosts, and if your server is being spoofed (or you reset your RSA key), you will see a warning like the one above when connecting.

---

### Post by Superdude_123 on 2009-04-06
So that means that a man in the middle attack would fail?

---

### Post by cdenley on 2009-04-06
Correct. It is very easy to test this if you connect by hostname. Add an entry to your /etc/hosts file which matches the hostname of your SSH server to the IP address of another ssh server. The result, when you try to connect:
```

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@       WARNING: POSSIBLE DNS SPOOFING DETECTED!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
The RSA host key for ubuntu has changed,
and the key for the corresponding IP address xxx.xxx.xxx.xxx
is unknown. This could either mean that
DNS SPOOFING is happening or the IP address for the host
and its host key have changed at the same time.
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx.
Please contact your system administrator.
Add correct host key in /home/username/.ssh/known_hosts to get rid of this message.
Offending key in /home/username/.ssh/known_hosts:1
RSA host key for hostname has changed and you have requested strict checking.
Host key verification failed.

```
The only time you have to worry is the first time you connect, and you will be warned accordingly (if you're using a proper client).

---

