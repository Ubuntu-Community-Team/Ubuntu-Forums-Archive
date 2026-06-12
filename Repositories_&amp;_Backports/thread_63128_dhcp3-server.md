---
title: "dhcp3-server"
date: 2005-09-07
forum: Repositories &amp; Backports
---

### Post by funkydrummer on 2005-09-07
Hello,

I'd like to set up a dhcp server for my home network on my new ubuntu hoary box.  Various online tutorials (such as [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/))  have pointed me to the "dhcp3-server" package which I can't seem to find in any of the standard repositories.  I've enabled (uncommented the appropriate lines) all the repositories found by default in my sources.list and have even added ubuntu-backports.mirrormax.net and none of these seem to have the dhcp3-server package.  I also can't seem to find it searching the Gnome Synaptic GUI.

apt-get returns "Package dhcp3-server is not available, but is referred to by another package..."

Any suggestions?  The howto docs have sufficiently scared me away from installing a standard debian package.

Thanks much.


(BTW if there's a better dhcp server I'm happy to use it.  I've just been directed to this dhcp3-server from various places.  I did, however, apt-get the standard dhcp package which includes dhcpd, but it didn't appear to support ddns-update options (to update the DNS server) so I removed it.)

---

### Post by funkydrummer on 2005-09-07
Ok nevermind, it turns out there was one more line to uncomment in my sources.list.  That one seems to have done the trick.  Now if I could only find out how to delete a post...

---

