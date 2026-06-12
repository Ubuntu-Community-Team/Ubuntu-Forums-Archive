---
title: "Mailserver Fun"
date: 2012-04-25
forum: Server Platforms
---

### Post by jonedney on 2012-04-25
Hello everyone!

So I've been working on my VPS and have Ubuntu 11.10 installed on it and it's running Apache/MySQL/phpMyAdmin without problem.

Tonight, I decided to tackle getting the mail server set up, so I can start using the service there instead of on the shared hosting I have.  I've been working off the Server Guide at [http://help.ubuntu.com](http://help.ubuntu.com)

I installed Postfix, went through the settings, generated my CSR for my self-signed certificate for the SMTP authentication, and completed with setting up SALS and installing Mail-Stack Delivery.  When I run the 'telnet mail.jonedneycreative.com 25' (mail.jonedneycreative.com is what I set up as the hostname), it gives an error.

```
root@jonedneycreative:~# telnet mail.jonedneycreative.com 25
telnet: could not resolve mail.jonedneycreative.com/25: Name or service not known
```

Then I ran a command to see what was running on port 25, and it is sendmail, so I'm unsure what is not working properly.

```
root@jonedneycreative:~# netstat -an | grep ":25"
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN
```

Thank you,
Jon Edney

---

### Post by SeijiSensei on 2012-04-25
You don't have DNS configured correctly.  

> could not resolve mail.jonedneycreative.com

Can you ping the machine using that name?

I can see the whois record for jonedneycreative.com, but the two authoritative nameservers ns1 and ns2 don't appear to exist.

---

### Post by jonedney on 2012-04-25
That would make sense and I'm not sure why I didn't realize that.  I didn't set up DNS on my VPS because it was a bit too complicated for me at this step.  

Would there be an alternate way to continue with the mail server using just my VPS IP?  I tried to telnet 216.119.142.16 25 and telnet mail.216.119.142.16 25 and neither worked.

Thoughts?

Jon Edney

---

### Post by darkod on 2012-04-25
If I am not mistaken actually you don't need to set up the DNS on the VPS.

You have the domain bought somewhere, right? All these companies usually have a control panel where you can create the A and MX records. So, all you need to do is login into your control panel and create the MX record for your domain pointing to your VPS fixed public IP.

That way the DNS servers at your registrar will route all mail to the VPS which will accept it on port 25.

I am not sure if you will need to create the mail.domain.com record too, with the VPS IP. Try it. Usually the MX record should be enough for the mail purposes.

---

### Post by jonedney on 2012-04-25
Hello,

Yes, I have an A record pointing to my VPS right now for web traffic.  I'm not too familiar with MX records, as it will not allow me to direct an MX record to an IP.  I tried the following.

* MX VPS IP
mail MX VPS IP

Both indicated the IP couldn't be accepted, that it needed to be a FQDN.  So, I figured I would specify a CNAME, to associate mail.jonedneycreative.com to the IP, then reference the CNAME in the MX record, but that also wouldn't take the IP address.

Thoughts?
Jon

---

### Post by SeijiSensei on 2012-04-26
MX and NS records point to hostnames, so you use something like this:

```

@     IN    SOA  example.com.  root.example.com. (
                 stuff
                 )


      IN    NS   ns1.example.com.
      IN    NS   ns2.example.com.

      IN    MX   0 mail.example.com.
      IN    MX   5 mail2.example.com.

ns1   IN    A    10.10.10.10
ns2   IN    A    192.168.0.10

mail  IN    A    10.10.10.11
mail2 IN    A    192.168.0.11

```

I'm pretty sure the hosts referenced in MX and NS records must have associated A records. CNAMEs aren't permitted in this situation.

---

### Post by jonedney on 2012-04-26
Thank you for your thoughts, SeijiSensei.

I created 2 DNS records, A record for mail pointing to my IP, then an MX, pointing to mail.jonedneycreative.com.

I don't have DNS service on my VPS yet, so I didn't set that up.  I'll give DNS some time for propagation, and check it out and let you all know the results.

Thank you,
Jon Edney

---

### Post by jonedney on 2012-04-29
Hello Everyone!

I've been able to get the mail server running properly, as when I telnet test local host and the hostname mail.jonedneycreative.com, it works.  But, it seems my VPS IP is refusing connections:

From MX Toolbox:
```
4/28/2012 11:10:00 PM  Connection attempt #1 - No connection could be made because the target  machine actively refused it VPS IP:25 [1.12 sec]
```Any ideas?

---

### Post by d4m1r on 2012-04-29
1) I'd recommend removing your IPs from all your posts, you're leaving yourself open to attack, especially because of the additional information you posted about what you are running.

2) Are you running this machine from your home or are you getting it hosted somewhere online? If you are paying for the hosting, I'd contact support to ask why connections are being refused.

---

### Post by SeijiSensei on 2012-04-29
If you have a firewall, e.g., one using iptables, you may not have port 25 open.  Make sure you have a rule that looks like this:

```
iptables -A INPUT -m state --state NEW -m tcp -p tcp -d your.public.ip.addr --dport 25 -j ACCEPT
```

Also make sure that your SMTP server is listening on the public address.  Most distributions nowadays ship servers that listen only on the localhost (127.0.0.1) interface by default.  For sendmail, find the line in sendmail.cf that begins "O DaemonPortOptions" and delete any "Addr=127.0.0.1" entry you find there. For postfix, read [this](http://www.postfix.org/postconf.5.html#inet_interfaces).

---

### Post by jonedney on 2012-04-29
Hello!

I took a look and it seems everything should be set up to listen on all IPs, but it's only listening to localhost.  I found another topic (though 2 years old) of someone who was having the same proiblem, but they never responded to complete the "troubleshoot".  I'm going to see where I can go from there.  If interested, the link is [http://ubuntuforums.org/showthread.php?p=11886942#post11886942](http://ubuntuforums.org/showthread.php?p=11886942#post11886942).

Thank you,
Jon Edney

---

