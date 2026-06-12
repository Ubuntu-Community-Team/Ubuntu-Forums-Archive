---
title: "repository gpg keys"
date: 2011-11-28
forum: Security
---

### Post by Ra'anan on 2011-11-28
hey,

i'd like to add repos from other versions of linux, obviously i need to add the correct keys for the servers.

is there a way to retrieve/append/modify or even copy .gpg files from other versions?

i've tried a couple but when I add the .gpg file in synaptic I get an invalid gpg error...

anyway tips or comments appreciated :)

---

### Post by BC59 on 2011-11-28
When you don't have a key, during the **sudo apt-get update** you have a similar message on terminal:

```
......The following signatures couldn't be verified because the public key is not available: NO_PUBKEY [COLOR="Blue"]xxxxxxx[/COLOR] 
```

Then on the terminal you copy the number of the key [COLOR="blue"]xxxxxxx[/COLOR] and execute:

```
gpg --keyserver subkeys.pgp.net --recv [COLOR="blue"]xxxxxxx[/COLOR]
```

```
gpg --export --armor [COLOR="blue"]xxxxxxx[/COLOR] | sudo apt-key add -
```

```
sudo apt-get update
```

---

