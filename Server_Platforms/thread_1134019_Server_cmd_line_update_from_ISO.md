---
title: "Server cmd line update from ISO?"
date: 2009-04-23
forum: Server Platforms
---

### Post by buchan on 2009-04-23
Ok, simple question ... I've been digging for a while and can't seem to come up with an answer so please feel free to slap me if I missed it somewhere.

I have several 8.04 servers that I would like to update, I know I have to go to 8.10 first, that's the simple part. 

Of course today doing the upgrade using "sudo do-release-upgrade" will probably take several decades I know the gui works for the desktop releases but I only have ssh access to these servers.  Is there a way to do the upgrade from a local CD ISO and only get the updated packages as needed from a cmd line?

Thanks, and sorry again if I missed the answer to this somwhere else

---

### Post by anderswestrup on 2009-04-23
I don't think there is a simple way to do this in the normal installer or upgrader.

But you can install a caching apt proxy server on one of your servers, e.g the package apt-proxy. It includes a command to import packages in its cache from a directory so you could import all packages from the CD.

---

