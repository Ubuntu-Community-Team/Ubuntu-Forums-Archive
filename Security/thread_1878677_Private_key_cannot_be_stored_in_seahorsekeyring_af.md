---
title: "Private key cannot be stored in seahorse/keyring after gnome-keyring import keyfile"
date: 2011-11-10
forum: Security
---

### Post by doodel on 2011-11-10
Hello everyone,

I am trying to add another private key to my keyring/seahorse additionally to my private key under ~/.ssh. The intended result is to have it analog to Pageant under Windows. ssh-add is not an option, I think, because I would have to enter all the passphrases after each login/restart. Seahorse/the keyring unlocks the keyring (with the passphrase) automatically upon login.

I figured out, that I can add the key by typing ```
gnome-keyring import /path/to/keyfile
```. I then have to enter the passphrase (which is shown in clear text for some reason) and to select the user keys repository. This action in turn prompts me with the request to unlock the keyring to store this passphrase. (However, the keyring is unlocked automatically when logging into the system.)

The point is, that my password for unlocking the keyring is not accepted while I believe that it is correct (equal to my user password).

Is there any way to reset the password? Is there any way to somehow use Seahorse's "own keys" tab to add the private key there manually? The key somehow seems to be integrated into Seahorse's "other keys" tab, but I cannot remove it there or inspect its properties.

Do you have any suggestions?

---

