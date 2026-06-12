---
title: "Viability of running SSH on default port using key auth"
date: 2010-03-08
forum: Security
---

### Post by CharlesA on 2010-03-08
Hi,

I don't think it would be harmful to run ssh on the default port of 22. Especially since the machine will only accept key-based logins and only accept traffic on port 22 from external IP addresses that I specify.

Thoughts about security risk/viablity?

Thanks!

---

### Post by bodhi.zazen on 2010-03-08
Personally I do not feel changing the port away from port 22 adds much.

If you use ssh, use keys, disable password authentication, and user something such as denyhosts, fail2ban, or a few (simple) rules for iptables.

---

### Post by CharlesA on 2010-03-08
I figured as much. Just wanted it confirmed. Thank you.

I suppose the only iffy part is if you have multiple servers with ssh access. I think you would only have to change which port you need to access a certain machine on the router, but forward it to ipaddress:22 on the local side, without needing to change the local port.

---

### Post by ikt on 2010-03-08
> **bodhi.zazen said:**
> Personally I do not feel changing the port away from port 22 adds much.

I initially got a lot of my log files filled with bots attempting to login, changing the port pretty much stopped the bots, however I hadn't heard of fail2ban or denyhosts at the time.

---

### Post by bodhi.zazen on 2010-03-08
> **CharlesA said:**
> I figured as much. Just wanted it confirmed. Thank you.

I suppose the only iffy part is if you have multiple servers with ssh access. I think you would only have to change which port you need to access a certain machine on the router, but forward it to ipaddress:22 on the local side, without needing to change the local port.

If you have multiple servers you can consider, as alternates, either ssh into a single server then ssh from there to others or VPN.

However, changing the port is easiest, and there is nothing wrong with that option. It is just, after several years experience, I no longer feel changing your port does much to increase security.

If you are using keys and iptables / TCP Wrappers, denyhosts, etc you are fine.

---

### Post by CharlesA on 2010-03-08
Thank you!

---

### Post by fargle on 2010-04-14
Changing the port can help if your server is Internet-facing though - it's not total security by a longshot, but at least there's much less chance of an automated script finding your SSH port to bang against.  There's nothing saying that even if you disable password authentication, a zero-day will come along that you don't know about and you'll be exposed.  Less risk if the script can't find your port.

Also some ISPs don't like listening services and look for them, they won't find them if they're on non-standard ports as they don't do a total portscan.

---

### Post by HermanAB on 2010-04-15
SSH is secure, so you will be safe.

However, there are brute force scripts on the wild wild web that will hammer a server with tens of thousands of login attempts per hour on ports 21 (FTP) and 22 (SSH).  The faster your server and internet connection, the worse it will be.    

My servers used to get two or three of these per day, so the log files would get filled up with crud and the mail delivery would get slow. Therefore I now always configure my servers to use non standard ports for these two services.

---

### Post by OpSecShellshock on 2010-04-15
> **HermanAB said:**
> SSH is secure, so you will be safe.

However, there are brute force scripts on the wild wild web that will hammer a server with tens of thousands of login attempts per hour on ports 21 (FTP) and 22 (SSH).  The faster your server and internet connection, the worse it will be.    

My servers used to get two or three of these per day, so the log files would get filled up with crud and the mail delivery would get slow. Therefore I now always configure my servers to use non standard ports for these two services.

+1

If your logs are cluttered up with events you know are failures, they might either hide or over-write events you'd be more concerned about. Other than that there's not much benefit, but I'd consider it quite a benefit to not get flooded with reports of non-issues when I'm responsible for checking the logs to make sure nothing weird is happening.

---

