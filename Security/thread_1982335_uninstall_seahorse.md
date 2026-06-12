---
title: "uninstall seahorse?"
date: 2012-05-18
forum: Security
---

### Post by ottosykora on 2012-05-18
I found  out that this seahorse does few things, but most of them are too bad and in fact very big security issue.

Tried to unistall it, but it wants also unistall ubuntu dektop with it.

What will happen when I try to unistall seahorse?


Seahorse attempts to manage all passphrase handling in such a way, that it is almost impossible to use it. There are no settings apperently for it, one can try to set the time to 1 minute for caching in the passphrase entry dialog, but this seems to have no effect. There is no way to clear the cache either.
With the seahorse present, also thunderbird can not be used properly, as the gpg control is taken from enigmail to seahorse.

---

### Post by ottosykora on 2012-05-19
ok, I have uninstalled seahorse, gpg-agent and the deamon and parts associated with the seahorse.

No results, something is still caching the passphrase.
When entering gpg passphrase, i can set the time out to 1 minute (zero is not possible!!??) but this also seems not to have any action. 
Enigmail in Thunderbird tells me, that I am using gpg-agent or similar software to control the passphrase caching and it has therefore no way of control.

Does someone know what component does cache the passphrase in ubuntu 12.04?

---

### Post by ottosykora on 2012-05-19
here few other thigs I found out


the passphrase caching is done also by other componenets.
In case of gpg1.4 it is gpgv which can not be unistalled in fact, as it seems to be very much integrated into the system and by the system connected with the gpg. 
The caching can not be switched off however.

In case of gpg2 the gpg-agent is installed and here there is some controll over caching, in fact it can be switched off.

However seahors-deamon does also catch the passphrase and this can not be controlled as there seem to be no settings or config for that, at least I did not find any.
The encrypt/decrypt part of the seahorse can not be installed without the deamon. As the encrypt decrypt function does not work , it can be well unistalled.
If the seahorse-deamon is not present, the chaching can be set to minimum (1min) with gpgv or even switched off in case of gpg-agent.


Anyone with some experience on those componenets?
What ways are there to controll the caching of the passphrase?


Why does the seahorse encryption choose just arbitrary keys from the public key ring and not the one selected? Is there any workarounds?

---

