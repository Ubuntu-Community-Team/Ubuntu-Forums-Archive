---
title: "Suddenly unable to connect to Apache web server outside of LAN"
date: 2017-08-12
forum: Server Platforms
---

### Post by painguin on 2017-08-12
Hi guys,

I've done a lot of googling and forum searching and I cannot find a solution to my problem.  I'm running Ubuntu Server 16.04 x64 on VirtualBox.  I've setup an Apache web server and have been building a WordPress  for about a week.  

Last week I was able to access my site from outside of my LAN if I forwarded port 80 to my VM's internal IP.  Today I forwarded port 80 and tried to connect using my phone over an LTE connection.  It failed.  Basically it timed out and I noticed that in the address bar/omnibox that once it  my external IP is replaced with the IP of my VM.  Just weird.

I can connect externally via SSH and glances if I start it as a web server.  But not my website.  This is sudden and unexplained.  I can access everything via LAN of course but not externally.  I Ann just coming back to Ubuntu after a while so  unsure how to troubleshoot this issue.

I'll be happy to provide whatever output you guys need.  I just need to figure out why I cannot access my site any longer from outside the network.

Thanks in advance,

PAinguIN

---

### Post by painguin on 2017-08-12
> **painguin said:**
> Hi guys,

I've done a lot of googling and forum searching and I cannot find a solution to my problem.  I'm running Ubuntu Server 16.04 x64 on VirtualBox.  I've setup an Apache web server and have been building a WordPress  for about a week.  

Last week I was able to access my site from outside of my LAN if I forwarded port 80 to my VM's internal IP.  Today I forwarded port 80 and tried to connect using my phone over an LTE connection.  It failed.  Basically it timed out and I noticed that in the address bar/omnibox that once it  my external IP is replaced with the IP of my VM.  Just weird.

I can connect externally via SSH and glances if I start it as a web server.  But not my website.  This is sudden and unexplained.  I can access everything via LAN of course but not externally.  I Ann just coming back to Ubuntu after a while so  unsure how to troubleshoot this issue.

I'll be happy to provide whatever output you guys need.  I just need to figure out why I cannot access my site any longer from outside the network.

Thanks in advance,

PAinguIN


This may actually be more of a networking question all in all.  If this needs to be moved to that thread that's fine.  

Also, to clarify, I can access servers running on the VM (externally) but not services using http (port 80 and https, 8080 for that matter).

Thanks!

---

