---
title: "Having problems surfing net via ssh/proxy server."
date: 2007-04-23
forum: Server Platforms
---

### Post by buckwheat12n on 2007-04-23
I have a client PC that I am dual booting Winxp/Ubuntu on.  I have another PC setup to run as a proxy server using ssh and privoxy.  On the client PC in both Windows and Ubuntu I am using putty to make my ssh connection.  This works fine on both operating systems.  I setup firefox to connect to use the proxy server via 127.0.0.1:8118.  I can connect and surf the net fine while in Windows but when in Ubuntu I get the follwing message:

The proxy server is refusing connections
Firefox is configured to use a proxy server that is refusing connections.  
 *   Check the proxy settings to make sure that they are correct.
 *   Contact your network administrator to make sure the proxy server is
      working.

There is no firewall running on the Ubuntu client.

---

### Post by STLuni on 2008-04-10
Probably way too late on this, but I think i solved the same prob u had. Instead of using "localhost" in the SOCKS proxy field, put 127.0.0.1. I dont know why it won't use localhost (IE actually did this, the first time i've ever seen IE beat firefox) if anyone one who had this problem actually reads this, tell me how it goes and if that fixed it.

---

