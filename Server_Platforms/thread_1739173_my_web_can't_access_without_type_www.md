---
title: "my web can't access without type www"
date: 2011-04-25
forum: Server Platforms
---

### Post by brondong on 2011-04-25
Hello, 

 I'm working to set up my first server to experiment hosting my own web pages. I have installed Ubuntu 10.04 server. my web only can access by typing [www.xxxxxx.com](www.xxxxxx.com), if we not typing www (xxxxxx.com), it will not responding.

My question is: how to access my web without type www, ?

---

### Post by volkswagner on 2011-04-25
Provided you have a dns entry at your registrar for "domain.com" vs. www.domain.com" you may just need an alias to your apache2 host file.

Under server name add the following:
```
ServerName www.mydomain.com
ServerAlias mydomain.com
```

The above will be added then restart apache2.  Where you put the above depends if you create an individual host file at /etc/apache2/sites-available/hostname or if you add it all to httpd.conf.

---

### Post by brondong on 2011-04-25
i have try it at httpd.conf, and i get this respond when i restart apache:

* Restarting web server htcacheclean
 * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
 ... waiting Syntax error on line 2 of /etc/apache2/httpd.conf:
ServerAlias only used in <VirtualHost>

---

### Post by Ryan Dwyer on 2011-04-25
The OP said that xxxxxx.com is not responding which indicates a DNS problem. Therefore volkswagner's post is irrelevant. Revert your changes to the httpd.conf file.

You need to add a DNS A record for xxxxxx.com, not just [www.xxxxxx.com](www.xxxxxx.com).

---

### Post by volkswagner on 2011-04-25
> **Ryan Dwyer said:**
> The OP said that xxxxxx.com is not responding which indicates a DNS problem. Therefore volkswagner's post is irrelevant. Revert your changes to the httpd.conf file.

You need to add a DNS A record for xxxxxx.com, not just [www.xxxxxx.com](www.xxxxxx.com).

Hmn, since my first sentance mentioned the DNS record, I sure don't feel my **post** is irrelevant.  Kudos to you for spelling out the A record though.


> **brondong said:**
> ...if we not typing www (xxxxxx.com), it will not responding.


I guess I loosely translated that.


Have a Coke and a smile  :)

---

### Post by SeijiSensei on 2011-04-25
Actually you're both correct.

First you need an A record in the DNS that points domain.name to an IP address.  How you do this depends on your DNS provider. If you're running your own DNS with bind9, add a record near the top of the zone file for the domain like this:

```

@   IN SOA domain.name. root.domain.name. (
            [stuff]
            )
         
    **IN  A   10.10.10.10**

    IN  NS  ns1.domain.name.
    etc.   

**www   IN A   10.10.10.10**

    more stuff


```

However you'll also need a ServerAlias directive in Apache.  As the error message says, it needs to be inside a <VirtualHost> stanza like this:

```

<VirtualHost *:80>
    ServerName   www.domain.name
    **ServerAlias  domain.name**
    
    stuff

</VirtualHost>

```

Taken together, the server will now respond identically to both "www.domain.name" and "domain.name" when used in a URL.

---

### Post by Ryan Dwyer on 2011-04-25
I believe you are both giving the OP information that is unneeded and this is clearly not helping. He's tried to follow this advice and now he's broken his Apache config.

The OP's opening post basically said that [www.xxxxxx.com](www.xxxxxx.com) works and xxxxxx.com times out. Nothing in his post indicates that his virtualhost is incorrect. If the virtualhost was incorrect he would be able to connect and would be seeing the default virtualhost instead. While it's possible both his DNS and virtualhost are configured incorrectly, there is no indication this is the case and you shouldn't assume this until his DNS problem is sorted.

And now, the OP hasn't said he's running his own DNS server but we've gone ahead and given him instructions for editing his own zone files. That's just going to confuse him.

I know I have no authority here, but please think carefully about problems and offer advice one step at a time instead of jumping to conclusions. Try not to give them information they might not need.

---

### Post by SeijiSensei on 2011-04-26
> Nothing in his post indicates that his virtualhost is incorrect.

> .. waiting Syntax error on line 2 of /etc/apache2/httpd.conf:
ServerAlias only used in <VirtualHost>

He specifically reports this error, where the ServerAlias directive is not inside his <VirtualHost> container.

We also have no information about how hostnames are being resolved.  Maybe he's using hosts files; maybe he has a DNS server; maybe he has his DNS hosted externally.  He certainly needs an A record for "domain.name".  I specifically said, "How you do this depends on your DNS provider."  Since he could have any of dozens of DNS providers, I can't give him specific advice on how to do that if he has hosted DNS.  I then proceeded to explain how to set this up if he is running his own DNS.  Do you want me to give him an answer if he's using /etc/hosts?  Then here it is:

