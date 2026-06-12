---
title: "Native SSH to Ubuntu vs Putty to Ubuntu"
date: 2014-11-15
forum: Security
---

### Post by project722 on 2014-11-15
qq here - I have setup both putty and a native Ubuntu SSH client to access another Ubuntu machine (acting as server) via ssh. I am using the same public/private keys for both but when I log in with putty it goes right in using the keys. When I use the native ssh in the Ubuntu client I can get in but it prompts for the private key passphrase. I am concerned that someone can bruteforce out the private key password then get in. Should I be concerned about this or would an attacker need to reverse engineer the private key to get the private key password? 

Also, how can I setup the native client to just get me in without asking for the private key password?

---

### Post by ian-weisser on 2014-11-15
Your local machine is prompting for the passphrase, not the remote machine. The remote machine should know your public key only.

If you are worried about someone bruteforcing your local machine, then consider locking it out of reach when you are not using it.

---

### Post by HermanAB on 2014-11-16
To answer you actual question:
When you create the public/private key pair wit ssh-keygen, press Enter when prompted for a passphrase.  You will then have keys with no passphrase for the private key and won't get a prompt when you use it.

---

