---
title: "Apache issues on Ubuntu 14.04.1"
date: 2014-11-06
forum: Server Platforms
---

### Post by dan145 on 2014-11-06
So, I am extremely new to this and just got Ubuntu Server running for the first time and also setup apache server for testing and learning. I used the 'sudo apt-get install apache2' method and everything seemed to install fine. But when I try to connect using the browser as localhost or 127.0.0.1 it just fails and says it can't connect. Although, when I try to connect by entering the IP of the server in the browser it loads the default page fine. Are there any helpful hints that could get me past this initial test phase?

I should also mention that I'm running my Ubuntu Server on VirtualBox.

Thanks,

Dan

---

### Post by nerdtron on 2014-11-06
What else did you changed on the Ubuntu server after you installed apache?
Did you activated the firewall?
Did you modify the /etc/hosts file?

And what is the output of
```
sudo netstat -tulpn
```

---

### Post by dan145 on 2014-11-06
I haven't changed anything except for changing the Listen port from just 80 to 0.0.0.0:80 in the ports.conf file. Someone else had recommended this may help. Other than that, it's a fresh server install and apache install. Firewall status is inactive and I haven't touched it at all. Attached is the output from your netstat request also.

[ATTACH=CONFIG]257791[/ATTACH]

---