### Post by painguin on 2017-08-14
ADMINS can you move my original thread to this forum please?
[https://ubuntuforums.org/showthread.php?t=2368553]("https://ubuntuforums.org/showthread.php?t=2368553")

I think there may be an issue with my routing tables but upon further inspection perhaps not.  I could access my server outside of the LAN no problem.  The. A couple of days later and a few ```
sudo apt upgrade
```  commands later I find I can suddenly not access port 80 from the outside world.  No doubt one of the updates has changed something.  

Yes, SSH and a glances server are accessible fine but nothing via http.

Thanks in advance!

---

### Post by ajgreeny on 2017-08-14
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

### Post by wildmanne39 on 2017-08-14
Please do not post duplicates, it dilutes community effort. Threads merged

Thanks

---

### Post by painguin on 2017-08-14
Sorry, not meant to create a duplicate hance why I requested my first thread be moved.  I saw no options to do this myself.  

But again, I apologize, I haven of been in the forums for some time. 
 
Thank you!

---

### Post by wildmanne39 on 2017-08-14
No worries, you can not move it yourself, but you can use the report button in the bottom left corner of any post to report it and ask staff to move it.

Thanks

---

### Post by painguin on 2017-08-14
Anyway, now that I am in the most appropriate place can anyone offer any suggestions or would there be any output I can post?

---

### Post by cariboo on 2017-08-14
Do you have a static external ip address or use a dynamic dns service?

---

### Post by painguin on 2017-08-14
> **cariboo said:**
> Do you have a static external ip address or use a dynamic dns service?

Thank you for responding friend..  Yes, I have a static IP address.  Additionally, all of the devices on my LAN have static ip's locally.  The range is the common range.  192.168.1.1 - 192.168.1.254.  My Ubuntu server is running virtually and in bridged mode so it has an IP within the range just mentioned.  

I could access my site a week or two ago externally but I tried the other day and discovered I could not.  But I can still access the server via SSH or glances if I have it up and running.  But nothing on port 80 or 8080 (http/https of course) can connect externally.  Basically the connection times out or is refused.

I'm not sure if I did this or if it was an update/upgrade.  I just don't know what to look  in Ubuntu....  Iptables seem ok but I'm not sure.  This is driving me nuts, lol!

---

### Post by darkod on 2017-08-15
1. It would be very rare for an update to do this. While not impossible, very improbable...

2. You mention iptables. Are you running a firewall on the server even though it is already protected behind your router and on a local LAN? I see no need for that, unless you need some specific iptables configuration. If you are running iptables best to post the output so we can take a look:
```
sudo iptables -Lnv
```

3. Are you sure the ISP hasn't started blocking those incoming ports, so suddenly you can access your http services externally?

---

### Post by painguin on 2017-08-15
[FONT=Verdana]I guess I'll throw something out here then.[/FONT]

[FONT=Verdana]Here is the output from a shell script I wrote listing ALL [/FONT]
[FONT=Verdana]iptables' chains and then some.  [/FONT]
[FONT=Verdana]This is how I ordered the commands, options, etc.[/FONT]
 iptables -t filter -L -v -n

 iptables -t nat -L -v -n

 iptables -t mangle -S -v

 iptables -t raw -S -v

 iptables -t security -S -v

Output From Shell Script


[LIST]
[*]**Filter Table:**
[*]Chain INPUT (policy ACCEPT 234K packets, 31M bytes)
[*]pkts bytes target     prot  opt in    out     source     destination
[*]Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
[*]pkts bytes target     prot  opt in    out     source     destination
[*]Chain OUTPUT (policy ACCEPT 215K packets, 36M bytes)
[*]pkts bytes target     prot  opt in    out     source     destination
[*]**NAT Table:**
[*]Chain PREROUTING (policy ACCEPT 392 packets, 71346 bytes)
[*]pkts bytes target     prot  opt in    out     source     destination
[*]Chain INPUT (policy ACCEPT 378 packets, 70616 bytes)
[*]pkts bytes target     prot  opt in    out     source     destination
[*]Chain OUTPUT (policy ACCEPT 84 packets, 7198 bytes)
[*]pkts bytes target     prot  opt in    out     source     destination
[*]Chain POSTROUTING (policy ACCEPT 84 packets, 7198 bytes)
[*]pkts bytes target     prot  opt in    out     source     destination
[/LIST]


[LIST]
[*]**Mangle Table:**
[*]-P PREROUTING ACCEPT -c 894 114822
[*]-P INPUT ACCEPT -c 893 114774
[*]-P FORWARD ACCEPT -c 0 0
[*]-P OUTPUT ACCEPT -c 393 44159
[*]-P POSTROUTING ACCEPT -c 405 47141
[*]----------------------------------
[*]**Raw Table:**
[*]-P PREROUTING ACCEPT -c 894 114822
[*]-P OUTPUT ACCEPT -c 393 44159
[*]----------------------------------
[*]**Security Table:**
[*]-P INPUT ACCEPT -c 316 39663
[/LIST]

-----------------------------------
This information may be overkill but I felt the need 
to post something that would show the state of my network's 
inner workings.  I hope that some of this information may be helpful 
in determining why I am unable to connect to my web server via HTTP 
all of the sudden.  If not, I will continue to post not revealing output 
which I think may be helpful or that others request of me for analysis.

Thank you for taking a look at my "iptables".

PAinguIN

---

### Post by painguin on 2017-08-15
> **darkod said:**
> 1. It would be very rare for an update to do this. While not impossible, very improbable...

2. You mention iptables. Are you running a firewall on the server even though it is already protected behind your router and on a local LAN? I see no need for that, unless you need some specific iptables configuration. If you are running iptables best to post the output so we can take a look:
```
sudo iptables -Lnv
```

3. Are you sure the ISP hasn't started blocking those incoming ports, so suddenly you can access your http services externally?


Darkod,

Thank you for the reply.  I made an enormous post before I actually noticed you had responded.  
But to answer your question, I did mention iptables simply due to the fact that they control traffic coming in and out of my VM.  It seemed as logical a place to start as any at this point I'm afraid.  

```
sudo iptables -Lnv
```

I ran the line of code you gave me and to my surprise the results were this:

```
**iptables: no chain/target/match by that name**
```

Can I assume it is safe to rule out iptables at this juncture?  Lol!  

I am here to resolve these issues and to also learn a bit and who knows, perhaps contribute.  Right now that may not seem likely but I'm just in a bit of a "rough" spot lately.
I've suffered a terrible loss in my immediate family within the past 2 weeks and I'm just not thinking as sharply as I normally would.  I have decided to take this loss as a sign that time is fleeting and we all must absorb as much knowledge as we possibly can each and every day.  This is true regardless of a tragedy but it has helped remind me of it.  

So with that said, thank you for your assistance on this matter as trivial as it may seem.  However rest assured that this all means a great deal to me.  

PAinguIN

---

### Post by darkod on 2017-08-16
Sorry, I tried to join all parameters together but obviously it can't be executed like that. Try this:
```
sudo iptables -L -nv
```

But we already sort of have the reply from your previous post. The filter table output shows that you are not blocking anything with iptables because all three (INPUT, OUTPUT and FORWARD) have a policy of ACCEPT. You can check with my above command though if there are any rules that might show blocked traffic (but I doubt it).

So iptables does not seem to be the problem. Have you tried checking the ports from any computer on the LAN that has a web browser? You can do something like that on [www.canyouseeme.org](www.canyouseeme.org). It is best to be run from the computer where the web server is actually installed, but being an ubuntu server with no GUI means you don't have a browser on it.

You can also try to use nmap to test if the ports are open, you can run it from any linux or windows machine, even outside the LAN.

---

### Post by painguin on 2017-08-16
> **darkod said:**
> Sorry, I tried to join all parameters together but obviously it can't be executed like that. Try this:
```
sudo iptables -L -nv
```

But we already sort of have the reply from your previous post. The filter table output shows that you are not blocking anything with iptables because all three (INPUT, OUTPUT and FORWARD) have a policy of ACCEPT. You can check with my above command though if there are any rules that might show blocked traffic (but I doubt it).

So iptables does not seem to be the problem. Have you tried checking the ports from any computer on the LAN that has a web browser? You can do something like that on [www.canyouseeme.org]("http://www.canyouseeme.org"). It is best to be run from the computer where the web server is actually installed, but being an ubuntu server with no GUI means you don't have a browser on it.

You can also try to use nmap to test if the ports are open, you can run it from any linux or windows machine, even outside the LAN.

Darkod, 

Again, thank you for your help.  

So good, iptables have been ruled out but I am about to post the output from the command you gave me but I think all looks good there.  

Just to be clear, I am running my Ubuntu server as a VM on VirtualBox.  The network is configured in bridged mode so it is pulling an ip from my LAN's DHCP pool, or at least was until I assigned it a static ip through my router.  

With that said I can easily check to see if these ports are open but would I not be blocked from ALL http traffic if port 80 was being blocked by my ISP or some other application or firewall?  I can still access the web on my VM's host machine and can still download updates via aptitude on the VM.

I visited canyouseeme.org and port 80 is open on my VM's host machine (which is running Windows 7 Ultimate x64, yes, I need to upgrade this system to Windows X).  

The output from ```
sudo iptables -L -nv
``` is as follows...

```

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts  bytes  target       prot opt in        out      source           destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts  bytes  target       prot opt in        out      source           destination

Chain OUTPUT (policy ACCEPT 0 packet, 0 bytes)
 pkts  bytes  target       prot opt in        out      source           destination

```

In addition, I just ran ```
netstat -plunt
```  
Check out these results...

[IMG]https://www.dropbox.com/s/perstk9cjzg9lqr/netstat%3Dplunt1.jpg?dl=0[/IMG][IMG]https://www.dropbox.com/s/perstk9cjzg9lqr/netstat%3Dplunt1.jpg?dl=0[/IMG][IMG][[IMG]http://i1087.photobucket.com/albums/j464/painguin1/netstatplunt1_zpsdrxitdmb.jpg[/IMG]]("http://s1087.photobucket.com/user/painguin1/media/netstatplunt1_zpsdrxitdmb.jpg.html")[/IMG]

After running ```
netstat -plunt
``` I see that port 80 is missing from the "tcp - local address" column.  It's just not there...  It is for tcp6 I see...  
Another important discovery I've made is that when I try to access the website from outside of the LAN and the request times out the IP address changes from my external to the internal IP address upon failure.  So imagine it's 99.45.22.xx and when the request to open my website via HTTP fails the IP changes to the VM's IP of 192.168.1.28.  Almost as if I have set that as a static setting or rule somewhere.  You know, that the adapter is to keep a static ip of 192.168.1.28.  (In the screen cap above I temporarily changed the VM's IP to 192.168.1.10.  It is back to .28 now. 

One final detail.  A few days ago I was trying to change my adapters name from enp0s3 back to the old school eth0 but was unable to do so with the time I had.  Perhaps in those attempts I made an unwanted change?

---

### Post by darkod on 2017-08-16
I wouldn't try to change the adapter name, it doesn't really have an impact. You use the name as it is and no problem. I really can't say if something got messed up with the operation to change it, it could be...

The netstat output really shows that apache is not running on port 80 for tcpv4. Try restarting the service with something like:
```
sudo systemctl restart apache2.service
```

I think that is the correct command.

Blocked port 80 by ISP would not stop you from browsing the internet, it makes a difference in which direction they block it. But if canyouseeme says it is open, then it is open.

You have to be careful about trying to switch server IPs because routers and switches often have something called arp table and can still trying to reach an older IP after a modification until its TTL expires. Assign your server static IP from the start and stick with it. And this static Ip should always be outside the router dhcp range. Do not rely on the router and use dhcp reservations or similar. For home setups you have plenty of range for the dhcp range and for static pool. No need to mix them up.

I'm not sure about the IP change in the browser address field, it might be how your router does it when it implements the port forward rule.

---

### Post by painguin on 2017-08-16
> **darkod said:**
> I wouldn't try to change the adapter name, it doesn't really have an impact. You use the name as it is and no problem. I really can't say if something got messed up with the operation to change it, it could be...

The netstat output really shows that apache is not running on port 80 for tcpv4. Try restarting the service with something like:
```
sudo systemctl restart apache2.service
```

I think that is the correct command.

Blocked port 80 by ISP would not stop you from browsing the internet, it makes a difference in which direction they block it. But if canyouseeme says it is open, then it is open.

You have to be careful about trying to switch server IPs because routers and switches often have something called arp table and can still trying to reach an older IP after a modification until its TTL expires. Assign your server static IP from the start and stick with it. And this static Ip should always be outside the router dhcp range. Do not rely on the router and use dhcp reservations or similar. For home setups you have plenty of range for the dhcp range and for static pool. No need to mix them up.

I'm not sure about the IP change in the browser address field, it might be how your router does it when it implements the port forward rule.

I'm afraid restarting the service changed nothing my friend.  I see you're running a version of Ubuntu 14.x.x.  Why have you decided to use this older version?  I'm only curious...  Perhaps 16.04 has a few issues and I should use an earlier version.

I've done so many things now...  I even created an iptable rule that forced port 80 to listen on inet and I still cannot connect outside of the LAN.  Also, I restored back to snapshot (image) I made in VirtualBox the day after I got the server up and running and knew that it could be accessed from outside the LAN and still cannot access the web server from the outside. 

I am starting to become frustrated at this point.  I've spent numerous hours troubleshooting this along with your help and still nothing.  It just doesn't make any sense for access to dissolve away like it has.  You know, the trouble seemed to begin once I installed "glances".  Of course Python had to be installed with it which should not have been an issue.  In fact, glances has a web server you can easily enable and I can access it from the outside world.  I'm stumped...

I think I need to take a break and come at this again with a fresh mind. 

Any suggestions, comments, ideas, longshots or even fixes for this issue  ;-) will be welcome.

