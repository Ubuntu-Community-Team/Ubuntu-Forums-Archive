---
title: "sendmail: gethostbyaddr(104.236.90.239) failed: 1"
date: 2017-03-04
forum: Server Platforms
---

### Post by tornado711 on 2017-03-04
I'm setting up an SMTP mail server for a website (ironfi.st) that has given me this task. After setting up sendmail and setting up an SMTP plugin on the admin page. Upon loading up the WP-SMTP-MAIL plugin, and having it send a test mail, I noticed it never sent out the mail. I decided to go and check the mail logs in /var/log and check the mail.log file. and I noticed this message repeating everytime: 

Mar  4 15:21:28 ironfist-droplet sendmail[7766]: gethostbyaddr(104.236.90.239) failed: 1

It seems to be having trouble connecting to the IP address associated with the website I am working. Below I've attached a copy of my hosts file and the System Identity so that it may be of additional help (it was unfortunately not much help to me as I'm very new to all of this and not well versed in all the specific terminology as I should be):

Hosts file:

127.0.0.1 localhost.localdomain localhost
104.236.90.239 ironfist-droplet.ironfi.st ironfist-droplet

System Identity:

============ SYSTEM IDENTITY (after readcf) ============
      (short domain name) $w = ironfist-droplet
  (canonical domain name) $j = ironfist-droplet.ironfi.st
         (subdomain name) $m = ironfi.st
              (node name) $k = ironfist-droplet
========================================================

If anyone knows of a solution to my issue please do not hesitate to let me know!

---

### Post by lisati on 2017-03-04
I'm assuming that the IP address is the one that will be used by the server. Do you have a rDNS associated with that IP address? If not, it could affect deliverability of outgoing email.

---

### Post by tornado711 on 2017-03-06
I'm very new to all this, it's been a learning experience. I know what DNS is but what do you mean an rDNS?

---

### Post by volkswagner on 2017-03-06
That would be 'Reverse DNS'. You may have a setting to change/set it in your VPS control panel. Some providers require you to submit a support ticket to request setting the rDNS.

---

### Post by tornado711 on 2017-03-07
We're not using rDNS  I believe. We are simply directly using the hosts file, as I believe I have seen others do.

---

### Post by lisati on 2017-03-07
I'm not sure where gethostbyaddr() gets its information from or how to configure it on your own network. It might not matter so much if the recipients of your emails are on the same network, but not having a publicly viewable rDNS can make a big difference for some email providers, as it helps confirm that the email is arriving via a legitimate email server.

---

### Post by tornado711 on 2017-03-08
> **lisati said:**
> I'm not sure where gethostbyaddr() gets its information from or how to configure it on your own network. It might not matter so much if the recipients of your emails are on the same network, but not having a publicly viewable rDNS can make a big difference for some email providers, as it helps confirm that the email is arriving via a legitimate email server.


