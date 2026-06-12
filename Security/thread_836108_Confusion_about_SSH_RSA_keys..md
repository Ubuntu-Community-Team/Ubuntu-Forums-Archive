---
title: "Confusion about SSH RSA keys."
date: 2008-06-21
forum: Security
---

### Post by madu on 2008-06-21
Hello,

I apologize for the n00bish question. This is my first attempt at RSA keys. I read around but have a confusion how the keys are used.

The basic idea is:
There are two keys; public key and private key.
A wants to send msg to B. A uses public key to encrypt the msg and sends it. B uses his private key to decrypt it. All is well.

But I'm confused how RSA can serve my purpose. 
I have a small server at home with OpenSSH enabled, to which I frequently connect from university to do some simple stuff.

What I want to do is, to make my home server only accept a SSH connection from a computer with a known key. I'm not sure if RSA can help me here.
Anyway what I want to achieve is, I have a key (which is very very long than a usual password so its difficult to brute-force) and I use this key to authenticate my university computer to my home server. 

So assuming nobody can get this key from my university computer, no other computer should be able to SSH connect to my home server.

I'd also would like to know what the purpose of the keys "ssh_host_rsa_key" and "ssh_host_rsa_key.pub" in /etc/ssh?
Are they a public/private key pair too?

How can I achieve this. Sorry for the long question. Even a guide is very welcome. Thanks heaps in advance.

---

### Post by brian_p on 2008-06-21
> **madu said:**
> How can I achieve this. Sorry for the long question. Even a guide is very welcome. Thanks heaps in advance.

See how you go on with

[http://ubuntuforums.org/showthread.php?t=732860](http://ubuntuforums.org/showthread.php?t=732860)

The securityfocus link in the thread looks useful.

---

### Post by madu on 2008-06-21
Thanks for that Brian.

I can understand why there is a  'ssh_host_rsa_key.pub' key in /etc/ssh, but not sure what the private key 'ssh_host_rsa_key' is used for.

---

### Post by hyper_ch on 2008-06-21
here's a howto for public key: [http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

---

### Post by brian_p on 2008-06-21
> **madu said:**
> Thanks for that Brian.

I can understand why there is a  'ssh_host_rsa_key.pub' key in /etc/ssh, but not sure what the private key 'ssh_host_rsa_key' is used for.

Please read the 'Verifying the host key' section at

[http://www.securityfocus.com/infocus/1806](http://www.securityfocus.com/infocus/1806)

and man sshd.

/etc/ssh/ssh_host_rsa_key contains the public and private keys identifying the host you are connecting to. It is not world readable or world writeable.

Connecting to the host for the first time produces a warning message and a fingerprint of the ssh_host_rsa_key file contents. You go ahead and connect. At that stage the **public host key** gets added to your $HOME/.ssh/known_hosts file. It cannot be copied from ssh_host_rsa_key on the remote host. However, ssh_host_rsa_key.pub contains the public key part of ssh_host_rsa_key and it is readable.

ssh_host_rsa_key identifies the host. ssh_host_rsa_key.pub allows that identity to be disseminated.

---

### Post by madu on 2008-06-21
> **brian_p said:**
> Please read the 'Verifying the host key' section at

[http://www.securityfocus.com/infocus/1806](http://www.securityfocus.com/infocus/1806)

and man sshd.

/etc/ssh/ssh_host_rsa_key contains the public and private keys identifying the host you are connecting to. It is not world readable or world writeable.

Connecting to the host for the first time produces a warning message and a fingerprint of the ssh_host_rsa_key file contents. You go ahead and connect. At that stage the **public host key** gets added to your $HOME/.ssh/known_hosts file. It cannot be copied from ssh_host_rsa_key on the remote host. However, ssh_host_rsa_key.pub contains the public key part of ssh_host_rsa_key and it is readable.

ssh_host_rsa_key identifies the host. ssh_host_rsa_key.pub allows that identity to be disseminated.

Thanks a lot Brian. That clears it up!

---