Thanks in advance.

---

### Post by darkod on 2017-08-16
Does netstat show port 80 for tcp now? Or still not?

I don't use glances so I don't know if installing it can clash with apache in some way if they are both trying to use port 80.

I do use 16.04, I just haven't changed my signature yet. :) In fact, for servers that would be the recommended version, the latest LTS available.

Double check the forwarding rule on your router. you mentioned you were changing the server IP for testing, maybe you forgot to update the rule in the router after the last change? In such case any external traffic would not get forwarded to the correct internal IP (server).

---

### Post by painguin on 2017-08-30
> **darkod said:**
> Does netstat show port 80 for tcp now? Or still not?

I don't use glances so I don't know if installing it can clash with apache in some way if they are both trying to use port 80.

I do use 16.04, I just haven't changed my signature yet. :) In fact, for servers that would be the recommended version, the latest LTS available.

Double check the forwarding rule on your router. you mentioned you were changing the server IP for testing, maybe you forgot to update the rule in the router after the last change? In such case any external traffic would not get forwarded to the correct internal IP (server).

darkod, 

Apologies for the late response....

It appears that netstat is not showing port 80 (http) as listening for "tcp" but does show "http" as listening for "tcp6".  

Moreover, the output for my routing table states the following:

```

Kernel IP routing table
Destination     Gateway       Genmask               Flags     MSS     Window     irtt     Iface
default           192.168.1.1   0.0.0.0                 UG             0      0               0     enp0s3
192.168.1.0   *                   255.255.255.0      U                0     0                0    enp0s3 

```

