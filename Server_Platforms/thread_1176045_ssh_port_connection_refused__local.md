---
title: "ssh port connection refused / local"
date: 2009-06-01
forum: Server Platforms
---

### Post by TheMagician001 on 2009-06-01
Hi im having problems with my server...

Fresh installed Ubuntu 9.04 Server  with LAMP + OPENSSH Server

Using ssh XXXXXXXXXXX.COM -p 22

I installed webmin and all required libaries and changed webmin port to 30000
then
sudo reboot

system came back up

I then logon with ssh   xxxxxxxxxxxxx.com - p 22 again sucsessfully...
I then logon to webmin  xxxxxxxxxxxx.com:30000 sucsessfully...

I come HOME

try to logon t the server with ssh I get connection refused
try webmin and  Firefox can't establish a connection to the server at 192.168.0.193:30000.

go back over to my friends house with the laptop and it works again... come home and nothing...

my firewall is open on port 22 and 30000 

I can connect remotely but not local

Thanks in advance
Mike

---

### Post by brian_p on 2009-06-02
> **TheMagician001 said:**
> 

I can connect remotely but not local

192.168.0.193 is definitely the ip address of the machine?

```
ssh user@92.168.0.193
```

fails?

---

