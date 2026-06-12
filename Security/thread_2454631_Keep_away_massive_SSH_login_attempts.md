---
title: "Keep away massive SSH login attempts"
date: 2020-12-03
forum: Security
---

### Post by Elmi77 on 2020-12-03
Hi,

during the last few days my SSHD-logfiles are full of entries like this

```

 Disconnected from authenticating user root 137.74.198.18 port 38522 [preauth] : 1 time(s)
 Disconnected from authenticating user root 190.171.133.10 port 40896 [preauth] : 1 time(s)
 Disconnected from authenticating user root 122.51.255.33 port 38079 [preauth] : 1 time(s)
 Disconnected from authenticating user root 202.153.37.194 port 26610 [preauth] : 1 time(s)
 Disconnected from authenticating user root 101.32.208.125 port 58386 [preauth] : 1 time(s)
 Disconnected from authenticating user root 138.197.89.212 port 44796 [preauth] : 1 time(s)
 Disconnected from authenticating user root 142.93.236.246 port 34274 [preauth] : 1 time(s)
 Disconnected from authenticating user root 119.96.120.113 port 33118 [preauth] : 1 time(s)
 Disconnected from authenticating user root 103.129.223.136 port 45700 [preauth] : 1 time(s)
 Disconnected from authenticating user root 47.103.205.33 port 58530 [preauth] : 1 time(s)
 Disconnected from authenticating user root 49.235.90.166 port 38788 [preauth] : 1 time(s)
 Disconnected from authenticating user root 198.199.89.226 port 52948 [preauth] : 1 time(s)
 ...

```

This is not only tried with user root but also with loads of other, random usernames. For each user it tries to log in about 40..60 times. As far as I can tell, until now none of these hacking attempts was successful but I would like to add some additional security measures against this.

