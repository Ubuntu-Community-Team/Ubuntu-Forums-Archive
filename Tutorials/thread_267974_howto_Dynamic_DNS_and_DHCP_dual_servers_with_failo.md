---
title: "howto: Dynamic DNS and DHCP dual servers with failover"
date: 2006-09-29
forum: Tutorials
---

### Post by Endwin on 2006-09-29
So you want to setup a few servers with redundant Dynamic DNS and dual DHCP that can handle one of them going out. Welcome to fun! 

_Tools of the trade..._

Let's assume we want 2 servers a master and a slave. Our network will be 10.10.0.0. Master will have an IP of 10.10.0.1, and slave will have 10.10.0.2. We have bought the domain [www.examplechangeme.com](www.examplechangeme.com)

_Install DHCP and Bind9..._

```
sudo aptitude -R install dhcp3-server bind9
```
Alright the setup...

**MASTER**

Master has some files we will want to mess with, first start with the main configure file. We don't need to make many changes to this one.

```
cd /etc/bind/
nano named.conf
```

At the bottom put...
```

controls {
	inet 127.0.0.1 allow {127.0.0.1; 10.10.0.1; 10.10.0.2; } keys { "rndc-key"; } ;
};
```

Wow, that is a lot of strangeness let us break it down.

**Controls** <= This block tells the bind server, "Hey these nice people here will be allowed to update you, please let them!"

**inet 127.0.0.1** <= Who am I modifying? Myself. Here we say we are talking about the local bind server.

**allow {127.0.0.1; 10.10.0.1; 10.10.0.2; }** <= here I am saying who (by IP) is allowed to modify the DNS enteries. I am saying I can locally modify (hence the 127.0.0.1) also through my network connection (10.10.0.1) modifications can take place. I will also allow the slave machine (10.10.0.2) to modify the server as well. Feel free to add additional servers/remove servers as your needs permit.

**keys {"rmdc-key";} ;** <= This is the name of a key that is generated to authorize that the process/computer is allowed to modify the DNS. We will get more into this later. The name of the key (in " " ) is what is given by the default ubuntu install you may need to change this for other systems, or feel free to rename it as your own. Just remember to carry it on through the rest of this guide.

Ok done with named.conf save it and get ready for the next bit.
```

nano named.conf.local
```

Here comes some of the fun bits...

