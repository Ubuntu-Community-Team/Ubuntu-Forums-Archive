---
title: "Backup plan of controllers, nodes and images?"
date: 2011-11-01
forum: Ubuntu Cloud and Juju
---

### Post by thomasjohansen on 2011-11-01
Hi, 

Im thinking of making a private cloud at work, consisting of a controller and 2 or 3 nodes.

Their primary goal is to have two ubuntu servers running, a intranet site and a zarafa mailserver. At the moment I'm running them as VM (virtualbox).

The reason for putting them in a cloud is scalability for the mailserver, but also for reliability/uptime for the mailserver.

And now to big question... Backup.

When then mailserver is running as an image in the cloud, wouldnt it be safe and kept running even if one node had a breakdown?

And what if the controller broke, would it be possible to create a new and continue?


Multiple nodes are cheaper than backup solutions/medias and maintenance of backup procedures, atleast in my perspective.

---

