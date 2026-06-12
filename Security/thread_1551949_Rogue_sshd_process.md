---
title: "Rogue sshd process"
date: 2010-08-13
forum: Security
---

### Post by drinian on 2010-08-13
Hi folks,

I was just messing around with my system, and discovered an sshd process running on my system. That's odd, because I've had sshd disabled for a long time through rcconf. However, the low process ID would suggest that it was spawned during system boot.

I double-checked that it was disabled using update-rc.d. It is.

"/etc/init.d/sshd stop" did kill the process, but it bounced right back with a new process ID. It's running as root on port 22.

Does Ubuntu have some other control mechanism that I'm not aware of for sshd, or is this looking like maybe I should run rkhunter? Thanks.

---

### Post by bodhi.zazen on 2010-08-13
That certainly sounds suspicious. I have not seen a ssh server restart like that.

---

### Post by drinian on 2010-08-13
rkhunter and chkrootkit do not show anything suspicious.

---

### Post by uRock on 2010-08-13
Is your router set up for port forwarding? 

Do you have Wireshark installed? If so, does it show packets for port 22 and the incoming IP address?

Have you activated UFW and blocked port 22?

You can also use Snort and write a definition that will give an alert for the connection and get the incoming IP and then block it within UFW.

---

### Post by drinian on 2010-08-13
There is no port forwarding to this laptop, and it is sitting on a private network behind NAT.

Netstat doesn't show any unusual connections, nor does ifconfig show more data being transmitted than I would expect. The sshd instance works as expected (lets me log into my machine with my normal user). Currently having a look at Wireshark.

---

### Post by uRock on 2010-08-13
Does the w or who command show another user logged in? (I face palmed myself for not thinking of that earlier.)

---

### Post by drinian on 2010-08-13
w, who, and users all check out ok. So far as I can tell, there's nothing nefarious going on, unless it's impressively well concealed.

daemon.log indicates:
Aug 13 00:27:41 init: ssh main process (620) terminated with status 255
Aug 13 00:27:41 init: ssh main process ended, respawning

---

### Post by drinian on 2010-08-13
I'm out of my depth now. The file /etc/init/ssh.conf has the following lines:

```
respawn
respawn limit 10 5
```

Is it possible this is overriding my rc settings?

---

### Post by uRock on 2010-08-13
That is beyond me also. I am going to ask an admin to move this to the security sub-forum to grab the best minds on this.

---

### Post by drinian on 2010-08-13
Thanks. I suspect that this is something to do with Upstart (and the fact that I haven't taken the time previously to familiarize myself with it). Back in the morning.

---

### Post by cariboo on 2010-08-13
This has everything to do with upstart, to stop ssh from restarting, remove the executable bit:

```
sudo chmod -x ssh
```

then stop the service:

```
sudo service ssh stop
```

**Note** this is only a temporary fix, you need to restart in order for the executable change to take affect.

---

### Post by cdenley on 2010-08-13
Unlike most services which have been configured to upstart, ssh seems to have both an upstart configuration file, and an actual /etc/init.d/ssh file (instead of a symlink to /lib/init/upstart-job). The upstart script seems to rely on /etc/init.d/ssh. The /etc/init.d/ssh script does not seem to stop the ssh daemon. However, the upstart command (sudo service ssh stop) seems to work fine. The update-rc.d command will not modify any upstart configuration. It can't disable ssh from starting.

---

### Post by bodhi.zazen on 2010-08-13
> **cdenley said:**
> Unlike most services which have been configured to upstart, ssh seems to have both an upstart configuration file, and an actual /etc/init.d/ssh file (instead of a symlink to /lib/init/upstart-job). The upstart script seems to rely on /etc/init.d/ssh. The /etc/init.d/ssh script does not seem to stop the ssh daemon. However, the upstart command (sudo service ssh stop) seems to work fine. The update-rc.d command will not modify any upstart configuration. It can't disable ssh from starting.

Should probably file a bug report on that one.

I have used upstart (sudo service start|stop|restart) for some time now and if the old init script is problematic it should be reported so it can be re-educated.

---

### Post by drinian on 2010-08-13
Bug filed.

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/617515](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/617515)

Thanks for your help.

---

