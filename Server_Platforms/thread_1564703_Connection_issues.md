---
title: "Connection issues"
date: 2010-08-30
forum: Server Platforms
---

### Post by oomar on 2010-08-30
Ok so I am running Ubuntu Server 10.04 on an old desktop PC. It has been running great.

But after some uptime (not sure exactly how long) it simply loses connectivity. Odddly, I can get on to the Server (Plug a monitor and keyboard in) and connect out (ie use lynx to go online or ping various websites) but I can't connect in from anywhere. I can't connect on the same LAN and I can't connect to it from the WAN IP address.

I have http, squid http proxy, webmin, and ssh running. I can connect to none of them when this happens. 

I am using ufw (I don't need the versatility of iptables... too complicated for my needs).

ummm I can't think of anything else extremely pertinent....

So basically, what could cause it to do this? I can proivide more details if required.

---

### Post by BULLIT22 on 2010-08-31
I am having this conectivity issue as well. Don't know if they are related. I am running Ubuntu server 9.10. After a week or so of uptime I also lose connectivity to my server. I did some looking around and my IP address had been switched from 192.168.1.3 to 192.168.1.2 in my router. Not sure what this means, or how it happened. Any help would be great for me as well.

---

### Post by pricetech on 2010-08-31
Not saying this is the OPs problem, though it's a possibility, but either set a fixed IP on your server "or" set your router to reserve an IP for your server according to the MAC address.

Outside of that, nothing jumps out at me as a potential problem.

---

### Post by oomar on 2010-08-31
I haven't set a specific IP that I remember but that was the first thing I checked and the IP hadn't changed and the router still recognized the IP address being leased to the correct server. 

So I don't know how that could be a problem...

---

### Post by arrrghhh on 2010-08-31
Either way, you need to configure a static IP on the server - make sure it's outside of your dhcp range on the router.  For example, my dhcp range covers 192.168.0.128/25, so anything below that is fine for a static IP.

---

### Post by BkkBonanza on 2010-08-31
When you ping it from another machine on the LAN what response do you get? Can you co-relate the failure to anything at all - power failure, system reboot, ISP re-assigned IP, anything that may trigger some change?

Static IP doesn't appear to be your problem here but just so you know you can usually still use DHCP but config a **static lease** for that MAC address so the DHCP server won't change it.

---

### Post by oomar on 2010-08-31
Thats what it was. I had a static lease. 

And When I pinged it, I didn't get any response packets.

---

### Post by arrrghhh on 2010-08-31
Do an ifconfig on the server to see if the IP changed... that'll let us know if we're barking up the wrong tree.

---

### Post by BkkBonanza on 2010-08-31
Have you checked if the interface is still "up" by looking at output from **ifconfig**? If it is then I would check cabling. I've seen this behaviour with cable problems. Everyone tends to assume it is rock solid but often there can be issues there. If the interface is down then perhaps something is interfering on the system. Even if the interface is active it could be something flaky in the hardware or the driver (bugs). It is a bit odd you can ping out but not in. Perhaps re-check any firewall config and make sure it is what you expect. At a low level you can list the rules with **sudo iptables -L** and see what it's doing.

---

### Post by oomar on 2010-08-31
i did if config when it was experiencing connection problems. Everything looked fine in ifconfig. I could ping out, use lynx to browse the web, but any connection made TO it did not work. only outbound connections worked. It wasn't even that it was being refused... the connections were simply being dropped...

I did also check the cable when I saw that ifconfig appeared normal. It was fine. 

If its a hardware bug... then why is it just now showing up...? the server has been running for over a month. this problem started a few days ago. 

I haven't had the problem again... (I restart it periodically just to make sure) but I'm going to let it happen again to see if I can diagnose the problem.

---

### Post by BkkBonanza on 2010-08-31
Later, if you can re-create the problem then be sure to also check output of **sudo netstat -lntp** to make sure the correct services are actually listening. And the iptables output would be useful as it sounds a lot like a firewall issue. It could allow outgoing but prevent connections and pings inbound.

---

### Post by arrrghhh on 2010-08-31
Hrm... the more you describe it, the more it does seem layer-1 related... but then you wouldn't be able to ping out or use lynx.  Baffling.  Anything odd in your syslog, /var/log/messages or dmesg?

---

### Post by oomar on 2010-08-31
so far it has not been re-created. I will use netstat if it causes trouble again.

arrrghhh what exactly should I be looking for? nothing really pops out at me.... i mean.... it looks normal as far as I can tell.

---

### Post by arrrghhh on 2010-09-01
Well I'm not positive.  That netstat command while it's happening may reveal more, and you can also check your logs around the time it occurs...

I'd guess some ethernet or strange network-related errors would be what to look for... but again I have no clue what it'll look like exactly, since I don't really know what's wrong ;)

---

### Post by oomar on 2010-09-08
well i still dont know what the problem is but ive just set a cron job to reset the computer every 12 hours and i havent had a problem since. so whatever that means.... lol

---

### Post by arrrghhh on 2010-09-08
> **oomar said:**
> well i still dont know what the problem is but ive just set a cron job to reset the computer every 12 hours and i havent had a problem since. so whatever that means.... lol

Hrm.  I guess that's a solution... but definitely doesn't make me feel very warm and fuzzy.

IF you manage to recreate it, dump your logs and pastebin 'em.  /var/log/messages, syslog, uhm... There's probably another one I'm missing, that's more directly related to network issues... But I can't find it right now!

---

### Post by oomar on 2010-09-15
well It's happening again this time even after a restart :/ so my temporary fix is not working. 

