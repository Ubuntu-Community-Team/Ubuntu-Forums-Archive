---
title: "ssh problem in Amazon cloud"
date: 2011-01-31
forum: Ubuntu Cloud and Juju
---

### Post by Japhering on 2011-01-31
Ok.. I have 6 slices in the Amazon EC2 cloud space.   I'm currently in the process of trying to move off of  Centos and on to Ubuntu Cloud.

The problem I've run into.. is that the Ubuntu issue doesn't recognize any rsa keys when the session originates out side of the Amazon cloud (slice to slice works)

ssh -vvv  shows that the Ubuntu  sshd is rejecting the  id_rsa key as invalid.   The key
has been generate on Ubuntu 10.10 on my laptop as well as on generated on the Ubuntu 10.10 cloud slice.   Both keys have the exact same format,  both fail when used to originate outside of the of the Amazon cloud space.

Anyone else seeing issue getting into Ubuntu from  outside the cloud.

Thanks

---

### Post by kim0 on 2011-02-04
hmm, feel free to ping me (kim0) on irc, I wouldn't mind trying to help hands on! This *should* be easy :)

---

