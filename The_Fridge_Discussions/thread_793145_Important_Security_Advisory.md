---
title: "Important Security Advisory"
date: 2008-05-13
forum: The Fridge Discussions
---

### Post by TheFridge on 2008-05-13
A weakness has been discovered in the random number generator used by OpenSSL on Debian and Ubuntu systems. As a result of this weakness, certain encryption keys are much more common than they should be, such that an attacker could guess the key through a brute-force attack given minimal knowledge of the system.
  This particularly affects the use of encryption keys in OpenSSH. This vulnerability only affects operating systems which (like Ubuntu) are based on Debian. However, other systems can be indirectly affected if weak keys are imported into them. 
  We consider this an extremely serious vulnerability, and urge all users to act immediately to secure their systems. The following Ubuntu releases are affected: Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS 
  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu. 
 Please see [usn-612-2]("http://www.ubuntu.com/usn/usn-612-2") for the latest information regarding updating your system and taking appropriate protective measures. More information will be released within 48 hours.
 

[More...](http://fridge.ubuntu.com/node/1445)

---

