---
title: "SSH, VNC and chipered home folder"
date: 2011-03-10
forum: Security
---

### Post by erotavlas on 2011-03-10
Hi,

I'm try to setting up a SSH tunnel to secury my VNC connection between client (windows or ubuntu) and server ubuntu 10.10 32 bit with ciphered home folder.
I have followed this procedure:

```
mkdir -p ~/.ssh
chmod 700 ~./ssh
cd ~/.ssh
ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/USER/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/USER/.ssh/id_rsa.
Your public key has been saved in /home/USER/.ssh/id_rsa.pub.
The key fingerprint is:
/home/user/.ssh/
cat ~/.ssh/id.pub >> authorized_keys
chmod 600 authorized_keys

backup
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.working
sudo nano /etc/ssh/sshd_config from

port 22 to

port 59000 
 
 
from
PermitRootLogin yes to
PermitRootLogin no
 
from #PasswordAuthentication yes
to 
PasswordAuthentication no  
# sudo /etc/init.d/ssh restart 

```I have configured remote desktop (vino).
Now I have the two following problems:
on ubuntu if I try to connect to server through SSH I get > Permission denied (publickey)on windows I can't convert with puttygen the key id_rsa to putty format. I get the > Couldn't load private key (chipers other than DES-EDE3-CBC not supported)How can I solve them?

Thank you

---

### Post by bodhi.zazen on 2011-03-10
You will have to specify the new port and key when you ssh in from Ubuntu.

From Windows you need to import the key to putty.

[http://bodhizazen.net/Tutorials/SSH_keys#PuTTY](http://bodhizazen.net/Tutorials/SSH_keys#PuTTY)

If it is not working, post the command you are using.

```
ssh -vv user@server
```

---

### Post by erotavlas on 2011-03-14
Hi,
I have restored the original parameters in file /etc/ssh/sshd_config and now all work. I can connect to the ssh server from the server itself

ssh -vv user@server - port 443



One question: should be the same keys inside the following folder and that inside /home/user/.ssh ?
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

Are they used only in SSH 2?

An other question related to the previous one: if I try sudo sshd -t I get no message while if I try sshd -t I get
```
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_ke
```

---

