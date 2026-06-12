---
title: "SSH issue with certificate authentication."
date: 2008-05-02
forum: Security
---

### Post by mmg-wm on 2008-05-02
Hopefully someone can help.
I have 3 systems (All running 6.06.2 server) that I'm trying to get to communicate using SSL certificates (srvg1, srvg2,srvb1).  I've create certs on all boxes using "ssh-keygen -t rsa" and saved the "id_rsa.pub" info into the "$USER/.ssh/authorized_keys" file on all boxes.  srvg1 and srvg2 can communicate fine in both directions.  srvb1 can ssh to both srvg1 and srvg2 without issue, but I can't initiate a ssh tunnel from srvg1 or srvg2 to srvb1 without being prompted for a password.  It will work with a password, but I need to schedule jobs without requiring the password.

Here are the steps I've taken so far:
*  update everything with apt-get
*  verify that file permissions on all servers are the same for .ssh directory and files(note, all users are using a login account "administrator").
*  make sure the /etc/ssh/ssh_confi and sshd_conf files are the same

I then ssh <IP ADDRESS> -vvv.  It looks like srvb1 isn't responding from the following snippet:

debug1: Trying private key: /home/administrator/.ssh/identity
debug3: no such identity: /home/administrator/.ssh/identity
debug1: Offering public key: /home/administrator/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password

compared to the following snippet when everything works:

debug1: Trying private key: /home/administrator/.ssh/identity
debug3: no such identity: /home/administrator/.ssh/identity
debug1: Offering public key: /home/administrator/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug2: input_userauth_pk_ok: fp f8:31:75:11:57:1e:2e:81:39:20:ab:51:2b:83:1b:d5
debug3: sign_and_send_pubkey
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).

Any ideas?  Thanks in advance for your help.  I'm a newbie and I've been banging my head trying to figure this one out.

Moe

---

### Post by lemming465 on 2008-05-02
Make sure that the home directory one level up from the .ssh directory isn't group writable.  If /etc/ssh/sshd_config has *StrictModes yes*, which it does by default, this can trip you up.  I've been bitten by that before myself.

If you need diagnostic messages from the sshd side, what you have to do is start an sshd in debug mode. If you don't mind a service interruption, the easiest way is```
sudo /etc/init.d/ssh stop
sudo sshd -d
# run the client test
sudo /etc/init.d/ssh start 
```

If you can't afford a service interruption, make a copy of /etc/ssh/sshd_config, change the Port specification from 22 to something else, say 2022, and do *sshd -d -f /the/alt/config/here*.  Be sure to specify the -p option on the client with the same alternate port number.

---

### Post by cdtech on 2008-05-12
You didn't mention the ssh-agent on the srvb1 server. Did you run it on srvb1? Just a thought.

---

