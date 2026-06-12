---
title: "Checking the signature for a package *before* I install it"
date: 2011-07-21
forum: Security
---

### Post by sneakyimp on 2011-07-21
Hello security folks.

I'm interested in GNU/Tiger as recommended by a security guru I know.  I did apt-cache search and located the package **tiger**:
```
tiger - Report system security vulnerabilities
```
I also checked the ubuntu web-based package search and found [tiger](http://packages.ubuntu.com/lucid/tiger) there too along with things like this [signed message](http://archive.ubuntu.com/ubuntu/pool/universe/t/tiger/tiger_3.2.2-11ubuntu1.dsc).

Using apt-cache policy, I see this package is **universe**.  I'd like to check the signature/cert/keys of this file before running apt-get install on it to see if it is acceptable given my current apt keys.  Can someone explain how to do this?

Also, what happens when I try to install a package using "apt-get install" and that package or one of its dependencies is:
* unsigned
* signed, but not by anyone whose key resides in my apt keyring?

Note that for the latter item, I don't care about any chain of trust, I want to know if the package is signed *directly* by one of my trusted keys.

---

### Post by stlsaint on 2011-07-21
As far as my knowledge goes a package will not even hit the ubuntu official repositories without a valid signature!! ;)

But for your toolkit see here: 
[http://pwet.fr/man/linux/administration_systeme/apt_secure](http://pwet.fr/man/linux/administration_systeme/apt_secure)

---

### Post by sneakyimp on 2011-07-22
Thanks for your response.  That's just the man page for apt-secure. I've tried to look up debsig-verify as instructed but no dice:
```

user@ubuntu-64:~$ man debsig-verify
No manual entry for debsig-verify

```

Personally, I'm a bit skeptical that apt-secure is working as everyone says it is, thanks to this line in every ubuntu user's dpkg configuration:
```

# Do not enable debsig-verify by default; since the distribution is not using
# embedded signatures, debsig-verify would reject all packages.
no-debsig

```

---

### Post by cariboo on 2011-07-22
if you don't have a package installed, you can't view the manpage. You can view it [here]("http://pwet.fr/man/linux/commandes/debsig_verify")

---

