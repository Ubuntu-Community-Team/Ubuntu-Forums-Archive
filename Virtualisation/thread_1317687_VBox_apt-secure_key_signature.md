---
title: "VBox apt-secure key signature"
date: 2009-11-06
forum: Virtualisation
---

### Post by MoebusNet on 2009-11-06
I confess I don't understand this, and Google & the apt man-pages aren't any help, so I figured I'd ask the community.

Update Manager tells me that I can update VirtualBox to 3.0.10 from 3.0.8. But it gives me this error message:

W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release: The following signatures were invalid: BADSIG DCF9F87B6DFBCBAE Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>


I've downloaded the Sun public key for apt-secure to my desktop and used:
<sudo apt-key add sun_vbox.asc> to install it. But Synaptic still shows:

6DFBCBAE 2008-07-14
Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>

in my System>Administration>Synaptic Package Manager>Settings>Repositories>Software Sources>Authentication;

whereas the VirtualBox download page says I should have:

AF45 1228 01DA D613 29EF  9570 DCF9 F87B 6DFB CBAE
Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>

I haven't been able to get rid of the error message. Any ideas so I can upgrade VirtaulBox without getting this error message? (I'd feel a lot better about security).

---

### Post by unamanic on 2009-11-06
Your sigs for virtualbox are the same as I have.  There are three possibilities, Sun signed the package with the wrong key, a bad download caused the the signature to be incorrect, or the package is not from Sun.  You may want to try a "sudo aptitude clean" to clear your cache and then try to install again.

---

### Post by MoebusNet on 2009-11-06
Thank you for the suggestion. :)

---

