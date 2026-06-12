---
title: "How to build custom ISO like Daily Build?"
date: 2016-01-20
forum: Ubuntu Development Version
---

### Post by Lambert_Lu on 2016-01-20
Hi There,

I am interesting of how the Daily Build ISO got build.

[xubuntu] or [Ubuntu]

Is there a automatic script build the ISO base on a configure file?

I would like to lean how to build my own up to date ISO just like the Daily Build iso with some changes.

Will keep most feature but trim/add few other packages.
Things like UEFI/SecureBoot will be required.

I tried #xubuntuX chat room, but no luck.


Really appreciate if anyone can help!

---

### Post by forcecore on 2016-01-20
[https://github.com/Distroshare/distroshare-ubuntu-imager](https://github.com/Distroshare/distroshare-ubuntu-imager) i personally use this, i could not imagine using Ubuntu without this as i prefer to create my custom lightweight bloat free version with every release.

Do not know how well it works for 16.04 as i have 15.10

---

### Post by oldfred on 2016-01-21
Another alternative if you have High Speed Internet, is just use scripts to install/uninstall whatever you want.
You can start with the mini install or the server install, I believe server supports UEFI, mini may not yet.
Normally the server install runs this to install groups of applications, but you can just install whatever you want instead or in addition.
 Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel

I install desktop and then run script to install many additional apps, reconfigure desktop, create mounts,  auto edit fstab, auto edit NFS and other configuration settings. 
Install takes about 10 minutes if partitioned in advance, script takes another 15 or 20 min to download & update.

---

### Post by Lambert_Lu on 2016-01-21
Thanks for reply, I am planning a xUbuntu replace project.

There will be not fast internet, All Windows Pre-Install machines, more than 500+ PC.

Need build a ISO just bring all the necessary tools on Boot, no additional over net install.

I will try [https://github.com/Distroshare/distroshare-ubuntu-imager](https://github.com/Distroshare/distroshare-ubuntu-imager) next.

So the Ubuntu Daily build team has a security script to build the ISO without any public access.

---

