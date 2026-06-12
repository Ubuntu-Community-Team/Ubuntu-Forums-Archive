---
title: "ssh -i public-key on same box still asking for password"
date: 2011-06-18
forum: Server Platforms
---

### Post by pgroarke on 2011-06-18
Hi Guys,
           I'm on Natty Narwhal and wanted to play with ssh but I can't seem to get ssh to work without having to specify a password.
I've installed openssh-server. 
I've generated a public/private key pair:

ssh-keygen

I can see my id_rsa and id_rsa.pub and known_hosts.

am logged in as user pgroarke and simply trying to run ssh on the same box.
Regardless of whether I specify either localhost or hostname I still get asked for a password:

ssh -i ~/.ssh/id_rsa.pub  pgroarke@spock date
pgroarke@spock's password:

Here is the relevant contents of my /var/log/auth:
Jun 18 16:21:37 spock sshd[30357]: last message repeated 2 times
Jun 18 16:21:37 spock sshd[30391]: Set /proc/self/oom_score_adj to 0
Jun 18 16:21:37 spock sshd[30391]: Connection from ::1 port 34207
Jun 18 16:21:37 spock sshd[30391]: Failed publickey for pgroarke from ::1 port 34207 ssh2

any help appreciated
Rgds
Peter

---

### Post by Lars Noodén on 2011-06-18
It is the private key, not the public key that you need to use to authenticate.  The private key is in your folder and the public key is in **authorized_keys**

```

[s]ssh -i ~/.ssh/id_rsa.pub pgroarke@spock date[/s]
ssh -i ~/.ssh/id_rsa pgroarke@spock date

```

---

### Post by pgroarke on 2011-06-18
Hi Lars,
              That gave the same error. Maybe its the IP version

ssh -i ~/.ssh/id_rsa  pgroarke@localhost date
pgroarke@localhost's password: 

Jun 18 16:57:51 spock sshd[30748]: Set /proc/self/oom_score_adj to 0
Jun 18 16:57:51 spock sshd[30748]: Connection from ::1 port 25055
Jun 18 16:57:51 spock sshd[30748]: Failed publickey for pgroarke from ::1 port 25055 ssh2

Rgds
Peter

---

### Post by pgroarke on 2011-06-18
Oops I hadn't copied the public key to the authorized_keys file

cp .ssh/id_rsa.pub .ssh/authorized_keys

Now I'm getting "Found matching RSA key" in the auth.log  but still being prompted for password:

Jun 18 17:18:49 spock sshd[31515]: Set /proc/self/oom_score_adj to 0
Jun 18 17:18:49 spock sshd[31515]: Connection from ::1 port 23292
Jun 18 17:18:49 spock sshd[31515]: Found matching RSA key: b6:12:00:bc:12:3f:ae:a8:34:aa:24:94:38:de:f7:5b


 ssh -i ~/.ssh/id_rsa  pgroarke@spock date
Agent admitted failure to sign using the key.
pgroarke@spock's password: 
Sat Jun 18 17:27:37 IST 2011

---

### Post by pgroarke on 2011-06-18
Logged out and in again and itw working now.

Tack for hjalpen Lars

-Peter

---

