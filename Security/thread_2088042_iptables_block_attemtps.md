---
title: "iptables block attemtps"
date: 2012-11-25
forum: Security
---

### Post by dkardell on 2012-11-25
Its been suggested that I use the following but not wure what the first line does:


Alternately you may learn to use iptables. Iptables has several additional features including the ability to black list an ip address after failed attempts.

```
sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH --rsource -j ACCEPT
sudo iptables -A INPUT -m recent --update --seconds 600 --hitcount 8 --rttl --name SSH --rsource -j DROP

```
"--hit count" is the number of new connections. Keep in mind each new connection gives multiple opportunities to enter a password. If you use scp, use a higher hitcount as each file will be a new ssh session.

"--seconds" How long an ipaddress will be blacklisted. 10 minutes is usually sufficient to deter most "script kiddies".

---

### Post by Doug S on 2012-11-25
For many many years now, I have used a similar method to help deal with SSH attacks. Just within the last couple of months, on some other ubuntu forums thread, I saw the method you posted. I do not understand it, although I didn't actually test it. Here is what I do:```
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT
```Notice how I have the DROP rule first, if there have alreay been "hitcount" attempts. Only, then does the SSH packet get accepted, and the hitcount bumped. I use a longer block time because I have had occurences where 10 minutes was not enough.
 
My "ESTABLISHED, RELATED" bypass of these rules is earlier in my rules INPUT chain.

---

### Post by Doug S on 2012-11-25
I tried the method of the original post on a test computer. It worked fine. To answer the orignal question: The first line allows packets for a NEW tcp connection for an ssh session through as long as "hitcount" has not been reached yet. Typically some sort of small hitcount allows legitimate users to log in.
I did lock myself out of my test machine, as once the rule triggers all packets from the IP are dropped, and I did not have an ESTABLISHED, RELATED bypass in this case.

---

### Post by dkardell on 2012-11-25
Thanks Doug.   My only question is then 

My "ESTABLISHED, RELATED" bypass of these rules is earlier in my rules INPUT chain.

What does that mean ?  I have not added any rules to my INPUT chain other than the individual IP's i've manually blocked this far with  -j DROPS.

What is your code segment that you posted.  What is

$IPTABLES 

versus my command line entry of the commands with

sudo iptables

---

### Post by CharlesA on 2012-11-25
> **dkardell said:**
> 
What is your code segment that you posted.  What is

$IPTABLES 

versus my command line entry of the commands with

sudo iptables

It's just a variable that probably uses the full path to iptables.

---

### Post by Doug S on 2012-11-26
Sorry, I guess I posted without claifying some things.
Thanks to Charles for explaining the variable.
 
In what I posted the variables are:
$IPTABLES means /sbin/iptables
$EXITIF means the external network interface. (On my system I have an internal and an external network interface.) You could delete the interface specifier if you want. You could also delete the logging rule if you want.
$EXTIP means my external IP address (see below)
$UNIVERSE means any IP address or "0.0.0.0/0" (see below)
 
When a new TCP session is started the first packet will be in a NEW state. Subsqequent packets for that same session are for either an ESTABLISHED or a RELATED state. Providing a path around the check for session already in progess is all I was saying. Your original rules included a "NEW" state check. Example:```
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT
```

---

### Post by Lars Noodén on 2012-11-26
I do about the same thing, but on a single line.  The default (last rule in the chain) I have for the chain is [reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject).

```

   ip6tables -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 8/minute --limit-burst 8 -j ACCEPT
   iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 8/minute --limit-burst 8 -j ACCEPT

```

---

### Post by dkardell on 2012-11-26
Thanks Doug this is now becoming a bit more clear.  I still want to be sure I know everything I'm doing first.

So if I go to the command line and issue 

sudo iptables -A INPUT -m recent --update --seconds 600 --hitcount 3 --rttl --name SSH --rsource -j DROP

That will add any IP that attempts to try and ssh to my server and is rejected 3 times to the DROP list correct?


Lars, I'm not sure what you mean by your comment of: I do about the same thing, but on a single line. The default (last rule in the chain) I have for the chain is reject.

 ```
ip6tables -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 8/minute --limit-burst 8 -j ACCEPT

iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 8/minute --limit-burst 8 -j ACCEPT
```

and what is ip6tables vs iptables?

---

### Post by CharlesA on 2012-11-26
ip6tables is iptables for IPv6.

---

### Post by Doug S on 2012-11-26
> **dkardell said:**
> That will add any IP that attempts to try and ssh to my server and is rejected 3 times to the DROP list correct?Yes, as long as there is not 10 minutes between login attempts. Also, The default sshd_config allows 6 password tries on one TCP connection before it kicks you out. Most automated ssh attack programs only try once per connection. Another change I make is to add these lines to sshd_config:```
#Smythies.com
#Limit the number of bad passwords per connection to 2. Default is 6.
#Then the iptables connection counter will kick in sooner to drop
#password attack hackers.
MaxAuthTries 2

