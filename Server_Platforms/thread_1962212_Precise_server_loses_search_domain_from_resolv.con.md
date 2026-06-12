---
title: "Precise server loses search domain from resolv.conf during pxe boot/install."
date: 2012-04-20
forum: Server Platforms
---

### Post by learn2mac on 2012-04-20
Hello,

I am currently having a problem where on attempting to perform a preseeded install, the pxe boot process overwrites the resolv.conf file dropping the search directive which is needed for the url that I am passing for the location of the preseed file. The domain used in this search directive was obtained from dhcp and is present initially. I have submitted a bug with further details at 

[https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/974454](https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/974454). 

I wanted to submit this post to see if anyone else has encountered this problem or a similar problem when attempting an automated install. 

I am using the following iso for the install: 
precise-server-amd64.iso

Running a dhclient on the server resolves the issue, but I need this to be an automated install with no user interaction.

---

### Post by newbie-user on 2012-04-21
Perhaps this is the issue you're having:

[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

Ubuntu is using resolvconf to automatically rewrite /etc/resolv.conf.

---

### Post by learn2mac on 2012-04-23
Yeah, I believe that resolvconf is most likely the culprit. However, the initial resolv.conf is also being dynamically generated from the dhcp information that it is receiving from the pxe server that is housing the install. If I manually specify the hostname or domain name using get_hostname or get_domainname in my pxelinux client config file, it maintains the appropriate search directive settings. I need this setting to be received from the dhcp server that it is connecting to since this install will need to be initiated from multiple provisioning servers.

---

### Post by learn2mac on 2012-04-25
It appears that there is some kind of reverse dns lookup to determine the hostname. Once this fails, it appears that this is the point where it is losing the domain and search directive.

---

### Post by SeijiSensei on 2012-04-25
Does the machine have an assigned hostname?  What is the contents of /etc/hostname?

You can force the dhcp client to send a specific hostname by editing /etc/dhcp/dhclient.conf and replacing the "<hostname>" entry in the "send host-name" directive with whatever you want.  The <hostname> construct tells dhclient to use the value of /etc/hostname.

---

