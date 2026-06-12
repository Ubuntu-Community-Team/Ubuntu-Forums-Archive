---
title: "Best SSH Login Strategy"
date: 2011-11-21
forum: Security
---

### Post by Hack.The.Pow. on 2011-11-21
Hello all.  I run a web/file server at my house.  I run ssh on it so I can ssh into it when I'm not at home or I can run sftp to grab  random files.

I currently only use password authentication for ssh logins.  I know that this is quite insecure and that I should be using public/private keys.  

However I like being able to log in from pretty much any computer I want and be able to access my machine.  The only reason I'm concerned now is looking at my auth.log file I have noticed tons and tons of automated log in attempts through ssh.  While they are all stupid and will not get in it still concerns me.

Now would there be any way to still allow me to log in from any computer through ssh yet keep out these automated(maybe eventually not automated) log in attempts?

---

### Post by Bachstelze on 2011-11-21
Security and convenience are often competing goals. Personally, I think you should never login through SSH from "any computer" (in particulat, any compuer whose security status you cannot ascertain). If you do, you're insecure anyway so it's not like it matters. To cut the noise in auth.log, look at fail2ban.

---

### Post by Hack.The.Pow. on 2011-11-21
> **Bachstelze said:**
> Security and convenience are often competing goals. Personally, I think you should never login through SSH from "any computer" (in particulat, any compuer whose security status you cannot ascertain). If you do, you're insecure anyway so it's not like it matters. To cut the noise in auth.log, look at fail2ban.

Most of the ssh logins are through my laptop that I use.  However I do use sftp occasionally on computers on campus when either my laptop is dead or I need a file on that machine for whatever reason.  Is there any way around this?

I will look into fail2ban though. thanks

---

### Post by Bachstelze on 2011-11-22
> **Hack.The.Pow. said:**
> Most of the ssh logins are through my laptop that I use.  However I do use sftp occasionally on computers on campus when either my laptop is dead or I need a file on that machine for whatever reason.  Is there any way around this?

SSH is not the only way to grab files. You can install Apache for example and put the files you want to download in your public_html.

But if you want to use SSH, either you enable password authentication or you don't. There's no way around that that I know of.

---

### Post by /dev/random/username on 2011-11-22
If you're going to use password authentication at least use PAM module for Google 2-step verification, that is assuming you have android/iphone/blackberry cellphone [Click]("https://code.google.com/p/google-authenticator/")

fail2ban or denyhosts are good for securing ssh too.

---

### Post by Lars Noodén on 2011-11-22
If you carry a valid key on a USB-stick then you can use keys and still log in from random computers.

---

### Post by boast on 2011-11-22
just don't use the default port. 

change the port forwarding on the router, like from 9999 to 22 local.

then just ssh -p 9999 ....

---

### Post by Slim Odds on 2011-11-22
> **boast said:**
> just don't use the default port. 

change the port forwarding on the router, like from 9999 to 22 local.

then just ssh -p 9999 ....

Changing the port number does NOT in ANY way improve the security.

---

### Post by boast on 2011-11-22
> **Slim Odds said:**
> Changing the port number does NOT in ANY way improve the security.

oh yes it does. I would bet $100 those bot login attempts will go away.

He is not trying to defend himself from a targeted attack....

---

### Post by Bachstelze on 2011-11-22
> **boast said:**
> oh yes it does. I would bet $100 those bot login attempts will go away.

He is not trying to defend himself from a targeted attack....

The bot login attemps are only a security threat if your password is lousy in the first place. I hope we can all agree that having a lousy password is always a bad idea.

---

### Post by gsgleason on 2011-11-22
Use a public key encrypted with a passphrase and do not use the default port.  Also do not allow root login.

I changed from the default to a random port and I saw a dramatic decrease in the amount of dictionary/brute force attacks.

---

### Post by Slim Odds on 2011-11-22
> **boast said:**
> oh yes it does. I would bet $100 those bot login attempts will go away.

He is not trying to defend himself from a targeted attack....

The "bots" these days are far smarter than that and will scan all ports for all services. It's extremely easy to program this and "bots" do not care how hard they have to work.

I had an ssh server listening on port 23 (which is the standard FTP port) and I still got plenty of SSH login attempts.

---

### Post by Bachstelze on 2011-11-22
> **Slim Odds said:**
> 
I had an ssh server listening on port 23 (which is the standard FTP port) and I still got plenty of SSH login attempts.

The FTP port is 21. 23 is the Telnet port. ;)

---

### Post by San_SS! on 2011-11-22
> **Slim Odds said:**
> The "bots" these days are far smarter than that and will scan all ports for all services. It's extremely easy to program this and "bots" do not care how hard they have to work.

I had an ssh server listening on port 23 (which is the standard FTP port) and I still got plenty of SSH login attempts.

Port 23 is telnet's standard port, which is also a target for bot scans. Once the bot knows a port is open they usually fingerprint the service running in that port.

If you want to avoid this bot attacks you should move your ssh service to a high, not common port like 10000 (choosing port 8080 or 6667 is also a bad idea). In that way you will avoid the service of being detected by average scans.

Of course this does not increase the security of the host but at least will make your log more readable and you'll be able to detect specific attacks against you.

---

### Post by mikejonesey on 2011-11-22
did i hear $100, so if i create a honey pot on port 9999 and if it gets scanned in a couple of weeks i get $100? :D :D :D

ok ok, as was said earlyer use a usb stick to cary a key with you, if that is not possible use ssl to secure an online login where you can download the key from. This will aid in the defence from mitem attacks althogh still far from best... i don't even open port 22 to the wan...

