---
title: "Ubuntu 20.04 Security Checkup"
date: 2020-11-22
forum: Security
---

### Post by andyuk2 on 2020-11-22
Hello everyone,

I am setting up some import Ubuntu servers which will be running version 20.04.

I would just like to run my security setup passed you to make sure I haven't missed anything important.

On all the servers I will be installing:

[LIST=1]
[*]    OpenSSH Server 
[*]    Fail2Ban 
[*]    UFW 
[*]    Bash Login Notifications 
[/LIST]

[B]OpenSSH Security
[/B]Only the Ubuntu user will be permitted to login via SSH using a certificate.
Here are the changes I have made to the sshd_config file:
```
AllowUsers ubuntu
PermitRootLogin no
PasswordAuthentication no
AllowTcpForwarding no
ClientAliveCountMax 2
Compression no
LogLevel VERBOSE
MaxAuthTries 2
MaxSessions 2
Port 44558
TCPKeepAlive no
X11Forwarding no
AllowAgentForwarding no
Protocol 2
PubkeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys
```

**Fail2Ban Security**
Here are the changes I have made to jail.conf
```
bantime  = 7d
findtime  = 1h
maxretry = 3
destemail = email@address.com
mta = mail
```

**UFW Security**
Here are the rules I have setup
```
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow from <myip> to any port 44558 proto tcp
sudo ufw enable
```

Additional rules will be added to specific servers based on it's purpose. For example:
My web server will only allow incoming traffic on port 443.
My mysql server will only allow incoming traffic from the apache web servers.

**Bash Login Notification**
I've also added the following line to the .bashrc to let me know of any logins.
```
echo 'ALERT - '$USER' shell access found on '$HOSTNAME' on:' `date` `who` | mail -s "Alert: User shell access" email@address.com
```


If you have any comments on the above I would love to hear them. Also, if you can think of anything else which might help, please let me know.

Kind Regards
Andy

---

### Post by EuclideanCoffee on 2020-11-22
Hello glad to do a review.

So far, besides the MySQL configuration, you configuration looks excellent. And except for the fail2ban configuration (I used a script to ban any server pinging me or using ssh x times), your setup looks a lot like my personal website, which makes me think you've already done that much research and only have time for a small project. I encourage you to play around with fail2ban. I have it set where the only acceptable route a user may choose is via 443 with a lot of HTTP mods enabled to prevent SQL injection and password attacks on web pages. Anyone using SSH, telnet, or port knocking are banned. Another trick is to force port knocking to not deny but to wait. Not essential but fun if you want to deploy.

For your MySQL configuration, it depends heavily on what you have stored there. I hope it's a secure installation. I would also recommend placing it in a place that is not Internet accessible. How would your server reach it? Use private IP space, meaning LAN or use a service like AWS or Digital Ocean to setup a boundary that is not reachable from online.

If these are very important servers, I recommend that you use a formal security framework like CIS. Ubuntu Advantage provides a CIS authorized image, which will better protect your server. There is also a FIPS option that works for Azure or AWS.

---

### Post by andyuk2 on 2020-11-22
Hi EuclideanCoffee,

Thanks for that :)

I have added a diagram below of my inital design thoughts.

[IMG]https://i.ibb.co/rb4fwgk/Untitled-Diagram.png[/IMG]

First the user will hit the Web Application Firewall. This will be a cloud service which is designed to protect against DDOS, hackers, bad bots, SQL injection, cross site scripting, and loads of vulnerabilities. It will also force HTTPS connections from the user, and also to the load balancer. It will not be possible for users to connect directly to the load balancer as this will be blocked.

If allowed, the user will then hit my Nginx load balancer which will proxy traffic to either Web01, Web02, or Web03. These web servers will be on a public IP address, but UFW rules will be added to only allow traffic from the load balancer directly.

Likewise, the SQL and FS server will only allow traffic from the web servers.

I was going to setup port knocking in case my IP address changed, but I now have VNC access to the boxes so this is no longer necessary.

I'll be taking a look into CIS next ;)

---

### Post by EuclideanCoffee on 2020-11-22
That looks sleek! Yes, CIS standardization would be a good framework. Then move on to continuous integration with Git or GitLab. You can pull it into a system configuration management tool like Puppet, Salt, or Anisble to maintain your compliance and automate some tasks.

---

### Post by skipbarker on 2020-12-07
Looks pretty close to my default security setup for new servers. Looks good to me.

---