Add this line to /etc/hosts on the server and any client machines connecting to it, replacing 10.10.10.10 with the IP address of the Apache server:
```
10.10.10.10     www.domain.name  domain.name
```
You still need the ServerAlias directive.

---

### Post by Ryan Dwyer on 2011-04-26
The Apache error was caused because he tried to follow volkswagner's irrelevant advice. That's my point. Nothing in his *original* post suggested a misconfigured virtualhost, but by jumping to conclusions volkswagner has steered him in the wrong direction and complicated the issue. The OP should revert his changes to httpd.conf because the instructions to edit them were made under false assumptions.

Regarding your response about DNS, don't provide any information unless you're sure it's applicable to the OP's setup. This is his first post on the forums and it might even be the first time he's used Linux. He asked a simple question and received a massively technical answer, most of which is probably not applicable to his situation. I wouldn't be surprised if he never comes back again.

It's best to explain what is wrong in simple terms like I did. I did it in once sentence. If the OP doesn't understand your answer, he can ask for more help then you can request more information specific to his setup (eg. "Did you register a domain through a registrar? Did you add your IP address somewhere in their web interface?"). As I said earlier, take it one step at a time otherwise you'll confuse them when you bombard them with information.

Part of my day job involves investigating problems similar to this, explaining why it doesn't work and providing advice to fix it. If I give incorrect information based on assumptions (like volkswagner did) then it makes us look bad and our clients lose faith in us. If I provide too much information (like you did) then the client will be overwhelmed, won't understand, will get frustrated and will dislike doing business with us. The same thing applies here.

Please don't think I'm being nasty. I'm just trying to teach you how to help people more effectively :)

---

### Post by rubylaser on 2011-04-26
> Please don't think I'm being nasty. I'm just trying to teach you how to help people more effectively 

How does cluttering up the post to explain that you're obviously a better instructor that two people that have many times the number of posts that you have help this situation either?  This is a forum, and they're trying to help.  Both of them specifically mentioned DNS, and the demonstrated how to setup a ServerAlias.  I fail to see how any of what they said was irrelevant or difficult to understand.

This is the Server section, so the crowd is typically more technical than the General section. I would contend that volkswagener's, response would be the correct answer for most people in this situation.  People that understand DNS enough to setup a functioning record (the OP has www working, so this is the case), should also know to add an A record for the domain name to have it resolve properly. This being true, the Apache configuration, and his answer would resolve the problem.

If you didn't believe that was the case, you should have asked more questions of the OP, to determine how they setup DNS, rather than ruling it out as "irrelevant", and jumping to the conclusion the the Apache config was solely at fault.

---

### Post by thinmintaddict on 2011-04-27
**Okay, Let's just start over.**

It seems we all need a bit more information before we can answer effectively.

OP:
1. How are you resolving DNS? are you using your own DNS? or ZoneEdit? or are you letting a registrar handle it (Such as GoDaddy.com)
2. When you access the website without [www.,](www.,) what do you see? does it simply time out?
3. If you wouldn't mind, please post your httpd.conf file, and if you're using it, vhosts.conf file.

Thanks! and I hope we can get it sorted out,

TMA

---

### Post by brondong on 2011-04-27
this is my httpd.conf setting:

**ServerName localhost**

and i can't find vhosts.conf in /etc/

and then this my /etc/hosts setting

[B]127.0.0.1	localhost
192.168.0.1	ns1 example.com smtp.example.com proxy.example.com
10.10.10.10	ns1 example.com smtp.example.com proxy.example.com[/B]

and When you access the website without www. i get this respond:
**Ping request could not find host example.com. Please check the name and try again.**

please help me, Whats wrong with my settings?
thankss

---

### Post by thinmintaddict on 2011-04-27
Ok, you're /etc/hosts file applies only to you're local LAN. do you only need this site visible locally? if so you can fix this by just adding "www.example.com" to both of the entries in your /etc/hosts file.

If you need everything to be visible to the internet, then we need to consider a DNS Solution. a DNS entry does something similar to your /etc/hosts file, but for the entire internet. For this we need to talk about your domain registrar, or dns provider, whichever you're using.

And is that the entire contents for you httpd.conf file? If so we may have corrupted it at some point during the proceedings.

---

### Post by volkswagner on 2011-04-27
> **brondong said:**
> 

and i can't find vhosts.conf in /etc/



As mentioned your vhost file location is /etc/apache2/sites-available.

```
ls /etc/apache2/sites-available
```

Check here for enabled sites:

```
ls /etc/apache2/sites-enabled
```

Do you have a dns record for www?  What do you get when running the following?

```
host www.yourdomain.com
```

vs.

```
host yourdomain.com
```

You should give the apache2 server guide a good read([sticky at the top of this thread]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html")).

---

