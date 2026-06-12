---
title: "Problem with UFW blocking traffic on port 80"
date: 2016-01-22
forum: Security
---

### Post by wtsn on 2016-01-22
Hi

I have been using UFW in conjunction with fail2ban to add a layer of protection to our webservers.

UFW is set to allow port 80, but seems to be blocking some traffic on port 80.

Jan 22 14:02:04 kernel: [UFW BLOCK] IN=eth0 OUT= TTL=57 ID=55539 PROTO=TCP SPT=57659 DPT=80 WINDOW=65535 RES=0x00 ACK RST URGP=0 

Now we've had confirmation that this is stopping people from accessing our site.  Is this only happening because fail2ban is configured to block repeat offenders or is it as a result of the UFW block.

As a possible solution i've added their ip address to the white list on the fail2ban rule.

I look forward to hearing from you.

---

### Post by QDR06VV9 on 2016-01-22
No expert here but this might get the ball rolling..
What is the output of this in the terminal
```
[COLOR=#111111][FONT=Consolas]sudo ufw status verbose[/FONT][/COLOR]
```

---

### Post by deadflowr on 2016-01-22
Moved to Security

(As more users who understand ufw will frequent this section)

---

### Post by mcparty2 on 2016-01-22
Can you show the output of the following, it might help us see what is happening?

```
 iptables -L
```

and

```
 cat /etc/fail2ban/fail2ban.local 
```

---

### Post by Doug S on 2016-01-22
> **wtsn said:**
> Jan 22 14:02:04 kernel: [UFW BLOCK] IN=eth0 OUT= TTL=57 ID=55539 PROTO=TCP SPT=57659 DPT=80 WINDOW=65535 RES=0x00 ACK RST URGP=0That is normal entry. Notice the "RESET" flag, it is merely trying to reset the TCP connection. However, the TCP connection has already been closed and forgotten about.

> **wtsn said:**
> Now we've had confirmation that this is stopping people from accessing our site. It shouldn't, as already mentioned it is normal.

> **wtsn said:**
> Is this only happening because fail2ban is configured to block repeat offenders or is it as a result of the UFW block.I do not use fail2ban, and so do not know. However, it seems likely that fail2ban might be triggering false positives on this innocent type of packet.

---

### Post by wtsn on 2016-01-25
> **Doug S said:**
> That is normal entry. Notice the "RESET" flag, it is merely trying to reset the TCP connection. However, the TCP connection has already been closed and forgotten about.

 It shouldn't, as already mentioned it is normal.

I do not use fail2ban, and so do not know. However, it seems likely that fail2ban might be triggering false positives on this innocent type of packet.


Great thanks for everyones help.  I've gone through the logs and have confirmed that it is fail2ban that is causing the disruption.  I've gone through the ufw.log and and ACK FIN, RST, ACK RST and ACK are also being blocked on port 80.  Can these also safely be ignored and deemed normal?

Thanks

---

