---
title: "pear command line not working"
date: 2012-04-06
forum: Server Platforms
---

### Post by kkruecke on 2012-04-06
I am setting up a Ubuntu (the problem also happens on Debian Squeeze) Virtual Private Server. I have installed the php5 and php-pear packages. When I go to install a pear package from the command, or if I attempt to upgrade packages, for example
```
# sudo pear upgrade-all
```
pear always gets a "could not download" message. The command above gave:

> Could not download from "http://pear.php.net/get/Structures_Graph-1.0.4.tgz", cannot download  "pear/structures_graph" (File [http://pear.php.net:80/get/Structures_Graph-1.0.4.tgz](http://pear.php.net:80/get/Structures_Graph-1.0.4.tgz) not valid (redirected but no location)) Error: cannot download "pear/Structures_Graph"

I tried purge php-pear and reinstalling. I tried Debian instead of Ubuntu, but got the same message.

---

