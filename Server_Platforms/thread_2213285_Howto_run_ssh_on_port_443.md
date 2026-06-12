---
title: "Howto run ssh on port 443"
date: 2014-03-25
forum: Server Platforms
---

### Post by josef3 on 2014-03-25
Hello. I just install ubuntu 12.04 and try to run sh on port 443. I updated /etc/ssh/ssh_config to 
[HTML]
Port 22
Port 443
[/HTML]
After I restart SSH I can access SSH on port 22, but on 443 it still not working. Any idea? I dont have install apache or set forewall. I just have base instalation.

I found similar problem on [http://stackoverflow.com/questions/7698675/cant-connect-to-ssh-over-port-443](http://stackoverflow.com/questions/7698675/cant-connect-to-ssh-over-port-443) But on my log /var/log/auth is nothing and if i run 
lsof -i :443 nothing happen.

Thanks for help

---

### Post by josef3 on 2014-03-26
So guys problem was i updated file /etc/ssh/ssh_config instead of /etc/ssh/sshd_config :-)

---

### Post by Lars Noodén on 2014-03-26
You can also [multiplex ssh and https](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Multiplexing) on the same port using [slh](http://www.rutschle.net/tech/sslh.shtml).  It won't hide anything but it will let you use the port for both protocols.

---

