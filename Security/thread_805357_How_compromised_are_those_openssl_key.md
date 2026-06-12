---
title: "How compromised are those openssl key?"
date: 2008-05-23
forum: Security
---

### Post by Biochem on 2008-05-23
I'm not necesseraly interested in the technicalities but on a more practical level.

Like how long will it take to brake a compromised openssl key on todays hardware?

---

### Post by Monicker on 2008-05-23
This might help to answer your question:  [http://www.metasploit.com/users/hdm/tools/debian-openssl/]("http://www.metasploit.com/users/hdm/tools/debian-openssl/")


[I]Q: How long does it take a crack a SSH user account using these keys?
A: This depends on the speed of the network and the configuration of the SSH server. It should be possible to try all 32,767 keys of both DSA-1024 and RSA-2048 within a couple hours, but be careful of anti-brute-force scripts on the target server.[/I]

EDIT: Though the above is specifically about ssh, I believe the ssl piece was also using the same relatively small key space because of the PRNG flaw.

---

### Post by Biochem on 2008-05-23
Hours! Wow i't worse thant I thought

---

