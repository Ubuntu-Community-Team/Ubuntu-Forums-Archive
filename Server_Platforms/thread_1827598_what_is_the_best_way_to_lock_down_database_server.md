---
title: "what is the best way to lock down database server?"
date: 2011-08-18
forum: Server Platforms
---

### Post by 007casper on 2011-08-18
what is the best way to lock down database server?

via ufw and iptables.

Should I close port 80 on it?

---

### Post by hawk2010 on 2011-08-18
by default ufw is turned off. Firstly you need to turn it on using
sudo /etc/init.d/ufw enable

next thing is that by default mysql server listens on its loopback address. that means it doesnt listen on your private or public IP interface. which means its safe by default.

You make want to run mysql_secure_installation which may delete test dbs and make your installation much secure.

---

### Post by 007casper on 2011-08-18
>>it doesnt listen on your private IP

how is it going to communicate with app server?

---

### Post by robgr85 on 2011-08-18
> **007casper said:**
> >>it doesnt listen on your private IP

how is it going to communicate with app server?

> 

next thing is that by default mysql server listens on its loopback address.


take a look at mysql config file, there is a lot of useful information commented. You may also read a bit about SELinux configuration.

---

### Post by SeijiSensei on 2011-08-18
> **007casper said:**
> >>it doesnt listen on your private IP

how is it going to communicate with app server?

If the application server runs on the same host, it will use the local interface.  For instance, Apache+PHP will talk to MySQL on the localhost interface by default.  Unless you need to run a remote client/server application, having everything be on one machine using localhost is the most secure since the DB traffic never leaves the machine.

If you're really concerned about protecting the information being stored, don't put it on an Internet-facing machine.  Run a separate database server behind a firewall.  Encrypting the database records can help, too.

---

### Post by 007casper on 2011-08-20
> Run a separate database server behind a firewall. Encrypting the database records can help, too.

It is on a separate database server behind a firewall. It is also encrpted.  However, I just want to make sure database server doesnt communicate internet-facing servers.  I want to only communicate with internal server on a specific IP.

Thats why I figured closing port 80 on database server would help.

---

### Post by Dangertux on 2011-08-20
I have a question about your set up : Is the application server that it is communicating with in front of the firewall? I see this commonly where there will be a firewall between the two, then the database server will be sitting on a network behind the firewall with a bunch of other systems. This is a REALLY bad idea. For some reason some sysadmins swear by this method, but it really provides a very unnecessary pivot point. 

Also the biggest issues with dbms security come down to these imho.

-- Default configurations
-- Empty passwords on users (sa, dba , root , etc)
-- permissions (it's really easy to give grant whatever user all privilages, it's also really stupid)

The second point is really more about web application security, but as it relates to your database it's important.

Make sure that whoever is designing the web app is sanitizing user input...SQL injection will always be a problem. That being said there isn't so much you can do about that if you're not involved in the application design aspect, HOWEVER -- failure to properly configure the above methods can change the impact of SQL injection. From say... Loss , or theft of data in one database to an attacker gaining a system shell on the dbms server. Obviously the latter is more upsetting because it could lead to the compromise of all databases and additional systems. Particularly if the network is configured in such away that compromising the database server allows a pivot through a firewall as I talked about in the first paragraph.

---

### Post by SeijiSensei on 2011-08-21
> **007casper said:**
> Thats why I figured closing port 80 on database server would help.

If it's only running as a database server and has no other tasks, I'd firewall off all the ports except 3306.  Another option is to set up a point-to-point [VPN]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") between the servers and bind MySQL to the VPN tunnel IP.

---

### Post by 007casper on 2011-08-22
on the database I have - 

```
ufw status...
--------------------------------------------------------------------------
Anywhere                   ALLOW       192.165.112.35 (application IP)
2222                       ALLOW       12.56.472.484 (client IP) 
3306                       ALLOW       192.165.112.35 (application IP)

```
does that look ok?

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
Note: Security by obscurity may be of very little actual benefit with modern cracker scripts. By default, UFW allows ping requests. You may find you wish to leave (icmp) ping requests enabled to diagnose networking problems.

how can I turn off the ping requests?

---

