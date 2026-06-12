---
title: "gpg --export --armor uses different packets"
date: 2024-01-16
forum: Security
---

### Post by patfer99 on 2024-01-16
Hi Ubuntu community! I'm here with an issue which doesn't really have much support, at least from what I can find on internet: when I generate an rsa keypair, for example with this website [https://www.attogtech.com/pgp-key-generator/](https://www.attogtech.com/pgp-key-generator/) then import them in gpg and export them again with the options --export --armor I get a public pgp block which is different from the one I previously imported. The only thread on stackexchange I could find about this [https://superuser.com/questions/1610188/gpg-imported-and-exported-public-keys-do-not-match](https://superuser.com/questions/1610188/gpg-imported-and-exported-public-keys-do-not-match) explains it has to do with some old type packets which in gpg are set as default to ensure compatibility with older versions. I think I understand what's written in the thred but I have no idea how to change this setting to get gpg export the public key so that it's identical to the imported one.

Does anybody know how to do that? Or do you know of any other software to do this? Please help a fellow linux noob :)

---

