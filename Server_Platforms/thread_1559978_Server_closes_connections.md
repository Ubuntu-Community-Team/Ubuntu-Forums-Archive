---
title: "Server closes connections"
date: 2010-08-24
forum: Server Platforms
---

### Post by phermansson on 2010-08-24
I have a strange problem with a rather fresh installation of Server 10.04. It's run as a server on an external IP, co-located at a hosting company. In Ubuntu we run Apache, Postfix and common server software. We also use VirtualBox to host a virtual Windows Server 2008 installation.
The problem is that the server often breaks the network connection. It can be running fine for a few hours, but then the virtual machine crashes and the remote desktop connection is closed. At first I suspected VirtualBox, but the strange thing is that the opened SSH-connections locks at the same time. I have an open session to the server that works, but after some time it locks and I can't write any commands in it. If I connect again it works fine, and I can then restart the virtual Windowsinstallation from it's aborted state. 

I find nothing obvious in the logs, somebody who can help me find the problem??

---

### Post by crackevil on 2011-03-21
I have the same issue, i´ve installed Ssh and a proxy service in my Lucid but every 15 or 10 or 20 minutes this services seems do not function properly. The proxy service does not show clients any web page and the SSL connections closes. Thus, the ethernet device stills answering pings.
 
Can anybody helps us?
 
Regards!

---

### Post by phermansson on 2011-03-22
My problem has been solved. But I don't know how :) Maybe some update did the trick, I don't remember...

---

