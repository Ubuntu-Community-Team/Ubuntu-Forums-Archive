---
title: "ssh not working"
date: 2009-05-20
forum: Server Platforms
---

### Post by salim.madni on 2009-05-20
dear all,

i have installed a new ubuntu server using putty

so i test also local machine itself

so when i say on local machine

ssh localhost

it was not working

during isntallation i select only samba

can you advise how to fixed this issue

regards
salim

---

### Post by volkswagner on 2009-05-20
ssh is not installed by default.  To install:

```
sudo apt-get update
```

```
sudo apt-get install ssh openssh-server
```

---

