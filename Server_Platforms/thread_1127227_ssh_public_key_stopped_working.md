---
title: "ssh public key stopped working"
date: 2009-04-16
forum: Server Platforms
---

### Post by eentonig on 2009-04-16
Yesterday, for some reason, public key authentication stopped working on my server.

Public key Authentication is enabled on my server, I created a public/private key pair, installed that on the server, ... But it doesn't work anymore. I re-enabled password authentication for now, but I want to solve this as fast as possible.


**sshd_config:**
[PHP]...
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
...
# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768
...
# Authentication:
LoginGraceTime 30
PermitRootLogin no
StrictModes yes
...
RSAAuthentication yes
PubkeyAuthentication yes
...
# Limit user access to me, myself and I
AllowUsers <user>
[/PHP]

**User keys info:**
[PHP]...
-rw-------  1 <user> <user> 1675 2009-04-16 12:11 id_rsa
...
-rw-r--r--  1 <user> <user>  628 2009-04-16 12:12 authorized_keys2
...[/PHP]


**Debug output:**

From the debugging output, it looks as if the client is sending his id_rsa info, but the server never responds to it. 
[PHP]...
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/<user>/.ssh/identity ((nil))
debug2: key: /home/<user>/.ssh/id_rsa (0xb8976f60)
debug2: key: /home/rfonteyn/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/<user>/.ssh/identity
debug3: no such identity: /home/<user>/.ssh/identity
debug1: Offering public key: /home/<user>/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/<user>/.ssh/id_dsa
debug3: no such identity: /home/<user>/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
<user>@localhost's password: [/PHP]

---

### Post by Xipher on 2009-04-18
What are the permissions on your .ssh directory? They should be read write and exectue only for the owner, and I would suggest removing the group and other read on the authorized_keys2 file as well just to be sure.

---

