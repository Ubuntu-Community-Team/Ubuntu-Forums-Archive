---
title: "Funky SSH behavior - permission denied when i kill the terminal session"
date: 2015-04-10
forum: Security
---

### Post by scojopa on 2015-04-10
[B]I have a new server that I can get the ssh key via ssh-copy-id. No problem. I can disable password authentication and connect to ssh using the key. No problem. 

As soon as I close the terminal session I can no longer get in I get Permission denied (publickey)

I have gone back and remove the key from authorized key file, re-enabled password authentication, and get it back on the server. Any insight would be appreciated - 

Here is a good connection:
===========================================================[/B]
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to web [192.168.1.2] port 22.
debug1: Connection established.
debug1: identity file /home/sp/.ssh/id_rsa type 1
debug1: identity file /home/sp/.ssh/id_rsa-cert type -1
debug1: identity file /home/sp/.ssh/id_dsa type -1
debug1: identity file /home/sp/.ssh/id_dsa-cert type -1
debug1: identity file /home/sp/.ssh/id_ecdsa type -1
debug1: identity file /home/sp/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/sp/.ssh/id_ed25519 type -1
debug1: identity file /home/sp/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH_6.6.1* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr [EMAIL="hmac-md5-etm@openssh.com"]hmac-md5-etm@openssh.com[/EMAIL] none
debug1: kex: client->server aes128-ctr [EMAIL="hmac-md5-etm@openssh.com"]hmac-md5-etm@openssh.com[/EMAIL] none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 
debug1: Host '[ter]:22' is known and matches the ECDSA host key.
debug1: Found key in /home/sp/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/sp/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 535
debug1: Authentication succeeded (publickey).
Authenticated to web ([192.168.1.2]:22).
debug1: channel 0: new [client-session]
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Welcome to Ubuntu 14.04.2 LTS (GNU/Linux 3.16.0-34-generic x86_64)
[B]===================================================
Then I close the terminal and it fails:
===================================================[/B]
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to web [192.168.1.2] port 22.
debug1: Connection established.
debug1: identity file /home/sp/.ssh/id_rsa type 1
debug1: identity file /home/sp/.ssh/id_rsa-cert type -1
debug1: identity file /home/sp/.ssh/id_dsa type -1
debug1: identity file /home/sp/.ssh/id_dsa-cert type -1
debug1: identity file /home/sp/.ssh/id_ecdsa type -1
debug1: identity file /home/sp/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/sp/.ssh/id_ed25519 type -1
debug1: identity file /home/sp/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH_6.6.1* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr [EMAIL="hmac-md5-etm@openssh.com"]hmac-md5-etm@openssh.com[/EMAIL] none
debug1: kex: client->server aes128-ctr [EMAIL="hmac-md5-etm@openssh.com"]hmac-md5-etm@openssh.com[/EMAIL] none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 
debug1: Host '[tre]:22' is known and matches the ECDSA host key.
debug1: Found key in /home/sp/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/sp/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/sp/.ssh/id_dsa
debug1: Trying private key: /home/sp/.ssh/id_ecdsa
debug1: Trying private key: /home/sp/.ssh/id_ed25519
debug1: No more authentication methods to try.
Permission denied (publickey).

---

### Post by scojopa on 2015-04-10
I seems that it is tied into an issue w/ Password Authentication - if I enable it - it still users publickey and works. If I disable password Authentication the public key fails:

```
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/sp/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 535
debug1: Authentication succeeded (publickey).
Authenticated to web ([192.168.1.2]:22).
debug1: channel 0: new [client-session]
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Welcome to Ubuntu 14.04.2 LTS (GNU/Linux 3.16.0-34-generic x86_64)
```

---

