---
title: "How to automatically email me with IP address?"
date: 2008-07-06
forum: Server Platforms
---

### Post by iissmart on 2008-07-06
Hi, I'm running an Ubuntu 8.04.1 server on a DHCP network (not behind a router), and although it doesn't happen often I'm afraid the IP address of the server will change and I won't be able to access it anymore. Also, sometimes the modem crashes and comes back up but leaves the server without a connection. Right now I set up a script to basically do ifdown/ifup daily to ensure that if the modem crashes and it loses an IP it will get it back within a day. But, I'm afraid that it will get a different IP when it does this. Is there a way to have the server email me with it's IP address, say, once a week? Also, with my ifdown/ifup script, is there a way to not have any output from the ifdown/ifup commands? Right now I get a "mail" message daily on my server with the output of ifdown/ifup and it's kind of cluttered and annoying to delete. I'm not familiar at all with sending emails via a terminal. Thanks in advance!
 
By the way, my idea was to perhaps send me an email with the contents of "wget http://whatismyip.org", since it would only contain the current IP address. Or perhaps getting the IP address via some internal method would work better.

---

### Post by windependence on 2008-07-06
You could use a dynamic dns provider like no-ip. That way you can always access the server by name no matter what the IP is. You run a client on the server that updates the no-ip service when the IP changes.

-Tim

---

### Post by iissmart on 2008-07-07
Sorry, I forgot to mention that I already own a domain name for the server, therefore I don't use a dynamic dns provider. So, I just need a script which emails me the IP address of itself, and I'll just put it in /etc/cron.weekly

---

### Post by koenn on 2008-07-07
so then, if your server has a (domain) name, why do you need to access it by address ? domain names were invented to avoid having to use addresses ...

---

### Post by Titan8990 on 2008-07-07
Also if your ISP does not give you a dynamic address then that would make it static, meaning it would never change.

---

### Post by simonapnic on 2008-07-07
Well, I guess this would do:
```
#!/bin/bash
echo 'Mailing your IP address...'
ip=`/sbin/ifconfig | grep inet | grep -v inet6 | grep -v 127.0.0.1 | awk '{ print $2 }' | sed -e s'/addr://'`
echo $ip | mail -s 'IP Address Info' <email>
```

Obviously, you'd have to replace <email> with your email address.
You could crontab the script each hour or so.

---

### Post by sp00ki on 2008-07-07
Your best bet would be to write a small shellscript piping the contents of ifconfig to an email message.
Since you're not behind a router, and your system is (i'm assuming) using the DHCP address itself (not NAT), this will work easily.
To make it smarter, add an if/then emailing you ONLY if the address changes from whatever it was previously.  
Then, add the script to cron to run hourly or daily or twice a day or whatever makes you comfortable.
Example:

```
#!/bin/sh

OLDADDR=`cat ~/dhcp_file`
CURADDR=`/sbin/ifconfig | grep Bcast`

if [ "$CURADDR" != "$OLDADDR" ]
        then
                echo "$CURADDR" > ~/dhcp_file
                mail -s 'Here is my new ip address' [email]your@email.addr[/email]ess < ~/dhcp_file
        else
                exit
fi

```

This will send an email to you every time your address changes, provided you've added it to someone's cron (specifically a user able to run ifconfig).
I just tested it on my Debian system, and it works with no problem.
Note:  you'll need to install sendmail before being able to do it:
apt-get install sendmail-bin

good luck!

ps, you probably won't ever get an email from this script as most isps don't often change user ip addresses these days, but i agree with you-- caution beats cure every time.

---

### Post by sp00ki on 2008-07-07
> **simonapnic said:**
> Well, I guess this would do:
```
#!/bin/bash
echo 'Mailing your IP address...'
ip=`/sbin/ifconfig | grep inet | grep -v inet6 | grep -v 127.0.0.1 | awk '{ print $2 }' | sed -e s'/addr://'`
echo $ip | mail -s 'IP Address Info' <email>
```

Obviously, you'd have to replace <email> with your email address.
You could crontab the script each hour or so.

lol... looks like i was beaten to the punch, though i like that mine only sends an email if the address changes as opposed to sending email every time.  gives more of an "alert" feel to it (and a duplicate email every hour can be a bit excessive).

---

### Post by windependence on 2008-07-07
> **iissmart said:**
> Sorry, I forgot to mention that I already own a domain name for the server, therefore I don't use a dynamic dns provider. So, I just need a script which emails me the IP address of itself, and I'll just put it in /etc/cron.weekly

Even if you own the domain, if your IP address is not static, you could make your life much easier with a redirect. You would point your domain at the redirect, and they would take care of always maintaining a connection to your server. No funky scripts necessary.