This usually starts off as a blank file with some comments at the top. The purpose of this file is to define all the user only zones (read domain names/networks). Again I will dump what I did and then work through it. Add the following to the end of the file (which is pretty much the begining just past the comments.
```

include "/etc/bind/rndc.key";

zone "examplechangeme.com" {
	type master;
	file "/etc/bind/examplechangeme.com.zone";
	allow-update { key "rndc-key"; };
	allow-transfer {10.10.0/24; };
};

zone "0.10.10.in-addr.arpa" {
	type master;
	file "/etc/bind/rev.0.10.10.in-addr.arpa";
	allow-update { key "rndc-key"; };
	allow-transfer {10.10.0/24; };
};
```


Well thats a mouthful...

**include "/etc/bind/rndc.key";** <= This line includes the file rndc.key which was generated as a MD5 hash to be used to validate programs updating the DNS. Sort of like an include statement in programing. It dumps the contents of the file in the spot where the include is put.

**zone "examplechangeme.com" {** <= Here we are defining a new zone whose name is examplechangeme.com. It can be anything you want to make a domain or sub domain for. It could be home.lan or linux orhome.linux.lan.moo.cow.milk you get the idea. =)

**type master;** <= Since this is the master (Read main) DNS server we have to say so here. On the slave this will be diffrent. See if you can guess what it will be. HINT it starts with an s.

**file "/etc/bind/examplechangeme.com";** <= Here we say where the address resolution database will be located. This is the file that holds the NAME => IP information along with some information. We will talk about the contents of this file later.

**allow-update { key "rndc-key"; };** <= Here we are saying who/what can update this zone. Here we say anyone who comes to us with the rndc-key will be allowed to update the DNS.

**allow-transfer {10.10.0/24; };** <= Here we are saying who can have a copy of our zone. (In this case I am saying anyone on the 10.10.0.0-10.10.0.255 network. This can be changed to just a set of IPs or left as is. For example you could have allow-transfer {10.10.0.2; 10.10.0.200;};

**zone "0.10.10.in-addr.arpa" {** <= Odd looking zone... This is a reverse lookup database one of these typically accompany a named zone. This file allows for reverse lookups. Say you typed in 10.10.0.5 and want to know what the name associated with that was. Everything else in the definition is the same as above.

On to creating the actual database files we made reference to in the two file directives above. From my research there are a few ways to make one of these files, the simplest method for me was to make a copy of one of the stock db files and modify it to my needs. So let's do that.
```

cp db.empty examplechangeme.com.zone
cp db.empty rev.0.10.10.in-addr.arpa

```
Let us edit....
```

nano examplechangeme.com.zone

```
Ok here I will display an example and explain as much of it as I know.
```

$TTL 86400
examplechangeme.com.       IN      SOA     master.examplechangeme.com. root.localhost. ( 
                              1       	; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                          86400 )       ; Negative Cache TTL

examplechangeme.com.	IN	NS	master.examplechangeme.com.
examplechangeme.com.	IN	NS 	slave.examplechangeme.com.

master			IN	A	10.10.0.1
slave			IN	A	10.10.0.2

```
From the top!

**$TTL 86400** <= Not exactly sure but from context I think it is the time to live (in secconds) of the names on the server.

**examplechangeme.com.     IN      SOA     master.examplechangeme.com. root.localhost. ( **<- sets the domain. The master.examplechangeme.com. bit needs to be there so we know this is the main server the one following looks like some sort of place holder I decided to let it be as it is.

The long bit with serial, refresh etc sets the times for the name leases. Serial according to some sites is important to increment every time the file is modified. However in my testing I never changed it and it apeared to work fine.

```
examplechangeme.com.	IN	NS	master.examplechangeme.com.
examplechangeme.com.	IN	NS 	slave.examplechangeme.com.

```
Here we set what the name servers are (hence the NS) make sure to resolve the names bellow.

```
master			IN	A	10.10.0.1
slave			IN	A	10.10.0.2

```
Here we set some static names (good for servers) here I define master, and slave. You can put other things (and probably should) here like www, @, mail etc. One thing of note mail servers are dified diffrently the two ways I have seen this is...
```

examplechangeme.com.      IN      MX     10       mta.examplechangeme.com.

```
and 
```

@       IN      MX      1       mail.examplechangme.com.

```
Make sure to define mail, mta, and @ bellow in the static sections if you add in mail servers.

Onto the reverse lookup database!

```

$TTL 86400
@       			IN      SOA     master.examplechangeme.com. root.localhost. ( 
                              1       	; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                          86400 )       ; Negative Cache TTL

					IN	NS	master.examplechangeme.com.	
					IN	NS 	slave.examplechangeme.com.

1					IN	PTR	master.examplechangeme.com
2					IN	PTR	slave.examplechangeme.com
```

A lot like above with a few differences. 

**@       			IN      SOA     master.examplechangeme.com. root.localhost. ( **<= Note here we replaced examplechangeme.com. with @

Bellow that at the name servers we dropped the proceeding examplechangeme.com.

In our static resolution section we replaced the names with the last numerical address, and instead of A we put PTR. Since we are doing a reverse lookup we put the name in for the reverse lookup. 

Save your changes and we will go to the next bit. In the folder we are in which should be /etc/bind/ we should make sure the files we will be modifying are owned by bind. Do a simple

```
chgrp bind * 
```

and that should help resolve reading/writing issues later on.

Let's take a look at that key file. We are not going to edit it I am just putting an example so you understand its format.
```

more rndc.key

key "rndc-key" {
        algorithm hmac-md5;
        secret "fjs8FjKDo320jpWdmvcdwf==";
};
```

NOTE: This is not my key I just made it up. However this is the file that we included in our named.conf.local and note the name of the key is rndc-key this is an arbitrary name. IE it can be whatever you want. I just left the default, but if you want to you can change it.

Now we need to copy our key so that the dhcp server can use it.
```

cp /etc/bind/rndc.key /etc/dhcp3/.

```
Head on over to the dhcp directory.
```

cd /etc/dhcp3

```
Make sure dhcp can read our key...
```

chown root:dhcpd rndc.key

```
And now we edit the files...
```

nano dhcpd.conf

```
This file comes with a lot of commented out examples we will ignore them and just modify the top, and add our own information. At the top you will see 
```

ddns-update-type none;

```
change it to
```

ddns-update-style interim;
```

next in
```

# options definitions common to all supported networks...
option domain-name "example.com";
option domain-name-servers ns1.example.con, ns2.example.com;

```
change it to 
```

option domain-name "examplechangeme.com";
option domain-name-servers 10.10.0.1, 10.10.0.2;

```
leave the default lease time, and max lease time alone, unless you want to change them.

after the lease times put:
```

one-lease-per-client on; 
```

Bellow that is:

```
# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
# authoritative;

```
Uncoment authoritative so it looks like...
```

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;
```


The log bit I left alone, however bellow it I put in our failover for dhcp directive.
```

failover peer "dhcp" {
		primary;
		address 10.10.0.1;
		port 519;
		peer address 10.10.0.2;
		peer port	520;
		max-response-delay 60;
		max-unacked-updates 10;
		mclt 600;
		split 128;
		load balance max seconds 3;
}

```

Ok the above works like this, failover peer "dhcp" { <- here we are declaring a failover peer and for the sake of simplicity we are naming it dhcp I could name it moo-cow or cookie-milk it is something so we can reference this failover peer. You can define multiple ones for different networks I think and as such have multiple decelerations of the above.

I set this server as the primary with an address, a port, and then I declare the peer (my failover/backup dhcp server) with an address and a port. Note the ports have to be different. From the few examples I was able to find 519 and 520 are the ones most used for this.

Max response delay, unacked, mclt, split, and load balance I am not sure on their exact purpose I think the max resonse is how long it will wait for the other server to respond before it takes over. Anyway the default settings here should work for most people.


Bellow our failover we should include our key, and the zones that we will be updating.
```

include "/etc/dhcp3/rndc.key";

zone examplechangeme.com. {
	primary 10.10.0.1;
	key rndc-key;
}

zone 0.10.10.in-addr.arpa. {
	primary 10.10.0.1;
	key rndc-key;
}
```

What this does is define the zones the DHCP is to update whenever a lease is given. Say bob.examplechangeme.com logs in gets an IP the DHCP server notifies the DNS server of the lease and modifies it so that whenever someone types in bob.examplechangeme.com they always get bob's machine no matter what address bob may have. Primary sets the server we will update and the key is to let the server know we are legitimate.
Now to make our subnet. bellow the zone section put.

```
subnet 10.10.0.0 netmask 255.255.255.0 {
	pool {
			failover peer "dhcp";
			range	10.10.0.50 10.10.0.254;
			deny dynamic bootp clients;
			allow unknown-clients;
		}
	option routers		10.10.0.1;
	option broadcast-address 10.10.0.255;
	option subnet-mask	255.255.255.0;
}

```

subnet 10.10.0.0 netmask 255.255.255.0 { <- here we define our network I am using subnet 10.10.0.0 with a mask (what bits of the Ips are mine) of 255.255.255.0 which means I have 253 Ips to play with.

```
	pool { 		
			failover peer "dhcp";
			range	10.10.0.50 10.10.0.254;
			deny dynamic bootp clients;
			allow unknown-clients;
		}

```
This section is specific to failover DHCP if you just want normal DHCP drop it all and just keep the range part. We set the failover peer definition (defined above) then the range of Ips it is allowd to toss out. The deny dynamic bootp clients; line is in reguards to a protocol for thin clients. If you have thin clients failover, from what I can tell, is not supported in the current dhcp server. The final line allow unknown-clients; lets you get an IP from the server. For some reason without it I was unable to grab an IP. You don't need it in a non failover setup.

```

	option routers		10.10.0.1;
	option broadcast-address 10.10.0.255;
	option subnet-mask	255.255.255.0;

```
This is info that you pass to the clients that connect. Your router may be a different IP and setting up a router is beyond this long howto.


We are done editing the master server! Our final finishing thing is to get a copy of the rndc.key file to the slave computer. You can do this via sftp, or copy/paste the contents of the file over. However you want to do it.


**SLAVE MACHINE**

Make sure you copied the key from master over to the slave. Put a copy in both /etc/bind/ and /etc/dhcp3 in bind make sure the group is bind and for dhcp make sure the group is dhcpd. 

in /etc/bind
```

chgrp bind rndc.key
```

in /etc/dhcp3

```
chgrp dhcpd
```

We will start with the DNS server first, and edit named.conf.
```

cd /etc/bind
nano named.conf
```

Like on master we will do the same here at the end of the file put. 
```

controls {
	inet 127.0.0.1 allow {localhost; 10.10.0.1; 10.10.0.2;} keys { "rndc-key"; };
};
```

Save exit and then to named.conf.local
```

nano named.conf.local

```
Again we have an empty file, things will be a little different. At the end of our comment file put:

```

zone "examplechangeme.com" {
	type slave;
	file "/etc/bind/examplechangeme.com.zone";
	masters {10.10.0.1; };
};

zone "0.10.10.in-addr.arpa" {
	type slave;
	file "/etc/bind/rev.0.10.10.in-addr.arpa";
	masters {10.10.0.1;} ;
};
```

A lot like before, the type of server is a slave (answer to pop quiz way at the beginning). File says where we are saving the files, and masters lets the slave know where to get the DNS information from.

Save and close.

We don't have to make our own databases for the slave since it will grab that information from the master. So that saves a lot of effort. Off to DHCP land, and dhcpd.conf!

```
cd /etc/dhcpd

nano dhcpd.conf

```

A lot of this will be the same as in master with a few differences. Since we will assume that if master is down we cannot modify the DNS on master I told it to modify the DNS on the slave. So whenever master is down slave's DHCP server takes over gives out IPs and modifies slave's DNS.
```

ddns-update-type interim; 


option domain-name "examplechangeme.com";
option domain-name-servers 10.10.0.1, 10.10.0.2;

default-lease-time 600;
max-lease-time 7200;

one-lease-per-client on;

authoritative;

failover peer "dhcp" {
	secondary;
	address 10.10.0.2;
	port 520;
	peer address 10.10.0.1;
	peer port 519;
	max-response-delay 60;
	max-unacked-updates 10;
}

```
Here we just change a few things around. We are the secondary server and we set things that were the peer on the master. Make sure to keep the ports and IPs straight.
```

include "/etc/dhcp3/rndc.key";

zone examplechangeme.com. {
	primary 10.10.0.2;
	key rndc-key;
}

zone 0.10.10.in-addr.arpa {
	primary 10.10.0.2;
	key rndc-key;
}

```
Note the change in the IP for the zone definitions. This is so the slave updates the DNS for itself whenever the master is down.
```

subnet 10.10.0.0 netmask 255.255.255.0 {
	pool {
			failover peer "dhcp";
			range 10.10.0.50 10.10.0.200;
			deny dynamic bootp clients;
			allow unknown-clients;
		}
		option routers 10.10.0.1;
		option subnet-mask 255.255.255.0;
		option broadcast-address 10.10.0.255;
}
```


Save and exit.

Wow I think we are done. On both servers issue the following commands to restart the dhcp and bind servers.
```

/etc/init.d/bind9 restart;
/etc/init.d/dhcp3-server restart;

```
In theory things should be working. Here are some troubleshooting/testing tips. This assumes your client machine is also a linux box.

NOTE: For the dynamic name update for DHCP to DNS you may need to edit /etc/dhclient.conf uncomment send host-name " STUFF HERE "; and replace STUFF HERE with the name of the machine, like bob, or joe, or mail etc.

Also make sure both master and slave's clocks are in sync DHCP and DNS failover/updating is VERY dependent on time. Set a cron job to update time.
[B]
dig[/B]

example 

```
dig examplechangeme.com
```

You should get back something like this.
```

; <<>> DiG 9.3.2 <<>> examplechangeme.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51050
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;www.examplechangeme.com.              IN      A

;; ANSWER SECTION:
www.examplechangeme.com.       120     IN      CNAME   examplechangeme.com.
examplechangeme.com.           120     IN      A       10.10.0.1

;; AUTHORITY SECTION:
examplechangeme.com.           120     IN      NS      master.examplechangeme.com.
examplechangeme.com.           120     IN      NS      slave.examplechangeme.com.

;; Query time: 187 msec
;; SERVER: 10.10.0.1#53(10.10.0.1)
;; WHEN: Fri Sep 29 11:15:05 2006
;; MSG SIZE  rcvd: 108

```
You are looking for the answer section to see if your IP was set. What this program does is check to see what the DNS has for whatever you sends its way.

dhclient is useful to see if the dhcp server is tossing out IPs like it should. The most useful flags were -r which releases the lease dhclient has.

example 

```
dhclient -r
dhclient
dhclient eth0 

```
If you have multiple cards using dhcp include the ethX in there so that you don't reset all of them.

Check /var/log/daemon.log and /var/log/syslog on the master and slave. I found this very helpful in tracking down problems.

You will want to edit /etc/dhcp3/dhclient.conf uncomment supersede domain-name and 
prepend domain-name-servers. replace the domain name with your domain name and add to the domain-name-servers the IPs of your domain names. By doing so resolv.conf will always keep that infotmation if you are on a dynamic IP connection. 


I hope this helps some people when I went on-line and looked for how to do dynamic dns, failover dns, dhcp failover, and the like I found poor/little documentation. If you have questions I will do what I can to help!

---

### Post by hellmet on 2006-10-13
wow that is a whole lotta
..
was thinking of doing this..
you've made it possible.
will possibly set it up tomorrow..

---

### Post by hellmet on 2006-10-14
uh... dude.. is it possible for you to cut short some of it..
and pm me ..? coz I have just one system, and one ISP
connection.. so I just need to setup Dynamic DNS server 
on it..

---

### Post by Endwin on 2006-10-16
It is actually quite easy to set it up for just one server (I did it at home) All you need to do is follow the master part and just remove the stuff refering to the other server (Remove the failover sectoon of DHCP) and drop the pool section to just range 10.10.0.50 10.10.0.254

---

### Post by btdown on 2006-10-16
Thank you for this...I'll have to try it out.

BT

---

### Post by simidau on 2006-11-28
While it looks like it's working - have not checked that removing the master will allow everything to continue.

I looked in syslog and and found the following lines on startup of dhcpd and another unsure line every time a client gets an address.

Master server is normal

Startup message 
--------------------------------------------------------------
Nov 29 14:37:47 server2 dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Nov 29 14:37:47 server2 dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Nov 29 14:37:47 server2 dhcpd: All rights reserved.
Nov 29 14:37:47 server2 dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 29 14:37:47 server2 dhcpd: Wrote 0 leases to leases file.
Nov 29 14:37:48 server2 dhcpd: failover peer dhcp: I move from recover to startup
Nov 29 14:38:02 server2 dhcpd: failover peer dhcp: I move from startup to recover
---------------------------------------------------------------

The last two lines ebing the ones I am unsure of?

Then when a client gets an address I get the following.
---------------------------------------------------------------
Nov 29 14:40:47 server2 dhcpd: failover peer dhcp: unexpected error
---------------------------------------------------------------

There is another error popping up
---------------------------------------------------------------
Nov 29 14:39:17 server2 dhcpd: failover peer dhcp: address not available

---------------------------------------------------------------

Any ideas?

---

### Post by Endwin on 2006-12-01
I would say it looks like something is misconfigured or needs to be tweaked. The lines

> Nov 29 14:37:48 server2 dhcpd: failover peer dhcp: I move from recover to startup
Nov 29 14:38:02 server2 dhcpd: failover peer dhcp: I move from startup to recover

indicates the mode the DHCP server is in. As for 
> Nov 29 14:40:47 server2 dhcpd: failover peer dhcp: unexpected error

and 

> Nov 29 14:39:17 server2 dhcpd: failover peer dhcp: address not available

I would need to see the setup for the files. Also check in /var/log/daemon.log. That sometimes gives a more detailed description of what is wrong then syslog.

---

### Post by zigford on 2006-12-02
Wish I had seen this earlier.  I had tried to configure this in the past, but failed.

Now seeing you point to /var/log/daemon

I had no idea thats where bind info goes and I was able to fix my setup in seconds. Amen!

---

### Post by makadam on 2007-01-08
Hi.

Thanks for this wonderful tutorial.

Best regards

Makadam

---

### Post by Abhi Kalyan on 2007-03-15
That is a very detailed work that you have crafted, Thank you a Tonne.
Hope the following request does not annoy you.
"When you mean "master" is it the hostname of the primary DNS server or is it a code that points the services to accept this system as master?"
Like the Primary DNS server  is "master.examplechangeme.com"
Hostname: master
Hostname -f: examplechangeme.com
Sorry if this is really a very small doubt.
hope you could throw some light on this subject.
I tried the WHole Manual asubstituteing things and am still not able to get it right.
Thank you

---

### Post by Abhi Kalyan on 2007-03-16
Tried every bit of this tutorial almost for two days continuously.
Abhi Kalyan=myself is blown to bits.
Am not able to get this thing right.
Please Help.
Hope i will see the light some day

---

### Post by Abhi Kalyan on 2007-03-16
The DHCP is working beautifully,
But the DNS is not working at all.
I dont know where am screwing it real bad.
Hope some one can help
All the best 
Thank you

---

### Post by JeevesBond on 2007-03-25
This tutorial has fixed my DNS/DHCP woes and everything seems to be working well.

Abhi, what exactly is the problem you're seeing? If it's DNS that's not working could you post the results of grep 'named' /var/log/syslog (hope that's right)?

---

### Post by mr_joe_rollins on 2007-04-30
guys,

thanks for the article and follow ups. Having an issue though. DHCP primary and secondary are up; so is master and slave named. Everything works fine when the master is responding. However, when I cut the cord on the master dhcp/named, i get leases from the secondary, bu the forward and reverse records are refused.

I am running FreeBSD 6.1, ISC DHCPD 3.0.3, and BIND 9.3.2. It seems to me that named is not allowing the updates as it knows the zone is a slave zone.


Any thoughts?


Thanks.

---

### Post by terrrorr on 2007-07-05
Hello you all

I hope somebody who knows more about these things, reads this.

I have a problem. I did as it shows in this how-to without DHCP-configuration. I need a BInd9 and named with primary and secondary server. i thought that this one could help me out, but no (I have been fighting with this over a week)

The problem is that the secondary server refuses to connect my primary server. I get everytime this error message:

[INDENT]root@dhcp2:/etc/bind# /etc/init.d/bind9 restart
 * Stopping domain name service...                                                                                                                           rndc: connection to remote host closed
This may indicate that the remote server is using an older version of 
the command protocol, this host is not authorized to connect,
or the key is invalid.
                                                                                                                                                      [ ok ]
 * Starting domain name service...                                                                                                                    [ ok ] 
root@dhcp2:/etc/bind# 
[/INDENT]


This is what I found my secondary servers syslog

[INDENT]root@dhcp2:~# tail -f /var/log/syslog | grep named
Jul  5 10:56:45 dhcp2 named[5017]: invalid command from 127.0.0.1#47696: bad auth
Jul  5 11:04:53 dhcp2 named[5017]: invalid command from 127.0.0.1#39800: bad auth
Jul  5 11:10:58 dhcp2 named[5017]: invalid command from 127.0.0.1#56527: bad auth
[/INDENT]

I have checked that my rndc.key includes the same "secret key"

Primarys rndc.key -file:

```
key "rndc-key" {
        algorithm hmac-md5;
        secret "PUaBP7bDezxJAlLqfeB2MQ==";
};

```

Secondarys rndc.key -file:

```
key "rndc-key" {
        algorithm hmac-md5;
        secret "PUaBP7bDezxJAlLqfeB2MQ==";
};

```


I'm confused... :confused:

I hope somebody could help me.

FYI: i'm using Ubuntu 6.06 LTS server with default installation

---

### Post by terrrorr on 2007-07-05
AAAARGH.... ](*,)


Finaly i got it.... now it works fine... phew.

My problems:

[LIST=1]
[*]rndc-key problem
[*]Directorys permissions
[/LIST]

Case1.

If you'll have to change rndc-key with rndc-congen -tool you'll have to make sure that rnd.key -file is correct in both servers (I did, but still no go). I get rid of the rncd connection error after rebootting my both servers. I'm sure there is better way to do it, but i just rebooted both servers.

[INDENT]* Stopping domain name service... rndc: connection to remote host closed
This may indicate that the remote server is using an older version of
the command protocol, this host is not authorized to connect,
or the key is invalid.
[ ok ]
* Starting domain name service... [ ok ]
root@dhcp2:/etc/bind# [/INDENT]

After rebooting, rndc-connection failures was history

Case2

Directory where Bind puts the data must be with right privileges. Mine didn't, so i got the following error message:

[INDENT]Jul  5 14:10:58 dhcp2 named[3951]: zone testi.com/IN: Transfer started.
Jul  5 14:10:58 dhcp2 named[3951]: transfer of 'testi.com/IN' from 10.16.0.4#53: connected using 10.16.0.2#41139
Jul  5 14:10:58 dhcp2 named[3951]: dumping master file: /**etc/bind/zones/t**mp-XgfowzVVvT: open: permission denied
Jul  5 14:10:58 dhcp2 named[3951]: transfer of 'testi.com/IN' from 10.16.0.4#53: failed while receiving responses: permission denied
Jul  5 14:10:58 dhcp2 named[3951]: transfer of 'testi.com/IN' from 10.16.0.4#53: end of transfer
[/INDENT]

this will help you:
```
chmod 775 <directory>
```

- Terrrorr -

---

### Post by technoanarkst on 2008-12-09
Good Day!

For reference - I'm running Ubuntu Server 8.04.1 (Hardy)

I too was experiencing this problem, but the above solution did not fix my issue.  After some searching, I ran into a note on launchpad.net that mentioned updating the apparmor profile for bind9.  I decided to use the manpage on apparmor, and I discovered that apparmor was doing its job by restricting bind's write permissions. 

You can see if apparmor is your issue by issuing the following in a shell

```

grep audit /var/log/syslog

```

if apparmor is denying write access, you'll see something similar to this:
```

Dec  9 17:43:14 myserver01 kernel: [113918.729284] audit(1228862594.464:41): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/etc/bind/slave-zones/tmp-xxxxxxxxxx" pid=15533 profile="/usr/sbin/named" namespace="default"

```


I prefer to keep my zone files in /etc/bind/slave-zones/ and tried many combinations of permissions, but continued to experience failure. 

The fix for me was simple though, and was acheived by editing:
**/etc/apparmor.d/usr.sbin.named**
```

# vim:syntax=apparmor
# Last Modified: Fri Jun  1 16:43:22 2007
#include <tunables/global>

/usr/sbin/named {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  capability net_bind_service,
  capability setgid,
  capability setuid,
  capability sys_chroot,

  # /etc/bind should be read-only for bind
  # /var/lib/bind is for dynamically updated zone (and journal) files.
  # /var/cache/bind is for slave/stub data, since we're not the origin of it.
  # See /usr/share/doc/bind9/README.Debian.gz
  /etc/bind/** rw,
  /etc/bind/ rw,
  /var/lib/bind/** rw,
  /var/lib/bind/ rw,
  /var/cache/bind/** rw,
  /var/cache/bind/ rw,

  # some people like to put logs in /var/log/named/
  /var/log/named/** rw,

  # dnscvsutil package
  /var/lib/dnscvsutil/compiled/** rw,

  /proc/net/if_inet6 r,
  /usr/sbin/named mr,
  /var/run/bind/run/named.pid w,
  # support for resolvconf
  /var/run/bind/named.options r,
}

```

Notice where it says "# /etc/bind should be read-only for bind"? This is incorrect for my desired setup (zone files in /etc/bind/slave-zones/).  I added "w" to the line "/etc/bind/** rw," to allow write access to the files in this directory, and I added the line "/etc/bind/ rw," to allow it access to the subdirectory.  Perms on my /etc/bind/slave-zones/ directory are 775.

It is pretty common to want to put your config files some place where you can find them.  I would have experienced this problem in regards to logging, as I have my BIND9 setup logging to /var/named/ as well, but fortunately this is a common setup, and it was anticipated by the dev crew (who deserve many thanks), and placed in the apparmor profile in anticipation of setups like mine.

I went back and checked, and discovered that many tutorials reference /etc/bind as a directory to use for the zone files. So be aware if you're following this tutorial. (and many others)

I hope this helps people out there that are scratching their heads on this particular point. 

Disclaimer:
Make sure that you understand the ramifications of modifying your apparmor profile.  Apparmor adds a layer of security to a system, and disabling or changing security options can result in bad things happening.

---

### Post by fellixx on 2010-07-14
Just as an update to this thread in case anyone comes across it....Im running 9.04 with the latest version of Bind 9 and this tutuorial is still relatively relevent.  Pay particular attention to the aparmor configuration and if possible I would highly recommend you have the DNS and BIND book from OReilly handy for reference.  
 
One peice of advice I would give is to start off small and build up from there.  I created a DNS server setup WITHOUT dynamic DNS to ensure I had everything correct with my BIND configuration files.  Then I moved on to a single DHCP server in support of implementing dynamic DNS and once that was working right, then I moved on to making DHCP redundant. All the while keeping a sharp eye on the daemon.log and syslog and corrected every error I came across before moving on to another phase of my project.
 
After doing this and following some of the tips in this thread you should be able to get your setup working.  I would be very leary of what permissions you change on files and directories in so much as I wouldnt go "opening" things up just to see what you can get working.  
 
As for my setup, one last thing I need to do is tighten up my configurations from a security standpoint.
 
Good Luck
 
Fellixx

---

### Post by utrescu on 2010-11-18
Another solution is put your dynamic zone files in /var/lib/bind:

zone "test.xxx" {
	type master;
	file "/var/lib/bind/test.xxx";
        allow-update { 127.0.0.1; }; 
};

It works without problems:

$ nsupdate
> server 127.0.0.1
> update add [www.test.xxx](www.test.xxx) 600 in a 192.168.3.33
> send
> quit
$ dig [www.test.xxx](www.test.xxx) @localhost +short
192.168.1.33

---

### Post by Circa Lucid on 2011-07-12
I recently ran into this issue as well. I edited /etc/apparmor.d/usr.sbin.named but got no love until I:

/etc/init.d/apparmor reload

---

### Post by wdschei on 2011-09-07
I am setting up an 11.04 KVM host with several virtual machines. One of the virts is a primary for LDAP, DNS, and DHCP while another is the failover secondary for each of these same services. This tutorial along with the /var/lib suggestion in #19 worked perfectly.

Now on to my Nagios/Munin virt... more to come...

Thanks for all the help.

---

