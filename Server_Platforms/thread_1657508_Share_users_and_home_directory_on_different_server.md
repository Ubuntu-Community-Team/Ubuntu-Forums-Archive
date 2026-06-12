---
title: "Share users and /home directory on different servers (and locations)"
date: 2011-01-01
forum: Server Platforms
---

### Post by stijnvb on 2011-01-01
I'm currently thinking of deploying an LTSP setup on different locations. 
Setting up LTSP is not a problem. 

What I would like:
On location 1: an LTSP server with user accounts and all files stored locally. this server will serve clients on this location.
On location 2 (and possibly 3 and 4): An LTSP server which serves clients on this location, but with a VPN tunnel to location 1. The /home directory and the user files should be mounted from the server on location 1, so they can be fully controlled on location 1.

Mounting the /home directory through the VPN tunnel using NFS should be doable (considering there is enough bandwidth available). Is there a way to get the users (passwd) file shared for the different locations? A possibility would be to make a daily copy from the file in location 1 to the other locations. However I'm afraid this might cause issues with system user and groups ...?

Is there maybe a possibility to store users and groups in a separate database (mysql/pgsql), which can serve from any location?

What about storing the /home folder on a server in a data center, and also mounting it through NFS on location 1?

I don't really like the option to synchronize the files on a regular (say daily) basis as could be done with MS AD.

Anyone has some experience with this?

Thanks a bunch! And happy new year!

Stijn

---

### Post by stijnvb on 2011-01-01
I think the best approach will be to use NIS. Currently installing a few systems in VirtualBox to see what happens next :-)

---

### Post by elico on 2011-01-01
well it depends on your line between location 1 2 and the others.
cause if it's a lan then ok you can use this thing.
but if it's wan in a slow speed compared to the storage size then.. you should use other method.

---

### Post by stijnvb on 2011-01-01
The locations will probably be able to have a fiber WAN connection of 50/50 mbit, which would make it possible for the user data to be transferred through internet (applications etc are stored on the local server). 
There would be some location(s) where we need to deal with a DSL connection, which will require local storage of data. 

I'm going to keep on playing around! Thanks for your input!

---

