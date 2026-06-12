---
title: "setting up public key for passwordless ssh login"
date: 2010-09-08
forum: Security
---

### Post by cinohpa on 2010-09-08
Using 10.4

So I am really stumped. I can't get this to work on my machines.

So far I have:
1. created a key with ssh-keygen on the server to be logged in to
2. copied the .pub key to  my local machine
3. chmod 700 ~/.ssh on both machines
4. chomd 600 ~/.ssh/ic_rsa on the server, and on known_hosts on my local machine
5. added the .pub key to ~/known_hosts on my local machine

one thing that is driving me crazy is that my local machine doesn't have an "authorized_keys" file which is what everything is telling me I should append my .pub key to. The only thing that was in my .ssh folder was known_hosts, so I tried that. I also tried making an authorized_hosts file to no avail, changing permissions appropriatly on all files.

Should I/Can I reset ssh in some way? Is there are reason I don't have an authorized_keys file or is my known_hosts file my authorized_keys file?

Would it be better just to uninstall/reinstall ssh?

Thanks.

---

### Post by CharlesA on 2010-09-08
It's the other way around:

The public key goes in ~/.ssh/authorized_keys on the server.
The private key goes in ~/.ssh/id_rsa on the client

Comment out PasswordAuthentication in /etc/ssh/sshd_config on the server.

Restart ssh on the server and it should be good to go.

---

### Post by cinohpa on 2010-09-08
Great. Thanks a lot. Solved!

---

