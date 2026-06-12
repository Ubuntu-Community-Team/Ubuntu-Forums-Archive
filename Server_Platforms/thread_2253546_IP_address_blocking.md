---
title: "IP address blocking"
date: 2014-11-20
forum: Server Platforms
---

### Post by Vaindil on 2014-11-20
Hello! I guess this isn't technically related to Ubuntu specifically, it's more of a general networking question, but I'm not sure where else to ask it. I apologize if I shouldn't ask it here!

I installed fail2ban on my server, and I've had a TON of bans (like 30 or so in the past week) originate from the same IP address block (IP.IP.x.x). Is there a way to search for IP address by block using wildcards to see if they're all allocated to the same ISP or something so I can just wildcard ban that entire IP block? The only public-facing thing I have on my server is my personal website, and all of the bans have originated from Chinese ISPs (I'm in the US), so I don't have an issue with using a wildcard to ban them, I just want to make sure I don't go too far with the ban.

Any information at all would be helpful. Thank you!

---

### Post by Lars Noodén on 2014-11-20
Yes, you can look up the address range in several steps.  First find out the ip number.  Then find out who owns that and the AS number:

```

whois 173.252.120.6 | grep "OriginAS:"

```

Then extract all the networks that belong to that AS number:

```

 whois -h whois.radb.net  '!g*AS32934*'| tr ' ' '\n'| sort -n -k1 -k2 -k3 -k4 > /tmp/rejects.txt

```

Edit out the two non-address lines.  Then you can add them with UFW one at a time or autoamtically:

```

for i in $(cat /tmp/rejects.txt);do sudo ufw --dry-run reject from $i;done

```

That will not work against machines that are attacking from a popular hosting provider because it would block all others using the same hosting service even though they are not part of the same group.

---

### Post by Habitual on 2014-11-20
> **Lars Noodén said:**
> Yes, you can look up the address range in several steps.  First find out the ip number.  Then find out who owns that and the AS number:

```

whois 173.252.120.6 | grep "OriginAS:"

```

Then extract all the networks that belong to that AS number:

```

 whois -h whois.radb.net  '!g*AS32934*'| tr ' ' '\n'| sort -n -k1 -k2 -k3 -k4 > /tmp/rejects.txt

```

Edit out the two non-address lines.  Then you can add them with UFW one at a time or autoamtically:

```

for i in $(cat /tmp/rejects.txt);do sudo ufw --dry-run reject from $i;done

```

That will not work against machines that are attacking from a popular hosting provider because it would block all others using the same hosting service even though they are not part of the same group.

Great Stuff Lars, Thanks!

---

### Post by Vaindil on 2014-11-21
This is awesome. Thank you so much, I greatly appreciate it!!!

EDIT: Not awesome, not awesome! All access to my site is now blocked via SSH, navigating to the external-facing site, everything! Eegads! The firewall is doing this; disabling it (sudo ufw disable) to test allowed the connections through. What do I need to do to restore normal access? sudo ufw status reports a bunch of REJECTed IP addresses To ANYWHERE.

[IMG]http://i.imgur.com/pgqyddm.png[/IMG]

---

### Post by Lars Noodén on 2014-11-21
You can clear UFW and restore the factory defaults this way:

```

sudo ufw reset

```

It goes / went without saying, but I should have said it anyway, that if you are serving up SSH, HTTP and HTTPS, you need to add lines for those too to allow them in.   The lines in #2 above are some of the actual ones I am using but for desktop / notebook.

---

### Post by SeijiSensei on 2014-11-21
Are you connecting to the server from a known, fixed IP address?  If so, I'd just add these rules:
```

/sbin/iptables -A INPUT -p tcp -s your.own.ip.addr --dport 22 -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 22 -j REJECT

```
Then connections from "your.own.ip.addr" will be accepted and all others blocked.  Much easier to manage than something like fail2ban.

If your local IP changes regularly, I recommend using OpenVPN instead.  Set up an OpenVPN instance on the server using a [shared key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html"), then connect to it from your local machine.  This is the method I use to communicate with my servers in the cloud.

---

### Post by Doug S on 2014-11-21
As I mentioned recently on [another thread]("http://ubuntuforums.org/showthread.php?t=2251760") "I have been noticing increased SSH brute force stuff from China recently  (several months). The attacks are also very sophisticated and  methodical, merely switching to another IP address on the same sub-net  or a different sub-net entirely once they are blocked."

When I observe an SSH attack from a couple or more IP addresses from the same China allocation block, then I permanently block the entire allocation block. I do not care about collateral damage. I use [this]("http://ip2location.com/free/visitor-blocker") as my allocation reference.

From your screen shot I observe that you have multiple entries that are actually from bigger China allocation blocks, where multiple entries could be combined.

---

### Post by Vaindil on 2014-11-21
I'd like to keep the IP addresses blocked that I already have blocked; I've manually checked each of those ranges and they're all ranges that I don't want traffic from. I'm using fail2ban and it's been working very well; is there a way to simply allow web/SSH connections from anywhere EXCEPT those IP address ranges that I or fail2ban explicitly ban? I know this is insecure, but I don't have anything secret on this server at all that could be compromising. I also frequently change locations (I use a VPN service, mainly), so I don't want to have to pull up my VPS panel every time I need to whitelist a new IP address.

I apologize if these are very simple questions; I've tried looking up guides for ufw and iptables but it all seems very complicated despite ufw's name.

---

### Post by Doug S on 2014-11-21
Actually, from what you posted it is not clear to me what is wrong or why everything for SSH is now being blocked. You'll have to post more information, like perhaps your entire ufw generated iptables (although I do not like trying to read ufw generated iptables).

---

### Post by Vaindil on 2014-11-21
I've attached a few different files, not sure which you'd prefer. They're named according to the command: ufw status numbered, ufw show raw, and iptables -nL. (Sorry ufwraw.txt is zipped, unzipped it's 30KB which is larger than the forum allows.)

---

### Post by Lars Noodén on 2014-11-22
Just out of curiosity, is the network you are connecting *from* included in the list  ufwstatusnumbered.txt?

---

### Post by Vaindil on 2014-11-22
> **Lars Noodén said:**
> Just out of curiosity, is the network you are connecting *from* included in the list  ufwstatusnumbered.txt?
Fair question, but no: I'm connecting from 35.32.x.x.

---

### Post by flaymond on 2014-11-22
If me...I will just use MAC filters to block devices using 192.168.1.1 from using my Internet Service.

---

### Post by Lars Noodén on 2014-11-22
In  ufwstatusnumbered.txt, the 4th line catches connections to port 22 and refers them to the target chain fail2ban-ssh which is on line 30.  That chain then does nothing with the connection but return to the INPUT chain for further processing and no other rules seem to address ssh, or for that matter HTTP Or HTTPS.  You have to set UFW (or fail2ban??) to allow incoming connections to port 22 somewhere.  If you are serving up SSH, HTTP and HTTPS, you need to add lines to allow them in.  I haven't used fail2ban at all, not even sshguard either, so I'm not sure whether rules added in UFW are processed before or after fail2ban chains.  A quick perusal of the online manual showed nothing in that regard so my guess would be that you have to do:

```

sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https
sudo ufw status verbose | less

```

and then check that UFW placed these after the block/reject rules in the *ufw-user-input* chain.

---

