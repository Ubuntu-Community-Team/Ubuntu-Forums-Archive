---
title: "Virtualbox - lubuntu guest"
date: 2014-04-23
forum: Virtualisation
---

### Post by Quarkrad on 2014-04-23
I'm trying to get full screen for a lubunu 14.04 guest on a ubuntu 14.04 host.  No luck with the normal process so I'm trying **sudo apt-get install virtualbox-ose-guest-utils  virtualbox-ose-guest-x11 virtualbox-ose-guest-dkms**  but I keep getting unable to locate package virtualbox-ose-guest-utils, unable to locate package virtualbox-ose-guest-x11, unable to locate package virtualbox-ose-guest-dkms.  Any help appreciated.

---

### Post by Elfy on 2014-04-23
Many of the ose packages don't go further than quantal - [http://packages.ubuntu.com/search?keywords=virtualbox&suite=default§ion=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=virtualbox&suite=default§ion=all&arch=any&searchon=names)

Not that it helps much - but I can go full screen with Xubuntu Guest - no reason that I can think of for Lubuntu being different.

That's with the ORacle version of vbox and installing it's guest additions, in addition the Extension Pack from the vb download page.

*Thread moved to **Virtualisation**.*

---

