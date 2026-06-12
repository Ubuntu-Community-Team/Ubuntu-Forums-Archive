---
title: "[SOLVED] google search re-directed to copy-book.com"
date: 2008-11-15
forum: Security
---

### Post by dougleduck on 2008-11-15
In the past day I occasionally get re-directed to a site copy-book.com. Also I seem to get caught in some strange loop with firefox going between google.com and google.co.uk.

I'm running ff 3.0.3. I have no-script running on a whitelist basis and iptables is also doing whitelisting. I've cleared cache and cookies so feel pretty safe.

Read in a  corner of the internet it might be a DNS re-direct. I have no idea what this is, or how to deal with it. Any help?

Thx in advance.

---

### Post by cariboo on 2008-11-15
Check /etc/resolv.conf, it should have the DNS addresses provided by your ISP. It should look something like this:

```
domain aplus
search aplus
nameserver 64.59.168.13
nameserver 64.59.168.15
```

In the above example the domain and search are my local network. If you don't have a network setup, the only thing in the file should be the nameserver entries.

To check /etc/resolv.conf Go to Places-->Home Folder-->Files System-->etc-->reslov.conf.

Jim

---

### Post by Kinstonian on 2008-11-15
DNS is like a phone book, but instead of mapping names to phone numbers, it maps domain names to IP addresses.  Like cariboo907 already mentioned, check your /etc/resolv.conf.  However, if it seems OK, check your router's DNS configuration.  It may of been compromised in a password guessing attack and be forwarding your DNS requests to malicious DNS servers that are redirecting requests to Google to it's malicious web servers.

---

### Post by dougleduck on 2008-11-15
Found out this is a network wide problem so isn't on our computers. This is what got returned but not sure what to do with this. Can't see how to change these. whois and the virgin site means im sure the last one is virgin though the other two seem potentially dodgy.


nameserver 0.255.112.65
nameserver 85.255.112.69
nameserver 194.168.4.100

---

### Post by Kinstonian on 2008-11-15
> **dougleduck said:**
> Found out this is a network wide problem so isn't on our computers. This is what got returned but not sure what to do with this. Can't see how to change these. whois and the virgin site means im sure the last one is virgin though the other two seem potentially dodgy.


nameserver 0.255.112.65
nameserver 85.255.112.69
nameserver 194.168.4.100

Yeah, that doesn't look right.  If it's affecting multiple computers on your network, your router very well may be compromised and reconfigured to point all of the computers on your network to the malicious DNS servers, which then points them to malicious web sites.  Do you have one of those popular Linksys or similar routers?  That perhaps had the default password?  Login to it using your web browser for example when I login to mine I go to [http://192.168.1.1](http://192.168.1.1) then type in your password (which may be the default) and then look at the DNS section to see if those DNS servers are specified manually there.  If they are, clear them out and set your router to DHCP so it will get the DNS server and other information from your ISP.

---

### Post by dougleduck on 2008-11-15
Thanks for all your help. How can this kind of attack be prevented?

---

### Post by Kinstonian on 2008-11-15
Was your router really reconfigured?  If so you should reset it to the factory settings by holding down the reset button for 15 or so seconds, and then reconfigure it to how it was before, plus change the password.

If some Windows machines went to those malicious web sites you should probably give them a quick checkup to make sure they weren't compromised.

The way it probably happened was you went to a web site that using java script or some other web code made your computer attempt to login to well known home routers with the default user name and passwords, then reconfigured the DNS settings, which were then propagated to other computers on your network.

The way to prevent it is to not use default passwords for your router (or anything else), and use NoScript to prevent your browser from running malicious web code like that.  It seems like you were doing the latter so maybe you trusted the wrong site or something, I don't know.

---

### Post by dougleduck on 2008-11-15
It had been re-configured. The DNS addresses have changed back now. Made sure the passwords were very secure now.

Do you know what potential damage could be? Could bank details, credit card details been intercepted?

---

### Post by Kinstonian on 2008-11-15
> **dougleduck said:**
> It had been re-configured. The DNS addresses have changed back now. Made sure the passwords were very secure now.

Do you know what potential damage could be? Could bank details, credit card details been intercepted?

Good question...  You could of gone to [www.bank.com](www.bank.com) and gotten redirected to a malicious copy of [www.bank.com](www.bank.com) where your password was compromised.  Similar to what phishers do, in fact compromising DNS like this is called pharming.  Basically a lot of the ways phishing sites can be detected apply to this situation.  Did you ever go to a banking website during this problem where you didn't have the lock icon in your browser?  Or did you accept a new SSL certificate when you went to a bank's website?  Or login only to be given some error and not be able to see your account after typing in your password?

It's also possible the sites that you got redirected to tried to install some malware on your computer.  Malware that could of done anything from install spyware taking over your home page, to malware that makes your computer part of a botnet.  Windows computers may of been compromised through a software or configuration vulnerability in Internet Explorer or 3rd party add-ons like Flash, Adobe Acrobat, etc. which is why I suggested investigating those computers.  Do a quick AV scan, but also look for suspicious processes using Process Explorer, check event logs around the time the incident took place, use TCP View for suspicious network connections, maybe use AutoRuns looking for suspicious startup entries, etc.

So basically yeah, it would be a good idea to change your passwords just in case.  However, changing your passwords without checking to see if your Windows computers are infected with something like a keylogger wouldn't do much good.

Oh yeah and you should probably type ipconfig /release then ipconfig /renew just to make sure your Windows computers are using the correct DNS servers now that you have restored your routers settings.

---

