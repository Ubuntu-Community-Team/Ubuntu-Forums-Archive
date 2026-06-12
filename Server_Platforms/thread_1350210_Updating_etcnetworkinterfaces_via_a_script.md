---
title: "Updating /etc/network/interfaces via a script"
date: 2009-12-09
forum: Server Platforms
---

### Post by shebangs on 2009-12-09
Via a script I need to update the IP address, Gateway and Netmask of eth0.   I have the new values in an Environment Variable.

Is there a safe/simple easy way to do this that doesn't involve sed?  Or do I need to sed each file?

I was hoping there was:

/foo/something eth0 ip <newip>
/foo/something eth0 netmask <newnetmask>
/foo/something eth0 gateway <newgateway>

---

### Post by HighCommander540 on 2009-12-10
Why would you need to do this? Can't you just go in an add the values to your /etc/network/interfaces file? If they are already env vars, it doesn't sound like you want to change them...

---

### Post by munky99999 on 2009-12-10
Are you trying to do this to many computers very quickly? Why not configure a dhcp server?

---

