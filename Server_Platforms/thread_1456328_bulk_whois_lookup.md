---
title: "bulk whois lookup"
date: 2010-04-17
forum: Server Platforms
---

### Post by zfreak7c5 on 2010-04-17
I have been trying to figure out how to have whois do a bulk lookup on my server running Ubuntu 10.04.  I am about the only one who uses the server and just want to see where the other IPs are coming from on inbound connections.  So far there are about 160 IPs.  What I have tried is cat ip.txt | whois > is.txt as well as cat ip.txt > whois > is.txt.  All it does is error out or does nothing.  Anyone have an idea?  Thanks,

---

### Post by uberlinuxnerd on 2010-04-17
If the file just has the IP's listed in it, with one per line. The below will work on the shell.

```
for i in `cat ips.txt`; do whois $i >> out.ips; done
```

---

### Post by zfreak7c5 on 2010-04-17
Still not working, it runs without errors, but the file is just full of No whois server is known for this kind of object.  My source file is one IP per line.

thanks,

---

### Post by uberlinuxnerd on 2010-04-17
> **zfreak7c5 said:**
> Still not working, it runs without errors, but the file is just full of No whois server is known for this kind of object.  My source file is one IP per line.

thanks,

I think what you may be looking to do is a reverse ip lookup. Is this correct?

---

### Post by zfreak7c5 on 2010-04-17
yeah, whois works fine if I run it with one IP, I know I figured it out a while ago, just can't remember what I did.

---

### Post by uberlinuxnerd on 2010-04-17
> **zfreak7c5 said:**
> yeah, whois works fine if I run it with one IP, I know I figured it out a while ago, just can't remember what I did.

odd... ```
whois 216.239.59.104
``` returned google for me so by rights the above for loop should work. Maybe if you pastebin out.ips and I will take a look.

---

### Post by zfreak7c5 on 2010-04-17
I think I found out what was happening, the script is fine, but some IPs the were listed are not accepted by whois. For example 239.255.255.250 errors out and seems to cause the rest of the IPs to not be looked up.  If I make a list without the IPs with the issue it runs fine, not sure why they are not accepted by whois though, I can look them up on a online whois database just fine.  I wonder if there is some way to modify the script to just ignore the ones that error out?  I got these IPs using the darkstat monitor if that helps at all.

---

### Post by koenn on 2010-04-17
239.255.255.250 is a multicast address, it does not belong to (a host in) a registered address range, that's probably why whois doesn't handle it.

[http://www.iana.org/assignments/multicast-addresses/](http://www.iana.org/assignments/multicast-addresses/)



I don't know why one lookup would cause all the following lookups to fail, though

---

### Post by zfreak7c5 on 2010-04-17
Got it working finally, the source file was created on a windows box and copied to the server with FileZilla, seems that some of the windows text formatting was left over and was causing it to trip up even though it appeared fine in vim.  Just copied the contents into a new file with vim and it runs fine.  Thanks for all the help.

---

### Post by sharimila on 2010-08-08
I found this site  [http://www.whoisxy.com/](http://www.whoisxy.com/)    It give domain name,ip address and got nice result at free of cost ...
Its equally to good to smartwhois

---

