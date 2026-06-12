---
title: "Webmin; DNS Lookup failed"
date: 2011-06-15
forum: Server Platforms
---

### Post by ptmuldoon on 2011-06-15
Recently, I can't seem to connect to Webmin on a headless ubuntu server via its name, ie: [https://somename:10000](https://somename:10000)

However, it does continue to connect if I use the actual ip address of 192.168.xx.xx.  The IP address is 'static' in that my router assigns this fixed address to it.

When I try to connect use the machine's name, I get an error of:
> The server at somename can't be found, because the DNS lookup failed. DNS is the web service that translates a website's name to its Internet address. This error is most often caused by having no connection to the Internet or a misconfigured network. It can also be caused by an unresponsive DNS server or a firewall preventing Google Chrome from accessing the network.

Does any have any thought on what may have changed?  I believe a recent upgrade of something may have caused this?

Thanks

EDIT.....  Nevermind, I think I'm tard :)    I'm connected to my machine via SSH and have my web browsers configured to tunnel through my home server to bypass work blocking some things.  Thus, I need to use localhost and not the machine's name.

---

