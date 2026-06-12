---
title: "Kerberos + SSH"
date: 2010-11-10
forum: Security
---

### Post by ibaniski on 2010-11-10
Hello all,

I am trying to setup Kerberos and (for now) use it as a mechanism for using SSH.

In my setup i have 3 boxes: client, server, kerberos; where client is where the SSH client will be used, server where  I will try to log on to, and kerberos is the kerberos server.

The kerbeors server has the following (releavnt) principals: ibaniski (me), host/client, and host/server.

I have the appropriate keytabs on both client and server (I can use kinit -k host/client(or /server) and get the TGT. Similarly, I can do kinit to obtain a TGT for my user, ibaniski.


SO, when I try to `ssh server` after having obtained the TGT by `kinit` I get the following error message:
    Permission denied (gssapi-keyex,gssapi-with-mic).


Could anyone please provide some feedback as to why this is happening and how I can fix it? In the process of running `ssh server` I actually end up getting the service ticket from kerberos; klist shows both.

My /etc/ssh/sshd_config on the server has the following:
[PHP]RSAAuthentication no
PubkeyAuthentication no

PasswordAuthentication no

KerberosAuthentication yes
KerberosGetAFSToken no
KerberosOrLocalPasswd no
KerberosTicketCleanup yes

GSSAPIAuthentication yes
GSSAPICleanupCredentials yes

UsePAM no[/PHP]
and my /etc/ssh/ssh_config on the client has:
[PHP]GSSAPIAuthentication yes
GSSAPIDelegateCredentials yes[/PHP]


Here are some logs/outputs that might be of some use:
ssh -v server
[PHP]ssh -v server
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to server [192.168.1.101] port 22.
debug1: Connection established.
debug1: identity file /home/ibaniski/.ssh/identity type -1
debug1: identity file /home/ibaniski/.ssh/id_rsa type -1
debug1: identity file /home/ibaniski/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'server' is known and matches the RSA host key.
debug1: Found key in /home/ibaniski/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: gssapi-keyex,gssapi-with-mic
debug1: Next authentication method: gssapi-keyex
debug1: No valid Key exchange context
debug1: Next authentication method: gssapi-with-mic
debug1: Authentications that can continue: gssapi-keyex,gssapi-with-mic
debug1: Authentications that can continue: gssapi-keyex,gssapi-with-mic
debug1: Authentications that can continue: gssapi-keyex,gssapi-with-mic
debug1: No more authentication methods to try.
Permission denied (gssapi-keyex,gssapi-with-mic).[/PHP]

and the log at the server
[PHP]sshd[1570]: Invalid user ibaniski from 10.192.168.1.102[/PHP]

Any help would be greatly appreciated.

Regards,
ibaniski

---

