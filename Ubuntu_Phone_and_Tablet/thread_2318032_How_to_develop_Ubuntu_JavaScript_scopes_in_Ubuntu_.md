---
title: "How to develop Ubuntu JavaScript scopes in Ubuntu trusty?"
date: 2016-03-22
forum: Ubuntu Phone and Tablet
---

### Post by ales-horak on 2016-03-22
I have tried to build a JavaScript scope as described in [https://developer.ubuntu.com/en/scopes/tutorials/developing-scopes-javascript/](https://developer.ubuntu.com/en/scopes/tutorials/developing-scopes-javascript/). My host is running Ubuntu 14.04 trusty. I have the Ubuntu SDK installed and running. After adding the [FONT=courier new]ppa:unity-api-team/unity-js-scopes[/FONT] repository and [FONT=courier new]apt-get update[/FONT], an error is reported:
```

W: Failed to fetch http://ppa.launchpad.net/unity-api-team/unity-js-scopes/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead. 

$ sudo apt install unity-js-scopes-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package unity-js-scopes-dev

```
Is it possible to develop JavaScript scopes with Ubuntu trusty?

---

### Post by grahammechanical on 2016-03-22
> **Note:** JavaScript scopes development is supported from Ubuntu 15.04 (Vivid) onwards.

There is not a version of this PPA for Trusty. That is the reason for the failed to download & the failed to locate errors.

[https://launchpad.net/~unity-api-team/+archive/ubuntu/unity-js-scopes](https://launchpad.net/~unity-api-team/+archive/ubuntu/unity-js-scopes)

Regards

---

