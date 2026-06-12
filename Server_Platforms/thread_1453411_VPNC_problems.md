---
title: "VPNC problems"
date: 2010-04-13
forum: Server Platforms
---

### Post by knowram on 2010-04-13
I am running ubuntu server 9.10 and am having problems with vpnc. it seems to only pass trafic for about a half hour to an hour. and then stops. I have added DPD idle timeout (our side) 0 to my conf file and have also setup the auto reconnect configuration from this post
[https://mknowles.com.au/wordpress/2009/05/03/persistent-vpnc-connections/](https://mknowles.com.au/wordpress/2009/05/03/persistent-vpnc-connections/)
however neither seemed to make any difference.

Anyone have any ideas what i can try next?

Thanks for the help.

---

### Post by HermanAB on 2010-04-13
Hmm, sounds like you need to open a 'ping console' to keep the link up.  Crummy client software...

---

### Post by knowram on 2010-04-13
Well that's to bad if that's the solution. Do you know of a better client for connecting to a cisco vpn from an ubuntu server?

---

### Post by BobVila on 2010-04-15
> **HermanAB said:**
> Hmm, sounds like you need to open a 'ping console' to keep the link up.  Crummy client software...

Sadly, HermanAB is right - vpnc likes to die for what seems like no reason at all. 

Here's what I've been doing for a workaround:

Create file /etc/event.d/vpnc   ```
console output
exec /usr/sbin/vpnc profilenamehere --no-detach
respawn
```[FONT=Verdana]

[/FONT]to start vpn:   $ sudo start vpnc

to stop vpn:   $ sudo stop vpn

---

### Post by knowram on 2010-04-15
Thanks for the info BobVila. I am still new to linux so if you don't mind could you give me some info about what this little script does please.

Thanks

---

### Post by BobVila on 2010-04-16
> **knowram said:**
> Thanks for the info BobVila. I am still new to linux so if you don't mind could you give me some info about what this little script does please.

Thanks

It basically daemonizes the vpnc process and tells it to respawn if it's dead. Doesn't get around the issue entirely, but when your connection drops, the process restarts in the background before you have to figure out what's gone wrong.

---

### Post by knowram on 2010-04-16
> **BobVila said:**
> It basically daemonizes the vpnc process and tells it to respawn if it's dead. Doesn't get around the issue entirely, but when your connection drops, the process restarts in the background before you have to figure out what's gone wrong.

That's kinda what I thought it was doing however my problem isn't that the client or process stops it's that traffic just stops flowing. when this happens it seems that the client is still running as i can't just reconnect. I have to disconnect and then reconnect again. 

also just running a continues ping didn't help.

---

### Post by knowram on 2010-04-19
I am new to linux so I can only assume that this is posible but really have no idea how to do it but I am assuming it would be posible to create a script that has test ping connectivity to an ip address and kill the vpnc process and restart it if the ping fails. how difficult would this be?

---

### Post by koenn on 2010-04-19
not too difficult.

something like this ...
```

#!/bin/bash

PINGHOST="123.123.123.123"

pingcheck(){
	ping -c4 $PINGHOST
	return $?
}


pingcheck
RESULT=$?  #return code from pingcheck

case $RESULT in 
	0)
		#ping OK, do nothing
	;;	
	1) 
		# no reply, host down
		# stuff to restart vpnc goes here
	;;	
	2)
	       ## Misc. ping errors, 
	        # do something sensible  
       ;;
esac

```
run this at a reasonable interval (consider that a failing ping will need time to time-out), eg with cron. 

It's still an ugly workaround, but it might be just good enough.

---

### Post by knowram on 2010-04-19
Thanks koenn for the info. My next question is how do I run this say every 5 min?

---

### Post by BobVila on 2010-04-20
> **knowram said:**
> Thanks koenn for the info. My next question is how do I run this say every 5 min?

The power of cron be with you...

Get familiar with cron and you'll be able to schedule a script like that at whatever interval you'd like.

---

### Post by koenn on 2010-04-20
according to [http://www.foogazi.com/2008/04/01/quickzi-how-to-set-cron-to-run-every-5-minutes/](http://www.foogazi.com/2008/04/01/quickzi-how-to-set-cron-to-run-every-5-minutes/)

you'd add something like this to /etc/crontab to run a script named  /usr/local/bin/checkvpnc.sh :
```

*/5  *  *  *  *     /usr/local/bin/checkvpnc.sh

```
that script, obviously, should contain the routine that does the pinging and restarts vpnc if needed

---

