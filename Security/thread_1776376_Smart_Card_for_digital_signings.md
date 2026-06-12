---
title: "Smart Card for digital signings"
date: 2011-06-06
forum: Security
---

### Post by CyberPingU on 2011-06-06
Hello all,
since I have a Smart Card, I have:
- one private keyword that I cannot export into a file;
- one public keyword, that I can export;
- a x.509 certificate.

I would like to know if there's a software that would let me sign files with my own key signature or encrypt/decrypt them using the smart card. I saw the project smart sign  here --> [http://smartsign.sourceforge.net/](http://smartsign.sourceforge.net/) but I cannot compile it since I don't own winscard.h (it appears to be provided by the package pcsclite-dev that is not into repositories). Anyhow that project seems to be old.
I found gpgsm (that is the mime version of gpg) but it hasn't got a graphic user interface, something like the gpg's one called `kgpg`. It works flawlessly from command line (using the pkcs11 way) but I'd like to use something that provides a GUI.
Any advice?

---

