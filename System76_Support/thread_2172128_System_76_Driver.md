---
title: "System 76 Driver"
date: 2013-09-03
forum: System76 Support
---

### Post by david12 on 2013-09-03
I have been trying to install the System 76 driver, however I cannot download it through the PPA.

The command **[COLOR=#800080]"[FONT=monospace]sudo apt-add-repository ppa:system76-dev/stable"[/FONT][/COLOR]**[COLOR=#000000][FONT=monospace] seems to work fine.
[/FONT][/COLOR]
> You are about to add the following PPA to your system:
 
 More info: [https://launchpad.net/~system76-dev/+archive/stable](https://launchpad.net/~system76-dev/+archive/stable)
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpLbKbpw/secring.gpg' created
gpg: keyring `/tmp/tmpLbKbpw/pubring.gpg' created
gpg: requesting key C8B7748B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpLbKbpw/trustdb.gpg: trustdb created
gpg: key C8B7748B: public key "Launchpad PPA for System76 Development" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK


Then. the command [COLOR=#800080]**"**[FONT=monospace]**sudo apt-get update"**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] yields[/FONT][/COLOR]:

> Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
W: Failed to fetch [http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/prcise/main/source/Sources](http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/prcise/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/prcise/main/binary-amd64/Packages](http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/prcise/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/prcise/main/binary-i386/Packages](http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/prcise/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones use instead.



So when the command **[COLOR=#800080]"sudo apt-get install system76-driver"[/COLOR]** is issued, the following is returned:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package system76-driver



What to do, please?

Thanks

---

### Post by houstonbofh on 2013-09-03
Start with this thread. [http://ubuntuforums.org/showthread.php?t=2165676](http://ubuntuforums.org/showthread.php?t=2165676)

Feel free to comment in it as well, but I don't think it matters to them that you prefer an LTS release.

Did that sound bitter?  Sorry... :)

---

### Post by isantop on 2013-09-03
If you're on 12.04, you'll need to download the driver from [http://planet76.com](http://planet76.com)

---

