---
title: "Connect to Amazon ec2 with ssh"
date: 2011-06-08
forum: Server Platforms
---

### Post by DSn0wMan on 2011-06-08
I am unable to connect to an Amazon ec2 instance with ssh. The ssh connection always hangs with the following output. 

[email]grayjo@asg-jp95yc1:~/.ec[/email]2$ ssh -vvv -i ~/.ec2/ec2_key.pem [email]ubuntu@ec2-50-16-83-229.compute-1.amazonaws.com[/email]
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ec2-50-16-83-229.compute-1.amazonaws.com [50.16.83.229] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/grayjo/.ec2/ec2_key.pem" as a RSA1 public key
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/grayjo/.ec2/ec2_key.pem type -1
debug1: identity file /home/grayjo/.ec2/ec2_key.pem-cert type -1


I am not sure what incorrect RSA identifier means, and I am also not sure why it's trying to load my private key as a public key.

debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/grayjo/.ec2/ec2_key.pem" as a RSA1 public key


Edit: Looks like this is related to port 22 inbound connections being blocked on our network

---

