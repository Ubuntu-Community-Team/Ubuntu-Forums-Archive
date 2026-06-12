---
title: "LUKS: Update key using hash only?"
date: 2019-02-06
forum: Security
---

### Post by dclabaut on 2019-02-06
Is it possible to change a LUKS passphrase by giving cryptsetup only a hash of said passphrase?
The goal is to set a recovery passphrase on each of my devices using Ansible, without the passphrase actually appearing in the Git repo.
Ansible Vault is not really an option, as I would need a passphrase to decrypt the vault, so I might as well ask for the LUKS passphrase with a prompt.
Thanks

---

