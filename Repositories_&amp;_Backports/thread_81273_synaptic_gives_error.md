---
title: "synaptic gives error"
date: 2005-10-24
forum: Repositories &amp; Backports
---

### Post by krcm on 2005-10-24
hello,
I get the following errormessage in synaptic and when I try to reload (or update, in dutch it says herladen):

[http://dinton.no-ip.org/dists/kubuntu/main/binary-i386/Packages.gz:](http://dinton.no-ip.org/dists/kubuntu/main/binary-i386/Packages.gz:) 404 Not Found
[http://dinton.no-ip.org/dists/kubuntu/main/source/Sources.gz:](http://dinton.no-ip.org/dists/kubuntu/main/source/Sources.gz:) 404 Not Found
[http://sh.nu/~crimsun/./Packages.gz:](http://sh.nu/~crimsun/./Packages.gz:) 404 Not Found [IP: 216.239.132.100 80]
[ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/Packages.gz:](ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/Packages.gz:) Kan bestand niet ophalen; bericht van server: Failed to open file.
[ftp://ftp2.caliu.info/backports/dists/hoary-backports/universe/binary-i386/Packages.gz:](ftp://ftp2.caliu.info/backports/dists/hoary-backports/universe/binary-i386/Packages.gz:) Kan bestand niet ophalen; bericht van server: Failed to open file.


and afterwards this error:

W: GPG error: [http://ftp.rz.tu-bs.de](http://ftp.rz.tu-bs.de) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

Does anybody know what I can do about his problem?
Can anyone give me a link to a howto on this topic. I'd like to know about the list(s) where synaptic gets thes updates from and how to put more sites in it.
I know of one list but it seems to me that there have to be more.

Thx
An

---

### Post by TristanMike on 2005-10-26
Well, it appears as though those first errors are addresses that are no longer in use, so comment them out, uncheck the boxes, do what you need to, to remove those particular addresses.

For the second issue,```
sudo rm /var/lib/apt/lists/*
```you will get some cannot delete directory error, no sweat. Wait about 10 minutes and try again.

Hope this helps.

---

### Post by ecobuntu on 2005-10-27
[QUOTE=TristanMike]Well, it appears as though those first errors are addresses that are no longer in use, so comment them out, uncheck the boxes, do what you need to, to remove those particular addresses.

For the second issue,```
sudo rm /var/lib/apt/lists/*
```you will get some cannot delete directory error, no sweat. Wait about 10 minutes and try again.

Hope this helps.[/QUOTE]

Yeah just retry 
sudo apt-get update
sudo apt-get upgrade

after running that rm /var/lib/apt/lists/* command

---

### Post by krcm on 2005-10-28
Hi,
Thx for your reaction.
I tried what you suggested, didn't change anything though.

there seem to be public keys missing: 
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
How can I fix this?

Also I forgot to copy the parts of the list that came from the ubuntu cdrom, how can I put these back?
I've put the line back into the list and did update withe the cdrom in place but that didn't work.

Grtz
An

---

### Post by dcstar on 2005-10-30
[QUOTE=krcm]Hi,
Thx for your reaction.
I tried what you suggested, didn't change anything though.

there seem to be public keys missing:
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
How can I fix this?
.......[/QUOTE]

You can't, these aren't really "errors", just warning messages that the particular repository does not have a Public Key.

This is just a security function to ensure that the repository you **think** you are connecting to is verified with PKI, it just happens that the server that these particular packages are on doesn't have this security feature set up - feel free to ignore them, I do!

---

### Post by TristanMike on 2005-10-30
[QUOTE=krcm]Hi,
Thx for your reaction.
I tried what you suggested, didn't change anything though.

there seem to be public keys missing: 
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
How can I fix this?

Also I forgot to copy the parts of the list that came from the ubuntu cdrom, how can I put these back?
I've put the line back into the list and did update withe the cdrom in place but that didn't work.

Grtz
An[/QUOTE]I didn't notice before the addressses, d'oh! Why are you even using those? It's not a good idea to have unofficial repo's, they can really bork your install. If you do use unoffical repo's for something, generally you just want to grab what you want and deactivate it again. I suspect they are for the w32codecs. If it is for the codecs, Hoary can be found [here](http://giannaros.org/public/hoarydebs/) and Breezy [here](http://giannaros.org/public/breezydebs/). And a ```
sudo dpkg -i filename.deb
```is all you need to to install it. Otherwise, it's not a good idea to use these particular addresses.

---