-Tim

---

### Post by gishaust on 2008-07-07
This thread is great, but I have a question how do you have the internet on without using a router?  Does this mean that the computer is attach straight to the phone line?  I not trying to be funny can someone tell what this means

---

### Post by ghostdog74 on 2008-07-07
> **simonapnic said:**
> Well, I guess this would do:
```
#!/bin/bash
echo 'Mailing your IP address...'
ip=`/sbin/ifconfig | grep inet | grep -v inet6 | grep -v 127.0.0.1 | awk '{ print $2 }' | sed -e s'/addr://'`
echo $ip | mail -s 'IP Address Info' <email>
```


no need that much pipes and greps/sed
```

ifconfig |awk 'BEGIN{FS="[: ]+"}!/inet6|127.0.0.1/ && /inet/{print $4}'

```

---

### Post by windependence on 2008-07-07
> **gishaust said:**
> This thread is great, but I have a question how do you have the internet on without using a router?  Does this mean that the computer is attach straight to the phone line?  I not trying to be funny can someone tell what this means

Well you don't <need> a router, but you do need a cable or DSL modem or if you have a dedicated line you have a CSU/DSU. You <could> connect directly to the internet that way, but most people don't either because they have a modem with a router built in, or they want to do NAT for several computers on thier LAN.

-Tim

---

### Post by gishaust on 2008-07-08
Ooh I miss understood!! I only have ever had a router with a built in modem thanks for clarification.

---

### Post by lisati on 2008-07-08
> **Titan8990 said:**
> Also if your ISP does not give you a dynamic address then that would make it static, meaning it would never change.
+1: Some ISPs are able to provide static address - the ISP I use charges for it though.

---

### Post by iissmart on 2008-07-08
> **koenn said:**
> so then, if your server has a (domain) name, why do you need to access it by address ? domain names were invented to avoid having to use addresses ...
To reply to this message, my server does have a domain name, but since the server's ip is dynamic the ip that the server gets could change, but the change doesn't update where my domain name points to.
 
To those who posted some code: I'll look through those tomorrow and see what I can do. Thanks for the replies!

---

### Post by windependence on 2008-07-08
> **iissmart said:**
> To reply to this message, my server does have a domain name, but since the server's ip is dynamic the ip that the server gets could change, but the change doesn't update where my domain name points to.
 
To those who posted some code: I'll look through those tomorrow and see what I can do. Thanks for the replies!

This is why we are trying to tell you to use a redirection service. This can be made really easy if you use a service like no-ip.com or similar services. Maybe you aren't understanding what we are trying to tell you? The redirection service gets your IP from a job that runs on your server. This way, they always know your IP and you point your domain at their nameservers which redirect your connection to whatever IP you are currently using. Understand?

-Tim

---

### Post by sp00ki on 2008-07-08
^
He's right.
The shell script suggestions i (and others) provided would work best in lieu of dns, not conjunct with it.  If you ran into a situation where dns would need to be updated due to a lease ending and your address changing, it could potentially (and likely) be days before the updates made to your nameserver propegates throughout the internet.  if you have a genuine fear that your address will change, something like no-ip.com is exactly what you want.
if you don't anticipate your address changing, though, the scripts could be a nice security blanket.

---

### Post by iissmart on 2008-07-08
Oh, sorry I didn't quite get what you were saying before. So you're suggesting to have this redirection address run side-by-side with my domain name, so if the IP does change and I can't access it through my domain name I can access it through the other name? OK, I'll think I'll try that instead of the whole email thing. Thanks.

---

### Post by windependence on 2008-07-08
<sigh> NO. Look at the diagram below:

Your Domain =====> No-ip <=====> Your server

Your server, runs a small application that tells no-ip what your IP address is. No-ip service always knows what your IP is. Your domain name is pointed at no-ip, NOT your server, and they in turn redirect all your traffic from your domain name to your server IP address no matter what it is, because their servers always know what your IP is, seconds after it changes. Got it? You go to [www.your_server_name.com](www.your_server_name.com) and your request is routed to no-ip, and then to your server. The end user never sees any of this.

-Tim

---

### Post by iissmart on 2008-07-08
OK, I get what you are saying now. Instead, I just installed ddclient on the server and configured it for zoneedit (which I'm using for the domain's name servers right now), which I think will update the ip for the domain directly, instead of using a separate service like no-ip. But I have no way of testing it...
 
And for my next question, is there a way to silence the output of ifdown/ifup so I don't get a mail message daily stating that it performed ifdown and ifup commands?

---

