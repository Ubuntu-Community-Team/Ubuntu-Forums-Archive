---
title: "China | Can my ISP stop services (Transmission Daemon)"
date: 2015-08-28
forum: Security
---

### Post by nitez on 2015-08-28
Hello

I am on ubuntu 12.04, using a combination of couchpotato and transmission (daemon 2.51 (13280)) and, important, I am based in China.

My Chinese ISP doesn't prohibit torrents officially but, in practice, they do block ports/protocols. Simple test = transmission-daemon (td) only starts to be active once my system (through router) is connected to a VPN. And with that system, I used to have a good bandwidth ... for a while.

That's changed now. When my VPN drops, not only does td stop all activity, the daemon actually stops (when checking STATUS). I actually have to START the daemon again (ONLY when VPN is activated!). If I start the daemon when the system is not connected to a VPN, it's simply killed (cannot even access the WebUI).

The reason may lie elsewhere, but I have high suspicions that my ISP actually stops the daemon?

I've been using Ubuntu for the past 10 years but mostly as a file server so I have little experience with security issues (beyond basic sharing rights). Where can I start to actually verify logs (start/stop of daemon, if my system is being hacked, connections oher than mine, etc.).

Many thanks for your help!

---

### Post by TheFu on 2015-08-28
Logs are in /var/log.

I doubt anyone has hacked the system if you keep it patched.

Programs check for certain connections at startup and if those connections cannot be made, shutdown. Could that be what is happening here?

---

### Post by Habitual on 2015-08-28
> **nitez said:**
> I used to have a good bandwidth ... for a while.I suggest you got 'caught' and silently received a 
cap, or other alteration to your account.

wrt:
> **nitez said:**
> I have high suspicions that my ISP actually stops the daemon? More like they blocked the protocol and or 
port for the daemon.

---

### Post by QIII on 2015-08-28
Hello!

Before you ask, the answer to the questions:

"How do I get around my ISP's limitations?"

and

"How do I get around the laws in my jurisdiction?"

are both "We won't help you violate EULAs, ToS or the laws in your local jurisdiction."

---

### Post by nitez on 2015-08-28
> **QIII said:**
> "We won't help you violate EULAs, ToS or the laws in your local jurisdiction."

This isn't what I'm asking. As highlighted, my ISP does NOT prohibit torrents.
What I'm asking is "How do I find out how transmission-daemon shuts down".

Thanks!

---

### Post by nitez on 2015-09-08
So, I finally managed to dig into my logs and found reference to a crash report for transmission-deamon. The crash report was so heavy that it gave me a hard time to actually read it. Although I didn't dig much further, it seems to be an issue in setting.json. Many months ago, I made a slight edit to broaden the IP white-listing (precisely indicated as in several fora). As I've seen references that transmission-daemon tends to crash if to heavily mobilised, I'm not sure if it's either one or the other. I'm not suffciently versed in reading logs yet and the file is so large that I couldn't possibly add everything here. Either way, not a security issue so I'll changed the prefix.

If that's of interest for anyone at all, I fixed the issue rather inelegantly by setting a cron job that starts the daemon every hour. No/little problem since. This also makes me think, how to setup a conditional cron job, e.g. IF transmission-daemon status = stopped, then start. The cron job I set hasn't generated any problems (say if it is running already), but I presume this may be different with other daemons?

---

### Post by Habitual on 2015-09-08
> **nitez said:**
> This also makes me think, how to setup a conditional cron job, e.g. IF transmission-daemon status = stopped, then start. The cron job I set hasn't generated any problems (say if it is running already), but I presume this may be different with other daemons?

working example from notes:
```
#!/bin/bash
### zabbix-agentd pidcheck cron script
### Written by John Jones 
### Date: Mon Apr 30, 2012

SERVICE='zabbix_agentd'
 
if /usr/bin/pgrep $SERVICE > /dev/null
then
    exit 0 
else
    # do stuff here.
    # Log maybe?
    exit 1
fi
#EOF


```
save. chmod. all that... Cron:
```
*/1 * * * * /root/zbxcheck.sh
```

 Stopped zabbix_agentd manually and waited 1 minute.
 It fired.

Hope that helps. There are as many ways to do this as there are Ubuntu Members. :)
And Good job, well done on digging the logs!

---

### Post by JKyleOKC on 2015-09-11
> **nitez said:**
> I fixed the issue rather inelegantly by setting a cron job that starts the daemon every hour. No/little problem since. This also makes me think, how to setup a conditional cron job, e.g. IF transmission-daemon status = stopped, then start. The cron job I set hasn't generated any problems (say if it is running already), but I presume this may be different with other daemons?Here's how I handled a similar problem here when my FTP server (which normally runs quietly in the background 24x7) would occasionally shut itself down and I'd fail to notice it until a customer would email me to ask how to get a file to me for repair.

I created this file and put it into the /etc/cron.hourly directory (file name doesn't matter, there):```
#! /bin/bash
#  Script to restart FTP server if not running
#  jk - 2 Dec 2014

s=$(service proftpd status)
r=$(echo "$s"|cut -c 50-56)

logger -p syslog.info "Checking FTP server..." 
if [ "$r" == "running" ]
  then logger -p syslog.info "$s"
  else logger -p syslog.info "$(service proftpd start)"
fi

exit 0

```Haven't had a problem with it since.

---

