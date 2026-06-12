---
title: "Server suddenly has no network connection"
date: 2015-02-19
forum: Server Platforms
---

### Post by Vaindil on 2015-02-19
*(Also posted on AskUbuntu [here]("http://askubuntu.com/questions/587447/server-suddenly-not-accepting-any-connections") if you would like to answer there. I will cross-post the final answer regardless.)*

I was in the middle of working on a Python script and I was disconnected from the SSH session. In case it matters, the basic algorithm is below.

[LIST]
[*]Define [sendmail function]("http://www.masnun.com/2010/01/01/sending-mail-via-postfix-a-perfect-python-example.html")
[*]Use [requests]("http://docs.python-requests.org/en/latest/") to check if a specific address is reachable
[LIST]
[*]If timeout occurs (>10 seconds), send email using sendmail and sys.exit(1). This is within a `try/except` block
[*]If address returns a 502 error code, send email
[/LIST]

[*]End of script
[/LIST]
I had tested the script several times and received a few errors, so I went back in to edit. While I was editing I was disconnected from SSH (PuTTY said "software caused disconnect"). Now the server is refusing, I assume, all incoming connections. I cannot connect to the web server (port 80) from a browser--Chrome says ERR_CONNECTION_REFUSED--and I can't telnet (port 25) or SSH (port 649, we manually changed this)--PuTTY says the connection was refused.

I have access to the physical server so I can do whatever is necessary. I rebooted the server and made sure all of the right ports are added to ufw, still nothing. This is a fully up-to-date Ubuntu Server 14.04.1. The server is not running anything like fail2ban to prevent brute-force attacks.

The output from netstat -plntu:
```
Proto Recv-Q Send-Q Local Address      Foreign Address     State      PID/Program name
tcp        0      0 0.0.0.0:25         0.0.0.0:*           LISTEN     1039/master
tcp        0      0 0.0.0.0:649        0.0.0.0:*           LISTEN     873/sshd
tcp        0      0 127.0.0.1:3306     0.0.0.0:*           LISTEN     1027/mysqld
tcp6       0      0 :::25              :::*                LISTEN     1039/master
tcp6       0      0 :::649             :::*                LISTEN     873/sshd
tcp6       0      0 :::80              :::*                LISTEN     1181/apache2
```

Contents of /etc/hosts (the local IP address is correct as confirmed by ifconfig, and I'm able to ping it):
```
127.0.0.1              localhost
127.0.1.1              machine-name
<local ip address>   machine-name     machine-name

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

---

### Post by Vaindil on 2015-02-19
I have no idea what happened, but the problem has resolved itself. After the described problem occurred, the system lost all connectivity to both the internal network and the internet (it couldn't be pinged by anything and it couldn't ping anything). It still claimed that it had an IP address and was connected, however. Now, through no action of my own (literally -- I just tried pinging one last time out of desperation) it is working again. Connections are not being refused, web access and SSH work fine.

---

