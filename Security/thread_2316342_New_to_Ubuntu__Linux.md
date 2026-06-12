---
title: "New to Ubuntu / Linux"
date: 2016-03-07
forum: Security
---

### Post by Miyoko on 2016-03-07
I'm rather new to having my own server running Ubuntu, i've had servers before but only Windows.
However i'm a little concerned about the amount of failed logins in sudo less /var/log/auth.log

They mostly seem to come from Asia and North America when i trace the ips
I've been blocking them off one by one, but just to be clear since i'm running a website this is not including those who visit me and just the ones trying to access my box?

Over just 2 days the log is extremely long and despite they all tried it doesn't appear like anything is compromised or anyone successfully logged in as i took every necessary step to secure my server.. (i think) i followed several guides on how to harden Ubuntu.

Still this has me worried about all the failed attempts, should i just leave it be or keep trying to block them one by one?

---

### Post by SeijiSensei on 2016-03-07
If your server is running an SSH server, you'll get lots of attempted logins.  If it's feasible, I suggest only permitting connections to port 22 from IP addresses/networks that you trust.  Suppose you have a router at home and want to connect from machines in your home to the server.  First, ascertain the IP address of your router by visiting [http://www.whatismyip.com/](http://www.whatismyip.com/).  Let's suppose it is 169.254.123.123.  Then you can add some firewalling rules to the server with the iptables command:
```
/sbin/iptables -A INPUT -p tcp -s 169.254.123.123 --dport 22 -j ALLOW
/sbin/iptables -A INPUT -p tcp --dport 22 -j REJECT
```
That permits machines using your router to connect, but blocks everyone else.

Now this method can have problems if your ISP routinely changes your router's IP address.  If all their addresses begin with 169.254, then you can make the rule a bit more open, but still limited to your ISP's network like this:
```
/sbin/iptables -A INPUT -p tcp -s 169.254.0.0/16 --dport 22 -j ALLOW
/sbin/iptables -A INPUT -p tcp --dport 22 -j REJECT
```
That will still permit other machines in your ISP's network to make connection attempts, but all other attempts will fail.

There are some other methods you can adopt to improve security with SSH.  One of them is to require the use of "keys"; another is to set "PermitRootLogins" to "no" in /etc/ssh/sshd_config.  Read this document for more details: [https://help.ubuntu.com/lts/serverguide/openssh-server.html#openssh-keys](https://help.ubuntu.com/lts/serverguide/openssh-server.html#openssh-keys)

Another method that I use is to set up an OpenVPN tunnel between a machine in my home office and my remote server.  Then I can limit connections to those coming in over the tunnel and block all others.  Take a look at [http://openvpn.net/static.html](http://openvpn.net/static.html) to see how to set up a simple shared-key connection with OpenVPN.

One other even simpler solution is to have sshd listen on a port other than 22.  In /etc/ssh/sshd_config, change the line "Port 22" to some other port between 1024 and 65535.  I often use mnemonics based on a telephone dialpad for this.  For instance, you could choose port 6496 because that spells "miyo" on a phone.  If you are running a firewall on the server, you'll need to open up the port you choose.  This method constitutes what's known as "security through obscurity" meaning it will thwart robots that just randomly attempt to connect to port 22, but it won't block a determined hacker that uses a port scanner like the [nmap]("http://www.nmap.org/") program.  Most of the junk you see in the logs comes from those robots, so it will cut down a lot of those log entries.  To keep out that hacker, you should forbid root logins and require keys.

---

### Post by Miyoko on 2016-03-07
Thanks for the reply, i changed my ssh port and i tried modsecurity but that really ruined my web server since i'm not advanced enough to edit the rules and i had to revert it back, my isp is using dhcp so it's static most of the time but if it changes one day i wont be able to login again so it's not a great idea.. the permitrootlogins is disabled already and i only use rsa keys to login so i guess they should not be able to get in right?

Really helpful~

---

### Post by SeijiSensei on 2016-03-07
You're welcome.  I think you're pretty safe, though I do prefer the OpenVPN tunnel because it's entirely private.  Also if you set it up with the local machine as the client, then it doesn't matter what the router's IP is.  OpenVPN uses SSL like HTTPS does and goes through firewalls.  You just need to leave a high port open on the server so the client can connect.

I ran mod_security on a server for a while, but I, too, ran afoul of some rules and don't use it any more.  I've run a lot of Apache web servers over the years and was hacked only once many years ago.  I neglected to upgrade Apache and someone began using my server as an ISC relay.  Obviously that was my fault and not Apache's. Those kind of vulnerabilities are pretty much gone these days.  You're more likely to be hacked via applications and content management systems like Drupal or WordPress.  I use the latter and enforce strict privileges on the directories to prevent intrusions.

---

### Post by HermanAB on 2016-03-08
The simplest solution is to add a rate limiting rule to iptables.  That will throw off any brute force login attempts and script kiddies, while allowing yourself just fine:

[http://www.aeronetworks.ca/2013/05/ssh-brute-force-attacks.html](http://www.aeronetworks.ca/2013/05/ssh-brute-force-attacks.html)

The script kiddies will try once or twice, then go away.

---