### Post by 007casper on 2011-08-22
> 
I have a question about your set up : Is the application server that it is communicating with in front of the firewall? I see this commonly where there will be a firewall between the two, then the database server will be sitting on a network behind the firewall with a bunch of other systems. This is a REALLY bad idea. For some reason some sysadmins swear by this method, but it really provides a very unnecessary pivot point. 

I am on vps.  I have a separate firewall for each server.  I am trying to allow only these two servers to communicate with each other.  I don't want database server to be open to public, nor other servers on the lan be connected to the database.

-- Default configurations
I should change the mysql port number. I am on 3306.  Probably, obscure port for mysql would be better. 

-- Empty passwords on users (sa, dba , root , etc)
checked.  No empty passwords.

-- permissions (it's really easy to give grant whatever user all privilages, it's also really stupid)
I should tune down the privileges.  However, sometimes plugins, app needs to be updated.  Maybe on those instances I will 'grant all' the privileges.

> 
Make sure that whoever is designing the web app is sanitizing user input...SQL injection will always be a problem. That being said there isn't so much you can do about that if you're not involved in the application design aspect, HOWEVER -- failure to properly configure the above methods can change the impact of SQL injection. From say... Loss , or theft of data in one database to an attacker gaining a system shell on the dbms server. Obviously the latter is more upsetting because it could lead to the compromise of all databases and additional systems. Particularly if the network is configured in such away that compromising the database server allows a pivot through a firewall as I talked about in the first paragraph.

at the moment, I don't want to offend you.... but I am using wordpress.  And at the rate I am growing, wordpress isn't going to last long. Regardless, sql injection is a real concern.

Above all, security is another major concern. I am mixing ufw with iptables.  After I covered these rule sets, I will try to set selinux, snort etc

---

### Post by Wim Sturkenboom on 2011-08-22
I would remove all database users that you don't need. You only need root@localhost and a dedicated user with just enough permissions to do what your application server has to do (e.g. absolutely no grant privileges and possibly no drop privileges (I'd rather drop on the mysql machine itself than from a remote application if dropping is necessary)). And a dedicated backup user (at localhost) that can only *select* and *lock tables*; I use a passwordless user for that.

A note and ufw and iptables (in case you did not know); ufw is just a frontend that generates a set of rules and uses iptables to 'enforce' those rules.

Oh, forgot that there is some dedicated debian user for maintenance after  updates.

---

### Post by 007casper on 2011-08-23
I am going to set it up as you suggested.  
root@localhost - all privileges
user@localhost - basic privileges
backup@localhost - lock and backup user

regarding ufw... thanks for the info. I didnt know it was a frontend for iptables.  I read in one of the ubuntu documentation is that you can ping ufw ports.

---

### Post by Dangertux on 2011-08-23
Why would that offend me I am confused. I use wordpress too lol.  It's actually a pretty decent cms. 

That also helps me help you the current version of wordpress is reasonably secure. Just watch your plugins also consider using a web application firewall such as mod security.

---

### Post by Wim Sturkenboom on 2011-08-23
> **007casper said:**
> I am going to set it up as you suggested.  
root@localhost - all privileges
user@localhost - basic privileges
backup@localhost - lock and backup user

Don't forget your application user that must be able to connect from the application server ;)

> **007casper said:**
> 
regarding ufw... thanks for the info. I didnt know it was a frontend for iptables.  I read in one of the ubuntu documentation is that you can ping ufw ports.Not sure how you can block icmp messages in ufw. I think it was said earlier in this thread that it's useful to have. I do block icmp and I'm seriously considering to unblock it. This is in an intranet and I have a (about) weekly fight with the IT department as the users of my applications all at a sudden can't connect to the lamp server. When IT tries to ping, it's blocked so they tell the user that the server is down. Next the user calls me, I check and it works. So I have to call IT and tell them what is wrong. The root cause is a misconfigured DNS somewhere but they don't seem to find that a problem.

---

### Post by Dangertux on 2011-08-23
To block icmp with UFW simply change the following in your /etc/ufw/before.rules file

```

-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```to
```

-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DENY
-A ufw-before-input -p icmp --icmp-type source-quench -j DENY
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DENY
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DENY
-A ufw-before-input -p icmp --icmp-type echo-request -j DENY

```

Coincidentally the same way you'd do it with iptables :-)

---

