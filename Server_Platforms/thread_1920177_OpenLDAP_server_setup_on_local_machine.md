---
title: "OpenLDAP server setup on local machine"
date: 2012-02-04
forum: Server Platforms
---

### Post by Berduchwal on 2012-02-04
I am trying to set up OpenLDAP server on a Ubuntu machine running 11.04 server 64.

There will be only local connections to the machine running on local network with only Ubuntu machines.

I am trying to follow guide from: 
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

It says that in line:
olcRootDN: cn=admin,dc=example,dc=com

example and com should be replaced by my own values.

This server will be running on local network hopefully with ip as referencing points.

So do I then put say 
olcRootDN: cn=admin,dc=192.168.0.1

or 
olcRootDN: cn=admin,dc=192,dc=168,dc=0,dc=1

or something else?

On the net I also seen it as
olcRootDN: cn=admin,dc=home,dc=local

but I am not sure how to adopt it.

Any suggestion or help welcome.

---

