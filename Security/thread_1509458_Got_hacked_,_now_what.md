---
title: "Got hacked , now what ?"
date: 2010-06-14
forum: Security
---

### Post by superheavy on 2010-06-14
Hello Everyone , 
  Someone caught me slipping , and exposed my noobness to the world and used my VPS for spamming.  
      My question is this , how do I go about finding out how they got in.  I checked my auth.log and nothing seemed strange , except for something about a PAM/dlopen not being able to complete.  
   The only ports open are http,ssh,mysql (local only) and glassfish ( running as glassfish user ).

Thanks  

P.S Don't smack me too hard

---

### Post by Ryan Dwyer on 2010-06-14
Out of curiosity, how do you know it was used for spamming?

---

### Post by superheavy on 2010-06-14
I got a message from my VPS provider that my server had been reported for spamming =(

---

### Post by bodhi.zazen on 2010-06-14
First you should ask your VPS provider for details. If they are confident you were compromised they should share what they know. 

Of those services my guess would be they got in via ssh.

Since you are new to all this I suggest you first read the security sticky.

Then back up your VPS data and re-install your VPS.

In the future, if you run ssh, use keys, disable passwords, and use a service such as denyhosts or fail2ban.

If you are interested you could image your VPS and try to run forensics.

---

### Post by Ryan Dwyer on 2010-06-14
I always run SSH on a non-default port. I suggest everyone do the same.

---

### Post by bodhi.zazen on 2010-06-14
> **Ryan Dwyer said:**
> I always run SSH on a non-default port. I suggest everyone do the same.

That does not help much, the non-default port is easily discovered (so take care). You need to user strong passwords (at a minimum), although I prefer keys only.

In addition consider denyhosts or fail2ban or a few rules in iptables.

If your ssh server is secure, the port does not matter, although you get more noise in the logs with a port of 22.

My point is, just changing the port is insufficient to secure ssh.

---

### Post by CharlesA on 2010-06-14
+1 to bodhi.zazen.

I recently switched from running SSH on a non default port to port 22. Mine is using keys only, and I don't have DenyHosts or Fail2Ban installed - however, I have locked SSH down to accept connections from only a couple IP addresses, so that's pretty much as secure as it's going to get.

---

### Post by ld.4lpha on 2010-06-15
By using tools such as fail2ban, you potentially implement a DOS vulnerability on your server.

---

### Post by CharlesA on 2010-06-15
> **ld.4lpha said:**
> By using tools such as fail2ban, you potentially implement a DOS vulnerability on your server.

Explain?

---

### Post by ld.4lpha on 2010-06-15
If someone spoofs your IP and throws a bunch of bogus login attempts at your server, it would add deny rules on your firewall for (or otherwise blackhole) your IP.

This is true unless, of course, fail2ban provides some kind of "whitelist" functionality to prevent this from happening (which it very well may...I'm not certain, as I don't use the tool).

So I guess I should have stated:

"By using tools such as fail2ban, you potentially implement a DOS  vulnerability on your server unless you take care to configure some form of 'whitelist' capability."

---

### Post by CharlesA on 2010-06-15
I've not heard of that happening, but I haven't used fail2ban. *shrug*

---

### Post by bodhi.zazen on 2010-06-15
> **CharlesA said:**
> Explain?

If somebody spoofs your ip address, these tools will lock you out.

The solution is to white list your ip address, which can be done with iptables and denyhosts, not sure about fail2ban .

---

### Post by CharlesA on 2010-06-15
> **bodhi.zazen said:**
> If somebody spoofs your ip address, these tools will lock you out.

The solution is to white list your ip address, which can be done with iptables and denyhosts, not sure about fail2ban .

Thanks for the info. I might have to play around with fail2ban, but idk.

---

### Post by bodhi.zazen on 2010-06-15
> **CharlesA said:**
> Thanks for the info. I might have to play around with fail2ban, but idk.

If you understand iptables (and I think you do), I find it easier then installing yet another service such as denyhosts or fail2ban.

denyhosts uses tcpwrapper (/etc/hosts.deny) plus it has the ability to track naughty ip addresses, both in a local data base but also in a central database.

fail2ban covers additional services and it a bit more complex to configure. fail2ban will monitory your logs and can be configured to watch ftp, ssh, http, etc. fail2ban uses iptables (I think).

Once I learned iptables, I fine it easier to configure iptables to cover the services I need.

tcpwrapper is also easy to configure and I use that for ssh.

---

### Post by CharlesA on 2010-06-15
Yup, I am using iptables so far and it's working great. :)

A lot easier to configure too. Heh.

---

### Post by Malac on 2010-07-19
fail2ban can be configured to ignore ip so that will stop DOS attacks from having effect. 
The value is in jail.conf, [DEFAULT] section and is called "ignoreip"
 
Hope this helps.

---

### Post by HermanAB on 2010-07-20
The most important security tip is not to use stupid short passwords.

---

### Post by ov3rcl0ck on 2010-07-20
if you use more than just SSH for admin access like Webmin, FTP, or something then I'd recommend channeling all your admin tools over VPN using OpenVPN, then any admin tools are locked down in a VPN tunnel.

Forensics is rather hard, so I'd find out what exactly has been going on before acting too fast, maybe something is bugging and just caught in a loop with sendmail, or something else that would appear as spamming.

---

### Post by CharlesA on 2010-07-20
> **ov3rcl0ck said:**
> if you use more than just SSH for admin access like Webmin, FTP, or something then I'd recommend channeling all your admin tools over VPN using OpenVPN, then any admin tools are locked down in a VPN tunnel.

I usually have those only have stuff like webmin tunneled over SSH and not accessible directly from the internet. It's a bit more secure that way.

Haven't bothered with VPNs for that.

---

### Post by Sporkman on 2010-07-21
You can configure iptables to limit the rate of connections attempts, which will render bruteforcing ineffective, for example:

```
iptables -A INPUT -p tcp --dport <your ssh port> -m limit --limit 6/minute -j ACCEPT

```

---

