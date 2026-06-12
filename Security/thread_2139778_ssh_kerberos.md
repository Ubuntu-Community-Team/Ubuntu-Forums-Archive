---
title: "ssh kerberos"
date: 2013-04-27
forum: Security
---

### Post by terminuzs on 2013-04-27
hello

operating system: Ubuntu 12.10 


so

How to configure SSH  that he paced the ticket of Kerberos, without password ?

kerberos configured, ticket ok
klist confirms this

some configure:

/etc/ssh/sshd_config 
PasswordAuthentication no
KerberosAuthentication yes
GSSAPIAuthentication yes
GSSAPICleanupCredentials yes
 

/etc/ssh/ssh_config 
GSSAPIAuthentication yes
GSSAPIDelegateCredentials yes


kinit user
ssh [EMAIL="user@example.com"]user@example.com[/EMAIL]
permission denied ( gssapi-keyex gssapi-with-mic password)

And if
 
/etc/ssh/sshd_config 
**PasswordAuthentication yes**
KerberosAuthentication yes
GSSAPIAuthentication yes
GSSAPICleanupCredentials yes

Requests password by password passes!
 but I want to on the ticket
Although sniffer says get me the TGT
maybe I'm missing something?

 file with ssh-vvv

---

