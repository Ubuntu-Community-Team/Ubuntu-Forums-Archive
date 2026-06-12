---
title: "Quantal How do I get rid of the remote login option?"
date: 2012-09-19
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Cavsfan on 2012-09-19
How do I get rid of that remote login option I see at bootup.
Here is the contents of my **/etc/NetworkManager/NetworkManager.conf** file.

```
[main]
plugins=ifupdown,keyfile
#dns=dnsmasq

[ifupdown]
managed=false
```

I do not want any option to remotely login period.
Thanks for any help! :D

---

### Post by mc4man on 2012-09-19
remove the service
```
sudo apt-get remove remote-login-service
```

---

### Post by philinux on 2012-09-19
> **Cavsfan said:**
> 
I do not want any option to remotely login period.
Thanks for any help! :D

Just to be sure have read the blurb on this? This is to remotely login to other machines, not the one you're normally logging into.
Apologies if you know all this.
[http://ubuntuforums.org/showpost.php?p=12234486&postcount=76](http://ubuntuforums.org/showpost.php?p=12234486&postcount=76)

---

### Post by Cavsfan on 2012-09-19
> **mc4man said:**
> remove the service
```
sudo apt-get remove remote-login-service
```

Thanks for that!!!

> **philinux said:**
> Just to be sure have read the blurb on this? This is to remotely login to other machines, not the one you're normally logging into.
Apologies if you know all this.
[http://ubuntuforums.org/showpost.php?p=12234486&postcount=76](http://ubuntuforums.org/showpost.php?p=12234486&postcount=76)

I did not know that Phil! But, since I have only one computer and do not plan to allow any one to login into mine nor will I remotely login to any one else's. I think I will remove it.
It just kind of scared me but, I should have known better #-o
Thanks to both of you for the quick reply! :D

---

### Post by Cavsfan on 2012-09-21
It worked like a charm! Thanks to both of you for the how to and the explanation!
I meant to resolve this but, have been busy.
Thanks again! :D

---

