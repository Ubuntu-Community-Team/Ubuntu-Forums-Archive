---
title: "puppetmaster dashboard on lucid server?"
date: 2010-10-05
forum: Server Platforms
---

### Post by samosamo on 2010-10-05
Anyone have a tutorial to get puppetmaster and Puppet Dashboard installed?  It is way over my head.  Requires knowledge of ruby, apache2 passenger module, etc.

> 
[http://github.com/reductivelabs/puppet-dashboard#readme](http://github.com/reductivelabs/puppet-dashboard#readme)

Puppet Dashboard
Overview

The Puppet Dashboard is a web interface for Puppet, an open source system configuration management tool. The Puppet Dashboard currently displays reports with the detailed status and history of Puppet-managed servers (nodes), and can assign Puppet classes and parameters to them.

---

### Post by BobVila on 2010-10-05
The puppet website's got some good information. As long as you can follow directions, all the info is there. Why not give it a crack and reply back if you get hung up on a particular step?

[http://docs.puppetlabs.com/guides/installation.html]("http://docs.puppetlabs.com/guides/installation.html")

---

### Post by samosamo on 2010-10-05
I installed it via puppetlab's apt repo along with it's dependencies.  I then configured apache2 with the example dashboard-vhost.conf file.  When pointing my web browser to the server's IP, the application reported permission errors at /usr/share/puppet-dashboard.  I chown'd it with www-data:www-data and that fixed it.

Puppet Dashboard is now working.  I just have no idea how to use it!  It apparently doesn't use /etc/puppetmaster to store data so I have no idea how to add clients, configs, etc. When I looked up documentation on their website, I laughed when I found they haven't got around to writing it yet.  All I found was this:

> 
[http://docs.puppetlabs.com/guides/using_dashboard.html](http://docs.puppetlabs.com/guides/using_dashboard.html)

Using Dashboard

Learn how to use Puppet dashboard.
About

**Puppet Dashboard is fairly self explanatory**, if you have set it up using the Installation Instructions just visit port 3000 to start using it. As Dashboard evolves, we&#8217;ll have more information here about using it, as well as screenshots and advanced feature information.


---

