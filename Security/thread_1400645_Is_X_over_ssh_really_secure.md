---
title: "Is X over ssh really secure?"
date: 2010-02-07
forum: Security
---

### Post by mahela007 on 2010-02-07
Hi.. I've just started using X over ssh between my two linux PCs. However, despite the connection being encrypted and everything I still have a kind of noobish question about ssh connections. 
When I started the connection for the very first time, the only message I got that anything was happening was when the client terminal asked me whether I was sure I wanted to connect to the other PC . (It said something to the effect of ' Are you sure you want to connect to IP adress xxxx.xxxx.xxxx). I can't see how this mechanism for connection would prevent an intruder from connecting to my host PC. He would obviously have to know my Linux username and password but this level of protection is provided by XDMCP (which people say is insecure) isn't it? So what prevents someone from logging into my ssh server machine?

---

### Post by erik2912 on 2010-02-07
X over ssh is quite secure, but how secure do you want it. You can make it much more secure by using certificates. 
I'm not going to post a howto here, but this is easy to do. You take a look at ssh-keygen and ssh-copy-id. And be sure to use a password.

---

### Post by mahela007 on 2010-02-07
I think the topic of this thread is misleading (sorry). What I'm wondering is how ssh prevents some unknown user from logging in to my ssh server? all they would need is the username and password of a linux account on the server PC..

---

### Post by falconindy on 2010-02-07
> **mahela007 said:**
> I think the topic of this thread is misleading (sorry). What I'm wondering is how ssh prevents some unknown user from logging in to my ssh server? all they would need is the username and password of a linux account on the server PC..
Right. So make sure that your password is secure. If you're not wanting to access your computer from outside your LAN, then make sure that your LAN is secure -- any wireless access should be secured with at least WPA, preferrably WPA2 and with a strong passphrase. A network level security checklist could go on and on...

And as erik2912 mentioned, you can secure the connection further with public key encryption and disable password access. This means that any intruders would need a copy of your private key to get access.

When people refer to SSH as being secure, it's the protocol that's being referred to as secure -- packets transmitted over SSH have an extremely low liklihood of being intercepted and read. However, it can't be helped if you implement a secure protocol but leave the door wide open by having a simple or, worse, no password.

---

### Post by mikewhatever on 2010-02-07
I hear fail2ban is pretty effective too.

---

### Post by mahela007 on 2010-02-08
Hmm.. thanks. How to I disable password access?

---

### Post by i.r.id10t on 2010-02-08
man sshd

You want to disable password logins and enable key based logins.

Of course, your key should have a password on it as well... but it can be different from your user account password.

You can also set SSH to only allow connections from specific hosts

---

### Post by mahela007 on 2010-02-08
OK.. thanks.

---