My SSHD is already runnign at a different port but this seems to be a somewhat sophisticated script, it already has found this port number (this is moething 99% of all other scripts don't).

The IP's the attack comes fro mall are different and are possibly spoofed.

So what else options do I have here?

Any idea is welcome!

---

### Post by TheFu on 2020-12-03
[https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) has the easy stuff. There is more possible.
Mainly, never allow passwords to be used over the internet.  Keys only.

---

### Post by EuclideanCoffee on 2020-12-03
fail2ban and non-standard ports work wonders. Both are in Fu's link.

I also allow only specific IP ranges to use my SSH port, which prevents most people commonly from a random IP subnet.

Let us know if you have trouble implementing any of that.

---

### Post by TheFu on 2020-12-03
> **EuclideanCoffee said:**
>  
I also allow only specific IP ranges to use my SSH port, which prevents most people commonly from a random IP subnet.
 

If you don't have road warriors in China or Russia or the USA, blocking all those subnets from access to your ssh port at the firewall would be smart. Basically, only allow internet networks any access if you **know** they need access.

If you've been seeing lots of attempts, change the port and put fail2ban in the way immediately. Use the WAN router to do port translation 
WAN:{WAN-IP}:64322 --> LAN:192.168.66.32:22
This will let the normal connections from inside the LAN keep working, fail2ban already knows how to block port 22/tcp so there won't be extra setup needed.  If you don't do it this way, then fail2ban needs more configuration and all your client machines need to know about the non-standard other port.  If that is needed (you don't control the WAN router), then use the ~/.ssh/config file to handle non-standard ports for each system.  All ssh-based tools honor that config file for ssh connections (ssh, scp, sftp, rsync, rdiff-backup, x2go, and 50 others).

If you feel like even more layers are necessary, EuclideanCoffee posted a link that had some added things last month.  It all depends on your risks and needed mitigations.

---

### Post by DuckHook on 2020-12-03
@ Elmi77

Please refrain from using nonstandard fonts and styles when posting. This is especially problematic in code boxes, as it badly throws off proper spacing.

---

### Post by SeijiSensei on 2020-12-03
None of my servers have a publicly-visible SSH port. I connect to them via [static tunnels using OpenVPN]("https://openvpn.net/community-resources/static-key-mini-howto/"). 

If you only have to connect from one place this is an easy option.

---

### Post by EuclideanCoffee on 2020-12-03
Sincerely curious about this, SeijiSensei. How is this better than SSH direct? I would assume the latter has more visibility and therefore more likely to report issues with security. Also adding something like this might open all of my available ports once the VPN connection is made, correct? It's harder to narrow my attack surface.

---

### Post by SeijiSensei on 2020-12-03
It makes the remote machines extensions of my local network. An attacker could only access the remotes if she broke into my local network. I also use non-standard ports for OpenVPN.  Someone trying to attack OpenVPN itself from outside would need to know both the port and, more importantly, my 2048-bit shared secret key.

I find this a much better solution than, say, SSH port-forwarding which is limited to the specified ports.  

I have four remote servers. One acts as a router with tunnels set up to each of the others.  That router is connected to my local network via its own OpenVPN tunnel with appropriate routing set up to manage the traffic.

I find this arrangement especially useful when transferring files. I can open KDE Dolphin and split the application into two windows. I point one window at a remote server with a "fish://" URL.  Then I can drag-and-drop files between my local machine and the remote server.

---

### Post by EuclideanCoffee on 2020-12-03
Thanks for the information, SeijiSensei. I'm asking specifically because I want to be sold on the idea, but I'm not quite there due to the two points you argue against SSH.

1. SSH does not need a specific port (like 22). I can assign one pretty simply. 
2. I can also use SSH, without using a standard port, to copy files from my native explorer Nautilus. You simply add ssh:// to the protocol, and it typically switches to sftp:// or the like. As long as you have a key in your .ssh folder, it works seamlessly.
3. (Not related to SSH) The key protects you from having brute force attacks access your system. However hackers typically use 0-day attacks, which are not known to the developers. These cracks break the system in a way that permits access without checking the key for example. As a result, the key becomes simply security theater. :(

Whenever I think I want to use a system like this, I become discouraged because I know the fundamentals remain. I have to open a port on my gateway. As a result, I open my whole network. Limiting access to that network can be done with SSH, but I wish to use a better method.

---

### Post by SeijiSensei on 2020-12-03
I know (1) and (2). Frankly I'm not worried about (3). Someone would have to develop a zero-day attack against OpenVPN and pick my machine out of the millions that are using it. I don't find any of that very likely. Why wouldn't sshd be equally subject to such an attack?

I'm just not as paranoid about these issues as other people I see online. I have over two decades of experience with Linux, and I've never encountered any problems of the sort you describe. Maybe I'm just lucky, but I doubt it. More likely it's because no one bothers with people like me. There are easier fish to fry.

---

### Post by EuclideanCoffee on 2020-12-03
I work in security. I've seen so many exploits in network forensics. I do not like opening my private home LAN for any reason.

---

### Post by TheFu on 2020-12-03
Don't think I've ever seen anyone attack openvpn ports. I have seen some scans and some bad connection attempts, but after a few attempts, they gave up and never returned. Just a few attempts in a week.

Back when I ran ssh on 22/tcp, I was seeing over 1000 attacks an hour, every hour, for weeks, before I put restrictions in place. Ignorance was bliss.

I wasn't paranoid until one of my systems was hacked and they attempted to convert it a C&C node.  It wasn't a high profile server, they just happened to scan and find it with some BIND software that was 3 months out of date. This was around 2002. Fortunately, they only got in and then attempted to gain root, but failed.  The method they used trying to gain root caused an warning email to be sent with each attempt - I awoke with over 1400 emails.  I wasn't going to miss that.

I think being lucky is good, but taking reasonable basic security steps and having automatic, versioned, backups is better.  The problem is that what we think is basic security, someone really new would see as being paranoid. After all, nobody has any interest in their little server, right?

---

### Post by Elmi77 on 2020-12-04
Hi,

fail2ban is a really nice tool and seems to do the job, so thanks for the hint!

No idea why it is not installed by default on Ubuntu Server...

---

### Post by DuckHook on 2020-12-04
> **Elmi77 said:**
> &#8230;No idea why it is not installed by default on Ubuntu Server...
Because many of us do not have our servers open to the WAN. We only run our servers within our local LAN. For me, fail2ban would be an impediment.

---

### Post by Elmi77 on 2020-12-05
OK, update: fail2ban could massively reduce the hacking attempts, but not completely stop it. So an other question: is there a possibility to limit SSH-access based on the geolocation of the source IP? I know that people from exactly two countries are allowed to log in, so a filter which permits only these countries would be a nice solution also for these spoofed IPs which are random.

---

### Post by The Cog on 2020-12-05
Good geolocation filters will limit hacking attempts to the those from the countries that you whitelist, but will not stop those.

Like  SeijiSensei, I would suggest using a VPN connection from your users. Except that I think I would favour wireguard over openvpn because I think it's much easier to configure. And wireguard won't even respond to callers unless their initial packet is encrypted with the correct key, so it's not easily discoverable.

---

### Post by TheFu on 2020-12-05
> **Elmi77 said:**
> OK, update: fail2ban could massively reduce the hacking attempts, but not completely stop it. So an other question: is there a possibility to limit SSH-access based on the geolocation of the source IP? I know that people from exactly two countries are allowed to log in, so a filter which permits only these countries would be a nice solution also for these spoofed IPs which are random.

Don't think blacklist. Think whitelist.  That means blacklist every IP (don't for get IPv6) and only allow the specific subnets access.  In short, ask your users.

fail2ban doesn't prevent hacking attempts.  It just catches most of them. They are still happening, but it would be better to have a belt AND suspenders when it comes to security since we all make mistakes and accidentally misconfigure things. Firewall controls are 1 layer. Which other layers have you decided to use?  

IMHO, the 3 most useful are:
* never allow passwords, use ed25519 ssh keys for all internet-based connections.
* move to a non-standard port
* setup fail2fan

My link above covers each of these.

If you add in blocking the world from access and adding a few whitelist subnets, that will drastically reduce your exposure and you won't need to trust fail2ban nearly so much.

And don't forget IPv6.  Your client machines on the LAN may be making IPv6 connections that your firewall isn't filtering at all.

---

### Post by Doug S on 2020-12-05
The simple iptables "recent" module method hasn't been mentioned on this thread yet (mentioned it many times on these forums).
Someone attempting to log in gets 3 tries, then they, and any other IP address within 10 least significant bits, are banned for over 1 day, from any port, not just the SSH port.
In recent years, it has been noticed that attackers simply change to another IP address once they get locked out, so I know default to blocking an entire sub-net:

```
#Arbitrary bit mask for the automatic IP blocking stuff (v2.08)
#
BIT_MASK="255.255.252.0"
...
# Allow any related traffic coming back to the server in.
#
#
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
...
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
# Sometimes make the lock time very long. Typically to try to get rid of coordinated attacks from China.
$IPTABLES -A INPUT -i $EXTIF -m recent --mask $BIT_MASK --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --mask $BIT_MASK --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --mask $BIT_MASK --set --name BADGUY_SSH -j ACCEPT
```

I also change the sshd_config file, adding this:

```
< #Smythies.com
< #Limit the number of bad passwords per connection to 2. Default is 6.
< #Then the iptables connection counter will kick in sooner to drop
< #password attack hackers.
< MaxAuthTries 2
<
103,105d88
<
< # Smythies.com allowed users:
< AllowUsers doug

```Someone asked about blocking by geo location. In the end I felt I had to block China, Russia and some others, using** ipset**:

```
    pkts      bytes target     prot opt in     out     source               destination
  239984 12814127 DROP       all  --  enp4s0 *       0.0.0.0/0            0.0.0.0/0            match-set china src
    4444   298983 DROP       all  --  enp4s0 *       0.0.0.0/0            0.0.0.0/0            match-set hongkong src
   17394   750936 DROP       all  --  enp4s0 *       0.0.0.0/0            0.0.0.0/0            match-set romania src
 1215881 50190401 DROP       all  --  enp4s0 *       0.0.0.0/0            0.0.0.0/0            match-set russia src
   20046   854677 DROP       all  --  enp4s0 *       0.0.0.0/0            0.0.0.0/0            match-set ukraine src

```

Now, truth be known, since I no longer travel for business and since SSH attacks were increasing at an alarming rate, I no longer allow any external SSH access, and have an iptables rule by-passing the above:

```
# OVERIDES: Secure Shell on port 22. email on port 25
#
# Sometimes I uncomment the next lines to simply disable external access.
# e-mail is too much hassle and I don't travel for business anymore.
# The conttant break-in attempts are a lot to keep up with.
echo disable external ssh access.
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 22 -j DROP
echo disable external email delivery.
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 25 -j DROP
```

Note: The reason I always left it as port 22, was because I used to study the attackers methods and methodology patterns.

---

### Post by TheFu on 2020-12-05
I suspect there's a typo? IPSEC should be **ipset**? 

I use ipset.  Thought it would be overkill for a small office, with a beginner admin, to protect ssh.  
What's that saying? "Perfect is the enemy of done."

I use ipset to protect attacks on smtp and http, but not specifically for ssh. My http and smtp servers don't allow ssh except from my specific IPv4 subnet.

---

### Post by skipbarker on 2020-12-07
Mirroring some of the other suggestions.
1. Use Fail2Ban
2. Use RSA key authentication (no passwords)

---

### Post by isrd on 2020-12-11
[https://help.ubuntu.com/community/PortKnocking](https://help.ubuntu.com/community/PortKnocking)

Port knocking, fail2ban, and non-standard SSH ports keep our bastion SSH servers nearly completely secure. The only thing you can do is rotate your port knocking sequence, but that's some pretty high-level infosec work. ;)

---

