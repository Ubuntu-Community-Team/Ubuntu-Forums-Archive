---
title: "a few general questions about server security"
date: 2014-11-04
forum: Security
---

### Post by mastablasta on 2014-11-04
[FONT=verdana]so after my wordpress got hacked, the security was tightened. passwords were changed. they are now very long. I've also added a few security plugins. in the past few days there was a stark increase in attacks. so I tightened it all up and started automatic blocks.

at first they were trying with admin username (which doesn't exists), but now they are doing it with no user name. which I find strange. I get reports that they tried to logging with "empty user name". it puzzles me even more as I set the following for login page in apache:[/FONT]
[FONT=Times New Roman][COLOR=#000000]```
<Files
wp-login.php>
order deny,allow
allow from myhomeIP
allow from myworkIP
deny from all
</Files>
```
[FONT=verdana]
shouldn't this stop them at even getting to that page let alone "pressing" the login button?
anyway the security plugins are banning them left and right. serious increase in the past 2 or 3 days.

---

next is my home server. I opened it to web (I might close it again). again an increase in attacks in past 2 or 3 days - trying to get via SSH and somehow login root user.  I have fail2ban setup to ban IP's after 3 failed attempts for 60 days. is it better to set this to 1 attempt? is it better to set this to block indefinitely? let's say if wrong IP is blocked can it be unblocked?

wish I had the time to setup the VPN. it's overly complicated but the idea was to have a VPN and then server to be accessible only from 1 IP and LAN and not opening it to internet at all.[/FONT][/COLOR][/FONT]

---

### Post by SeijiSensei on 2014-11-04
For SSH, you could use iptables rules to block traffic to port 22 from IPs other than your own.  If your addresses are dynamically assigned, then the VPN is the best choice.

I have a machine in my home office that uses OpenVPN to maintain a tunnel with my cloud server at Linode.  I use [static-key tunnels]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") because they are quite easy to set up.  You should give it a try.

---

### Post by mastablasta on 2014-11-04
my brother and father's connection has dynamic addresses eventhough they change it very rarely. what they do is reassign same address to them  every night... what is the point?!?! :)

anyway we are trying to move those to static as well. mine is static. besides LAN is not such an issue. 

I will try with iptables. or maybe install UFW.

the problem with OpenVPN is their setup is complicated. it's not as easy as for example LogMeIn. so I need a bit more time to go through the documentation and learn the basics first etc. And in a month or so I plan to take a few days off work and that would give me some time to configure it 
better. I guess for now I will rely on fail2ban to continue blocking the IPs.

one of the aims of having this server (besides doing backups and sharing pics with family) is also to learn but I need time for that. :)

---

### Post by SeijiSensei on 2014-11-04
Before you write off OpenVPN for the time being, please read the document I linked to.  The whole process consists of creating a private encryption key with "openvpn --genkey --secret /path/to/the/keyfile".  Then you create a couple of configuration files for each end of the connection, put the key on both ends, and fire up the VPN.

On my server I have this configuration file:
```

dev tun
ifconfig 10.1.1.1 10.1.1.20
up /etc/openvpn/my_optional_routing_script
secret /etc/openvpn/mykey
port 12345
user nobody
group nogroup
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3

```
On the client I have
```

dev tun
remote hostname.of.my.server
ifconfig 10.1.1.20 10.1.1.1
port 12345
secret /etc/openvpn/mykey
up /etc/openvpn/another_optional_routing_script
user nobody
group nogroup
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3

```
That connects to port 12345 using UDP and creates a point-to-point tunnel with 10.1.1.1 at the server end and 10.1.1.20 on the client.  

There's lots of ways to make an OpenVPN connection complex, but this solution is pretty simple to set up if all you want is a point-to-point tunnel.

The routing scripts are designed to let all the machines on my home network see all the remote servers I have connected to the main server at 10.1.1.1.  For instance, on the server I have the script:
```

#!/bin/sh
# route packets to home network
/sbin/ip route add 192.168.1.0/24 via 10.1.1.20

```

---

### Post by bashiergui on 2014-11-04
You might consider running ssh on a high port, something other than 22. My ssh server rarely sees brute force attempts on 2222.

---

### Post by Habitual on 2014-11-04
> **mastablasta said:**
> [FONT=Times New Roman][COLOR=#000000][FONT=verdana]
shouldn't this stop them at even getting to that page let alone "pressing" the login button?[/FONT][/COLOR][/FONT] No, just a 403, forbidden.

ufw should be installed but not activated.
```
ufw enable
``` fires it up. Rules are persistent.

ufw combined with 2 /etc/hosts.allow and /etc/hosts.deny ([for openssh-server ! >  6.6]("http://ubuntuforums.org/showthread.php?t=2251123&p=13158182#post13158182")) rules can help
```
/etc/hosts.allow:sshd: 127.0.0.1 <safe_ip> <safe_ip2> 
/etc/hosts.deny:sshd: ALL
```

hosts.allow accepts wildcards in the form of 10. You must include the period. (for all of 10.0.0.0/8) so dynamic IPs are also possible with "xxx.yyy."
IPs change, but MAC hardware addresses rarely do, so [iptables with MAC address filtering]("http://www.cyberciti.biz/tips/iptables-mac-address-filtering.html") is also possible.

setting ufw rules is a simple as 
```
ufw deny to any port 22
ufw allow from <safe_ip> to any port 22 
```
should also help.

Finally.
```
[FONT=Times New Roman][COLOR=#000000]<Files
wp-login.php>
order deny,allow
allow from myhomeIP
allow from myworkIP
deny from all
</Files>[/COLOR][/FONT]
``` in an .htaccess rule is a resource hog, so I advise putting this restriction in the site.conf where is it less resource intensive.

---

### Post by povlhp on 2014-11-05
SSH is considered safe, just disable password authentication and use keys.
Generate different key per client, such that you can disable those that you suspect are compromised.
I am doing that on all my equipment, and don't bother to move the port.
I have a key at work Windooze, on my iPhone, iPad, Mac, and Linux. My OpenWRT router at home also has SSH enabled with keys.

Password authentication is the weak link.

And missing patches of course.

---

### Post by mastablasta on 2014-11-07
I didn't have the chance to act on all advice yet, so I will probably be back when I am doing something or on IRC :)

 but I did do some monitoring and SSH attacks subsided (or are gone). the ones that tried to enter got blockd.

but today I was checking the authentication log (auth.log) and found this (brute force attack from single IP):

> Nov  7 06:13:41 blekbox sshd[826]: input_userauth_request: invalid user root [preauth]
Nov  7 06:13:43 blekbox sshd[826]: Connection closed by 61.174.51.215 [preauth]
Nov  7 06:14:04 blekbox sshd[828]: Connection closed by 61.174.51.215 [preauth]
Nov  7 06:17:01 blekbox CRON[842]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  7 06:17:01 blekbox CRON[842]: pam_unix(cron:session): session closed for user root
Nov  7 06:21:44 blekbox sshd[853]: Did not receive identification string from 1.93.32.212
Nov  7 06:25:01 blekbox CRON[862]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  7 06:25:01 blekbox CRON[862]: pam_unix(cron:session): session closed for user root
Nov  7 06:39:01 blekbox CRON[893]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  7 06:39:01 blekbox CRON[893]: pam_unix(cron:session): session closed for user root
Nov  7 06:55:48 blekbox ajenti: user root logged in through AjentiSyncProvider from 192.168.1.3
Nov  7 06:57:07 blekbox sshd[987]: reverse mapping checking getaddrinfo for [192-161-81-90.rdns.cloudradium.com]("http://192-161-81-90.rdns.cloudradium.com/") [192.161.81.90] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  7 06:57:07 blekbox sshd[987]: User root from 192.161.81.90 not allowed because not listed in AllowUsers
Nov  7 06:57:07 blekbox sshd[987]: input_userauth_request: invalid user root [preauth]
Nov  7 06:57:07 blekbox sshd[987]: Received disconnect from [192.161.81.90]("http://192.161.81.90/"): 11: Bye Bye [preauth]
Nov  7 06:57:09 blekbox sshd[989]: reverse mapping checking getaddrinfo for [192-161-81-90.rdns.cloudradium.com]("http://192-161-81-90.rdns.cloudradium.com/") [192.161.81.90] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  7 06:57:09 blekbox sshd[989]: User root from 192.161.81.90 not allowed because not listed in AllowUsers
Nov  7 06:57:09 blekbox sshd[989]: input_userauth_request: invalid user root [preauth]
Nov  7 06:57:09 blekbox sshd[989]: Received disconnect from [192.161.81.90]("http://192.161.81.90/"): 11: Bye Bye [preauth]
Nov  7 06:57:10 blekbox sshd[991]: reverse mapping checking getaddrinfo for [192-161-81-90.rdns.cloudradium.com]("http://192-161-81-90.rdns.cloudradium.com/") [192.161.81.90] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  7 06:57:10 blekbox sshd[991]: Invalid user x from 192.161.81.90
Nov  7 06:57:10 blekbox sshd[991]: input_userauth_request: invalid user x [preauth]
Nov  7 06:57:11 blekbox sshd[991]: Received disconnect from [192.161.81.90]("http://192.161.81.90/"): 11: Bye Bye [preauth]
Nov  7 06:57:17 blekbox sshd[993]: reverse mapping checking getaddrinfo for [192-161-81-90.rdns.cloudradium.com]("http://192-161-81-90.rdns.cloudradium.com/") [192.161.81.90] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  7 06:57:17 blekbox sshd[993]: Invalid user http from 192.161.81.90
Nov  7 06:57:17 blekbox sshd[993]: input_userauth_request: invalid user http [preauth]
Nov  7 06:57:17 blekbox sshd[993]: Received disconnect from [192.161.81.90]("http://192.161.81.90/"): 11: Bye Bye [preauth]
Nov  7 06:57:19 blekbox sshd[995]: reverse mapping checking getaddrinfo for [192-161-81-90.rdns.cloudradium.com]("http://192-161-81-90.rdns.cloudradium.com/") [192.161.81.90] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  7 06:57:19 blekbox sshd[995]: Invalid user mp3 from 192.161.81.90
Nov  7 06:57:19 blekbox sshd[995]: input_userauth_request: invalid user mp3 [preauth]
Nov  7 06:57:19 blekbox sshd[995]: Received disconnect from [192.161.81.90]("http://192.161.81.90/"): 11: Bye Bye [preauth]
Nov  7 06:57:21 blekbox sshd[997]: reverse mapping checking getaddrinfo for [192-161-81-90.rdns.cloudradium.com]("http://192-161-81-90.rdns.cloudradium.com/") [192.161.81.90] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  7 06:57:21 blekbox sshd[997]: Invalid user oracle from 192.161.81.90
Nov  7 06:57:21 blekbox sshd[997]: input_userauth_request: invalid user oracle [preauth]
Nov  7 06:57:21 blekbox sshd[997]: Received disconnect from [192.161.81.90]("http://192.161.81.90/"): 11: Bye Bye [preauth]
Nov  7 06:57:22 blekbox sshd[999]: reverse mapping checking getaddrinfo for [192-161-81-90.rdns.cloudradium.com]("http://192-161-81-90.rdns.cloudradium.com/") [192.161.81.90] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  7 06:57:22 blekbox sshd[999]: User root from 192.161.81.90 not allowed because not listed in AllowUsers
Nov  7 06:57:22 blekbox sshd[999]: input_userauth_request: invalid user root [preauth]
Nov  7 06:57:23 blekbox sshd[999]: Received disconnect from [192.161.81.90]("http://192.161.81.90/"): 11: Bye Bye [preauth]
Nov  7 06:57:24 blekbox sshd[1001]: reverse mapping checking getaddrinfo for [192-161-81-90.rdns.cloudradium.com]("http://192-161-81-90.rdns.cloudradium.com/") [192.161.81.90] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  7 06:57:24 blekbox sshd[1001]: Invalid user r00t from 192.161.81.90
Nov  7 06:57:24 blekbox sshd[1001]: input_userauth_request: invalid user r00t [preauth]
Nov  7 06:57:24 blekbox sshd[1001]: Received disconnect from [192.161.81.90]("http://192.161.81.90/"): 11: Bye Bye [preauth]
Nov  7 06:57:26 blekbox sshd[1003]: reverse mapping checking getaddrinfo for [192-161-81-90.rdns.cloudradium.com]("http://192-161-81-90.rdns.cloudradium.com/") [192.161.81.90] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  7 06:57:26 blekbox sshd[1003]: Invalid user cgi from 192.161.81.90
Nov  7 06:57:26 blekbox sshd[1003]: input_userauth_request: invalid user cgi [preauth]
Nov  7 06:57:26 blekbox sshd[1003]: Received disconnect from [192.161.81.90]("http://192.161.81.90/"): 11: Bye Bye [preauth]
Nov  7 06:57:28 blekbox sshd[1005]: reverse mapping checking getaddrinfo for [192-161-81-90.rdns.cloudradium.com]("http://192-161-81-90.rdns.cloudradium.com/") [192.161.81.90] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  7 06:57:28 blekbox sshd[1005]: Invalid user roo from 192.161.81.90
Nov  7 06:57:28 blekbox sshd[1005]: input_userauth_request: invalid user roo [preauth]
Nov  7 06:57:28 blekbox sshd[1005]: Received disconnect from [192.161.81.90]("http://192.161.81.90/"): 11: Bye Bye [preauth]
Nov  7 06:57:29 blekbox sshd[1007]: reverse mapping checking getaddrinfo for [192-161-81-90.rdns.cloudradium.com]("http://192-161-81-90.rdns.cloudradium.com/") [192.161.81.90] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  7 06:57:29 blekbox sshd[1007]: Invalid user dede from 192.161.81.90
Nov  7 06:57:29 blekbox sshd[1007]: input_userauth_request: invalid user dede [preauth]
Nov  7 06:57:30 blekbox sshd[1007]: Received disconnect from [192.161.81.90]("http://192.161.81.90/"): 11: Bye Bye [preauth]
Nov  7 06:57:41 blekbox sshd[1009]: Invalid user bash from 192.161.81.90
Nov  7 06:57:41 blekbox sshd[1009]: input_userauth_request: invalid user bash [preauth]
Nov  7 06:57:41 blekbox sshd[1009]: Connection closed by 192.161.81.90 [preauth]

and I have a few questions:
1. what is this break in attempt? I mean to what? it's not SSH. so how are they trying to logging and to what? how do I find that out? otherwise I will be blocking that IP today in some way and strengthening the password for the GUI admin login. though I am curious why fail2ban hasn't picked it up and blocked it.

2. what is the netiquette in such cases. should I report the offending IP?

local jail:

should I just change this and other settings in fail2ban to -1 retries and use the safe IP list for those that might need more than one try?:

```
[FONT=Times New Roman][COLOR=#000000][ssh]

enabled  = true
port     = ssh
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 4[/COLOR][/FONT]
```

---

### Post by SeijiSensei on 2014-11-07
> **mastablasta said:**
> 1. what is this break in attempt? I mean to what? it's not SSH. so how are they trying to logging and to what? how do I find that out? otherwise I will be blocking that IP today in some way and strengthening the password for the GUI admin login. though I am curious why fail2ban hasn't picked it up and blocked it.

They are repeated attempts to break into SSH using a variety of likely usernames, a so-called "dictionary" attack.  Apparently the script hopes to hit one that doesn't require a password.  I'm always amazed that there are enough insecure boxes out there that simple brute-force attempts like this one ever work.

I don't use fail2ban, so I can't help with that.

> 2. what is the netiquette in such cases. should I report the offending IP?

[Cloudradium]("http://cloudradium.com/") looks to be a hosting company [with offices in Shanghai and a data center in Wyoming]("http://whois.arin.net/rest/net/NET-192-161-80-0-1/pft").  You can try reporting the IP, but I doubt it will matter.  With millions of compromised machines around the world, no one can keep up.  I deal with the problem by locking down my servers as tightly as possible.

---

### Post by Doug S on 2014-11-07
In addition to what Seiji already mentioned:> **mastablasta said:**
> 
and I have a few questions:
1. what is this break in attempt?If the reverse lookup, followed by a forward lookup with the result does not give the same IP or no answer, then that line is added to the auth.log file. Example:```
Nov  3 06:05:21 doug-64 sshd[22465]: Connection from 95.181.18.62 port 51753
Nov  3 06:05:28 doug-64 sshd[22465]: reverse mapping checking getaddrinfo for 95-181-18-62.goodline.info [95.181.18.62] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  3 06:05:28 doug-64 sshd[22465]: Invalid user zhangyan from 95.181.18.62
Nov  3 06:05:28 doug-64 sshd[22465]: input_userauth_request: invalid user zhangyan [preauth]
``````
doug@s15:~/temp$ [COLOR=#ff0000]nslookup 95.181.18.62[/COLOR]
Server:         192.168.111.1
Address:        192.168.111.1#53

Non-authoritative answer:
62.18.181.95.in-addr.arpa       name = [COLOR=#ff0000]95-181-18-62.goodline.info[/COLOR].

Authoritative answers can be found from:
18.181.95.in-addr.arpa  nameserver = ns2.eltc.ru.
18.181.95.in-addr.arpa  nameserver = ns.eltc.ru.
ns.eltc.ru      internet address = 212.75.210.80
ns2.eltc.ru     internet address = 212.75.211.2

doug@s15:~/temp$ [COLOR=#ff0000]nslookup 95-181-18-62.goodline.info[/COLOR]
Server:         192.168.111.1
Address:        192.168.111.1#53

** [COLOR=#ff0000]server can't find 95-181-18-62.goodline.info[/COLOR]: NXDOMAIN
```

 > **mastablasta said:**
> I mean to what?To your computer. > **mastablasta said:**
> it's not SSH.Yes it is via ssh. > **mastablasta said:**
> so how are they trying to logging and to what? how do I find that out?They are trying to log into your computer via ssh. Obverse that the auth.log entry is from the sshd daemon.

---

### Post by Habitual on 2014-11-08
See [http://www.fail2ban.org/wiki/index.php/Fail2ban:Community_Portal#failregex_POSSIBLE_BREAK-IN_ATTEMPT_in_filter_sshd.conf](http://www.fail2ban.org/wiki/index.php/Fail2ban:Community_Portal#failregex_POSSIBLE_BREAK-IN_ATTEMPT_in_filter_sshd.conf)

---

### Post by mastablasta on 2014-11-09
thanks, thanks and thanks... all.

just implemented blacklisting and added stuff from Habitual link. le'ts see how it goes. as an experiemnt. 

i am thinking doing a whitelist next. if there is too many attempts...

---

