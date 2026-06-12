---
title: "Public CA SSL certificate for SSH"
date: 2011-11-08
forum: Security
---

### Post by al_mic on 2011-11-08
Hello,

I need to know if you ever used (and if it is possible to use) a certificate signed by a public Certificate Authority for the ssh authentication.

What happens when you connect to a ssh server (or sftp) is that you have to accept the key the server is sending to you.

What I want to do is to put a key that is signed by a public CA so that the authentication skips this part and continues with the password login.

Can you please help me?

Thank you.

---

### Post by emiller12345 on 2011-11-08
I don't know about a CA for SSH, but I think you can maybe set something up using > ~/.ssh/known_hostsyou'll need to review the docs for the proper format for the file though. But I think that it will allow you to by-pass verifying the key.

---

### Post by al_mic on 2011-11-10
Thank you for your reply.

It appears not to be possible to have a signed certificate for ssh login.

The closes thing I found was this link:
[http://serverfault.com/questions/43889/is-there-such-a-thing-as-a-signed-ssh-keypair](http://serverfault.com/questions/43889/is-there-such-a-thing-as-a-signed-ssh-keypair)

In one of the last posts it says that ssh supports certificate signing, but not from public CA.
I do not understand it yet.
[http://www.openssh.org/txt/release-5.4](http://www.openssh.org/txt/release-5.4)
[http://www.openbsd.org/cgi-bin/cvsweb/src/usr.bin/ssh/PROTOCOL.certkeys?rev=1.8;content-type=text/plain](http://www.openbsd.org/cgi-bin/cvsweb/src/usr.bin/ssh/PROTOCOL.certkeys?rev=1.8;content-type=text/plain)

---

