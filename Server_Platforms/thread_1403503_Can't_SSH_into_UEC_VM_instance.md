---
title: "Can't SSH into UEC VM instance"
date: 2010-02-10
forum: Server Platforms
---

### Post by john-boy on 2010-02-10
I am running Ubuntu Enterprise Cloud on two PCs, one as Controller, one as a node. I have downloaded two Ubuntu virtual machine images from the Ubuntu Enterprise Cloud Store and can successfully start instances of them with:
euca-run-instances -k mykey emi-XXXXXXXX -t c1.medium

If I run this command I can see the instance is running:
watch -n5 euca-describe-instances

I can ping the IP address of the VM instance from my Controller but I can't make an SSH connection to it. I'm following the instructions @ [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)
so I have tried connecting with:
ssh -i ~/.euca/mykey.priv ubuntu@192.168.1.250

The result is:
Permission denied (publickey).

Can anyone offer any advice on how to resolve this or any pointers as to what I should look at to resolve the problem? Its really frustrating because I'm almost there!
Thanks all.

If I try adding -v to the ssh command I get:
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.250 [192.168.1.250] port 22.
debug1: Connection established.
debug1: identity file /home/cloud/.euca/mykey.priv type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.1.250' is known and matches the RSA host key.
debug1: Found key in /home/cloud/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/cloud/.euca/mykey.priv
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).

---

### Post by stlsaint on 2010-02-10
Are you sure that you have the key in your authorized_files config on the server side?

---

### Post by dragos2 on 2010-02-10
Check the key's permissions. It might be the problem.

---

### Post by john-boy on 2010-02-11
Thank you both very much for replying. I checked permissions and all seemed OK. I then reinstalled both Controller and Node and I can now make an SSH connection to a virtual machine instance.

The instructions on the UEC 'How To' page are straightforward but perhaps I still managed to screw it up first time...

---

### Post by ashishrevar on 2011-03-17
Hi john-boy,

Can you please explain how to log into instances? Reinstalling controllers doesn't seems to be a good solution, as I have to implement all it again.

Is there any permission kind of issues there with mykey.priv?

---

