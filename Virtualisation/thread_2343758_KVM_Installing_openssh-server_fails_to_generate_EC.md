---
title: "KVM: Installing openssh-server fails to generate ECDSA key"
date: 2016-11-18
forum: Virtualisation
---

### Post by stlu on 2016-11-18
Hello,

I have installed 2 guest VMs with Ubuntu 16.04.1 amd64 server edition under a KVM host.  For both virtual machines, I am not able to successfully install openssh-server.  There must be something wrong with the way the guests are running under KVM because this doesn't happen in the majority of cases.  I have tested myself and the key generation succeeds when ubuntu server is installed on a bare metal machine.

The host is an HP Proliant ML110, with an Intel Xeon E3110 CPU.

```

# apt-get install openssh-server
...
Setting up openssh-server (1:7.2p2-4ubuntu2.1) ...
Creating SSH2 RSA key; this may take some time ...
...
Creating SSH2 DSA key; this may take some time ...
...
Creating SSH2 ECDSA key; this may take some time ...
/etc/ssh/ssh_host_ecdsa_key.pub is not a public key file.
dpkg: error processing package openssh-server (--configure):
 subprocess installed post-installation script returned error exit status 255
...
Errors were encountered while processing:
 openssh-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Now something has changed since the first time I had a problem.  First time I tried to install openssh-server, I got a "key_generate failed" message, just like the message reported in:
[http://askubuntu.com/questions/817074/cannot-install-openssh-on-ubuntu-server-virtual-machine-kvm](http://askubuntu.com/questions/817074/cannot-install-openssh-on-ubuntu-server-virtual-machine-kvm)

I had run "apt-get purge openssh-server" and installed again, and now I am getting the "not a public key file" error.  Perhaps this is a different version of openssh-server that I am now working with.  Either way, the problem revolves around the ECDSA key.


I tried copying over an ECDSA key pair from the bare-metal machine (that I installed ubuntu server on as a test) and ran "apt-get -f install".  It appears to accept the new pair of keys, and moves on to generate the ED25519 key successfully.  However, when restarting sshd, the guest still rejects the key as invalid, according to journalctl:
```

key_load_private: invalid format
key_load_public: invalid format
could not load /etc/ssh/ssh_host_ecdsa_key

```


Finally, I wanted to see if the guest-generated host key pair was indeed invalid.  I copied over to the bare metal machine, and it worked!  So the key pair is not the problem in itself, it is the way openssh-server is seeing them.


Please help me tackle this problem.  I need to know if there is a critical problem with my KVM host before I put it into production.  Let me know what files are needed, if any.

---