And that's it and I keep seeing the 3rd octet with a "1" and the 4th octet as a "0" when looking at my settings.  I am not using a subnet of 192.168.1.0 so I am unsure why this is showing up unless it's just some odd default networking setting that I am foolishly overlooking (which may very well be the case). 

At this point I'm seriously considering creating a brand new webserver under a new Ubuntu Server VM just to see if it's something I have changed/done which is preventin gme from accessing my web server from my external IP.  I just started the Glances web server and I can access it just fine externally so there is no reason that I should not be able to access my site through http.  

I just do not know what else to try or look for.   Is there a way I can reset all of my network settings, rules, routing tables, etc, etc back to default as if I just started my server for the first time?  Linux is great when it comes to commands to allow you to do things simply not possible in Windows...for instance wiping your entire HDD from within the OS as it's running.  Not very useful in most cases but still, it shows the power of the shell.

Any last suggestions are welcome. 

And thank you again for your assistance thus far. 

Regards, 

PAinguIN

---

### Post by darkod on 2017-08-30
I'm confused. You say you are not using network 192.168.1.0/24 but earlier you said you were switching the server IP between 192.168.1.10 and 192.168.1.28. So the server IP does look to be in the subnet 192.168.1.0/24 in fact.

Your router public IP assigned by the ISP is a different thing. The server local LAN IP is one, and the router public IP another value.

