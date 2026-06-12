---
title: "SSH error when trying to connect to launchpad"
date: 2015-01-27
forum: Ubuntu Dev Link Forum
---

### Post by arvindv on 2015-01-27
Hi
I am trying to upload a package to ppa with sftp. I have a local ssh agent running and uploaded the public key in launchpad. When I run the dput command I get the following error,

**rejected by the upload queue management software.**
**Uploading to ppa (via sftp to ppa.launchpad.net):**
**  xxxxxxx_xxxx-.dsc: **
**Unable to connect to SSH host ppa.launchpad.net; EOF during negotiation**
**E: Error uploading file.**

When running, 
```
ssh  -T ppa.launchpad.net

```**No shells on this server**.

I could ssh to my github account with the same public keys from the same machine. I could not find any useful help online either. Can some one help ?

---

