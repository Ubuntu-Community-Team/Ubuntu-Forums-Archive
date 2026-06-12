---
title: "Can't login trough SSH"
date: 2008-06-30
forum: Server Platforms
---

### Post by k31k0 on 2008-06-30
Hi. I have Ubuntu 7.10 server installed on my server and I am trying to connect to it using SSH. Until now everything worked perfect (for couple of months), but this morning I got this message
```
sasa@ubuntu:~$ ssh <username>@<domain>
ssh_exchange_identification: Connection closed by remote host
```
I went to the server, logged in and tried restarting the SSH deamon (/etc/init.d/ssh restart). That didn't help. Then I did full restart and that helped for a short while. After about 30 minutes I again tried logging into server trough SSH and got the same error again. Can somebody tell me what's wrong?

Thanks.

---

### Post by k31k0 on 2008-06-30
I don't get it... I didn't do anything and now I can log in using SSH. It would be great, but I feel a little scared - how can server repair itself? No one should be able to login to the server beside me and I didn't do anything. Does someone have any idea what the hell is going on?

---

### Post by windependence on 2008-06-30
Check /etc/hosts.deny and make sure the paranoid setting is NOT uncommented.

Also, check the logs in /var/log on the machine you are trying to ssh into and see what the reason was.

-Tim

---

### Post by k31k0 on 2008-06-30
I think I know what was wrong... I checked /var/log/auth.log and there was a lot of requests from the same IP address (and I saw the message "POSSIBLE BREAK-IN ATTEMPT!" a lot of times in that log file - every 2-3 seconds someone from that IP was trying to log in).
I added that IP to the /etc/hosts.deny file and now everything is OK.

---

### Post by windependence on 2008-06-30
This is a safety feature of ssh, and a good one at that.

-Tim

---

### Post by MJN on 2008-06-30
Sounds like a potential DOS vector to me!
 
k31k0, presumably the IP address you added was someone elses? It sounds to me like you doing this was just another coincidence as per previously when you found you could log in without having done anything.
 
Mathew

---

