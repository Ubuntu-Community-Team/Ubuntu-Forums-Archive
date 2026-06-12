---
title: "The connection has timed out"
date: 2010-02-09
forum: Security
---

### Post by shahidpazeez on 2010-02-09
Hi All,

I have a linux server running Ubuntu 8.04 server edition. And it was working fine. And this server is not open to the world, I can access port 22 and 80 of this server form other two server which is white listed. 

So to access port 80 of this server I did a port forwarding on both of the white listed server. And it was working. 

But the issue is, when I upload a file with more than 450 KB size through white listed servers using IPTABLES I get connection timeout error. There will not be any issue for very small files.

I am getting the error:

**[SIZE="5"]The connection has timed out[/SIZE]**
[SIZE="4"]The server at <IP> is taking too long to respond.[/SIZE]

Thanks in advance.

---

### Post by byStanderone on 2010-02-09
...seems like a bandwidth problem, try to focus on that.

---

### Post by shahidpazeez on 2010-02-10
@ byStanderone

Its not a bandwidth problem. I tried to upload the file from connections with high bandwidth.

Its working well from the white listed  servers and I am able to upload files with 25MB size. There is only one web application in the server for uploading files.

I did a port forwarding in the white listed servers so that I can upload the file from any where. The problem occurs when I upload a file using port forwarded IP and port.

---

