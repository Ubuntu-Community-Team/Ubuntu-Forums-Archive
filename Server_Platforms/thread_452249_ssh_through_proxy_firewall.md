---
title: "ssh through proxy firewall"
date: 2007-05-23
forum: Server Platforms
---

### Post by erasmo.da.rotterdam on 2007-05-23
Hi!
I have a local server (192.168.88.11) behind a proxy firewall (192.168.88.33)
I'd like to connect via ssh to another remote server.
On my proxy firewall I have port 5112 forwarded on remote server's ssh port
however if I try on the local server
```
#ssh user@192.168.88.33 -p 5112
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
ff:95:b8:35:99:97:c1:19:9c:a9:88:95:50:79:4b:88.
Please contact your system administrator.
Add correct host key in /home/om/.ssh/known_hosts to get rid of this message.
Offending key in /home/tom/.ssh/known_hosts:1
RSA host key for 192.168.88.33 has changed and you have requested strict checking.
Host key verification failed.

```

ssh checks my proxy key but being redirected on a remote server tells him that I am going on a different machine.
How to securely avoid this message and successfully connect to the remote machine?
I suppose I have to add the remote server key to my local server known hosts. This would probably tell ssh this is a trusted machine...
Is this sufficient? How to do it since I cannot access to the remote server?:confused:

---

### Post by Jussi Kukkonen on 2007-05-23
There is already a key in your known_hosts fo this host and it doesn't match the fingerprint... If there is a good eplanation for this (like proxy pointing to another server now) just remove the line from known_hosts (it's probably on line 1).

---

### Post by erasmo.da.rotterdam on 2007-05-23
Yeah!!!:popcorn:
That works great!!

```
#cd /home/user/.ssh
#mv known_hosts known_hosts.original
#ssh user_on_remote_server@192.168.88.33 -p 5112

```

entering the password creates the fingerprint we need

```
#ssh user_on_proxy_firewall@192.168.88.33
```

Did the same nasty error!!

```
#cat known_hosts.original >> known_hosts
#ssh user_on_proxy_firewall@192.168.88.33
```

Now it works:guitar:

Thank you very very much Jussi

---

