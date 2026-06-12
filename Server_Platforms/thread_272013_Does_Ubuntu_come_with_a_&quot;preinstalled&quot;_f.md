---
title: "Does Ubuntu come with a &quot;preinstalled&quot; firewall?"
date: 2006-10-05
forum: Server Platforms
---

### Post by GTHvidsten on 2006-10-05
Having gotten everything up and running on my server, I thought it was about time I got the software on my laptop to work with the server. Especially MySQL, since some software I use connect to the database on my server. This worked just fine on my previous installation, but now I just can't get it to work. Whenever I try to connect to the mysql server using the mysql client on my laptop I get this error:

ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.1.1' (10061)

Since I can connect just fine directly from the server, and I have made a user is the 'user' table in the 'mysql' database that allows me to connect from my laptop's IP-address, I'm suspecting Ubuntu comes with some kind of firewall that doesn't have TCP port 3306 open by default.
How can I make this work (either by tweaking the firewall, if it is there, or by making some unknown changes to the mysql tables)?

---

### Post by jpkotta on 2006-10-05
As far as I know, all Linux firewalls use iptables.  This should show the settings.  Are you sure you have a daemon up and properly configured on the server?

```
[jpkotta@goedel fah_install](0)$ sudo iptables --list
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

Also,
```
nmap -p 3306 192.168.1.1
```

---

### Post by GTHvidsten on 2006-10-05
Wow. It seems iptables is installed. I just couldn't find the config file in the location I anticipated, which obviously confused me. However, doing a 'locate iptables' I can't find where the file I need to edit to open / close certain ports is located. Could you please give me the location of the config file?
Also, do you know of any good iptables frontend that will make it easier and more intuitive to configure it?

---

### Post by sonic2000gr on 2006-10-05
Ubuntu has iptables, but no rules are active by default, so this is not probably a firewall problem. 

From your error, I assume you are trying to access mysql from a network machine. By default MySQL listens only on the localhost (loopback address) that is 127.0.0.1
From your post, the server seems to be on 192.168.1.1

If this is the case, just edit the file /etc/mysql/my.cnf
and add the line:

```
bind-address = 192.168.1.1
```

the restart MySQL:

```
sudo /etc/init.d/mysql restart 
```

you should then be able to access MySQL from the network. (This should also be a good time to consider strong passwords and a firewall...)

---

### Post by jpkotta on 2006-10-05
Disclaimer: I don't have too much experience here, but I'll try.  

I don't think iptables has configuration files.  I think you configure it by running scripts that call iptables with various options.  

I use Firestarter for a frontend.  It's easy to use but it does have limitations (most notably, it can't handle two interfaces).

---

### Post by sonic2000gr on 2006-10-05
You will also find a small tutorial for a do-it yourself iptables configuration plus a script to load it on my own wiki site, [http://debian12.dyndns.org]("http://debian12.dyndns.org")

Note this is running on my home server and is bound to be slow at times...

---

### Post by GTHvidsten on 2006-10-05
> **sonic2000gr said:**
> I assume you are trying to access mysql from a network machine. By default MySQL listens only on the localhost (loopback address) that is 127.0.0.1

That was exactly it. Added your suggested line, and I can now connect through a network machine just fine. Thanks a lot :)

I'm still interrested in tweaking iptables, though. I'll give your site a read through, sonic200gr.
In my previous server installation (Fedora Core) I had the file that set up iptables located here:

/etc/sysconfig/iptables

I'm guessing iptables on Ubuntu has a similar file somewhere.


EDIT:

Firestarter - The biggest limitation, though, is that it's too much of a GUI frontend. I don't run X, so I would need a textbased frontend ;)

---

### Post by sonic2000gr on 2006-10-05
> **GTHvidsten said:**
> 
In my previous server installation (Fedora Core) I had the file that set up iptables located here:

/etc/sysconfig/iptables

I'm guessing iptables on Ubuntu has a similar file somewhere.

Not really, as someone else said iptables alone does not have any configuration file -it is all saved in memory.
However when you create a set of rules you wish to save, there is a command:

```
 sudo /sbin/iptables-save > myrules 
```

will save you rule set to a file called myrules
if you execute:

```
 sudo /sbin/iptables-save 
```

without a file name, you will see the rules on screen.
To load your rules back from a file, you would use:

```
 sudo /sbin/iptables-restore < myrules 
```

I have made a script based on the above, and is all on my site so have a look ;)

---

### Post by Macchi on 2006-10-05
Have you tried FireHOL? In my opinion it creates good firewalls for Linux.

Firehol is a higher level notation for the configuration of iptables. It can be easily installed from the universe repositories and is configured through a text file. In the long run it is also more reliable since it is easier to understand, install and maintain. Thus reducing the risk for potential mistakes around iptables that could lead to security holes on the firewall.

---

### Post by thesofa on 2006-10-21
This may not be a firewall issue, have a look at this post and the answer below
[http://ubuntuforums.org/showthread.php?t=277874&highlight=mysql]("http://ubuntuforums.org/showthread.php?t=277874&highlight=mysql")

---

### Post by Ronbo on 2006-10-21
I've been playing with Firehol and for the most part it seems to work OK,  although it seems ast though there may be an issue in Edgy.  See my post [http://www.ubuntuforums.org/showthread.php?t=281535](http://www.ubuntuforums.org/showthread.php?t=281535) I haven't tried it in Dapper so I don't know if the problem exists there.  Two tutorials I was using were:

[http://www.unix-tutorials.com/go.php?id=662](http://www.unix-tutorials.com/go.php?id=662)
[http://www.unix-tutorials.com/go.php?id=663](http://www.unix-tutorials.com/go.php?id=663)

and the website is at [http://firehol.sourceforge.net](http://firehol.sourceforge.net)

---

