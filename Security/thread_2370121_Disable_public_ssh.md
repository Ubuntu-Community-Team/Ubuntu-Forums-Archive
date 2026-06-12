---
title: "Disable public ssh"
date: 2017-08-30
forum: Security
---

### Post by theoldgnews on 2017-08-30
[COLOR=#242729][FONT=Arial]I would like to disable public access to ssh. How do I still access the server but block port 22? Do I need to create another instance just for openvpn (which is fine)? Is there a tutorial somewhere to basically "hide" ssh behind a vpn?

Thanks.[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-08-31
Go to the **/etc/ssh/sshd_config** and look for the entry at the top where the port to use is specified and change it from Port 22 to whatever you want. Some users change this default for extra security, though it's not a very strong change to the default.

If you do make that change you will need to let all the client machines know and they will have to change the port they use to the same value by either specifying each time in the ssh command or by editing the **ssh_config** file in the same **/etc/ssh** folder
```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
```

The best security measurer is to disable password authentication and make security key access the only way; see [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Disable_Password_Authentication](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Disable_Password_Authentication)

I am not able to help with yur VPN query as it is not something I have ever used.

---

### Post by pqwoerituytrueiwoq on 2017-08-31
If your issues is the thousands of automated ssh attacks you are seeing filling up your log files you can get rid of most by running on a different port number, you can also use fail2ban the decent bots will adapt and make a few attacks wait and do some more
I am not sure what your network setup is but if you expand your VPN to a location you have access to for 'remote' access you can remove the forward for port 22 on your router and access ssh vial the servers local network within the vpn

---

### Post by HermanAB on 2017-08-31
Simple: Edit /etc/ssh/sshd.conf and change port 22 to something else, then restart sshd.

Ferinstance:
Port 2222

---

