---
title: "Error Message"
date: 2009-06-05
forum: System76 Support
---

### Post by mysteriousdarren on 2009-06-05
I have been getting the error message 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: Failed to fetch [http://deb.mulx.net/dists/hardy/Release.gpg](http://deb.mulx.net/dists/hardy/Release.gpg)  Could not resolve 'deb.mulx.net'

W: Failed to fetch [http://deb.mulx.net/dists/hardy/main/i18n/Translation-en_US.bz2](http://deb.mulx.net/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'deb.mulx.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

just wondering what i could do. thanks for the help.

---

### Post by thomasaaron on 2009-06-05
To fix your GPG key error, run this command...

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6AF0E1940624A220
```

These two...

W: Failed to fetch [http://deb.mulx.net/dists/hardy/Release.gpg](http://deb.mulx.net/dists/hardy/Release.gpg) Could not resolve 'deb.mulx.net'

W: Failed to fetch [http://deb.mulx.net/dists/hardy/main...tion-en_US.bz2](http://deb.mulx.net/dists/hardy/main...tion-en_US.bz2) Could not resolve 'deb.mulx.net'

...are because Update Manager could not connect to those servers. You may want to wait a day or two and see if it fixes itself. Could be a server down.

If not, you can comment those repositories out in /etc/apt/sources.list.

---

### Post by skreeves on 2009-06-05
I believe the repository formerly at deb.mulx.net has been moved.

See [http://ubuntuforums.org/showpost.php?p=7325918&postcount=4](http://ubuntuforums.org/showpost.php?p=7325918&postcount=4)

---

### Post by mysteriousdarren on 2009-06-17
I would like to thank you for all the help.

---

