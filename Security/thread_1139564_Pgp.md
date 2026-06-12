---
title: "Pgp"
date: 2009-04-27
forum: Security
---

### Post by bbourdet on 2009-04-27
Hello All -

I have recently switched over to Ubuntu and have really been enjoying myself. :)

I do have a problem though. I created a PGP key in windows and now I am not sure how to bring that same key over to Ubuntu. I have exported the public key, and my private key. How do I bring them to Ubuntu?


Also, on a side note. Does anyone know of anything in linux that would encrypt my browsing and allow me to encrypt local drives and what not?

Thanks so much!

Tark

---

### Post by Nepherte on 2009-04-27
To import your gpg keys, try seahorse. I believe it's installed by default.

---

### Post by bbourdet on 2009-04-27
Ok, so I imported it now. Now when I try to send a message I get this:

Could not create message.

Because "gpg: skipped "-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.6 (GNU/Linux)

mQGiBEn09mARBACe1VK0p+No0nOEqXzCT63JJnai17fWgMdw1TV82ET0uNsPk/e5
0DnaTtL5O2fl0fIjfoZyyv0M0kIRwdy8G8ncx7ZzjuPv6QCFlFYZJ7P9SxrzCdRq
Mezw01ajWAn0HBRKIGvYR6+WLwN7/oIGxHCCHi1R48iJxG4xY2QGMMzdZwCgvyFK
Pf8UF3kssHLyZwqkHONwBxMD/0bFrY0QpowTB8ITymgQrYaPqFay580LaxGA/6zj
TlCaRuj0niwyjdh14ssomu8d2rag3m/2Zf9NxNzplcYJOB+VGne74so8+V7qVigo
qElOCCweT2TfEJabd34OqbzLgL4Srlwt+Ho77wS60gsvTZM6SYbA62Y6LBeHjk1H
rpCNA/4/IFA60DCCyj+1QpJufVn+eW1NnXVvUHBH9Uyki35jS7tu36YurQVlUUcA
CXN+jfuHNDCkyzULfEw6G9QEze76REKOOKeuwHmwiMG+4nDj2m6WCE9dhWhOFg0Y
Ncxs4QQZHi4hq6Pe6XgK8tx7rnl7GZl34Ii3vY7FTDZu7QzlrbQiQnJpYW4gQm91
cmRldCA8YmJvdXJkZXRAZ21haWwuY29tPohgBBMRAgAgBQJJ9PZgAhsDBgsJCAcD
AgQVAggDBBYCAwECHgECF4AACgkQeYOSV4ZumWxXsgCgh7tOHCb4lG4WMI8UGHX4
GmIQKo4An11qWDhMu8Nlfto5AXsomXbBgeFTuQINBEn09mAQCADsY/v4tGfsdXBn
0xWXiQB1KMLdBGDqhXSetGkOSJHNc8+nkDyO7SNaoLi5rrVJ43YWkmEf3J50S4g2
quyvGH9377PRAhkDj8Mq20K43xg8kVJPPeV1m+sMsaP0Qex3VQqJ5Aw6PKuG0zOc
bK/CTeD1yq8blubtjMt3jf+pMNUc98Rx1ibEP7pYDmtNcqc7CMwvBOsYYf92jm7k
pOyHH30GTBYHe/stZlaAjoGDQudtp0l4Msl5pb75mEopOmYXGU4CxlrbNfTSwpVh
lBEh1NMrSODZWrpSoR9n0u0Jz60kbBKP+mAS2JL6e2HAtmS7D12uZ0O/LwruOQOa
7WUqd/FPAAQNCADTDeH2PB3qOBPqC1yYwLyvCqrsiBZ5qoorCeJi4ZewjuaUwZPD
Jk4yOVQ3HQKXWhBIaPOoaFP2FvlCNDowrcng0mkHHfhgzGE777vXErFcrUbvts9p
4deonZjIVe+EYOcSNoR0JeMPWaJ5p9OncToLUexJsU7V6tZFf5Kown6tW/3WEi1S
4nOEa0JjXzyk69pqxY+lkeR588UWUEg++mz7vl2+uT4phI7MpKpCxPMVM5TcTs2I
ZbDCQ5ZqvMCjhJN7mWhI9M2PMsCcZhCt4z5wgJSBbV70xU1Bytqvo680VQZNd3Wc
2ywu/uA+QiEUe22XFcS6k/6bK/xpJ12Lk48niEkEGBECAAkFAkn09mACGwwACgkQ
eYOSV4ZumWxtdQCfauqH6TJ96az+PxnpUFkTXVQ0FLkAnR9DMlh11+v9vyFsoK1X
QEVxWjl1
=Z6t2
-----END PGP PUBLIC KEY BLOCK-----
": secret key not available
gpg: signing failed: secret key not available
", you may need to select different mail options.

What now?

---

### Post by stimpack on 2009-04-27
sounds like you only imported the public keys and not the secret ones?

```
gpg --allow-secret-key-import --import ./secretkey.asc
gpg --import ./publickey.asc
```

Though I never need to import the public key as the secret seems to contain it as well.

beyond that I only know Kgpg not seahorse.

---

### Post by kevdog on 2009-04-27
Are you using gpg or pgp?  Second you can recreate the public key from the private key (as stated above).

---

### Post by jflaker on 2009-04-27
> **kevdog said:**
> Are you using gpg or pgp?  Second you can recreate the public key from the private key (as stated above).

The public key is what you would give to others and therefore the secret key can not be created from a public key -- that would circumvent the idea of PGP/GPG security.

If your PGP version was 9 or above, you may have issues with importing your secret key as some proprietary algorithms are in pgp so you would have compatibility issues.

Worst case scenario, you may need to revoke your current pgp key and create a new key under gpg....Not sure if that would be feasible for you depending on how many people have your current pgp public key.

---

### Post by bbourdet on 2009-04-27
Well I still could not get that key to work.

So I created a new key in Seahorse, and everything looked fine, I open evolution mail and went into the properties and put my public key in the box.

It sends mail now. But I am not sure that it is working. I sent an email to the PGP test bot at adele - en at g n u p p dot dee eee

She responds with a encrypted message that I cannot read. Seems like it is not working.

Any thoughts?

---

