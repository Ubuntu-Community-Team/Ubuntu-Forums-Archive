---
title: "Set up SSH"
date: 2007-02-17
forum: Server Platforms
---

### Post by psi36 on 2007-02-17
I have a desktop and an laptop, both on the same lan. I want to log in to the desktop from my latop. I've installed SSH with ```
sudo apt-get install ssh
``` on the desktop and I try to login with ```
ssh my_username@10.0.0.9
``` on my latop (10.0.0.9 being the IP of my desktop in my lan) as explained on [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_SSH_Server_for_remote_administration_service](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_SSH_Server_for_remote_administration_service). 
But after a few minutes i get ```
ssh: connect to host 10.0.0.9 port 22: Connection timed out
```. Is there anything more I need to set up on the desktop to get SSH to run? Or what am I doing wrong?

---

### Post by steve0921 on 2007-02-17
Hmm,

I don't see any obvious reason why this isn't working. That's all that should be needed to set up ssh. On quick silly thing to try is to just restart the daemon on your desktop with:
```
sudo /etc/init.d/ssh restart
```

I'd also check to make sure there are no connection issues. Try to ping your desktop. Make sure there isn't a firewall on any of the computers/router that might block the ssh port (22 I think).

Sorry I can't be of more help.

---

### Post by psi36 on 2007-02-17
Pinging the desktop works. 
Is there a way to ping a certain port, like port 22?

I did a shh restart, but that didn't help.

On [http://www.cyberciti.biz/tips/howot-install-ubuntu-linux-ssh-server.html](http://www.cyberciti.biz/tips/howot-install-ubuntu-linux-ssh-server.html) it says to do ```
netstat -tulpn
```to see if ssh is running.
For port 22 this terurned the following, which seems to be OK, no?```
 netstat -tulpn
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp6             0            0 :::22                            :::*                                 LISTEN     -                   

```How can I check if it's a firewall setting?

It seems to me that could be the problem, because I also can't login using XDMCP or VNC.
When i try XDMCP there aren't any servers fould.
And VNC doesn't do anything either.

---

### Post by psi36 on 2007-02-17
OK, it was the firewall. I opened port 22 in Firestarter and now it's works fine. I did the same for VNC and that works fine now also.

---

