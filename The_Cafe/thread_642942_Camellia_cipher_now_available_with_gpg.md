---
title: "Camellia cipher now available with gpg"
date: 2007-12-17
forum: The Cafe
---

### Post by kevdog on 2007-12-17
Camelia cipher now available for testing and use with gpg.  Ive managed to compile and patch the gpg v 1.45 sources. Currently working on getting this running with the svn 1.4 branch.

Info on camellia can be found here:
[http://en.wikipedia.org/wiki/Camellia_(cipher](http://en.wikipedia.org/wiki/Camellia_(cipher))
[http://www.is.titech.ac.jp/~yanagis0/text/camellia-e.html](http://www.is.titech.ac.jp/~yanagis0/text/camellia-e.html)

SVN sources have been compiled in the cygwin environment -- 

```

$ gpg --version
gpg (GnuPG) 1.4.8rc2
NOTE: THIS IS A DEVELOPMENT VERSION!
It is only intended for test purposes and should NOT be
used in a production environment or with production keys!
Copyright (C) 2007 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Home: ~/.gnupg
Supported algorithms:
Pubkey: RSA, RSA-E, RSA-S, ELG-E, DSA
Cipher: 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH, CAMELLIA128,
        CAMELLIA256
Hash: MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2

```

---

