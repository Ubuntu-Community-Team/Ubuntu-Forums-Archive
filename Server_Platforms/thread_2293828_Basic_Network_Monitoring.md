---
title: "Basic Network Monitoring"
date: 2015-09-07
forum: Server Platforms
---

### Post by Marc-NJ on 2015-09-07
So right now I have two Ubuntu servers (each located in a different physical location).  One is running 12.04 LTS and one is running 14.04 LTS.  Earlier today, the location where the one running 12.04 LTS resides lost power, and eventually the UPS died and so did the server obviously.  Unfortunately, right this second I don't have any cloud/hosted monitoring (I know there are a million different services for this) for either of them (although I do plan to eventually sign up for some cloud/hosted monitoring service in the future).  I know a bunch of these cloud/hosted solutions offer free versions, but it's been my experience that they have limitations, such as how often they check to see if a service/website/etc. is running, etc.

Instead of using a free version of a cloud/hosted monitoring solution, is there some pretty quick simple software I can install on each of these two Ubuntu servers that will allow me to check to see if the other one is up and running on whatever time frame I specify?  And then if it determines the other one is down, it can notify me via email (hopefully via a 3rd party email service)?

Thanks!

---

### Post by SeijiSensei on 2015-09-08
If you can write bash scripts, run a script on each machine from cron that pings the other machine and sends you an email if it cannot connect.  Something like this:
```

#!/bin/bash
REMOTE=host.example.com
NOTIFY=you@somewhere.net

TEST=$(ping -c 5 $REMOTE | grep '100% packet loss')
if [ "$TEST" != "" ] 
then
     mail -s "$REMOTE down!" $NOTIFY
fi

exit 0

```
Set up a cron job to run this periodically, say every five minutes.

I also run simple scripts that use the results of "ps ax" to check to see which services are running.  If any of them are not, the script restarts the service and sends me an email to that effect.

I no longer maintain any physical servers but rent VMs from Linode instead.  The only time they have been down is when the host systems are taken down for maintenance.  That happens less than once a year.  I also pay a couple of dollars each month for nightly snapshot backups of the VMs just in case something goes wrong.

---

### Post by Marc-NJ on 2015-09-08
> **SeijiSensei said:**
> If you can write bash scripts, run a script on each machine from cron that pings the other machine and sends you an email if it cannot connect.  Something like this:
```

#!/bin/bash
REMOTE=host.example.com
NOTIFY=you@somewhere.net

TEST=$(ping -c 5 $REMOTE | grep '100% packet loss')
if [ "$TEST" != "" ] 
then
     mail -s "$REMOTE down!" $NOTIFY
fi

exit 0

```
Set up a cron job to run this periodically, say every five minutes.

I also run simple scripts that use the results of "ps ax" to check to see which services are running.  If any of them are not, the script restarts the service and sends me an email to that effect.

I no longer maintain any physical servers but rent VMs from Linode instead.  The only time they have been down is when the host systems are taken down for maintenance.  That happens less than once a year.  I also pay a couple of dollars each month for nightly snapshot backups of the VMs just in case something goes wrong.

Thanks so much for the info!

I was actually hoping for something that might be a little bit more complete though, such as a small software package with a web GUI that could possibly do more than just ping and email if the ping doesn't go through (like perhaps try to load a web site, and if that doesn't work, send out an email, etc.).  Any thoughts/suggestions/recommendations?

Thanks!

---

### Post by Bucky Ball on 2015-09-09
> **Marc_Bressman said:**
> ping and email if the ping doesn't go through (like perhaps try to load a web site, and if that doesn't work, send out an email, etc.).

In many ways trying to ping and trying to load a web page are one in the same thing. :)

---

### Post by Marc-NJ on 2015-09-09
> **Bucky Ball said:**
> In many ways trying to ping and trying to load a web page are one in the same thing. :)

I'm not sure I understand - can you provide some add'l information?  For instance, can't I disable it so that inbound ICMP packets are simply dropped and don't respond, which would disable ping, and yet still have active websites loading?  Additionally, since both servers are behind a hardware firewall device, the pings would be handled by that device which wouldn't necessarily tell me if the server itself was up and running, right?

Thanks!

---

### Post by Habitual on 2015-09-09
[Testing Network Services with netcat]("http://www.rackspace.com/knowledge_center/article/testing-network-services-with-netcat") ?

