---
title: "Controling multiple remote installs"
date: 2011-04-26
forum: Security
---

### Post by pAsM on 2011-04-26
Hello,
[INDENT]I have a rather complex setup that I am proposing. Our company has several remote workers who work out of their homes. We are planning on deploying multiple ubuntu desktops to the staff members however we are wondering if there is a centralized management tool. While I cannot share all of the details just yet, here is what I can share

1) The users will be behind their own NAT Firewall and setting up port forwarding for SSH is not really an option.
2) We need to be able to deploy commands via SSH to all units at once (100+ remote clients)
3) The users are not in the sudoers group, there is a special admin user on the machine to perform admin tasks (root crontab is the best way I can find)

I was thinking on setting up a cron to connect to a box that is available on the public internet and use a reverse SSH tunnel, but with 100+ connections, I am not sure if it could scale
[/INDENT]

---

### Post by Lars Noodén on 2011-04-27
Using an authentication agent and keys for the logins will make the process easier.

---

### Post by Lars Noodén on 2011-04-27
So you'd have 100+ machines connect to your server and each set up a reverse tunnel.  Then you'd have an admin user connect from your server to the remote machines using the reverse tunnels.  

Be sure that you have NTP running on the machines to synchronize the system clocks.
  
For the reverse tunnels you might want to use the [ServerAliveCountMax](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh_config) and [ServerAliveInterval](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh_config) configuration directives so that a broken connection can be detected more quickly.

---

### Post by spynappels on 2011-04-27
You could set up an OpenVPN server in house and connect each remote machine to this server, so the "client" initiates the connection, so no NAT or port forwarding issues at the client end.

You can do a lot with the OpenVPN conf file, including prohibiting clients from communicating with or even seeing each other on the VPN subnet.

You can then use a number of tools from the server side to control each individual client node, made easier by using Public Private Key authentication. I can't think of the name of it at the moment, but a search of the forums will throw up a tool which allows you to send the same command to each node through SSH at the same time.

We use this system to manage about 85 remote nodes and it works extremely well, with the added benefit of having all traffic from the remote nodes routed through an encrypted tunnel.

---

### Post by HermanAB on 2011-04-27
Parallel SSH is normally used to manage large numbers of identical machines.

---

### Post by spynappels on 2011-04-27
> **HermanAB said:**
> Parallel SSH is normally used to manage large numbers of identical machines.

Thanks HermanAB, that is the one I was thinking of.

---

