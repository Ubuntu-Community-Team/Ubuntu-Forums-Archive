---
title: "iptables rules for minimal webfilter vm"
date: 2011-09-19
forum: Security
---

### Post by HarriU11-04 on 2011-09-19
Hello

I have a WinXP system on which I have created a virtual machine Ubuntu11.04 web filter (Dansguardian + squid). I'm having trouble with ufw (firewall) in that, when I enable it, connectivity from the Windows Firefox disappears. Now I thought about just throwing in a few iptables rules instead of using ufw, but I do not know what the best ruleset is.

The vm is ubuntu server minimal install (no GUI), but has clamav. Is there an agreed set  of minimal rules that I should apply?

The physical Windows box already has Norton Internet Security, BlackIce, and a hosts file to protect it against viruses, adverts, etc.

Does anybody have a suggestion for 'standard' iptables rules?

Thank you

---

### Post by OpSecShellshock on 2011-09-19
Just guessing here, but it almost seems as if the Ubuntu server is refusing incoming connection attempts from the Windows machine when ufw is enabled. This makes sense in a default scenario. I'm assuming that the server has a service on it that is listening for connections from the Windows computer that you're running Firefox on. If that's the case, then you'll want to enable the port for that service in ufw. Doing so with iptables will have the same net effect since those rules are what ufw acts on. You'll want to make sure that the incoming connections are only allowed from the Windows desktop, and not from just anywhere. If I knew how I'd say so, but I don't deal with servers much (sorry). There's bound to be a tutorial around here somewhere.

---

### Post by Dangertux on 2011-09-19
When you say you enabled ufw, did you just turn it on or did you allow connetions to the squid proxy server?

I'm assuming (correct me if I'm wrong) you're using squid as a transparent proxy? 

If so you need to allow a connection to the squid server itself, outbound connections should be fine with default rules. However, in UFW you would have to add something like this.

```

sudo ufw allow from 172.16.16.0/24 to 172.16.16.10 port 80 proto tcp

```This assumes the following 172.16.16.0 is the network that your VM is running on 172.16.16.10 is the address of the VM and port 80 is the port your Squid Proxy is running on.

and the iptables equivalent

```

iptables -A INPUT -s 172.16.16.0/24 -d 172.16.16.10 -p tcp --dport 80 -j ALLOW

```Hope that helps ;-)

---

### Post by HarriU11-04 on 2011-09-29
> **Dangertux said:**
> When you say you enabled ufw, did you just turn it on or did you allow connetions to the squid proxy server?

I'm assuming (correct me if I'm wrong) you're using squid as a transparent proxy? 

Thanks for responding. I did "sudo ufw enable", like all good little security-conscious newbs do, then i saw the whole list of iptables rules that it created ("iptables -L").

I am using squid as a transparent proxy.

With those commands you gave, I found that executing them first, then enabling ufw afterwards works best. Obviously ordering of the rules is important. One thing: for the iptables command, the target to jump to should be "ACCEPT", not "ALLOW".

I will now test some more and then incorporate this into bootup, but thank you very much for your help!

---

### Post by HarriU11-04 on 2011-09-29
On reboot after enabling ufw I get various error messages:

iptables-restore: line 66 failed
iptables-restore v1.4.10: Couldn't load target 'skip-to-policy-input': /lib/xtables/libipt_ufw-skip-to-policy-input.so: cannot open shared object file: No such file or directory
.....

and  so on?

---

