---
title: "Where do I get the debsig policies?"
date: 2012-01-18
forum: Server Platforms
---

### Post by D-LINC on 2012-01-18
Hi. I recently took over management of a small Ubuntu-based e-mail server. I tend to be at least somewhat security-conscious, so I wanted to figure out how the package verification system works in Debian/Ubuntu. (I.e., how I know my packages come from trusted sources and have not been modified.) Through a more generic Linux forum I learned about debsig-verify. However, when I run it on a deb, I get this error:

```
debsig: Origin Signature check failed. This deb might not be signed.
```I read up in DEBSIG-VERIFY(1) that there are supposed to be policy sub-directories in /etc/debsig/policies, along with related keyrings, but there are none. How do I install these policies, or where do I download them?

---

