---
title: "Encrypted Connection for Ubuntu Updates?"
date: 2017-04-27
forum: Security
---

### Post by KenUBF on 2017-04-27
I recall reading something about forcing all updates to go through HTTPS connections but I don't recall the method to use this feature. Is it possible to do this? Thanks!

---

### Post by Floppyjoe on 2017-04-27
This thread may be of interest to you. It is about using the TOR anonymity network to download partially encrypted updates.

[https://ubuntuforums.org/showthread.php?t=2357369](https://ubuntuforums.org/showthread.php?t=2357369)

I think the connection through the three tor nodes would be encrypted with the path from the third Tor node to the repositories unencrypted.

There is also apt-transport-https but I'm not sure if any of the repositories use https.

---

### Post by deadflowr on 2017-04-28
apt-transport-https should already be installed.
(As almost every other repo you might add be it 3rd party or ppa is probably using https; comical sometimes that the main archives do not...)

https mirrors do exist, though they are few and far between.

I guess I'll rinse and repeat myself here:
[https://ubuntuforums.org/showthread.php?t=2355907&p=13622116#post13622116]("https://ubuntuforums.org/showthread.php?t=2355907&p=13622116#post13622116")

^^I literally felt deja-vu as I typed the above, and remembered i posted that about a month ago.

---

### Post by anoda on 2017-04-28
Hi. As we know, all the data that APT and of course similar tools transfers is signed by GPG keys. And the signed **Releases** files contain hashes for all the packages, and APT can check the hashes during downloads packages and so on. On the other side, HTTPS would mean that users would need to configure their clients to check certificates for the individual mirrors.   Anyway, this would not protect users against a hacked mirror site.  There is also functionality in APT to respect a **Valid-Until** tag in **Release** file, but it is not implemented, because a malicious mirror could simply use this **Release** file for e.g. an earlier Ubuntu release and prevent install of available updates.  Thanks.

---

### Post by Floppyjoe on 2017-04-28
> **anoda said:**
> Hi. As we know, all the data that APT and of course similar tools transfers is signed by GPG keys. And the signed **Releases** files contain hashes for all the packages, and APT can check the hashes during downloads packages and so on. On the other side, HTTPS would mean that users would need to configure their clients to check certificates for the individual mirrors.   Anyway, this would not protect users against a hacked mirror site.  There is also functionality in APT to respect a **Valid-Until** tag in **Release** file, but it is not implemented, because a malicious mirror could simply use this **Release** file for e.g. an earlier Ubuntu release and prevent install of available updates.  Thanks.

Is there any reason why using apt-transport-https and apt-transport-tor would result in hash sum mismatches when using the apt-get commands other than a man in the middle changing the data?

---

### Post by KenUBF on 2017-04-29
Thank you all for the tips! Deadflowr, I remember now, yes, the article I read mentioned apt-transport-https. The main reason I wanted to encrypt was more for privacy about what I'm downloading rather than authentication. Anyway, I installed it, but I noticed that none of the links are https when I run apt-get update. How do I enable this package? There seems to be little info about it. Unless I'm just not looking in the right place.[COLOR=#000000]

[/COLOR]

---

### Post by deadflowr on 2017-04-29
> How do I enable this package? There seems to be little info about it. Unless I'm just not looking in the right place.

Nothing needed to do to get apt-transport-https to start.
It works out of the box.
The only changes you would need to do is setup the sources for https.
(basically find an https-able mirror and change your sources.list to that mirror.)

---

### Post by KenUBF on 2017-05-05
Thanks for the tip!

---