---

### Post by mastablasta on 2017-08-31
> **darkod said:**
> the router public IP another value. also known as WAN on some routers.



can you ping the public (external) IP from your mobile phone? have you checked the apache log (in /var/log )? can you post your apache config file? not sure right now if it needs to be sanitized or not. i don't have access to my server from work and i forgot, but does wordpress use index.php? if so is index.php accessible in apache config where you set outside access?

did you restrict access on apache (e.g. to deny external network, but allow LAN access)?

are the ports correctly forwarded on router?

is there any error shown or does it just time out?

---

### Post by painguin on 2017-09-10
> **mastablasta said:**
> also known as WAN on some routers.



can you ping the public (external) IP from your mobile phone? have you checked the apache log (in /var/log )? can you post your apache config file? not sure right now if it needs to be sanitized or not. i don't have access to my server from work and i forgot, but does wordpress use index.php? if so is index.php accessible in apache config where you set outside access?

did you restrict access on apache (e.g. to deny external network, but allow LAN access)?

are the ports correctly forwarded on router?

is there any error shown or does it just time out?



> **mastablasta said:**
> also known as WAN on some routers.



can you ping the public (external) IP from your mobile phone? have you checked the apache log (in /var/log )? can you post your apache config file? not sure right now if it needs to be sanitized or not. i don't have access to my server from work and i forgot, but does wordpress use index.php? if so is index.php accessible in apache config where you set outside access?

