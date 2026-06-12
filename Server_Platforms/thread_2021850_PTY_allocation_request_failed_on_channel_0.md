---
title: "PTY allocation request failed on channel 0"
date: 2012-07-09
forum: Server Platforms
---

### Post by thanigaivelan19 on 2012-07-09
Hi,

I am getting error when i connect with ssh

My command is
ssh -p 7822 [EMAIL="qsolvinc@svn.qsolv-inc.com"]qsolvinc@svn.qsolv-inc.com[/EMAIL] -v


OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to svn.qsolv-inc.com [75.98.165.130] port 7822.
debug1: Connection established.
debug1: identity file /home/thanigai/.ssh/id_rsa type -1
debug1: identity file /home/thanigai/.ssh/id_rsa-cert type -1
debug1: identity file /home/thanigai/.ssh/id_dsa type -1
debug1: identity file /home/thanigai/.ssh/id_dsa-cert type -1
debug1: identity file /home/thanigai/.ssh/id_ecdsa type -1
debug1: identity file /home/thanigai/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1_ct
debug1: match: OpenSSH_5.8p1_ct pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 9d:c9:88:4c:08:6f:35:74:3f:85:41:c5:87:56:84:8a
debug1: Host '[svn.qsolv-inc.com]:7822' is known and matches the RSA host key.
debug1: Found key in /home/thanigai/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Next authentication method: publickey
debug1: Offering DSA public key: thanigai@thanigaivelan
debug1: Server accepts key: pkalg ssh-dss blen 434
debug1: Authentication succeeded (publickey).
Authenticated to svn.qsolv-inc.com ([75.98.165.130]:7822).
debug1: channel 0: new [client-session]
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug1: Remote: Forced command.
debug1: Remote: Port forwarding disabled.
debug1: Remote: Pty allocation disabled.
debug1: Remote: Agent forwarding disabled.
debug1: Remote: X11 forwarding disabled.
debug1: Remote: Forced command.
debug1: Remote: Port forwarding disabled.
debug1: Remote: Pty allocation disabled.
debug1: Remote: Agent forwarding disabled.
debug1: Remote: X11 forwarding disabled.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
PTY allocation request failed on channel 0


**I had tried this **

rm -rf /dev/ptmx
mknod /dev/ptmx c 5 2
chmod 0666 /dev/ptmx
rm -rf /dev/pts
rm: cannot remove `/dev/pts/0': Operation not permitted
rm: cannot remove `/dev/pts/ptmx': Operation not permitted


Please Help me

Thanks

Thanigaivelan

---

