---
title: "Can not SSH in, always says invalid password"
date: 2009-07-28
forum: Server Platforms
---

### Post by harry71194 on 2009-07-28
Hello, I have used SSH on my server box at home for a while. When I try to SSH into my home box from a shell (ie, it isn't at my home, it is on a different network), it connects fine, and it asks me for my password. I type it in. "Permission denied, please try again.". After 3 times, it disconnects. I am using the correct username and password, and it just will not work.

I know for a fact that the IP is not banned in deny.hosts, and the username and password is correct (I can ssh into the box from another box on the same network; just not any connections outside my home).

Help me please D:

---

### Post by R.Bucky on 2009-07-29
Check your sshd_config (/etc/ssh/) to make sure that you can or cannot use root login. You should not be logging in as root anyway... Also, check to make sure you have not configured your system to listen only on a ListenAddress. 

Check your logs and see what is happening. Open up your port for ssh (ufw or other) and Port Forward on your router.

Check those items...

---

### Post by harry71194 on 2009-07-29
Thanks for the reply.

My config looks fine, listening on port 22. I try to log on as a non-root user, does not work either.

My ports are forwarded fine, I think.

But it still will not work.



Edit: Oookay. Weird. I just sshed in using my router's password, and it worked..not what I want.
:~$ ssh admin@my ip etc
admin@ip's password: 
Ambit U10C019 CableModem

>


My cable modem has no option to turn off sshd in the webui @ 192.168.0.1 ..... and the ports ARE forwarded to my real computer though..




Edit2: Turned off the ssh-access in the cable modem. SSH is working now, and with fail2ban :) Thanks.

---

### Post by R.Bucky on 2009-08-01
I am fairly new to fail2ban. It is great! Two things: i was registering hundreds of break-in attempts per day. Change your ssh port from 22 to something else. I have not had a break-in attempts in weeks! Next, if you regularly ssh from specific locations, only allow ssh connections from certain ip's in your jail.local. [Read this article too]("http://buckycomputing.net/blog/securing-ssh-on-your-server/") for information on how to do both of those things.

---

