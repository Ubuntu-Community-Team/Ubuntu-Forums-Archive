---
title: "restricting access with iptables // dynamic ip"
date: 2012-10-31
forum: Security
---

### Post by krs360 on 2012-10-31
Afternoon,

I've been playing around a little with the iptables in unbutu 12.04.. I'm fairly new to this but I'm able to restrict access to points to a certain ip address which is what I wanted.

However, the catch comes in when I want to connect home from my mobile phone to ssh/use other services. My mobile provider gives me a dynamic ip and it seems to range so much - sometimes it's 92.x.x.x and other times 94.x.x.x.x - is there going to be anyway I can allow for this within the rules?
Other thoughts were connecting to a VPN with a static IP and then connecting home? (pref not to do this)
Within the rule under src you could add something like a no-ip.org service but im assuming it would just resolve the address there and then and stick with that IP?

Cheers,

Ben.

---

### Post by CharlesA on 2012-10-31
Lock SSH down with keys (or a super strong password) and leave the SSH port open in iptables. Maybe not ideal, but it gets the job done.

---

### Post by krs360 on 2012-10-31
> **CharlesA said:**
> Lock SSH down with keys (or a super strong password) and leave the SSH port open in iptables. Maybe not ideal, but it gets the job done.
 
hey buddy thanks for replying.
ssh is locked with keys now and disabled root login through ssh.
 
would still like to be able to access shares, etc from my phone to stream videos, etc.. but meh I guess it may not be possible to do it securely as I do not want samba to be shared via the internet.

---

### Post by CharlesA on 2012-10-31
> **krs360 said:**
> hey buddy thanks for replying.
ssh is locked with keys now and disabled root login through ssh.
 
would still like to be able to access shares, etc from my phone to stream videos, etc.. but meh I guess it may not be possible to do it securely as I do not want samba to be shared via the internet.
Indeed. Allowing Samba direct access to the internet is a bad idea. You could do sftp over ssh, but that wouldn't exactly stream the file.

---

### Post by chadk5utc on 2012-10-31
I use iptables and my mobile phone to access servers try doing MAC filtering in addition to ssh/keys. something like this:

-A INPUT -i eth1 -p tcp --destination-port 22 -m mac --mac-source 00:0F:EA:91:04:07 -j ACCEPT
I would also change the default port

---

### Post by krs360 on 2012-10-31
> **chadk5utc said:**
> I use iptables and my mobile phone to access servers try doing MAC filtering in addition to ssh/keys. something like this:
 
-A INPUT -i eth1 -p tcp --destination-port 22 -m mac --mac-source 00:0F:EA:91:04:07 -j ACCEPT
I would also change the default port
 
yeah changing the port as the first thing I did.
I'll have a go with the mac address thing - cheers.

---

### Post by Doug S on 2012-10-31
By MAC address: For a from the WAN application I do not understand. For a LAN application I do understand. As far as I know, the original source MAC address does not cross the gateway boundaries.
On my network I see the source MAC address for all external world traffic as the MAC for my ISP gateway IP address.
 
I do as Charles said earlier, however I add a "bad guy" detector so that my auth.log file doesn't get annoyingly big:```
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP idiots that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT
```I also edit sshd_config and add:```
#Limit the number of bad passwords per connection to 2. Default is 6.
#Then the iptables connection counter will kick in sooner to drop
#password attack hackers.
MaxAuthTries 2

```And yes, I have messed up when away and locked myaelf out and had to wait 90 minutes to be able to have SSH access.

---

### Post by CharlesA on 2012-10-31
Nice addition, Doug!

I use something similar that I grabbed from Bodhi:

```
# 10 minute lockout if trying to bruteforce
-A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name  SSH --rsource
-A INPUT -m recent --update --seconds 600 --hitcount 4 --rttl --name SSH  --rsource -j REJECT

```

Except, I use iptables-restore to apply the rules, not a shell script.

---

