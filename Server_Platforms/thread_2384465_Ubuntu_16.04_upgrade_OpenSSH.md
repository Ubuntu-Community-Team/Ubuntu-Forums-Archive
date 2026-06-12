---
title: "Ubuntu 16.04 upgrade OpenSSH"
date: 2018-02-07
forum: Server Platforms
---

### Post by bizhat on 2018-02-07
I need to upgrade OpenSSH on Ubuntu 16.04 server because  PCI  compliance give some warning about openSSH version provided by Ubuntu 16.04

[http://free.bizhat.com/pci.pdf](http://free.bizhat.com/pci.pdf)

What is the best way to upgrade OpenSSH on Ubuntu 16.04 server ?

Any PPA available ?

I tried downloading these and install with dpkg -i, but it fail

```

wget http://mirrors.kernel.org/ubuntu/pool/main/o/openssh/openssh-client_7.5p1-10ubuntu0.1_amd64.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/o/openssh/openssh-server_7.5p1-10ubuntu0.1_amd64.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/o/openssh/openssh-sftp-server_7.5p1-10ubuntu0.1_amd64.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/k/krb5/libgssapi-krb5-2_1.15.1-2_amd64.deb

```


[https://gist.github.com/serverok/26dbffac8a8d0750227395bdfa8e9ccc](https://gist.github.com/serverok/26dbffac8a8d0750227395bdfa8e9ccc)

---

### Post by wildmanne39 on 2018-02-07
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

