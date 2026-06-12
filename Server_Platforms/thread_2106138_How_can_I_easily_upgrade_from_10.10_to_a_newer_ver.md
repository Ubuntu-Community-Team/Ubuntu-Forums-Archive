---
title: "How can I easily upgrade from 10.10 to a newer version without losing applications?"
date: 2013-01-18
forum: Server Platforms
---

### Post by c3ntury on 2013-01-18
I've got a server with OVH, running Ubuntu 10.10, I really wanted to upgrade it to the latest version of Ubuntu, but how can I do this without disrupting my applications (having to reinstall them and so forth)?

---

### Post by SeijiSensei on 2013-01-18
If all the applications came from the repositories, and anything you installed yourself is in /usr/local, then you can just use "do-release-upgrade" to migrate from one version to the next.  I updated a server this way a few months ago.

[This guide from Linode]("http://library.linode.com/upgrading/upgrade-to-ubuntu-12.04-precise?format=print") looks pretty comprehensive.

---

