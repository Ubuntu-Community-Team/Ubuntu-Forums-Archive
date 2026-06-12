---
title: "PPA signing problem"
date: 2009-01-22
forum: Server Platforms
---

### Post by martinjh99 on 2009-01-22
Im trying to make sure that I have the GPG Signature for Dustin Kirklands PPA installed properly.

I have the follwing in my sources:
```

#Screen configs
deb http://ppa.launchpad.net/kirkland/ubuntu hardy main
deb-src http://ppa.launchpad.net/kirkland/ubuntu hardy main

```

When I do a apt-get update I get the following message:
```

W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7781BA0134BEEE14
W: You may want to run apt-get update to correct these problems

```

having emailed Dustin I got his key and imported it as he said in his email with:

```

gpg --keyserver keyserver.ubuntu.com --recv 83A61194

```

Updated again but still got the same error...  Anyone know why this is?  How can I stop the error from happening?

The package I wanted from the PPA has been installed OK just got a warning that there is no way to verify the package and was wondering how to fix it.

---

### Post by Contrast on 2009-01-23
Give this a shot:
```
wget -q [http://ppa.launchpad.net/kirkland/ppa/ubuntu/dists/intrepid/Release.gpg](http://ppa.launchpad.net/kirkland/ppa/ubuntu/dists/intrepid/Release.gpg) -O- | sudo apt-key add -
```

I always preferred wget over gpg for authenticating repos - just feels a lot simpler, so long as you know where to get the key from.

[edit] Blarg. You'll obviously want to copy the URL above and replace the truncated one in the command.

---

### Post by martinjh99 on 2009-01-23
```

martin@Willow ~ $ wget -q http://ppa.launchpad.net/kirkland/ppa/ubuntu/dists/intrepid/Release.gpg -O- | sudo apt-key add -
gpg: no valid OpenPGP data found.
martin@Willow ~ $

```

Something is not right with the data I guess.

---

### Post by blackgr on 2009-01-24
[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743)  check this out

---

### Post by dox_drum on 2009-01-27
Thank you blackgr. Your scrip works wonderfully well.

---

