---
title: "Reporting Hackers"
date: 2009-07-31
forum: Security
---

### Post by JohnnySage50307 on 2009-07-31
Though I have a fairly good firewall and strong passwords, I tend to get a little concerned when I see an out-of-the-norm malicious hack attempt. Granted, when I look at my auth.log file, I am amused to see how many noobs attempt to break in (usually after 5 tries, they give up), I was a lil jilted by seeing what appears to be a professional job. Thankfully it failed.
 
Whoever the perp was, his IP is 213.192.56.14. He attempted 68 root accesses in a span of 9min exactly. Again, thankfully all attempts failed, though looking at the periodicity of it, it looks like he was using a weak brute-force prog to break in.
 
While this is great and all, does anyone know of how one would report a suspected hacker such as the one I mentioned? This is merely to the benefit of those around me--I know i have a fairly good knowlege of network security, but I know alot of newcomers do not.

---

### Post by JohnnySage50307 on 2009-07-31
I would also like to add the IP of 202.151.219.178 to the list.  I noticed that while I was writing my last post, I was being hacked again.  Facinating.

---

### Post by jrusso2 on 2009-08-01
Only thing you can do is to report them to their ISP.  But it does not seem to do much good.  What your looking at is probably a robot program that just tried to hack ssh or other service.

Many people change the port ssh runs on and use a key instead of a password.

---

### Post by x33a on 2009-08-01
and it's more than likely that the ip is that of a proxy, or part of a botnet.

---

### Post by dlmarti on 2009-08-01
run denyhosts!

---

### Post by TuckLive on 2009-08-01
> **x33a said:**
> and it's more than likely that the ip is that of a proxy, or part of a botnet.

+1

The IP's you are seeing are probably not hackers themselves, but compromised computers that are part of a botnet.  Lookup the ISP and abuse email given for the IP's that your seeing and report them.

---

### Post by lisati on 2009-08-01
According to [www.whatismyipaddress.com](www.whatismyipaddress.com) 213.192.56.14 is in the Czech Republic and 202.151.219.178 is in Malaysia

---

### Post by JohnnySage50307 on 2009-08-01
> **TuckLive said:**
> Lookup the ISP and abuse email given for the IP's that your seeing and report them.
 
How would one look up someone's ISP given their IP address? Also, it doesn't appear that I have the "denyhosts" program available--how does one acquire it?  And thanks for the partial reverse-lookup, lisati!
 
As I was saying, sofar no successful break-ins to report. Again, I'm not too worried about someone breaking in--I would just like this to help anyone who doesn't have sufficient protection.

---

### Post by sasho_zl on 2009-08-01
You can use the "whois" command followed by the IP address to see the contact information of the ISP.

---

### Post by panhandle on 2009-08-01
I don't use it, but I think it's available via the repositories. Thus:


```
sudo apt-get install denyhosts
```

---

