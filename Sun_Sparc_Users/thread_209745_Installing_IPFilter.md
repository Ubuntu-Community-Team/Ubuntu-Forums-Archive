---
title: "Installing IPFilter?"
date: 2006-07-05
forum: Sun Sparc Users
---

### Post by MickyLee on 2006-07-05
Has anyone had any success or tried to install IPFilter? If you have, could you explain the process you went through? Thanks...

---

### Post by chris_andrew on 2006-07-05
Can you tell us what form the software is in?  .deb, tarball, etc?  What problems have you had?

Is this for use on the Sparc platform?

Thanks,

Chris.

---

### Post by allnameswereout on 2006-07-06
[http://www.phildev.net/ipf/IPFlinux.html](http://www.phildev.net/ipf/IPFlinux.html) should get you started. Read the howtos. They're RedHat/Fedora centered but the principle is the same. Consider ignoring aspects such as having to install Squid or BIND as they're not necessary. Consider writing a howto and/or .deb specific for Ubuntu.

What it comes down is that you'll need to install the appropriate kernel source and compile IPF using that.

The packages *filtergen* and *hlfl* are able to help you creating your IPF ruleset. Both are in the universe repository.

Let us know if you have any specific questions.

---

