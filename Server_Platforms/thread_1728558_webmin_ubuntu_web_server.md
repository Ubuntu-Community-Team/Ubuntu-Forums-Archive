---
title: "webmin/ ubuntu web server"
date: 2011-04-13
forum: Server Platforms
---

### Post by Sailor-Moon on 2011-04-13
I have a friend who has a static IP address.
Today I took my linux box over, which has ubuntu server 10.10 and webmin 1.540 on it.
We set his router to port forward port 80 to 192.168.1.55
We set his windows server 2003 machine running WAMP to that ip address and it hosted fine.
We then disconnected the windows server, connected the webmin server, set it's ip address to the same as the windows server, so as not to have to change the port forward rule.
We were unable to access the web-server from an external source, only using it's internal ip address.
We were testing using a different network for external connectivity.
We have both looked over many websites, technical manuals, posts blogs and even you-tube videos, and as far as we can see, the firewall is set to allow everything, we can't understand why the webmin web-server was not working correctly. 
Any suggestions would be appreciated, thank you.

---

### Post by falko on 2011-04-14
Are you trying to access the web server (port 80) or Webmin (port 10000)? If you try to access Webmin, you must open port 10000 in the firewall as well.

---

### Post by Sailor-Moon on 2011-04-14
web server.   we can access web min on port 10000 fine and we can see the web server using 192.168.1.55 fine. we just can't see it from an external ip address when using a different network, as if viewing from the internet

---

### Post by elico on 2011-04-14
what about iptables settings on this machine?
did you try to check the port forwarding rules?
you can try to put the machine in DMZ as only host and it's like forwarding everything to the server.
if you do telnet to the external ip and port 80 what do you get?
did you tried to work this ubuntu machine using other internet connection or just to the internet?
it seems like simple setiings.

can this ubuntu server get to the internet at all?

---

### Post by Sailor-Moon on 2011-04-14
"what about iptables settings on this machine?"   all set to allow

"did you try to check the port forwarding rules?"   on the router yes. it worked for another server

"you can try to put the machine in DMZ as only host and it's like forwarding everything to the server."  Router we were using did not have a DMZ. It was an old one

"did you tried to work this ubuntu machine using other internet connection or just to the internet?"     we tried it only on the static ip line my friend has. The other server worked fine on it. We tried to access it using a cell phone, 3g dongle to a laptop, dial up connection and phoned a friend to ask them to access it on their network.  the windows server was a sucess every time. The linux machine times out every time

"it seems like simple setiings."   I agree, just can't see what's wrong

"can this ubuntu server get to the internet at all?"   it can. it updated webmin while connected to the internet. FTP also worked. It just wont allow people to see the webserver part.

---

