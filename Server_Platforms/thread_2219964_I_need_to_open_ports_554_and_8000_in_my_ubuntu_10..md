---
title: "I need to open ports 554 and 8000 in my ubuntu 10.04 server."
date: 2014-04-26
forum: Server Platforms
---

### Post by vineet3 on 2014-04-26
Hello Everyone,
We are currently a small isp having 20 customers. We need to open ports 554 and 8000 for a client. He has 4 camera's installed at his office and needs to do port forwarding in his router. For that he wants me to open the ports 554 and 8000 so that he can have live streaming of his videos on his mobile. So now i just want to open the ports 554 and 8000 in  my server and i dont know how to do it. :confused:  :confused: 
Thanks in advance.:)

---

### Post by dudumomo on 2014-04-26
Hi Vineet3,

On the Ubuntu Server, do you have iptables installed? Which firewall are you using on the server? 
I won't be surprised if you don't have any.... and if this is the case, your customer need to open these 2 ports in its own router. This should be enough probably...

---

### Post by nerdtron on 2014-04-26
Post the output of "sudo ufw status" and are you using iptables? Post the output of "sudo iptables -L".

---

