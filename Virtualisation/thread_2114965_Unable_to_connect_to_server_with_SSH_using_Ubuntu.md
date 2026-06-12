---
title: "Unable to connect to server with SSH using Ubuntu"
date: 2013-02-11
forum: Virtualisation
---

### Post by bosra1 on 2013-02-11
I am having trouble logging into a server with SSH. I have pasted a log of events below. Please can someone help me trouble shoot the problem. It appears that I am making some connection from the events log file.

ssh -vT [email]ubuntu@ec2-176-34-121-133.eu-west-1.compute.amazonaws.com[/email]

OpenSSH_6.0p1 Debian-3ubuntu1, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to ec2-176-34-121-133.eu-west-1.compute.amazonaws.com [176.34.121.133] port 22.
debug1: Connection established.
debug1: identity file /home/bosra/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/bosra/.ssh/id_rsa-cert type -1
debug1: identity file /home/bosra/.ssh/id_dsa type -1
debug1: identity file /home/bosra/.ssh/id_dsa-cert type -1
debug1: identity file /home/bosra/.ssh/id_ecdsa type -1
debug1: identity file /home/bosra/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.0p1 Debian-3ubuntu1
debug1: match: OpenSSH_6.0p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.0p1 Debian-3ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 59:c4:29:87:87:50:f7:eb:fb:ea:2a:39:8b:07:1a:33
debug1: Host 'ec2-176-34-121-133.eu-west-1.compute.amazonaws.com' is known and matches the ECDSA host key.
debug1: Found key in /home/bosra/.ssh/known_hosts:3
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/bosra/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/bosra/.ssh/id_dsa
debug1: Trying private key: /home/bosra/.ssh/id_ecdsa
debug1: No more authentication methods to try.
Permission denied (publickey).

---

### Post by markbl on 2013-02-11
Also look at /var/log/auth.log on the server for sshd messages.

Permission errors on the server side are common. Ensure your home dir is mode 755 and ~/.ssh is 700.

---

### Post by markbl on 2013-02-15
Oh yeah, and thanks for my help ... :|

---

### Post by Habitual on 2013-02-15
[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)

correct format might be:
```
 ssh -i /home/$user/.ssh/ec2_key_file ubuntu@ec2-176-34-121-133.eu-west-1.compute.amazonaws.com
```

---

