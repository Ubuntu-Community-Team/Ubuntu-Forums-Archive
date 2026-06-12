---
title: "problems while trying to install lamp - Proxy"
date: 2012-04-10
forum: Server Platforms
---

### Post by wurstsalat on 2012-04-10
I'm new to Ubuntu and Linux at all. I've set up a Ubuntu Server. Till now the only thing I've done is to update the server with "apt-get update"...

Now I'm trying to install lamp ([https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)).
Installing tasksel was no problem but if I enter "sudo tasksel install lamp..." my server obviously doesn't receive any packages. It shows only "Installing packages" "1 out of 26". Thats it. 

I conclude from the fact that I had to configure the proxy settings "http_proxy" before updating the server that I'm now having the same problem with tasksel. Therfore I tried to configure the proxy, lets say "global" in /etc/bash.bashrc.

If I now write "echo $http_proxy" while being root it seems that the proxy is configured. 
But why the hell isn't it receiving any data?

Has anybody an idea?

---

### Post by FreeD01 on 2012-04-11
It may be that the proxy will work only with apt-get. I have configured my in a different way so it is hard to say what is going on on your server. Maybe firewall? To install LAMP try:

[B]sudo apt-get install lamp-server^

[/B]

---