did you restrict access on apache (e.g. to deny external network, but allow LAN access)?

are the ports correctly forwarded on router?

is there any error shown or does it just time out?


Thanks for the response mastablasta, 

So, no, I cannot PING my external IP using my phone.  However, if I go to canyouseeme.org it shows that port 80 is accessible and not blocked.  So, unsure why I cannot ping my machine now...  There is no error message per say but this is what happens:

1.) I enter my external IP into a web browser outside of the LAN/WLAN.
2.) The external IP literally changes in the address bar from xx.xxx.xxx.xx to 192.168.1.28 (the local ip of my VM).  In Chrome, it reads, "This page isn't working - 192.168.1.28 didn't send any data.  ERR_EMPTY_RESPONSE"  
and that's all.

I do not believe I restricted access to the external ip on apache but at this point anything is possible...

Yes, all of my ports are forwarded properly.  While my skills with Linux are not up to par I do have over 12 years of Windows domain administration experience under my belt so in spite of typos and mistakes made in the thread on my part I can assure you that I am aware of what an external ip address is and what a local ip address is.  But thank you for pointing out the fact that I may not have.  :-P  

Also, I am not switching between 192.168.1.10 and .28.  192.168.1.28 is the static ip for the VM now.  It had only changed once before in the past.  

My access.log and access1.log files have my external ip in some spots which is interesting.  I do not want to post that until I can properly edit out the ip's which won't take long but I do not have the time tonight.  

However, here is my apache2.conf output...

```

# This is the main Apache server configuration file.  It contains the# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.4/ for detailed information about
# the directives and /usr/share/doc/apache2/README.Debian about Debian specific
# hints.
#
#
# Summary of how the Apache 2 configuration works in Debian:
# The Apache 2 web server configuration in Debian is quite different to
# upstream's suggested way to configure the web server. This is because Debian's
# default Apache2 installation attempts to make adding and removing modules,
# virtual hosts, and extra configuration directives as flexible as possible, in
# order to make automating the changes and administering the server as easy as
# possible.


# It is split into several files forming the configuration hierarchy outlined
# below, all located in the /etc/apache2/ directory:
#
#	/etc/apache2/
#	|-- apache2.conf
#	|	`--  ports.conf
#	|-- mods-enabled
#	|	|-- *.load
#	|	`-- *.conf
#	|-- conf-enabled
#	|	`-- *.conf
# 	`-- sites-enabled
#	 	`-- *.conf
#
#
# * apache2.conf is the main configuration file (this file). It puts the pieces
#   together by including all remaining configuration files when starting up the
#   web server.
#
# * ports.conf is always included from the main configuration file. It is
#   supposed to determine listening ports for incoming connections which can be
#   customized anytime.
#
# * Configuration files in the mods-enabled/, conf-enabled/ and sites-enabled/
#   directories contain particular configuration snippets which manage modules,
#   global configuration fragments, or virtual host configurations,
#   respectively.
#
#   They are activated by symlinking available configuration files from their
#   respective *-available/ counterparts. These should be managed by using our
#   helpers a2enmod/a2dismod, a2ensite/a2dissite and a2enconf/a2disconf. See
#   their respective man pages for detailed information.
#
# * The binary is called apache2. Due to the use of environment variables, in
#   the default configuration, apache2 needs to be started/stopped with
#   /etc/init.d/apache2 or apache2ctl. Calling /usr/bin/apache2 directly will not
#   work with the default configuration.




