---
title: "Linode VPS vs. EC2"
date: 2013-06-06
forum: Virtualisation
---

### Post by jonathanhayward on 2013-06-06
I am on a Linode VPS node and have been trying to migrate to EC2. I've experienced a couple of issues:

[LIST=1]
[*]The server does not have enough space to store the image (N.B. That was with logs included; I tried to slim down the tarball size; see #2).
[*]I stopped the server, and when it restarted it had a different IP, and I couldn't log in and see if the tarball was small enough. I tried to generate and download a fresh keypair, but got "Permission denied (publickey)" when I tried to shell in with the new key.
[*]
[/LIST]
I wanted to check in and ask a sanity check about Linode vs. EC2. Is this a red flag about EC2, or are these just growing pains in a transition? In a product comparison between a Linode VPS and EC2, which would you recommend?

Thanks for any advice,

---

