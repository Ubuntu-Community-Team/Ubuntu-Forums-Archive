---
title: "PTY allocation request failed on channel 0"
date: 2011-07-25
forum: Server Platforms
---

### Post by compulsiveguile on 2011-07-25
I recently ran into the following problem when trying to ssh into my Ubuntu 11.04 server:

>> ssh [email]user@site.com[/email]
PTY allocation request failed on channel 0

I don't know for sure, but I think this happened after one of the latest Ubuntu updates I installed. In case it's of relevance, I'm remoting in from Terminal (Mac OS X 10.7 - Lion). 

Edit: The problem seems to be with Lion... still any help would be appreciated.


Here's the -v dump:

GLPro:~ greg$ ssh -v [email]user@site.com[/email]
OpenSSH_5.6p1, OpenSSL 0.9.8r 8 Feb 2011
debug1: Reading configuration data /etc/ssh_config
debug1: Applying options for *
debug1: Connecting to xxxx [xxx.xx.xx.xx] port 22.
debug1: Connection established.
debug1: identity file /xxx/xxx/.ssh/id_rsa type 1
debug1: identity file /xxx/xxx/.ssh/id_rsa-cert type -1
debug1: identity file /xxx/xxx/.ssh/id_dsa type -1
debug1: identity file /xxx/xxx/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-1ubuntu3
debug1: match: OpenSSH_5.8p1 Debian-1ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.6
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'neek.us' is known and matches the RSA host key.
debug1: Found key in /xxxx/xxxx/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /xxxx/xxxx/.ssh/id_rsa
debug1: Server accepts key: pkalg xxx-xxx xxxx xxxx
debug1: Authentication succeeded (publickey).
Authenticated to xxxx ([xxx.xx.xx.xx]:xx).
debug1: channel 0: new [client-session]
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug1: Remote: Forced command.
debug1: Remote: Port forwarding disabled.
debug1: Remote: X11 forwarding disabled.
debug1: Remote: Agent forwarding disabled.
debug1: Remote: Pty allocation disabled.
debug1: Remote: Forced command.
debug1: Remote: Port forwarding disabled.
debug1: Remote: X11 forwarding disabled.
debug1: Remote: Agent forwarding disabled.
debug1: Remote: Pty allocation disabled.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
PTY allocation request failed on channel 0

---

### Post by compulsiveguile on 2011-07-27
I've made some progress... it may be more of a local ssh key problem...?

I am able to ssh into this account from another local account on my Mac. I am also able to remote in as another user from the same local account on my Mac.

---

