---
title: "How Do I make a Key Revocation Certificate in Seahorse?"
date: 2008-12-07
forum: Security
---

### Post by carl393 on 2008-12-07
Does anyone know how to make a key revocation certificate in seahorse 2.24?

---

### Post by tubbygweilo on 2008-12-07
carl393,
I also looked and could not find a way via Seahorse so all I can offer is [gnupg revocation ]("http://www.gnupg.org/gph/en/manual.html#REVOCATION")
which shows ```
alice% gpg --output revoke.asc --gen-revoke mykey 
```

and being a Mozilla Thundebird Enigmail user I rely upon the key manipulation functions within the application to look after my keys, sorry I can't offer help via Seahorse.

---

### Post by carl393 on 2008-12-07
i managed to get rid of it before you posted the answer but it's very similar, for anyone having the same problem, go to this website it explains how to do it!

[http://fedoraproject.org/wiki/DocsProject/UsingGpg/CreatingKeys#Generating_a_Revocation_Certificate](http://fedoraproject.org/wiki/DocsProject/UsingGpg/CreatingKeys#Generating_a_Revocation_Certificate)

after you generate the certificate you have to import the certificate, and then upload the certificate to the keyserver so that it actually revokes the key.

---

