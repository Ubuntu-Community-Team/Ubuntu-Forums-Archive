---
title: "Making MX Records"
date: 2012-09-23
forum: Server Platforms
---

### Post by Xalogen on 2012-09-23
Alright so I am very new to running my own DNS server and having to configure it all up but this is what I got so far. I have my DNS servers responding and actually being seen and they are routing the addresses and I can send and receive emails but however when I try to use mxtoolbox to lookup my mx my dns servers report nothing. Here is a copy of what is in my dns record

```
$ttl 38400
example.net.	IN	SOA	ns1.example.net. user.example.net. (
			1348391469
			10800
			3600
			604800
			38400 )
example.net.	IN	NS	ns1.example.net.
www.example.net.  IN      CNAME   example.net.
mc.example.net.   IN      A       11.11.1.111
example.net.      IN      A       11.11.1.111
ns1.example.net.  IN      A       11.11.1.111
example.net.      IN      MX   50 11.11.1.111
ns2.example.net   IN      A       11.11.1.111
```

I've removed the domain and my IP Address

Thanks for any help. The system is Linux Debian, I know this is Ubuntu Forums but I had saw another user who had trouble with his  NS records and he was able to get help so I hope this doesn't cause a problem.

---

### Post by Cheesemill on 2012-09-23
Your MX record is wrong.

You can't have an IP address as an MX record, it has to point to a named A record.

---

### Post by Xalogen on 2012-09-23
> **Cheesemill said:**
> Your MX record is wrong.

You can't have an IP address as an MX record, it has to point to a named A record.

Oh I feel like such an idiot, ok its working now thank you. :)

---

### Post by Xalogen on 2012-09-23
Alright now I got another problem, after a couple of hours I went to do a diagnostics of my email server and it came back with this.

```

[red] Test MX Records
[green] trying to resolve MX records for example.net
[red] Error: MX recrods for domain example.net could not be resolved

[red] Test local connect
[green] Connecting to TCP/IP address in MX records for local domain domain example.net...
[red ERROR: MX records for local domain example.net could not be resolved
```

Key: [red] = red circle [green] = green circle

and my dns record file is 

```
$ttl 38400
example.net.	IN	SOA	ns1.example.net. user.example.net. (
			1348391482
			10800
			3600
			604800
			38400 )
example.net.	  IN	  NS	  ns1.example.net.
example.net.      IN      NS      ns2.example.net.
www.example.net.  IN      CNAME   example.net.
mc.example.net.   IN      A       11.11.11.111
example.net.      IN      A       11.11.1.111
ns1.example.net.  IN      A       11.11.1.111
ns2.example.net.  IN      A       11.11.1.111
example.net.	  IN	  MX	1 example.net.


```

what could be wrong here?

---

### Post by Xalogen on 2012-09-23
> **Xalogen said:**
> Alright now I got another problem, after a couple of hours I went to do a diagnostics of my email server and it came back with this.

```

[red] Test MX Records
[green] trying to resolve MX records for example.net
[red] Error: MX recrods for domain example.net could not be resolved

[red] Test local connect
[green] Connecting to TCP/IP address in MX records for local domain domain example.net...
[red ERROR: MX records for local domain example.net could not be resolved
```

Key: [red] = red circle [green] = green circle

and my dns record file is 

```
$ttl 38400
example.net.	IN	SOA	ns1.example.net. user.example.net. (
			1348391482
			10800
			3600
			604800
			38400 )
example.net.	  IN	  NS	  ns1.example.net.
example.net.      IN      NS      ns2.example.net.
www.example.net.  IN      CNAME   example.net.
mc.example.net.   IN      A       11.11.11.111
example.net.      IN      A       11.11.1.111
ns1.example.net.  IN      A       11.11.1.111
ns2.example.net.  IN      A       11.11.1.111
example.net.	  IN	  MX	1 example.net.


```

what could be wrong here?

NVM the thing fixed itself maybe just a connection error.

---

### Post by TopCoder01 on 2012-09-25
You can also test to see if everything is set up properly by sending an email to mailtest [at] unlocktheinbox.com

It will auto respond, telling you if everything is configured correctly. 

You can read more about the tool here: [Testing your Email Authentication]("http://www.unlocktheinbox.com/resources/emailauthentication/")

---

