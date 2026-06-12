---
title: "Server Advice Needed"
date: 2011-04-30
forum: Server Platforms
---

### Post by rainleader on 2011-04-30
I need to host multiple websites and currently use Rackspace Cloud Server (virtual machines) with Ubuntu 10.10. So far, I have LAMP fully operational and configured on one of my servers but I'd like to offer custom DNS and VirtualMin (for client management) to each of my virtual hosts. I'm thinking of changing my configuration to get DNS up and running:

==CURRENT==
SERVER 1 (master, hosts all VHOSTS)

==NEW==
SERVER 1 (same)
SERVER 2 (primary DNS)
SERVER 3 (secondary DNS)

Under the new setup, (I believe) DNS records stored on SERVER 2/3 for each virtual host will likely consist of a few MX records (mail hosted elsewhere) and an A record that points to SERVER 1 which uses named virtual hosts.

Does this seem like it would work? Can I simplify this at all (less servers)?

Can I just use the VirtualMin installer to set this up? ([http://www.virtualmin.com/download.html](http://www.virtualmin.com/download.html))

---

