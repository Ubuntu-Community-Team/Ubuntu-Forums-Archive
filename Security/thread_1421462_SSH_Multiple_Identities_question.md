---
title: "SSH Multiple Identities question?"
date: 2010-03-04
forum: Security
---

### Post by bradcan on 2010-03-04
Why I can't use multiple identities!

I have two sets of RSA key files:
id_rsa, id_rsa.pub
test and test.pub

I want two different SSH logins to the same server, so I create the following in ~/.ssh/config

host H
 hostname xxx
 user me
 IdentityFile ~/.ssh/id_rsa

host G
 hostname xxx
 user me
 IdentityFile ~/.ssh/test

Then in my server account on xxx in ~/.ssh/authorized_keys I have:

ssh-rsa AAA.............................==id_rsa
command "ssh me@yyy" ssh-rsa AAA......................==test

The idea is to use:
ssh H
ssh G
The latter as a transparent gateway to yyy through xxx.

Now this works just fine, but I have to remove either id_rsa or test! Why?

Can I user .ssh/config like this?

TIA

---

### Post by bradcan on 2010-03-05
Here I go again answering my own questions. ;)

If I kill gnome-keyring-d:
ps -A | grep key
 5472 ?        00:00:00 gnome-keyring-d
kill 5472

start ssh-agent:
eval `ssh-agent`                 << NOTE the back ticks

then ssh-add my keys:
ssh-add ~/.ssh/id_rsa
ssh-add ~/.ssh/test

Now: ssh H and ssh G work correctly.

The big question now is how to stop gnome-keyring-d running? This question has be asked a thousand times and probably never answered adequately.

Well this seems to work:
 Un-check ssh in gconf-editor - apps, gnome-keyring, daemon-components.
 RENAME id_rsa and id_rsa.pub

And behold ssh-add works correctly:
ssh-add -D
All identities removed.
ssh-add -l
The agent has no identities.           << CORRECT
ssh-add .ssh/renamed_rsa
ssh-add .ssk/test

Presumably id_rsa if it exists is force-ably re-loaded by gnome-keyring-d or seahorse!

---

