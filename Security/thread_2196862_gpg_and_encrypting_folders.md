---
title: "gpg and encrypting folders"
date: 2013-12-31
forum: Security
---

### Post by riceroma on 2013-12-31
Hello. All

Firstly, safe New year! Now can someone in the name of New years ;-) Tell me how do you encrypt a folder and all of its contents? Using gpg command line. Please I know you can use right click if one has seahorse installed. I am new to linux and ubuntu, so I'm trying as much as possible to stay using the command line.


Thanks

---

### Post by r3dd on 2014-01-01
```

sudo apt-get install signing-party

```

Encrypt
```

gpgdir -e <directory> -K <keyid>
```Decrypt```

gpgdir -d <directory> -K <keyid>
```

Check out the man page for information on more options and whatnot.
[http://manpages.ubuntu.com/manpages/saucy/man1/gpgdir.1.html](http://manpages.ubuntu.com/manpages/saucy/man1/gpgdir.1.html)

---