```By the way, for this line:> If you use scp, use a higher hitcount as each file will be a new ssh session.from your original post. I tested it and it is not true. There will one TCP ssh session per scp session, regardless of the number of files transferred. I also tested WinSCP from a windows computer, with the same results.

---

### Post by Lars Noodén on 2012-11-27
> **dkardell said:**
> Lars, I'm not sure what you mean by your comment of: I do about the same thing, but on a single line. The default (last rule in the chain) I have for the chain is reject.


I do the rate limiting with a single line, as shown above in #7.  
However, I allow in connections that don't exceed the rate limit and reject everything else.  SSH connections that are under the limit are accepted, SSH connections that exceed the limit are ignored by that rule and it passes down the chain to the next rule(s) in the chain.  If nothing else accepts the connection, then it hits the last rule in my chain which I have decided to be reject.  It should be pointed out that there is a difference between drop and reject targets.

[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)
[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)

---

### Post by dkardell on 2012-11-27
Thanks again Doug.

So will this stop these attacks or only those ssh's on port 22?

```
Failed password for root from 61.191.61.2 port 45805 ssh2
pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.191.61.2  user=root
Failed password for root from 61.191.61.2 port 47037 ssh2
pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.191.61.2  user=root
Failed password for root from 61.191.61.2 port 48096 ssh2
pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.191.61.2  user=root
Failed password for root from 61.191.61.2 port 48970 ssh2

```

---

### Post by dkardell on 2012-11-28
Lars listed 2 interesting posts.

According to them we should use REJECT rather than DROP.

Comments?

---

### Post by CharlesA on 2012-11-28
I always use reject instead of drop now.

I've run into issues when using drop instead of reject that causes programs to just keep trying to connect and just sit there. With reject set, the program spits out an error message saying it couldn't connect.

---

### Post by SeijiSensei on 2012-11-28
I solve this problem by blocking all SSH access and only allowing specified IP addresses that I control to connect.  If I need a mobile connection, I use a static OpenVPN tunnel from my laptop to the server.  I can count on one or at most two hands the number of IP addresses that need to connect legitimately to my servers.  I suspect that's true for a lot of folks.

---

### Post by CharlesA on 2012-11-28
> **SeijiSensei said:**
> I solve this problem by blocking all SSH access and only allowing specified IP addresses that I control to connect.  If I need a mobile connection, I use a static OpenVPN tunnel from my laptop to the server.  I can count on one or at most two hands the number of IP addresses that need to connect legitimately to my servers.  I suspect that's true for a lot of folks.

I do the same minus the OpenVPN thing. If I know I will need to connect from a different IP than usual (traveling, relative's house, etc), I start a VM with only SSH installed on it and run it on a random high port. Both machines used keys for authentication, so I don't get too many hits from bad guys. ;)

---

### Post by dkardell on 2012-11-30
> **SeijiSensei said:**
> I solve this problem by blocking all SSH access and only allowing specified IP addresses that I control to connect.  If I need a mobile connection, I use a static OpenVPN tunnel from my laptop to the server.  I can count on one or at most two hands the number of IP addresses that need to connect legitimately to my servers.  I suspect that's true for a lot of folks.

Thanks, I think I'll move towards that.  Being a newbie to Ubuntu and remote servers (just over a year now), I guess I'm worried that if my ISP changes my home IP then I won't be able to get into the system.

I don't know much about OpenVPN but will educate myself on that as well.

---

### Post by CharlesA on 2012-11-30
> **dkardell said:**
> Thanks, I think I'll move towards that.  Being a newbie to Ubuntu and remote servers (just over a year now), I guess I'm worried that if my ISP changes my home IP then I won't be able to get into the system.

I don't know much about OpenVPN but will educate myself on that as well.
Dynamic DNS would fix that problem. Check out no-ip or dyndns.

---

### Post by SeijiSensei on 2012-11-30
> **dkardell said:**
> Thanks, I think I'll move towards that.  Being a newbie to Ubuntu and remote servers (just over a year now), I guess I'm worried that if my ISP changes my home IP then I won't be able to get into the system.

I don't know much about OpenVPN but will educate myself on that as well.

OpenVPN is an excellent solution to this problem.  I run simple point-to-point tunnels with a [shared static key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  My server is out in the "cloud" at Linode and is configured to listen for an OpenVPN connection on a specified high port.  At home I have a machine configured as a client that connects to the server and sets up the tunnel.  It doesn't matter if my home IP changes since the client simply connects through the firewall.  I do have to leave a high port open accepting UDP traffic for the tunnel, but that's not much of a vulnerability since even if you find the port you'd need my encryption key to exploit it.

Here are the configuration files I use for future reference:

Server:
```

dev tun
ifconfig 10.1.1.1 10.1.1.20
#up /etc/openvpn/add_routes
secret /etc/openvpn/keys/my.key
port 43434
user nobody
group nogroup
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3
no-replay

```

Client:
```

