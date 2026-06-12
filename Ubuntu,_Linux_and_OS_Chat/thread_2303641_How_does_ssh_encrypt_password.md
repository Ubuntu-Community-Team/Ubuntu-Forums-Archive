---
title: "How does ssh encrypt password?"
date: 2015-11-20
forum: Ubuntu, Linux and OS Chat
---

### Post by lastopier on 2015-11-20
It clearly doesn't send it in plain text. Here: [https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process) it says that client and server negotiate encryption, but the site doesn't say how. Does the server like just generate a key pair and sends the public key to the client, so that the client encrypts the password, or is there a more complex method?

---

### Post by fjgaude on 2015-11-20
I guess if they said "how" then it would be too easy to bypass.

---

### Post by papibe on 2015-11-20
Hi lastopier.

The section 'Negotiating Encryption for the Session' describes how encryption is set up. If you want more gritty details, I'd recommend researching the Diffie-Hellman algorithm.

Then, acording to the ssh's man the password, the password (plain) is sent over the encrypted channel:
> The password is sent to the remote host for checking; however, since all communications are encrypted, the password cannot be seen by someone listening on the network.
Regarding this:
> **fjgaude said:**
> I guess if they said "how" then it would be too easy to bypass.
That is the well-known principle of 'security by obscurity'. Although there are tools that work this way, **open source tools don't work this way**. If you can see the source code, you know every little detail.

In this case, and the case of most open source tools, security is based in peer-reviewed math and algorithms.

By the way, here you can find the OpenSSH's source code:
[LIST]
[*]clone only: git://anongit.mindrot.org/openssh.git
[*]web and clone: [https://anongit.mindrot.org/openssh.git](https://anongit.mindrot.org/openssh.git)
[/LIST]
Does that helps? Let us know if you have more questions.
Regards.

---

### Post by Lars Noodén on 2015-11-21
> **lastopier said:**
> It clearly doesn't send it in plain text. Here: [https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process) it says that client and server negotiate encryption, but the site doesn't say how. Does the server like just generate a key pair and sends the public key to the client, so that the client encrypts the password, or is there a more complex method?

Here is a diagram over the Diffie-Hellman exchange:

[http://linuxnow.ru/files/84/Diffie-hellman_Exchange.png](http://linuxnow.ru/files/84/Diffie-hellman_Exchange.png)

and depending on how your C is, you can take a look by examining the source:

```

cd /tmp
apt-get source openssh
tar zxf openssh-<tab>
cd openssh<tab>

```

---

