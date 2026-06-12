---
title: "UFW firewall doesnt start up on restart"
date: 2016-02-10
forum: Security
---

### Post by cam17 on 2016-02-10
All my Ubuntu 14.04.3 workstations do not start up the UFW firewall automatically after the computer is restarted. My ufw.config file is 
# Set to yes to start on boot. If setting this remotely, be sure to add a rule
# to allow your remote connection before starting ufw. Eg: 'ufw allow 22/tcp'
ENABLED=yes

# Please use the 'ufw' command to set the loglevel. Eg: 'ufw logging medium'.
# See 'man ufw' for details.
LOGLEVEL=low

---

### Post by Habitual on 2016-02-10
```
sudo ufw enable
```

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by cam17 on 2016-02-13
UFW enable does not correct the issue.This occurs on all 3 of my Ubuntu 14.04.3 LTS workstations.

---

### Post by Habitual on 2016-02-14
Did you set it on all 3 workstations?

---

### Post by cariboo on 2016-02-14
What are you using to determine whether your firewall is working or not? 

```
sudo ufw status
```

If it isn't working the output of the above command should look like this:

```
 sudo ufw status
[sudo] password for cariboo: 
Status: inactive
```

The best way to check if your firewall is active, is to do a port scan from another system on your local network

---

