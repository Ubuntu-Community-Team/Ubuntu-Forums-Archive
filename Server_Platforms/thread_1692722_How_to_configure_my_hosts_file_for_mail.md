---
title: "How to configure my hosts file for mail"
date: 2011-02-21
forum: Server Platforms
---

### Post by insafeuste on 2011-02-21
In trying to configure a mail server, I ran into issues requesting me to change settings in my hosts file. Right now all i have in my hosts file is 
127.0.0.1 localhost
127.0.1.1 Linux
 
I've read that I need a fully qualified domain name, but I'm not sure what my fqdn would be for the mail server. I have the server's external ip, which i use for ssh/ftp.. then I have 2 domain names setup through apache's virtualhosts, which each point to their respective site directories.

---

### Post by tangerine0469 on 2011-03-29
There should be an entry with those two that follows this layout:

xxx.xxx.xxx.xxx hostname.example.com

where the IP is that of your servers network connection where all the traffic is going to come in on, the host name is the name of the server and example.com is replace by your domain name.

---

