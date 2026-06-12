---
title: "I know nothing about servers but have a question"
date: 2011-07-05
forum: Server Platforms
---

### Post by Genesius10 on 2011-07-05
OK,
 
so i know nothing about servers but im going to have to learn.
 
What i need to do i set up a server and schedule it to switch the incoming port every 2 hours.
 
So 
10am - 12pm port 8000 is incoming
12pm - 2pm port 8000 is off and port 8020 is incoming
2pm - 4pm port 8020 is off and port 8040 is incoming.
 
 
Is this possible.
 
Basically different computers need to stream to my server at different times, but only one stream at a time.
 
Is this possible and how hard is it.
 
I dont really need how to's at this stage as im sure i wouldnt understand the lingo anyway.
 
If it is possible im going to go ahead and buy a server and have a go.
 
 
Thank you

---

### Post by Grenage on 2011-07-05
In theory, it should be relatively simply.  I have not done what you mention (and it sounds a little messy), but there's no reason you couldn't manipulate iptables using a cron schedule.

---

### Post by rubylaser on 2011-07-05
You could just do port forward all of those ports through your firewall to this box, then open and close the ports via cron and iptables. Here's a brief example.

**crontab**
```
00 10 * * * /root/scripts/port_8000.sh
01 12 * * * /root/scripts/port_8020.sh
01 14 * * * /root/scripts/port_8040.sh
etc
```**/root/scripts/port_8000.sh**
```

#! /bin/bash
# Port you want opened
iptables -A INPUT -p tcp --dport 8000 -j ACCEPT
# Port you want closed
iptables -A INPUT -p tcp --dport <last_port_here> -j DROP
```Something like that isn't elegant, but could be made to work. I'm just not sure why you'd want to bother with this.  It could be prone to error, if time sources aren't exact on each end.  Wouldn't a VPN connection be much more secure and less prone to error?

---

### Post by Genesius10 on 2011-07-05
Thank you rubylaser & Grenage.
 
I cant help but laugh. 'manipulate iptables using a cron schedule. '
 
When i read that for 1 second i thought 'yeah ok' then i just thought 'what am i getting myself into'.:confused:
 
So ill look up cron schedules and ip tables and then ill probably have a sit down with a large gin!.
 
 
Thank you for your help.
 
Grenage you said it soulds a little messy.  Is there a better way?  basically i want people to be able to log on and send their single stream to a specific port on my server then i want my server to send that stream through one output.
 
so in laymans terms the input device (port) changes and the output (port)stays the same.

---

### Post by Grenage on 2011-07-05
> **Genesius10 said:**
> Thank you rubylaser & Grenage.
 
I cant help but laugh. 'manipulate iptables using a cron schedule. '
 
When i read that for 1 second i thought 'yeah ok' then i just thought 'what am i getting myself into'.:confused:
 
So ill look up cron schedules and ip tables and then ill probably have a sit down with a large gin!.
 
 
Thank you for your help.
 
Grenage you said it soulds a little messy.  Is there a better way?  basically i want people to be able to log on and send their single stream to a specific port on my server then i want my server to send that stream through one output.
 
so in laymans terms the input device (port) changes and the output (port)stays the same.


It shouldn't be too difficult, and rubylaser's examples should make it that much easier. :)

When I say messy, I'm talking from an administration side of things - you may not need to make any further changes.  Is it customers who are sending data, or do you have control of the machines?  I'm guessing that you don't, or you wouldn't have suggested your current path.

I have a several 'messy' solutions here and there, sometimes there's no getting around it; just make sure you document it well. ;)

---

### Post by Genesius10 on 2011-07-05
basically im working on an internet radio station.
 
Dj's send a stream to a certain port when their show starts and as their show ends that port closes and the port for the next dj opens.
 
Then the stream comes out of my server and onto my streaming server and then to the listerners.
 
Because the stream from myserver to my rented streaming server is constant then the end listener wont get kicked everytime the port is switched on my server.
 
So
 
DJ>audio line in>shoutcast>port xxxx on my server>output port on my server>shoutcast to port on rented audio streaming server> website/listener.
 
because there is a shoutcast stream constantly supplying the rented audio server the listener shouldnt get kicked when the port switches on my server.
 
i hope ive got this right?

---

### Post by Grenage on 2011-07-05
I haven't used Shoutcast in about 12+ years (fun times), but that sounds feasible.  I don't know how it was configured back then, as we just jumped straight onto a server.  You'll want to use an NTP server for the time, but I believe Ubuntu does that out of the box.

Give it a go!

---

### Post by Genesius10 on 2011-07-05
i will and i will keep you posted.

---

### Post by dozycat on 2011-07-05
> **rubylaser said:**
> You could just do port forward all of those ports through your firewall to this box, then open and close the ports via cron and iptables. Here's a brief example.

**crontab**
```
00 10 * * * /root/scripts/port_8000.sh
01 12 * * * /root/scripts/port_8020.sh
01 14 * * * /root/scripts/port_8040.sh
etc
```**/root/scripts/port_8000.sh**
```

#! /bin/bash
# Port you want opened
iptables -A INPUT -p tcp --dport 8000 -j ACCEPT
# Port you want closed
iptables -A INPUT -p tcp --dport <last_port_here> -j DROP
```Something like that isn't elegant, but could be made to work. I'm just not sure why you'd want to bother with this.  It could be prone to error, if time sources aren't exact on each end.  Wouldn't a VPN connection be much more secure and less prone to error?

It's not going to work very very well because you are going to be adding rules to the end of the iptables, and you must remember that iptables checks until the first rule it can apply and then it will stop checking the rest.
However the idea is great, just create different scripts for the full table, and before applying then flush the tables.

---

### Post by Genesius10 on 2011-07-05
dozycat, i wish i knew what you were saying.  Is there any other solution that will work well?

---

### Post by dozycat on 2011-07-05
how are you working with iptables in this moment?

This link must help a little:
[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")

---

### Post by rubylaser on 2011-07-05
You are correct that this won't work as is, I was just providing an example :) And, after hearing how this is going to be used,  I really don't like this method. The OP would have to wait for cron to run, and rebuild the iptables at each interval.  I can see this causing a slight hiccup, which might not be desirable for listeners.  I'd try to think of a better way to implement this than cron+iptables.

---

### Post by Genesius10 on 2011-07-06
Hi i would just like to say again
**'so i know nothing about servers but im going to have to learn.'**

i dont even know what cron and iptables are.
 
I just need a solution that will work.  Once i have the solution i will have to learn how to implement it.
 
So has anybody got any ideas how i can make this work?

---

### Post by Grenage on 2011-07-06
> **Genesius10 said:**
> Hi i would just like to say again
**'so i know nothing about servers but im going to have to learn.'**

i dont even know what cron and iptables are.
 
I just need a solution that will work.  Once i have the solution i will have to learn how to implement it.
 
So has anybody got any ideas how i can make this work?

cron is basically a scheduler, like Windows Task Scheduler.
iptables is a very configurable firewall.

The best way to go about this would be to install a copy of linux somewhere and play about with it, you'll need to do some testing to see how it goes.  Searches on cron syntax (it's *very* simple) will show you how to add the command; as for the command you'll be running, the iptables commands will also be readily available on many guides.

While there may be better solutions available, it would be worth forging ahead until someone suggests (or you discover) a better way.

---

