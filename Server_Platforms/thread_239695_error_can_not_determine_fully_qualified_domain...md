---
title: "error: can not determine fully qualified domain.."
date: 2006-08-19
forum: Server Platforms
---

### Post by goneskiing on 2006-08-19
After changing ports.conf to:

Listen 127.0.0.1:80 

to keep the server just for localhost development, I now get an error every time I reload Apache as:

"Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName  httpd (pid 4988?) not running "

and then it hangs. Any suggestions ?

---

### Post by dazedandconfused on 2006-08-20
Hiya,

What's in /etc/hosts ?

Cheers,

jools

---

### Post by goneskiing on 2006-08-21
in /etc/hosts: 

127.0.0.1 localhost mymachine
127.0.0.1 mymachine

then some other stuff

Is this correct ?  what is supposed to be here?

---

### Post by dazedandconfused on 2006-08-21
Try setting it up like this:

I have a server called server1 with an ip of 192.168.0.2 and my local domain is called homenet.local.

My hosts file is therefore:
### start of /etc/hosts ###

127.0.0.1    localhost.localdomain  localhost
192.168.0.2  server1.homenet.local server1

### end of /etc/hosts ###


The server's fully qualifed domain name is server1.homenet.local without this in the hosts file you'll get the error message. Change the relevant bits of the example above to match your network. You can make up any domain name you like if your network is not visible on the net i.e. it's behind a firewall and you can then set the domain of client machines to the same.

Cheers,

Jools

---