I'm able to send emails directly through the server using "echo "Subject: test" | /usr/lib/sendmail -v [EMAIL="me@domain.com"]me@domain.com[/EMAIL] **Example"** and the email will send just fine. However, mail will refuse to send through our website's contact page, so I believe the server is able to get mail out just fine, so it might not be an rDNS issue (but it may be, after all I'm new to this). Part of me has suspicion in how the hosts file is set up.

---

### Post by volkswagner on 2017-03-08
Whether you believe revers DNS is the cause or not, it still is part of proper email server setup and should not 
be ignored.

---

### Post by lisati on 2017-03-08
Like I said, I do not know for sure if not having a valid rDNS is the cause of the error message, but it does matter when sending mail out. Have a look [here]("https://en.wikipedia.org/wiki/Anti-spam_techniques#PTR.2Freverse_DNS_checks") and [here]("http://multirbl.valli.org/lookup/104.236.90.239.html"). When I checked the IP address was flagged on 5 blacklists.

I'm not familiar with configuring exim (my limited experience is with Postfix), but suspect that if you are able to fix the rDNS, it's possible that the error message will go away.

---

### Post by tornado711 on 2017-03-10
> **lisati said:**
> Like I said, I do not know for sure if not having a valid rDNS is the cause of the error message, but it does matter when sending mail out. Have a look [here]("https://en.wikipedia.org/wiki/Anti-spam_techniques#PTR.2Freverse_DNS_checks") and [here]("http://multirbl.valli.org/lookup/104.236.90.239.html"). When I checked the IP address was flagged on 5 blacklists.

I'm not familiar with configuring exim (my limited experience is with Postfix), but suspect that if you are able to fix the rDNS, it's possible that the error message will go away.



I'll check into the rDNS. Blacklisting could also be the issue. How could I get my IP  removed from those blacklists?

---

### Post by lisati on 2017-03-10
Most of the listings I saw can probably be safely ignored. Have a look here: [http://multirbl.valli.org/lookup/104.236.90.239.html](http://multirbl.valli.org/lookup/104.236.90.239.html) - it will provide the links necessary to learn more.

---

### Post by tornado711 on 2017-03-11
> **volkswagner said:**
> Whether you believe revers DNS is the cause or not, it still is part of proper email server setup and should not 
be ignored.

I found rDNS and it has it's name set to "ironfist-droplet" would that be acceptable for rDNS? Could it still be a contributing factor to the gethostbyaddr error?

---

### Post by SeijiSensei on 2017-03-12
Only your provider can set up reverse DNS for the IP addresses it controls.  They have not done so with yours:
```

$ host 104.236.90.239
Host 239.90.236.104.in-addr.arpa. not found: 3(NXDOMAIN)

```

Names for the 104.236.90.0/24 subnet are managed by digitalocean:
```

$ host -t ns 90.236.104.in-addr.arpa
90.236.104.in-addr.arpa name server ns2.digitalocean.com.
90.236.104.in-addr.arpa name server ns3.digitalocean.com.
90.236.104.in-addr.arpa name server ns1.digitalocean.com.

```

Also the names must be "fully-qualified" with a domain attached.  So "ironfist-droplet" is not going to work.

---

### Post by tornado711 on 2017-03-18
> **SeijiSensei said:**
> Only your provider can set up reverse DNS for the IP addresses it controls.  They have not done so with yours:
```

$ host 104.236.90.239
Host 239.90.236.104.in-addr.arpa. not found: 3(NXDOMAIN)

```

Names for the 104.236.90.0/24 subnet are managed by digitalocean:
```

$ host -t ns 90.236.104.in-addr.arpa
90.236.104.in-addr.arpa name server ns2.digitalocean.com.
90.236.104.in-addr.arpa name server ns3.digitalocean.com.
90.236.104.in-addr.arpa name server ns1.digitalocean.com.

```

Also the names must be "fully-qualified" with a domain attached.  So "ironfist-droplet" is not going to work.

Thank you for all this information! What could I change ironfist-droplet to, to make it qualified? Also where could I go to change it? The hosts file? Why would ironfist-droplet not work? Because in the system information I see ironfist-droplet used in ironfist-droplet.ironfi.st? Would that not be a fully-qualified domain name? hostname returns ironfist-droplet and hostname -f returns ironfist-droplet.ironfi.st is all of that not qualified? Sorry for so many questions, again this is very much a learning experience for me!

---

### Post by SeijiSensei on 2017-03-18
Yes, ironfist-droplet.ironfi.st would be a fully-qualified domain name, but it doesn't resolve to anything.

```

$ host ironfist-droplet.ironfi.st
Host ironfist-droplet.ironfi.st not found: 3(NXDOMAIN)

```

You need to discuss these issues with your provider as only they can really help.  This isn't an Ubuntu issue and not one you can resolve on your own.

---

### Post by Habitual on 2017-03-19
Looks like there's part of it in place,
```
host ironfi.st
ironfi.st has address 104.236.90.239
``` but rDNS on .239 isn't set.
```
ironfi.st mail is handled by 0 mx-caprica.easydns.com.
jj@toaster ~ $ host 104.236.90.239
Host 239.90.236.104.in-addr.arpa. not found: 3(NXDOMAIN)
```

Try
```
[COLOR=#000000](short domain name) $w = [/COLOR]ironfi.st
``` and for fluid delivery, rDNS is 
the usual check for legitimate mail servers|hosts.

Your DNS appears to be a bit chaotic, from looking at it at [https://intodns.com/ironfi.st](https://intodns.com/ironfi.st)
But...
One thing at a time, ***especially*** when manipulating dns.

---

### Post by tornado711 on 2017-03-19
> **Habitual said:**
> Looks like there's part of it in place,
```
host ironfi.st
ironfi.st has address 104.236.90.239
``` but rDNS on .239 isn't set.
```
ironfi.st mail is handled by 0 mx-caprica.easydns.com.
jj@toaster ~ $ host 104.236.90.239
Host 239.90.236.104.in-addr.arpa. not found: 3(NXDOMAIN)
```

Try
```
[COLOR=#000000](short domain name) $w = [/COLOR]ironfi.st
``` and for fluid delivery, rDNS is 
the usual check for legitimate mail servers|hosts.

Your DNS appears to be a bit chaotic, from looking at it at [https://intodns.com/ironfi.st](https://intodns.com/ironfi.st)
But...
One thing at a time, ***especially*** when manipulating dns.

Sorry again for the basic question. How exactly could I change the short domain name? From what I've seen it's affected by how you edit the host file, but i'm not sure how to edit the host file specifically to change the short name, I'm not sure what order to put all the stuff in. Could you please explain it to me? Again sorry for the basic questions this is all extremely new territory for me :(

---

