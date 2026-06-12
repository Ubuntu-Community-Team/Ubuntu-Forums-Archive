---
title: "SSH private key not used for login"
date: 2010-09-17
forum: Security
---

### Post by ygoe on 2010-09-17
Hi,

I am trying to access another Linux machine through SSH. Therefore I have created a new SSH key pair on the remote machine, added the public key to my authorized_key (there's already one in, but now I need another one with no passphrase) and copied the private key to my Ubuntu box into ~/.ssh/id_rsa. Now I tried to log into the Debian machine with 'ssh my.host.name' but then I'm asked for a password. Why doesn't ssh use the key to login?

I do have access to both machines but I need to transfer a lot of files now with scp and I'd like to use a key with no passphrase for this so I don't have to enter a password every time.

---

### Post by Bachstelze on 2010-09-17
Use ssh-agent. A key with no passphrase is asking for trouble.

---

### Post by ygoe on 2010-09-17
Argh... I switched to a root shell using 'sudo bash', but that meant that $HOME was still my non-privileged user's home directory. I need to do 'sudo -i bash' so that $HOME is changed. Before, I copied the key file to ~/.ssh = /home/me/.ssh and not /root/.ssh. Now it works as expected. Nevermind...

---

### Post by bodhi.zazen on 2010-09-17
This is what "ssh-copy-id" is for :

[http://manpages.ubuntu.com/manpages/lucid/en/man1/ssh-copy-id.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/ssh-copy-id.1.html)

---

