---
title: "Setting up WordPress on one Server and the Database on another"
date: 2023-10-05
forum: Server Platforms
---

### Post by jderosa32 on 2023-10-05
I have Wordpress installed on 1 Ubuntu Server (22.04) and the MySQL Database on another.

I configured the config.php file to use the DB information of the Database server. I specified it by IP address and I get the Error Establishing Database Connection Error.

This post here says you can do it: [https://stackoverflow.com/questions/39569889/is-it-possible-to-host-wordpress-database-from-other-server](https://stackoverflow.com/questions/39569889/is-it-possible-to-host-wordpress-database-from-other-server)

However, you need to make sure that the server will listen for the request from the WordPress Apache server.

To be more specific, these servers are both VMs running in a virtual box  on the same hardware, just doing this for testing purposes.

Any ideas how to do this? Thanks.

---

### Post by darkod on 2023-10-05
In general, it is true that you can use app on one server and db on another. In your case, you have various things to check to make sure you set up everything right.

Does telnet work? I believe the mysql port is 3306 so from the app server you should test the following to see if it can establish a connection:
```
telnet <db_server_ip> 3306
```

It could be a case where VBox puts the VMs as isolated, so in such case no traffic would flow between them. Do you have the VM NICs as bridged to your LAN, or set up to be part of the same network etc? I find it best to use them bridged so your VMs act like they are computers connected to your home LAN. That way you know there is no isolation between them.

Also make sure there is no firewall (iptables) active on the db server that would refuse the connection from the app server.

---

### Post by jderosa32 on 2023-10-05
I tried to telnet as you said and got the following:

[COLOR=#0000ff][FONT=courier new]telnet: Unable to connect to remote host: Connection refused[/FONT][/COLOR]

and I checked the firewall status of the DB Server:

[COLOR=#0000ff][FONT=courier new]$ sudo ufw status
Status: inactive

[/FONT][/COLOR]I can ping the DB server from the app server. FYI.

---

### Post by darkod on 2023-10-06
OK, so ping works remotely but 3306 doesn't. Did you set up mysql correctly? I don't remember much details, get on google some tutorials to set up and troubleshoot mysql and follow them in parts related to confirming mysql is listening correctly and accepting connections.

Checking the listening ports on the DB server, does it list it?
```
sudo netstat -plunt
```

If you didn't change mysql standard port number you can use something like:
```
sudo netstat -plunt | grep 3306
```

That will show you if mysql is listening on 3306 and to which IPs it is binded.

---

### Post by darkod on 2023-10-06
Review these short instructions how to allow remote conections to mysql and see if it helps. I think by default it listens only to local connections, so probably you will have to do the part with the bind-address if you didn't do it already.
[https://easyengine.io/tutorials/mysql/remote-access/](https://easyengine.io/tutorials/mysql/remote-access/)

---

