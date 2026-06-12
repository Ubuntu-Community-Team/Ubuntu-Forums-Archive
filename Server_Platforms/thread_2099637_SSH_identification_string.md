---
title: "SSH identification string"
date: 2012-12-30
forum: Server Platforms
---

### Post by d4rk0wl on 2012-12-30
Hi all,
I am encountering an odd problem. My auth.log is filled with these messages.
```

sysadmin@d4rkb0x:~$ cat /var/log/auth.log | tail
Dec 29 23:37:07 d4rkb0x sshd[2552]: Did not receive identification string from 127.0.0.1
Dec 29 23:37:12 d4rkb0x sshd[2554]: Did not receive identification string from 127.0.0.1
Dec 29 23:37:17 d4rkb0x sshd[2556]: Did not receive identification string from 127.0.0.1
Dec 29 23:37:22 d4rkb0x sshd[2559]: Did not receive identification string from 127.0.0.1
Dec 29 23:37:27 d4rkb0x sshd[2561]: Did not receive identification string from 127.0.0.1
Dec 29 23:37:32 d4rkb0x sshd[2563]: Did not receive identification string from 127.0.0.1
Dec 29 23:37:37 d4rkb0x sshd[2566]: Did not receive identification string from 127.0.0.1
Dec 29 23:37:42 d4rkb0x sshd[2569]: Did not receive identification string from 127.0.0.1
Dec 29 23:37:47 d4rkb0x sshd[2572]: Did not receive identification string from 127.0.0.1
Dec 29 23:37:52 d4rkb0x sshd[2574]: Did not receive identification string from 127.0.0.1

```
Throughout my searching of the forums and of google I have found nothing. Some people have said it is a possible DDOS attack although I doubt that because my logs are spammed with this message from the second I turn the server on after not being on for a few days. I recentally re-installed the server OS to get a clean slate (it is my dev server). Ubuntu 12.10 is installed on an old IBM Netvista I had lying around, SSH is not on port 22 and I am using RSA authentication for log in.

Any help is appriciated, thanks in advance
- D4rk0wl

---

### Post by thnewguy on 2012-12-30
According to this thread ([http://ubuntuforums.org/showthread.php?t=1551004](http://ubuntuforums.org/showthread.php?t=1551004)) the admin said the issue stopped once gnome-keyring had been updated.

Some things I would try: Make sure not other network services are running, things which might also try to monitor SSH to see if it is alive or not. Remove openssh from the server and monitor the network traffic to see if something is still trying to connect to to port 22.

---

### Post by d4rk0wl on 2012-12-30
Thanks for the reply,

I also saw that post I have not yet attempted to update the gnome-keyring, I will attempt that when I get home and post back the results. Although is Ubuntu server running Gnome Keyring without a GUI? The services I have running on the server are Apache, Samba, Subsonic (Music), and Webmin. I thought webmin might be the culprit because I know it adds a nice GUI front end. Although it is the same thing when I turn it off. 
Another thing I might note is that I do not have SSH running on the deafult port. I did this in attempts to weed out the bots and kiddies. On my last setup I was successful.

Thanks in advance,
- D4rk0wl

---

### Post by d4rk0wl on 2012-12-30
Update:

So through trial and error I have discovered that it is in relation to the port I am running it on. If I set it to the deafult port I do not get these error messages anymore however when I change the port number that is when the error starts popping up.

I attempted to start the service with all other services disabled and that had no effect.

I know the sshd_config is for the server and ssh_config is for the client. I attempted to change the port in the client config to the same port and that had no effect.

Regards,
- D4rk0wl

---

### Post by SeijiSensei on 2013-01-01
Since all the entries reference 127.0.0.1 this is not happening from outside the server.  Whoever suggested a DDOS attack either wasn't paying sufficient attention to the logs you provided, or didn't know what he or she was talking about.

---

### Post by d4rk0wl on 2013-01-01
That is what I thought as well, although other people were saying it was possible for an attacker to spoof localhost. Which I didn't think was possible.

As I said before, when I change the port back to 22 this message goes away and currentally port 22 is blocked by my firewall. It is only when I put the service on the alternate port that this message appears. Which is odd because on my old setup this was not an issue.

Regards,
- D4rk0wl

---

### Post by Cheesehead on 2013-01-01
See example #2 at [http://scottlinux.com/2012/03/07/troubleshooting-ssh-server-logs-and-error-messages/](http://scottlinux.com/2012/03/07/troubleshooting-ssh-server-logs-and-error-messages/)

Perhap another benign process (network monitor, port scanner, netcat, etc) is connecting to your SSH port, leading sshd to request authentication...which of course never arrives.

---

### Post by d4rk0wl on 2013-01-02
Update:
So it seems another process was using the port I was attempting to run the SSH service on. I was running the service on port 9902 and I deiced to change it. After I changed the port to another random port those error messages seemingly stopped.

I don't know why they were not there last time I ran the server on that port and now they were, but I would much rather change my firewall configuration around then chase a problem I have no idea about.

So I guess I can concider this one solved for now, thanks everbody! ):P

Regards,
- D4rk0wl

---

### Post by d4rk0wl on 2013-01-03
Sorry to bump up one of my posts, but I found the real solution to the problem.

After I changed it to another port within a few days the same error started popping up. Through more trial and error I found the error started occuring after I changed my pcmonitor configuration. I feel so stupid now, I should of known the PC monitor would of been listening on the port I told it to :P Oh well, at least I now know my problem.
Regards,
- D4rk0wl

---

