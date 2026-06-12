---
title: "SSH problem"
date: 2016-06-09
forum: Server Platforms
---

### Post by jmarcfrappier on 2016-06-09
I've installed a new 14.04 server and since i've set it with a static address i<m having problems with ssh.
I connect once after about 2 minutes i get an error "Write failed: Broken pipe"
If i try to reconnect i get "connection refused"
I have to reboot my machine in order to reconnect to the server or connect from another machine.
I have multiple 14.04 servers and it's the first time this has ever happened.
I've added 
echo "ClientAliveInterval 60" | sudo tee -a /etc/ssh/sshd_config
Restarted the server and it didn't change anything.

Any help would be appreciated.

Thanks

---

### Post by Habitual on 2016-06-09
I use these on my localhost:
~/.ssh/config
```
Host *
ServerAliveInterval 120
ServerAliveCountMax 30
ConnectTimeout 30
```
and I never get broken pipe messages any more, or rarely.

---