I did netstat -lntp like bonaza said and everything looks right. (I'll post it when I get the chance. soon.) Its listening on all the ports i tell it to with all the right programs so I don't see a probelm there.

I ran ss and saw a bunch of connections to my squid proxy server (i have since blocked it on ufw and disabled the port forwarding rule on the router so if that the problem then that should be fixed now.) 

Then I saw one connection on port 60860... I'm not sure what that is.
I'll post that output soon as well.

just noticed that functionality is back... Weird. I can now ssh in and get to webmin. :/

I ran dmesg and 1. it moves insanely fast across the screen so i dont really know what to do with it in CLI. but I do see that I am repeatedly getting a connection from 66.252.2.45. Not sure what that is...

Any more information you want?

EDIT:
I just blocked 66.252.2.45 so we'll see if i was being DDOSed or something

---

### Post by arrrghhh on 2010-09-15
/var/log/messages?  syslog?  You can also redirect the output of dmesg to a file to make it easier to read.  Shift+PGUP will let you scroll in the terminal, but it ain't pretty.

---

### Post by oomar on 2010-09-15
ok... so what would you consider to be a normal size for a log file? because syslog and messages combined are over 1GB i think... that doesn't seem normal to me.... i haven't looked at them yet theyre still copying from the server to my laptop

---

### Post by arrrghhh on 2010-09-15
> **oomar said:**
> ok... so what would you consider to be a normal size for a log file? because syslog and messages combined are over 1GB i think... that doesn't seem normal to me.... i haven't looked at them yet theyre still copying from the server to my laptop

Damn... that does seem high.  My syslog is ~300k and messages is 1.1 megs.  My ENTIRE /var/log is 139 meg.

So before pastebinning 1gb worth of text... taking a quick look at maybe just a tail or tail -n 200 something like that of messages?  Any themes in there?  I know when our NMIS server was messed up its logfile would grow about 1gb every day... that was ludicrous amounts of errors tho, I could watch the log file grow by the second.

Either way, your logs sound ridiculously big.

---

### Post by CharlesA on 2010-09-15
Holy crap @ 1GB logs. Mine are around 10 MB (new install)

But yeah, check for patterns. I'm guessing there are a ton of errors in some of those logs.

---

### Post by oomar on 2010-09-16
The only pattern that immediately jumps out is that 66.252.2.45 made A TON of connections. I have already blocked him so let's hope that works...

Just about everything I can see in there is a UFW Audit or UFW Allow

---

### Post by CharlesA on 2010-09-16
Oh ok, Were the failed login attempts made via SSH?

You could turn off logging, that would cut down on the size of the logs.

---

### Post by oomar on 2010-09-16
> **CharlesA said:**
> Oh ok, Were the failed login attempts made via SSH?

You could turn off logging, that would cut down on the size of the logs.

forgive me, I don't deal with the logs as much as I should.

How do i see what service they were for? if the login was successful etc  and how do i turn off logging or at least cycle the logs?

---

### Post by CharlesA on 2010-09-16
> **oomar said:**
> forgive me, I don't deal with the logs as much as I should.

How do i see what service they were for? if the login was successful etc  and how do i turn off logging or at least cycle the logs?
Was it in a auth.log or another log?

If it was auth.log, it'll say something like sshd if it was an attempt to connect to SSH.

---

### Post by oomar on 2010-09-16
thats the one i didnt copy! ill have to look at that one from school. I don't have time to copy it right now.

---

### Post by oomar on 2010-09-16
After a quick look at the auth.log file... most everything looks normal...

except I see A LOT of 
```
Sep 16 10:09:01 loganncserver CRON[1573]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 16 10:09:01 loganncserver CRON[1573]: pam_unix(cron:session): session closed for user root

```

That happens again and again and again. I'm not quite sure what that means but its root so it worries me slightly.

---

### Post by CharlesA on 2010-09-16
Oh that's fine. It just means that cron is checking for/running a job. I've got a bunch of those. :)

```
Sep 16 08:39:01 thor CRON[29241]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 16 08:39:01 thor CRON[29241]: pam_unix(cron:session): session closed for user root

```

---

### Post by arrrghhh on 2010-09-16
Hmmmm... Still makes me wonder.

After blocking that IP, perhaps you should clear out the logs and run again, see if the error persists... and then we'll take another look at the logs, hopefully they won't get 1+gb lol!

As a sidenote, CharlesA, looks like you're now forum staff!  Congrats!

---

### Post by CharlesA on 2010-09-16
> **arrrghhh said:**
> Hmmmm... Still makes me wonder.

After blocking that IP, perhaps you should clear out the logs and run again, see if the error persists... and then we'll take another look at the logs, hopefully they won't get 1+gb lol!

As a sidenote, CharlesA, looks like you're now forum staff!  Congrats!

Indeed. Make a backup copy of the logs and see if they have the same errors in the new ones.

@arrrghhh: Thanks! :)

---

### Post by oomar on 2010-09-16
How do I make the logs cycle?

---

### Post by arrrghhh on 2010-09-16
> **oomar said:**
> How do I make the logs cycle?

Well... there's an actual package called ['logrotate'](http://manpages.ubuntu.com/manpages/lucid/man8/logrotate.8.html), but you shouldn't really need to use that... you can just mv the file to another name, the log file should recreate.

---

### Post by CharlesA on 2010-09-17
> **arrrghhh said:**
> Well... there's an actual package called ['logrotate'](http://manpages.ubuntu.com/manpages/lucid/man8/logrotate.8.html), but you shouldn't really need to use that... you can just mv the file to another name, the log file should recreate.

You could probably just run a script that'll move the logs and throw it into a crontab.

---

