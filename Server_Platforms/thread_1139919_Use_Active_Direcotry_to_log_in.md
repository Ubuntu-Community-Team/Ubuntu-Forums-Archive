---
title: "Use Active Direcotry to log in"
date: 2009-04-27
forum: Server Platforms
---

### Post by zeroroom on 2009-04-27
I have a server running Ubuntu 9.04 joined to our domain using Likewise.

I would like to be able to log into the server using credentials from Active Directory instead of creating a whole new set of accounts.

Can anyone point me towards documentation on how to do this? I have taken a look but I am teh fail.

Thanks!

---

### Post by HermanAB on 2009-04-27
Here is something:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Note that Mandriva, Suse and Redhat Fedora now have working wizards for that.

---

### Post by drave on 2009-04-27
> **zeroroom said:**
> I have a server running Ubuntu 9.04 joined to our domain using Likewise.

I would like to be able to log into the server using credentials from Active Directory instead of creating a whole new set of accounts.

Can anyone point me towards documentation on how to do this? I have taken a look but I am teh fail.

Thanks!

once the machine is joined to the domain any user can login as "DOMAINNAME\username"

---

### Post by Perkins on 2009-04-29
Works a little better to do it as user@domain

---

