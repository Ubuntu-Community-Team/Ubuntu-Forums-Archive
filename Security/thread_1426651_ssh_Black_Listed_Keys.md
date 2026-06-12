---
title: "ssh Black Listed Keys"
date: 2010-03-10
forum: Security
---

### Post by R_Lopez on 2010-03-10
I cannot ssh to one server because ssh-vulnkey says my key is blacklisted.

I ran into this problem last year and regenerated my key and had to endure the pain until my new key was on the many servers upon which I work.
A server was replaced (new hardware) last April. I replaced my ssh key last May. I have been connecting to it without a password until today. The passwords on all servers were replaced last month. I had not been on that server since the new passwords. I went through the process to replace the key in known_hosts for that server. Then it started demanding a password.
I discovered my key is one of two that ssh-vulnkey lists as blacklisted. The person who has the other key was asked to test his ssh login. It is still working for him. He is the person who changed the root password on that system. He is blacklisted but he can ssh in as root. I am blacklisted and I can not ssh in as root without having to use a password. We do not want to use PermitBlacklistedKeys.

Any ideas why one blacklisted works but the other does not?

---

