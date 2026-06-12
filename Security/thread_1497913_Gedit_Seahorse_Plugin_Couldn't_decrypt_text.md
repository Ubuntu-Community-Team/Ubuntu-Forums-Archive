---
title: "Gedit Seahorse Plugin: Couldn't decrypt text"
date: 2010-05-31
forum: Security
---

### Post by 1awesomeguy on 2010-05-31
Using Ubuntu 10.04, gedit 2.30.2, seahorse 2.30.0. gedit-plugins and seahorse-plugins are installed.


I get the following message when trying to decrypt a text file using Gedit:

```
Couldn't decrypt text

Decryption failed. You probably do not have the decryption key.
```

This particular file was created using the same Gedit plugin on a previous Ubuntu install. The correct key has been imported and signed. Gedit does not seem to recognize the key. Is this a bug? Is there any way I can retrieve my data? Seahorse is working fine decrypting PGP files, but this content is plain text (TXT file) content that looks like this:

```
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.9 (GNU/Linux)

[encrypted content]

-----END PGP MESSAGE-----

```

Thanks for your help!

---

### Post by FuturePilot on 2010-05-31
Is this your own key you're trying to use? If you exported your key from your previous Ubuntu install using Seahorse, note that it does not export your private key.

---

### Post by 1awesomeguy on 2010-06-01
> **FuturePilot said:**
> Is this your own key you're trying to use? If you exported your key from your previous Ubuntu install using Seahorse, note that it does not export your private key.

Sorry, I am not sure what you mean. Seahorse is probably the most confusing encryption program I have ever needed to deal with.

I did export my key using Seahorse. It was a key created by me in a previous Ubuntu install. I would think exporting the key would preserve my key in it's entirety... I remember being able to decrypt content using this same key on a different computer... All I want to do is decrypt my content.

---

