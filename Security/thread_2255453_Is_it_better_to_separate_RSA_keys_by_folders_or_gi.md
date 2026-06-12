---
title: "Is it better to separate RSA keys by folders or give each key a special name?"
date: 2014-12-05
forum: Security
---

### Post by stevenmw on 2014-12-05
I've moved away from Debian and over to Ubuntu Server 14.04 LTS. Since my server is a small personal server that only I access I've never taken security seriously. I decided it was time I started to learn about getting my SSH secure.

I've been reading all about key pairs. From what I've read you can change the name of a key pair from id_rsa, but since id is what is the key name that is looked for by default you must specify the name and host in a config file.

Reading through documentation I've noticed what a lot of people do is they keep the key named id_rsa, and then they create a separate directory for each of the keys. Then in their config file they point to each key individually.

What I'm wondering is, if I'm going to have to point to the key no matter what, why not just give each key its own specific name but not create an individual directory for each key? If I were to create directories for each key I would only have one file in every one of those directories.

Is it considered poor practice, or would it hurt anything to just have /home/stevenmw/.ssh/ with multiple private keys each having their own name with a config file saying which to use for which connection?

I just don't see the point of creating multiple folders only to put one file in each. Especially if I only plan to have around 4 private keys in the .ssh directory.

---

### Post by TheFu on 2014-12-05
Maybe I'm just stupid, but why would any userid have more than 1 key per server?
For ssh, you push the public key to the remote system ... which is fine (use the ssh-copy-id tool).  They remote connections are easier, secure, nice.

Don't make it any harder than it needs to be.

Also - on each server do not allow password-based authentication, and use either fail2ban or denyhosts to block brute-force ssh attacks. I've had to modify the fail2ban ssh-jail config to get it working on 14.04, but on all prior LTS releases, it worked fine out of the box.  I don't use non-LTS releases. Just not worth my time.

---

