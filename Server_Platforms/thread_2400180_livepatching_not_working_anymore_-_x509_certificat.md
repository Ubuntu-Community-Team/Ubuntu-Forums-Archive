---
title: "livepatching not working anymore - x509: certificate signed by unknown authority."
date: 2018-09-03
forum: Server Platforms
---

### Post by l.seitz on 2018-09-03
Hi Forum,  

since a few days my livepatching doesnt work anymore. 
I tried to remove and reenable it and now i got the following error:  

canonical-livepatch enable *token*
 [[A2018/09/03 18:29:16 error executing enable: Couldn't send req: Post [https://livepatch.canonical.com/api/machine-tokens:](https://livepatch.canonical.com/api/machine-tokens:) x509: certificate signed by unknown authority. Server communication failed.  

i allready tried to reconfigure the ca-certificates package but it didnt help.  

any ideas? regards

---

### Post by l.seitz on 2018-09-03
I just tried with another 16.04 (in the post above its 18.04) VM which never had livepatch installed and same result.

---

