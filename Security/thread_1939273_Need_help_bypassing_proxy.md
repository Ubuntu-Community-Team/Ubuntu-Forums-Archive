---
title: "Need help bypassing proxy"
date: 2012-03-11
forum: Security
---

### Post by ppparadox on 2012-03-11
Hello everybody, this is my situation:
i need to ssh from a machine (on the which i am a logged in as a common user with no super user privileges) inside a restricted network which only allows outgoing HTTP & HTTPS traffic.
Plain ssh connection attempts get silently dropped and timeout after a while, _attempts to avoid port 22 fail too_ so i think there's some kind of **_deep packet inspection_** going on.
Also, in my ~/.bashrc i've noticed that the following variables are set:
HTTP_PROXY=x.x.x.x:y
HTTPS_PROXY=x.x.x.x:z

So... what i'd like to do is to run the simplest HTTPS client possible to connect to my home computer and from there redirect the SSH session to the real target host (on port 22, not my home machine).
In short i'd like to encapsulate the SSH session inside an HTTPS tunnel. I'd like to stress the fact that plain SSH gets dropped so simple ssh chaining\hopping is a big no-no.
I haven't been able to find a simple solution for this yet because every guide required me to install something on the client machine.

Ideally this should go like this:
```

user@unprivileged:~$ ./httpsclient $homeIP:443 $localport &
user@unprivileged:~$ ssh -p $localport $targetHostUser@localhost

```

---

### Post by Dangertux on 2012-03-11
We dont support circumventing the security measures of your host network

---

### Post by Elfy on 2012-03-11
Closed.

Contact whoever's network it is you are trying to bypass the proxy on.

---

