---
title: "Why won't honeyd start on boot?"
date: 2013-05-10
forum: Security
---

### Post by mf23 on 2013-05-10
I have installed honeyd on my machine and configured the  appropriate settings to get it to run as a service.  The service will  run fine and functions as expected if I start it with command:

```
sudo service honeyd start 
``` 

However, the service does not automatically start when I reboot the machine.

I have run the command

```
 sudo update-rc honeyd defaults 
```  

And I receive the output "System start/stop links for /etc/init.d/honeyd already exist."

I have attempted to find any useful log information on the failure to start with

```
more /var/log/* | grep honeyd 
``` 

The results of this search show the output of the service starting  and stopping when I do so manually, but no events are listed during  bootup of the machine, leading me to believe it is not even attempting  to start.
  
I can post the contents of the various honeyd configuration files if  needed, though I believe they are correctly setup since I can start the  service manually.

Any guidance is most appreciated.

**Edit:**Some additional information: I'm running Ubuntu 12.04 LTS 64-bit.  honeyd was installed with apt from default repos.  Let me know of any other pertinent info that would be helpful.

---

### Post by 2F4U on 2013-05-10
Looks as if you are having the same issue as the guy in this post:

[http://askubuntu.com/questions/9382/how-can-i-configure-a-service-to-run-at-startup](http://askubuntu.com/questions/9382/how-can-i-configure-a-service-to-run-at-startup)

The cause of his problem is that a symlink already exists. Remove the symlink and try update-rc again.d.

---

