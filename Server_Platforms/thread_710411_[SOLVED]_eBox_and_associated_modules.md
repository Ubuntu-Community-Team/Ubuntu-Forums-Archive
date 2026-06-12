---
title: "[SOLVED] eBox and associated modules"
date: 2008-02-28
forum: Server Platforms
---

### Post by altonbr on 2008-02-28
According to: [http://ebox-platform.com/installation-guide](http://ebox-platform.com/installation-guide), you should run

```
sudo apt-get install **ebox** **libebox** \
**ebox-network** **ebox-objects** ebox-mail \
**ebox-firewall** ebox-trafficshaping ebox-samba \
ebox-dns ebox-dhcp ebox-squid \
ebox-usersandgroups ebox-software **ebox-ntp** \
ebox-printers ebox-jabber **ebox-ca** ebox-openvpn
```

To install eBox. The only problem is, in Ubuntu (Gutsy/Hardy), not all of those modules are in the repos. I've bolded the ones Ubuntu does have. As you can see, a lot are missing...

How can I get ebox-dns, ebox-usersandgroups and ebox-mail working in Ubuntu? Compile?

EDIT:: I've found that those modules do not comply with 'Debian policy' and thus can not be included in Ubuntu ([http://trac.ebox-platform.com/query?status=closed&milestone=Ubuntu+Hardy](http://trac.ebox-platform.com/query?status=closed&milestone=Ubuntu+Hardy)). Is there anything I can do in the meantime? Should I wait for Hardy in two months?

---

### Post by faulkes on 2008-02-28
Please see Chuck Short's work on eBox for 8.04 in the following thread

[http://ubuntuforums.org/showthread.php?t=707492](http://ubuntuforums.org/showthread.php?t=707492)

You may also find a list of the modules at 

[https://launchpad.net/~zulcss/+archive](https://launchpad.net/~zulcss/+archive)

Thanks,

Faulkes

---

### Post by altonbr on 2008-02-28
> **faulkes said:**
> Please see Chuck Short's work on eBox for 8.04 in the following thread

[http://ubuntuforums.org/showthread.php?t=707492](http://ubuntuforums.org/showthread.php?t=707492)

You may also find a list of the modules at 

[https://launchpad.net/~zulcss/+archive](https://launchpad.net/~zulcss/+archive)

Thanks,

Faulkes

That's fantastic. Thank you, thank you, thank you!

---