# Global configuration
#


#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the Mutex documentation (available
# at <URL:http://httpd.apache.org/docs/2.4/mod/core.html#mutex>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"


#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
Mutex file:${APACHE_LOCK_DIR} default


#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}


#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300


#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On


#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100


#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 5




# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off


# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog ${APACHE_LOG_DIR}/error.log


#
# LogLevel: Control the severity of messages logged to the error_log.
# Available values: trace8, ..., trace1, debug, info, notice, warn,
# error, crit, alert, emerg.
# It is also possible to configure the log level for particular modules, e.g.
# "LogLevel info ssl:warn"
#
LogLevel warn


# Include module configuration:
IncludeOptional mods-enabled/*.load
IncludeOptional mods-enabled/*.conf


# Include list of ports to listen on
Include ports.conf




# Sets the default security model of the Apache2 HTTPD server. It does
# not allow access to the root filesystem outside of /usr/share and /var/www.
# The former is used by web applications packaged in Debian,
# the latter may be used for local directories served by the web server. If
# your system is serving content from a sub-directory in /srv you must allow
# access here, or in any related virtual host.
<Directory />
	Options FollowSymLinks
	AllowOverride None
	Require all denied
</Directory>


<Directory /usr/share>
	AllowOverride None
	Require all granted
</Directory>


<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>


#<Directory /srv/>
#	Options Indexes FollowSymLinks
#	AllowOverride None
#	Require all granted
#</Directory>


<Directory /var/www/html/>
     AllowOverride All
</Directory>




# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#
AccessFileName .htaccess


#
# The following lines prevent .htaccess and .htpasswd files from being
# viewed by Web clients.
#
<FilesMatch "^\.ht">
	Require all denied
</FilesMatch>




#
# The following directives define some format nicknames for use with
# a CustomLog directive.
#
# These deviate from the Common Log Format definitions in that they use %O
# (the actual bytes sent including headers) instead of %b (the size of the
# requested file), because the latter makes it impossible to detect partial
# requests.
#
# Note that the use of %{X-Forwarded-For}i instead of %h is not recommended.
# Use mod_remoteip instead.
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.


# Include generic snippets of statements
IncludeOptional conf-enabled/*.conf


# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet





```

I could not post my access.log output.  I received a forbidden error..

I hope this information helps...

If I need to clear anything up or remove/add anything please let me know.  

Thanks in advance!

PAIN

---

### Post by darkod on 2017-09-10
1. Ping to the public IP would usually not work because the ISP router is blocking it, unless you have modified its firewall to let ping through. Plus you need apache to work, so there is no point wasting time with ping.

2. In apache, did you change any of its general config files, or only the .conf files in folder sites-available? You should only work with sites-available, most other apache settings are OK to start with, especially for users with little experience. If you start changing apache config files without knowing what are you doing you can indeed have very unexpected results.

3. At this point it might be much better solution to purge apache and install it again. I assume you have all your web files in another location, and their backup. So purging apache and installing it again will install it with the standard configuration that works, and after that you only need to create the virtual host .conf file. That's all...

---

### Post by painguin on 2017-09-10
> **darkod said:**
> 1. Ping to the public IP would usually not work because the ISP router is blocking it, unless you have modified its firewall to let ping through. Plus you need apache to work, so there is no point wasting time with ping.

2. In apache, did you change any of its general config files, or only the .conf files in folder sites-available? You should only work with sites-available, most other apache settings are OK to start with, especially for users with little experience. If you start changing apache config files without knowing what are you doing you can indeed have very unexpected results.

3. At this point it might be much better solution to purge apache and install it again. I assume you have all your web files in another location, and their backup. So purging apache and installing it again will install it with the standard configuration that works, and after that you only need to create the virtual host .conf file. That's all...


Darko,

Thank you for your response...  There were some things that were changed based on tutorials for features or permissions that were required supposedly.  

If, however I were dead set on fixing this problem without a purge would you have any advice? 

Thanks!

---

### Post by darkod on 2017-09-10
Well, I would undo all those changes and made sure apache works again. But that is the same like starting from clean (purged) apache.

Then if you wish you can start applying the modifications one at a time, testing and detecting when it will stop working (if it does again). When you know which modification it is, you can ask here for users more experienced with apache to give you their opinion if the modification is needed at all. Don't forget that apache is very old software, and there are many tutorials online which doesn't mean you should go apply all of them. Depending where you found them, anyone can post anything on the internet... And also there are different versions of apache, maybe those tutorials are for the older one?

That's what I would do...

---

### Post by mastablasta on 2017-09-12
> **painguin said:**
> 
I could not post my access.log output.  I received a forbidden error..



access via SSH then use nano or some other editor to see the logs.
usage:

nano* logfilename.log*

in this case you might be interested in its access logs.

---

### Post by painguin on 2017-09-14
> **mastablasta said:**
> access via SSH then use nano or some other editor to see the logs.
usage:

nano* logfilename.log*

in this case you might be interested in its access logs.


I have no problem accessing the logs.  I have the problem when trying to paste them into my response here in the forums.   I think I was trying to post too much at once though....

---

### Post by painguin on 2017-09-18
Ok guys, I'm going to take your advice and purge this Apache install and then re-install and configure... 

That said, is there a NEW tut that you guys can recommend I use?

Thanks!

---

### Post by mastablasta on 2017-09-19
just use bitnami stack wordpress image (alternatively install Ubuntu , LAMP and wordpress) then use bridged connection. 
> Bridged networking
This is for more advanced networking needs such as network simulations and running servers in a guest. When enabled, VirtualBox connects to one of your installed network cards and exchanges network packets directly, circumventing your host operating system's network stack.

make sure you router lets the port 80 through (as well as any host OS firewall) and you should be good to go.
virtual box networking: [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

i don't know what other configurations of apache you thought were necessary. or better yet what you were attempting to do.

---

### Post by painguin on 2017-09-19
> **mastablasta said:**
> just use bitnami stack wordpress image (alternatively install Ubuntu , LAMP and wordpress) then use bridged connection. 


make sure you router lets the port 80 through (as well as any host OS firewall) and you should be good to go.
virtual box networking: [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

i don't know what other configurations of apache you thought were necessary. or better yet what you were attempting to do.


Well I was not attempting I was actually running an Apache web server on a local VM.  I have done this many times before...  Things went wrong when I decided to install "Glances" (and Python as well of course) which worked out just fine.  I was able to run Glances in web server mode and access it from outside of my LAN without issue (once the proper port had been forwarded) but after that I was no longer able to access my website from outside of the LAN.  

Regardless, these things happen and I thank you and everyone else in this thread for their advice and assistance with this matter. 

Once I purge and reinstall I will post an update to show the results.  

Thanks again!

---

### Post by mastablasta on 2017-09-20
glances maybe overwrote some configuration. or perhaps it setup apache to only use it as the only website. i am not sure. 

i do not use it. Ajenti provides me with a quick view of system resources usage in it's dashboard, but even that is not necessary as all that stuff is actually available (though separately) via SSH.

on hosted website they offer various metrics and quick data over cpanel. if you need or want some GUI hosting panel check out this guide: [http://www.hostingadvice.com/blog/cpanel-vs-plesk-vs-webpanel/](http://www.hostingadvice.com/blog/cpanel-vs-plesk-vs-webpanel/)

just avoid zPanel it really isnt' maintained anymore and it has major security holes that are being exploited actively.

EDIT: also avoid webmin - it has issues on Ubuntu.

---

