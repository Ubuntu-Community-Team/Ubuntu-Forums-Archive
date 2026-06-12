---
title: "Troubleshooting why customer cannot SSH in: ufw"
date: 2019-03-26
forum: Server Platforms
---

### Post by sam_w2 on 2019-03-26
I'm learning the new, to me, ufw tool to manage the underlying iptables firewall in our new server. I've set up initial rules for port 22, 80, 443, 3306 and they work. One duty of this server is to block IP's from certain countries so I was grateful that ufw had a better interface for setting up my list of IP blocks and set them up in my /etc/ufw/before.rules as it's important that these blocks are set up early on. I believe I placed them in the right place in the before.rules. I ran 
[FONT=courier new]sudo ufw enable
sudo service ufw restart[/FONT]
And I could see the result in 
[FONT=courier new]sudo ufw status[/FONT]
where I saw the new rules in their place.

My customer has to SFTP in as well to do some work. With these rules in place, he and I have been able to use port 22. Until yesterday. I was able to SSH, SFTP but my customer lost the ability to do so as port 22 was blocked. My customer was able to SFTP into an unrelated server so it doesn't seem to be his firewall in his place of work.
I had set up logging for UFW and saw in syslog his blocked attempts earlier. Ah, I can fix that in ufw! 

[FONT=courier new][COLOR=#000000]sudo ufw insert 1 allow from 96.87.0.0/24 to any port 22[/COLOR][/FONT][COLOR=#000000][FONT=-webkit-standard]
And I confirmed in /etc/ufw/user.rules its place after I ran
[/FONT][/COLOR][FONT=courier new]sudo ufw enable
sudo ufw reload[/FONT]
[COLOR=#000000][FONT=-webkit-standard]
Customer complains that he is still unable to log in. His ssh -vv output:
[/FONT][/COLOR][COLOR=#000000][FONT=-webkit-standard][FONT=Menlo]Connection refused[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Connection closed
But syslog reveals only the earlier blocked attempts which suggests that ufw did its job but [/FONT][/COLOR][FONT=Menlo][COLOR=#000000]he's still blocked. The logs also reveal that there are lots of other IP blocked, presumably from my country blocks.

One thing I'm surprised is that the output of 
[FONT=courier new]sudo ufw status[/FONT] 
now shows only the bare minimum of the initial firewall setup before I added the country blocks in before.rules. 
That said, I've run 
[FONT=courier new]sudo iptables -L > iptableoutput[/FONT]
and used vim to find any mention of '[/COLOR][/FONT][FONT=-webkit-standard][SIZE=3][COLOR=#000000][FONT=courier new]96.87.0[/FONT]'[/COLOR][/SIZE][/FONT]
[FONT=-webkit-standard][SIZE=3][COLOR=#000000]in this output because a subsequent online search suggests that even if I whitelisted his block, there might be another rule elsewhere that's blocking him suddenly. But vim returned nothing with those search terms in its rules.

Perhaps ufw refreshed itself over the weekend? But iptables still has the rules from my initial setup using before.rules.

I've rebooted the server and my customer reports the same output using ssh -vv.

I know this is something goofy with my environment, but I'm hoping others may suggest any false assumption, goofed rules or other troubleshooting things to try so that my customer can still get into this server, thx sam[/COLOR][/SIZE][/FONT]
[COLOR=#000000][FONT=-webkit-standard]

[/FONT][/COLOR]

---

### Post by Doug S on 2019-03-26
Myself, I wouldn't be able to help without a complete iptables rules listing (even though I am not a fan of ufw, and have difficulties reviewing its resulting iptables rules).
> **sam_w2 said:**
> That said, I've run 
[FONT=courier new]sudo iptables -L > iptableoutput[/FONT]
and used vim to find any mention of '[/COLOR][/FONT][FONT=-webkit-standard][SIZE=3][COLOR=#000000][FONT=courier new]96.87.0[/FONT]'[/COLOR][/SIZE][/FONT]
[FONT=-webkit-standard][SIZE=3][COLOR=#000000]in this output because a subsequent online search suggests that even if I whitelisted his block, there might be another rule elsewhere that's blocking him suddenly. But vim returned nothing with those search terms in its rules.to avoid IP addresses being converted to domain names where possible, you would have to run:
```
sudo iptables -L -n
```Myself, I only ever run:
```
sudo iptables -v -x -n -L
```

---

### Post by sam_w2 on 2019-03-27
Excellent! Thank you for suggesting better commands. Having said that, the only instance I find of this substring of his IP in the output of iptables is found a few lines at the bottom where his whitelist exists for both TCP and UDP.
 0        0 ACCEPT     tcp  --  *      *       96.87.0.0/24       0     .0.0.0/0            tcp dpt:22
Unless I'm wrong, iptables, and ufw is not the cause of his being blocked and would then suggest that another factor is in play?

---

### Post by Doug S on 2019-03-27
> **sam_w2 said:**
> Unless I'm wrong, iptables, and ufw is not the cause of his being blocked and would then suggest that another factor is in play?Without seeing the entire iptables rule set, we can not say for sure. However, I observe that the packet counters are 0, so that path has never been taken since the last time the counters were zeroed. They should have incremented when your customer tried to ssh in. So my first suggestion is to check that. I find the packet counters extremely useful for iptables debugging.

I would also suggest to use tcpdump (or wireshark, if you prefer) to observe your customer packets arriving and leaving the server. Sometimes that can help to determine if the issue is one of: The packets not arriving at all; Packets arriving but no reply; Packet replies going out, but not getting to the customer. For example, change the interface name and the IP address:
```
sudo tcpdump -n -tttt -i enp2s0 host 96.87.0.13
```

Perhaps also double check your rule sub-net mask. You are using /24 but that particular sub-net is /21. i.e. 96.87.0.0/21. See [here]("https://whois.arin.net/rest/net/NET-96-87-0-0-2/pft?s=96.87.0.1")

---

### Post by TheFu on 2019-04-20
I use **ipset** to have entire blocklists in a single rule.  There are a few how-tos out there. [https://www.linuxjournal.com/content/advanced-firewall-configurations-ipset](https://www.linuxjournal.com/content/advanced-firewall-configurations-ipset)  We are blocking about 8K subnets today. Having a separate rule for each of those would really slowdown the server. When we hit 7K rules, I moved everything over to ipset. It was easier to manage, that is certain.  I didn't measure performance, except the startup time for all the rules to be applied.  ipset is instantaneous.  On one system, we had about 50 ufw rules, those were taking about 1 sec per rule to be applied.  It was painful and I didn't appreciate ufw putting manually entered rules in /lib/ufw/ instead of into /etc/ufw/ .  I wasn't backing up anything in /lib/ .... since libraries would be put back with any OS re-install.  

I thought it was a bad idea to mix ufw and iptables interfaces to the firewall? Too easy to have conflicts is what I was told.  I saw some conflicts, so switched to using ufw only for trivial needs and using iptables for everything else, especially server needs.

For ssh, we try to only open specific IPs where we know our people will be and block everything else. We also run it on a non-standard port (I have the internet router setup to handle the port translation) and we don't allow any passwords to be used for ssh-based access. If they don't have a ssh-key or a ssh-cert, then they don't get in.  Period.  The sshd_config file has support for all of that - so passwords can be used from corporate network subnets and everything external must use anything except a password for authentication.

Anyway, just some thoughts.

---

### Post by SeijiSensei on 2019-04-20
Perhaps the client's IP address has changed? Do you have any logging rules in the iptables set?

---