dev tun
remote myserver.example.com
ifconfig 10.1.1.20 10.1.1.1
port 43434
secret /etc/openvpn/keys/my.key
up /etc/openvpn/add_routes
user nobody
group nogroup
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3

```

They are essentially identical except that the client has the "remote" directive telling it where to connect, and the order of IP addresses in the "ifconfig" directive are reversed.  The server assigns 10.1.1.1 to its tunnel interface and 10.1.1.20 to the client.

---

### Post by dkardell on 2012-12-05
so SeijiSensei help the newbie out here.  Again I'm a programmer of some 30 years and have been playing around with Ubuntu for a little over a year and am now doing remote admin of a server via SSH.  This whole thread started because of the number of sshd root failures I'm seeing for other ips.  I've read over the OpenVPN stuff and really want to understand it but a bit worried that I may screw someithing up and lock myself out.  I have heard about shared static key's but have slept since then.  How do I go about using keys on my mac local and on a Ubuntu server hosted at Godaddy?  

Next what are your code examples above. Are scripts inside of executable files? or are these configs?

Thanks!

Dan]

---

### Post by dkardell on 2012-12-05
> **Doug S said:**
> Yes, as long as there is not 10 minutes between login attempts.

Hey I just tried this on my local Ubuntu Server to test it out.  Before adding the rule I could SSH to my local machine.  After adding the rule and then attempting to access it 3 times I got the Permission denied (publickey,password).


HOWEVER, I was able to try ssh again and was prompted for a password 3 more times before it failed again.

I thought this command would add the ip to the DROP/REJECT list after 3 failed attempts such that they could not try ssh again (or in this case try any access to the server).

Am I missing something?  After 3 successive failed attempts I want to block the IP from accessing everything.

---

### Post by SeijiSensei on 2012-12-05
> **dkardell said:**
> so SeijiSensei help the newbie out here.  Again I'm a programmer of some 30 years and have been playing around with Ubuntu for a little over a year and am now doing remote admin of a server via SSH.  This whole thread started because of the number of sshd root failures I'm seeing for other ips.  I've read over the OpenVPN stuff and really want to understand it but a bit worried that I may screw someithing up and lock myself out.  I have heard about shared static key's but have slept since then.  How do I go about using keys on my mac local and on a Ubuntu server hosted at Godaddy?  

Next what are your code examples above. Are scripts inside of executable files? or are these configs?

Thanks!

Dan]

Those are the server and client configuration files for OpenVPN.  They are stored in /etc/openvpn.  You can name them anything you want as long as they end in .conf.  (I have a server that manages multiple VPNs; each tunnel has a separate file in /etc/openvpn.)

The steps in that "how-to" I linked above are pretty straightforward.  Here's a quick summary:

1)  First generate a key that will be used on both machines to encrypt the traffic over the tunnel.  OpenVPN provides a convenient method to do this with the command:

```

sudo openvpn --genkey --secret /etc/openvpn/mykey
sudo chmod 600 /etc/openvpn/genkey

```

This will create the file /etc/openvpn/mykey.  Place a copy of the key in the same location on both machines.  Make sure the files are owned by root and use the same chmod command to limit their visibility to the root user.

2)  Install openvpn.

```
sudo apt-get install openvpn
```

3)  Create a file on the server, call it /etc/openvpn/something.conf, and put the commands I gave above for the server in that file.  The port number is arbitrary; pick something between 1024 and 65535 that is not being used for anything else.  Make sure your iptables ruleset opens this port.  If you chose port 12345, you would include an iptables rule that reads:

```
iptables -A INPUT -p udp --dport 12345 -j ACCEPT
```

to allow incoming UDP traffic on port 12345.  If the server is locked down, you probably need to add another rule to enable traffic over the tunnel like this:

```
iptables -A INPUT -i tun0 -j ACCEPT
```

This allows all traffic to the "tun0" interface, which will be created when OpenVPN starts.  Add this to the iptables rulesets on both machines.

The addresses in the ifconfig directive are also arbitrary. All my tunnels are numbered in the 10.1.1.0/24 subnet, but you could use any other private addressing space like 192.168/16.  Just make sure the order of addresses is reversed in the client configuration file.

4)  Install OpenVPN on the client and create an equivalent .conf file like the one above.  Replace "myserver.example.com" in the "remote" directive with the actual name of your server.

5)  Start OpenVPN on the server:

```
sudo service openvpn start
```

Look in /var/log/syslog for any errors.  

6)  Now start OpenVPN on the client and check the logs for errors.  

7)  Try pinging the private address on the other side of the tunnel.  Does it work?

Adding OpenVPN won't interfere with SSH access; they operate on entirely separate ports and use different protocols.  If you can SSH to the public IP of your server now, you should still be able to do so after starting OpenVPN.

I use [Linode](http://www.linode.com/) for my external virtual servers.  One nice feature they offer is the ability to access a text-mode terminal session on the machine over the web so I can log in even if SSH doesn't work.  Things like that make the $20/month it costs for a VM on Linode worth it.

---

