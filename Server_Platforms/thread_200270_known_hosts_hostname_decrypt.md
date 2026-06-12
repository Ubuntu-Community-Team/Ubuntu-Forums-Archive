---
title: "known_hosts hostname decrypt?"
date: 2006-06-20
forum: Server Platforms
---

### Post by saaz on 2006-06-20
Anyone know how to decrypt the hostname for an entry in the ~/.ssh/known_hosts file to actually make it usable by a human? I'd like to be able to know which key goes with which host (crazy idea, I know). ](*,) 

Thanks

---

### Post by Azrael on 2006-06-20
If you set *HashKnownHosts* to *no* in /etc/ssh/ssh_config, you should be able to identify new hosts by hostname or IP address. I don't know if that will help you with already hashed entries though.

---

### Post by saaz on 2006-06-20
[QUOTE=Azrael]If you set *HashKnownHosts* to *no* in /etc/ssh/ssh_config, you should be able to identify new hosts by hostname or IP address. I don't know if that will help you with already hashed entries though.[/QUOTE]


Thanks! :D  That did the trick. It doesn't work for the existing entries but I just deleted those and reconnected to each server to recreate the entries.

---

