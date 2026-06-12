---
title: "torproject key expired?"
date: 2012-09-11
forum: Security
---

### Post by ottosykora on 2012-09-11
the signing key of the torproject.org is expired apparently and so no update are possible for the Tor components.

Does anyone found some new key somewhere to enable the installation and update of the Tor software?

---

### Post by ottosykora on 2012-09-12
I have now checked the gpg key in question and as far as I can see it it is still valid and expires some time in 2016. So it is not just the key itself.

However there seem to be no way to make any updates to Tor and components, as ubuntu refuses to verify the files form the torproject repository.

It is not some problem of one particular installation, it is on all my ubuntu installs, 5 of them currently having same problem. From start of september, no more updates to Tor possible.
If I keep the repository in the list of software sources, then the whole update manager is kind of blocked by that.


Any idea what to do?

---

### Post by rookcifer on 2012-09-12
I fixed it by reimporting the Tor project's key as outlined on their [website.]("https://www.torproject.org/docs/debian.html.en#ubuntu")

Like so:

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```

Then run apt-get update, etc.  This fixed it for me.  

The key ID that Ubuntu said expired does not match the key they have on their website right now (not sure what happened there).  I am positive I imported the key when I installed Tor months ago.  I suppose the key has changed since then.

Also, be sure to install the .deb package to keep the signing key current:

```
sudo apt-get install deb.torproject.org-keyring
```

This should stop it from happening in the future.

---

### Post by ottosykora on 2012-09-12
ok thanks, at leats I know I am not the only one.

In fact I never had the tor keyring, I just imported the mentioned key to my normal keyring and it did work.

Will try to install their keyring deb and see.

---

### Post by Ms. Daisy on 2012-09-12
I had the same issue recently.  I followed the instructions on this page
 
[https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian)
 
which fixed it.  Those instructions seem to mirror rookcifer's recommendations.

---

### Post by ottosykora on 2012-09-13
no clue what it was, the key was on my ring and was otherwise OK.

Reimported the key, gpg even told me there was nothing to change, but after that all works again.

---

