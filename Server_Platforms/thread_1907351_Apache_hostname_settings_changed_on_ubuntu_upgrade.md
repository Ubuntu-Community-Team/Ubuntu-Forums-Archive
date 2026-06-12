---
title: "Apache hostname settings changed on ubuntu upgrade"
date: 2012-01-11
forum: Server Platforms
---

### Post by Corbey on 2012-01-11
I recently upgraded my version of Ubuntu, and now I'm having a problem with the server's hostname.

My server hosts an intranet, which I could access before from any computer on the network at [http://intranet](http://intranet)
This url still works on the server machine, but now no other machines can use this url. I can still access it through the IP address from other machines, so I know it's up and working, but I just can't get the hostname to work again.

I've checked the etc/hosts file and everything seems to be fine. I'm a bit new to this so not sure where else to check. Any help would be appreciated!

---

### Post by Corbey on 2012-01-11
Some more info. Upgraded from 9.10 to 10.04.
My IP address changed in the process, which I updated in etc/hosts but this only allowed the local server to access through [http://intranet](http://intranet). Didn't solve the problem for any other computers on the network.
 
Found some info on changing 'NameVirtualHost *:80' back to 'NameVirtualHost *' in ports.conf and sites-available/default, but this didn't work either. Any ideas?

---

