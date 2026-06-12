---
title: "Apache Installation Cook Book?"
date: 2023-10-14
forum: Security
---

### Post by congleal2 on 2023-10-14
I've been running Ubuntu with apache2 for many years without issues, until recently I have been hacked on 3 separate occasions where the hacker was able to get my password, make changes to web pages. He obviously was playing on my lack of knowledge from security aspect. I quickly took the server off the network, changed passwords, check the rule set of UFW and he was able to get in again. I thought I had .htaccess configured and check for file permissions, and was using ssl.
  - I connect to the server via ssh public key. (I changed port number in the apache2.conf but later discovered the updated version of Ubuntu disregards that command in that particular file)
  - I submitted changes to the website via ssh public key and rsync[COLOR=#0000cd] command to update the changes, not knowing that file permissions may be changed in using rsync.

I have since installed a fresh version of Ubuntu Server with ssh and looking help for a secure way of installing and configuring apache2 to avoid being hacked yet again. Its not an important or controversial site that would draw attention. I'm a disable vet; 70 years old; and just completed surgery for mouth cancer in March this year. I enjoy http work but am exhausted trying to fight this hacker. Help[/COLOR]

---