i too recomend you use a usb device to carry a key around with you.

i too recomend denyhosts if you are to enable password auth to the wan (expect alot of emails)...

also if you are open to the wan protect yourself from the latest vulns by ensureing your software is up to date!

also switch of all headers that can identify you software versions wether it's ssh/apache/tomcat/ftp/mail whatever...

also yes bots only use weak/boaring passwords, however they also post back details on software versions found... could make you a next targeted attack...

and for info on port scan it takes me around 40min to scan 10000 ports... 

also firewall your server!

there are 3 major ip ranges that can easily be blocked: european, asian and us... choose the acordingly...

---

### Post by Slim Odds on 2011-11-23
> **Bachstelze said:**
> The FTP port is 21. 23 is the Telnet port. ;)

My mistake, I did have it on 21.

Point being was that it STILL got SSH hits.

---

### Post by Hack.The.Pow. on 2011-11-23
thanks for all the advice guys.  I ended up just setting up public/private key authentication.  I figure I can make all the files I need to access available through http and email myself for all the files I want to put back on the server.

I have also installed fail2ban.  I'm not entirely sure if its working as I pretty much have the default config installed.  when I run sudo iptables -L I find this though.  Not sure if it means that it is working or not.

```
jonzo@jonzo-station:~$ sudo iptables -L
[sudo] password for jonzo: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh 
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere       
```

As for a firewall I'm not doing anything with iptables(as you can see) or any other firewall.  I am sitting behind a router that forwards port 80 and 22(i will consider changing the port for ssh).  Is this adequate or does it still leave me at risk?

---

### Post by boast on 2011-11-24
I guess I must just be a special case where I haven't gotten a single ssh login attempt in years being a different port (for a home server, not some commercial server).

---

### Post by San_SS! on 2011-11-24
You're not a special case. Same happened to me and most people I know who did the same. :D

---

### Post by sh4d0w808 on 2011-11-25
> **San_SS! said:**
> You're not a special case. Same happened to me and most people I know who did the same. :D

Don't care, changing the default ssh server port number does NOT in ANY way improve the security...

I also had a lot of attempts on port 22, changed to a higher one, there is no hit. I think I will put it back to 22 with an installed IDS and fail2ban.

---

### Post by San_SS! on 2011-11-25
> **sh4d0w808 said:**
> Don't care, changing the default ssh server port number does NOT in ANY way improve the security...

I also had a lot of attempts on port 22, changed to a higher one, there is no hit. I think I will put it back to 22 with an installed IDS and fail2ban.

I'm not saying it does improve security. But it certainly makes logs easier to read, at least I do read logs regularly and it's not the same having them full with bot hits that with just my own logins. Thus, detecting an attack is easier and if someone gets in, it is also easier to detect.

---

### Post by sh4d0w808 on 2011-11-25
It does - at least you don't have to take care with script-kiddies. Of course if somebody really want to attack your system, there are a lot of tools out there to find an open port, so he/she will find your listening ssh. But you are one step ahead.

---

### Post by Doug S on 2011-11-25
I always watch my logs files very carefully. I also hate them becoming filled with stuff from SSH bot login attempts, as yes, and as others have mentioned, then I might miss something important. I have never bothered to change the SSH port away from port 22, but rather identifiy and eliminate the bad guy on the fly with these iptables rules:```
 
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP idiots that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT
```
(I know I am still logging stuff via iptables in the above example, but that line can be deleted. I just prefer it, at least for now. And the attack normally stops within about 3 attempts after getting on the DROP list.)

---

### Post by CandidMan on 2011-11-26
At one point I had iptables set up to only accept ssh traffic to a server from a specific MAC address, that combined with ssh key authentication I felt was a pretty sensible set up.

Only, just recently my motherboard 'died' and had to be replaced so obviously I have a new MAC address. Didn't affect me too much as I had physical access to the computer in question to change the firewall rules anyway

---

### Post by Doug S on 2011-11-26
At the risk of digression of this thread, and about iptables trust based on MAC addresses, 2 things:
 
First: Wouldn't a MAC address iptables rule only be applicable to a local area sub-net? All the packets coming from the WAN would have the MAC address of the ISP gateway.
 
Second (and this one I admit is pretty obscure): At least in my case, I have two WAN static IP addresses on the same sub-net. So one might think that I could set up some trust based on MAC addresses between the two. However, and as unbeliveable as it sounds, there is [a bug in the most recent firmware for the linksys BEFSR81 router]("http://www.smythies.com/~doug/network/mac_adr/index.html"), and it will bounce a packet destined for the other static IP address, but with its MAC address. If, because of MAC based trust, my system were to respond, the response would go to the original IP address, but now there would be an established connection. Solution: go back two versions of firmware in the BEFSR81. 
 
Anyway, as CandidMan said, for his SSH case there is another level with the key.

---

### Post by CandidMan on 2011-11-27
That's a good point, I assumed that like the originating IP address, the MAC address would remain intact. There was some trouble logging in and it could be attributable to that.
 I can think of a quick test involving canyouseeme.org to rule that out
The key authentication is arguable enough protection but my aim was to leave any possible attackers in the dark.
In an aside; if you're going to drop incoming packets with a firewall, consider dropping *everything* as unique ports that drop packets can be as telling as ports that respond to requests :-)

---

### Post by Lars Noodén on 2011-11-27
There's also not much advantage to using [drop versus reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject).  In fact there are some clear disadvantages.

---

