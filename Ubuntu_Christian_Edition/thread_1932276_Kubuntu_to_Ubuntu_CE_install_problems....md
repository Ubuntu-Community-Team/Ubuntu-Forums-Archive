---
title: "Kubuntu to Ubuntu CE install problems..."
date: 2012-02-27
forum: Ubuntu Christian Edition
---

### Post by joemartin on 2012-02-27
I tried to install Ubuntu CE from a Kubuntu Wubi install...

Can someone assist with the error message I got below?  Thanks.  Is there a workaround?

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1880AFA1287A2031
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-ce : Depends: xiphos but it is not going to be installed
             Depends: wine-christian-repos but it is not going to be installed
             Depends: ubuntu-ce-xsplash-artwork but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by jonathonblake on 2012-03-03
> **joemartin said:**
> 
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1880AFA1287A2031

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys missing_pubkey
sudo apt-get update

```

Change the values as appropriate, and the pgp keys should be correctly imported and installed.

> Depends: xiphos but it is not going to be installed

That was fixed in the current version of xiphos.  You'll probably have to go to the ppa for it.

> Depends: wine-christian-repos but it is not going to be installed

That has been broken for years. The fix is to rewrite the code, and remove unneeded dependencies.  IIRC, it is a batch file that includes some extremely unusual scripting.

> Depends: ubuntu-ce-xsplash-artwork but it is not going to be installed

I'm not sure what the issue there is.  Download, but do not install it.  I think that breaking apart the DEB file results in data that can be correctly installed manually.

jonathon

---