---

### Post by SeijiSensei on 2015-09-09
You can install **nmap** and have it scan the remote to determine what ports are open and act accordingly. Wrap it in a script like the above.

---

### Post by MAFoElffen on 2015-09-09
You are right in that the tools you presented were basic tools that tell a lot of things that are going on and not... but are text based, commandline utils with lots of options to remember.

I believe what the OP is looking for is more along the lines of "WireShark." (He said he was looking for a GUI presented network monitor.)

Although WireShark is not really *basic. *Most people using it only scratch the surface of that tool.

Either way (commandline or GUI), you have to know something about how to use your tools and how to interpret the results.

---

### Post by Marc-NJ on 2015-09-11
Hmm...it's possible I may not have been as clear as I should have been.  Basically, I'm looking for a piece of (free/open-source) software that I can install on two servers (located in different physical locations) that will monitor websites on the other server.  So that if server A goes down, server B will not be able to access the websites served up by server A and will alert me, and vice versa.  Does that make sense?

I found some possible options, but haven't had a chance to try them and was wondering if anyone had any more information about them or any other alternatives:

- Cabot ([http://cabotapp.com/](http://cabotapp.com/)) -> this seems like it might be exactly what I'm looking for? *(but not sure if I can install on my Ubuntu server?)*

- PHP Server Monitor ([http://docs.phpservermonitor.org/en/latest/intro.html](http://docs.phpservermonitor.org/en/latest/intro.html))

- Possibly some other alternatives: [http://www.servermom.org/free-self-hosted-server-monitoring-tools/1824/](http://www.servermom.org/free-self-hosted-server-monitoring-tools/1824/)

Thanks for any help or information!

---

### Post by SeijiSensei on 2015-09-11
On server B, run
```
nmap -p 80 server_A
```
then grep for the line
```
80/tcp open  http
```
Again you could do this with a script like the one I gave above.

If the machine is behind a firewall, you might see "filtered" instead of "open."  What you don't want to see is "closed."

I always prefer simple solutions I can code myself over some third-party solution that usually has more features than I want.

---

### Post by MAFoElffen on 2015-09-12
> **SeijiSensei said:**
> Again you could do this with a script like the one I gave above.

If the machine is behind a firewall, you might see "filtered" instead of "open."  What you don't want to see is "closed."

I always prefer simple solutions I can code myself over some third-party solution that usually has more features than I want.
@Marc-- 

Now that you explained what you are trying to do and check, I agree with SeijiSensei. I do the same type of thing, with other checks, with scripts, and if certain failures occur, alerts get sent to my phone.

You said:
> 
....that will monitor websites on the other server. So that if server A goes down, server B will not be able to access the websites served up by server A and will alert me, and vice versa. Does that make sense?

What SeijiSensei provided is a start. What would build onto that would be something like 
```

#!/bin/sh
# I send my system email to the Gmail account on my Android phone using sSMTP

# if found, the output would be '80/tcp open  http'

FOUND='80/tcp open  http'
# query remote server
OUTPUT=$( nmap -p 80 server_A | grep -i $FOUND )
# if not found, email me
if [ $OUTPUT != $FOUND ]; then
    echo "Server_A is unreachable on $(date)" |
     mail -s "Alert: Server_A is unreachable" my_sysadmin_account@gmail.com
fi

```
Alternately, on some scripts, I send an XServer xmessage to open a dialog box on my admin console to tell me there is a problem.

---

### Post by koenn on 2015-09-13
> **Bucky Ball said:**
> In many ways trying to ping and trying to load a web page are one in the same thing. :)

Really ?
Verifing that your network has a route from one host to another  and that this host is connected to the network, and, otoh, verifing a web server is up and running and serving the pages you expect it to serve, are the same thing ?

---

### Post by koenn on 2015-09-13
> **Marc_Bressman said:**
> Thanks so much for the info!
I was actually hoping for something that might be a little bit more complete though, such as a small software package with a web GUI that could possibly do more than just ping and email if the ping doesn't go through (like perhaps try to load a web site, and if that doesn't work, send out an email, etc.).  Any thoughts/suggestions/recommendations?

Thanks!

That's nagios, almost by definition. 


 ... except that nagios is a rather elaborate framework, so it could be overkill for just two servers, and it can take a while before you know your way around.

---

