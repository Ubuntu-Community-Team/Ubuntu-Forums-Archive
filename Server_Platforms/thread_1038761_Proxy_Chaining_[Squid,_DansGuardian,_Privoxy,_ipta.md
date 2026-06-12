---
title: "Proxy Chaining [Squid, DansGuardian, Privoxy, iptables]"
date: 2009-01-13
forum: Server Platforms
---

### Post by Dr Small on 2009-01-13
I'm going to try to give you an idea of my setup, before giving the problem and questions, so you can understand my situation to the fullest.

I have a headless server [MYCROFT] that has DansGuardian + Squid running on it. I have several clients running on the network. The one I will be focusing on is [DARKGHOST].

[DARKGHOST] can configure Firefox to connect to [MYCROFT] on port 8181 (DansGuardian) and it proxies everything through DansGuardian, through Squid and then to the internet.


I am trying to setup a transparent proxy on [DARKGHOST] by using Privoxy. I have configured Privoxy to use the HTTP Proxy on [MYCROFT]; so Privoxy is running on port 8118 and directing traffic to [MYCROFT] on port 8181. 

I now configured Firefox on [DARKGHOST] to use "localhost", "8118" and I connect through Privoxy, to DansGuardian, to Squid and to the internet. Everything works up to this point.

Now, following [the tutoria]("http://www.linux.com/articles/113733")l on DansGuardian and Squid at Linux.com, I attempt to make a transparent proxy with iptables to route all outbound connections on port 80 to the destination port of 8118. Sounds simple enough.


So, I write this little script:
```
#!/bin/bash

# Set iptables rules for transparent proxy
PRIVOXYPORT=8118
PRIVOXYUSER="privoxy"
HTTPPORT=80


# Allow privoxy to connect to DansGuardian
iptables -t nat -A OUTPUT -p tcp --dport $HTTPPORT -m owner --uid-owner $PRIVOXYUSER -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 8181 -m owner --uid-owner $PRIVOXYUSER -j ACCEPT

# Redirect users who access $HTTPPORT to $PRIVOXYPORT
iptables -t nat -A OUTPUT -p tcp --dport $HTTPPORT -j REDIRECT --to-ports $PRIVOXYPORT

# Keep users from connecting to Squid and bypassing Dansguardian
iptables -t nat -A OUTPUT -p tcp --dport 3128 -j REDIRECT --to-ports $PRIVOXYPORT
```

Now, I am no iptables expert, and I am still learning it (I learn by experience, rather than book knowledge), so perhaps my error is with iptables. I don't know.


Next, I disable the proxy connection in Firefox on [DARKGHOST], run the script, and this is what I get as an output (I am guessing, from Squid):
> Invalid header received from client.


That's all the data I get. I was really hoping I would be able to make this chain transparent (not have to manually edit the proxy connection in Firefox all the time), but I am at a loss of what to do.

Any suggestions?

Dr Small

---

### Post by spiderbatdad on 2009-01-13
You've probably found this, but I'll post it in case you haven't: [http://osdir.com/ml/web.privoxy.user/2003-06/msg00014.html](http://osdir.com/ml/web.privoxy.user/2003-06/msg00014.html)

idk if reversing the lines ```
iptables -t nat -A OUTPUT -p tcp --dport $HTTPPORT -m owner --uid-owner $PRIVOXYUSER -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 8181 -m owner --uid-owner $PRIVOXYUSER -j ACCEPT

```will make a difference.

---

### Post by Dr Small on 2009-01-13
> **spiderbatdad said:**
> You've probably found this, but I'll post it in case you haven't: [http://osdir.com/ml/web.privoxy.user/2003-06/msg00014.html](http://osdir.com/ml/web.privoxy.user/2003-06/msg00014.html)

idk if reversing the lines ```
iptables -t nat -A OUTPUT -p tcp --dport $HTTPPORT -m owner --uid-owner $PRIVOXYUSER -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 8181 -m owner --uid-owner $PRIVOXYUSER -j ACCEPT

```will make a difference.
Just tried as you suggested and didn't help any. Somehow, I think the header is getting cut or removed by redirecting it through iptables (don't ask me how). I thought this would have been as simple as running it right through privoxy, but apparently it isn't.

Thanks for the help though. I'll keep trying stuff. :)

---

### Post by Dr Small on 2009-01-14
Solved the problem. I went keyword searching through /etc/privoxy/config and found "accept-intercepted-requests" and set the value to 1, and everything worked.

So, to complete the documentation on this side-project so I can do it again sometime later(!) and so anyone trying the same experiment can do it also, let's see what all I did.


Squid & DansGuardian running on a separate box (192.168.0.70). Squid on port 3128 and DansGuardian on port 8181.

On any client machine that I want to pass through this proxy, I install Privoxy and add these two lines:
```

forward  /  192.168.0.70:8181
accept-intercepted-requests 1

```

(As as side note, please be sure to find "accept-intercepted-requests" in the file and comment it out, so your newline will be effective.)

Start Privoxy:
```
sudo /etc/init.d/privoxy start
```


Now, save this script to /etc/init.d/transproxy:
```

#!/bin/sh
# Transparent Proxy designed to use Privoxy to connect to another
# system that is running DansGuardian & Squid. Privoxy needs to
# be configured before using this.

PRIVOXYPORT=8118
PRIVOXYUSER="privoxy"
HTTPPORT=80
SQUIDPORT=3128
DANSPORT=8181

# Location to save old iptables rules
LOCATION="/etc/iptables/rules.old"

flush () {
	echo "Saving old rules to $LOCATION"
	# Save the old rules
	iptables-save > $LOCATION

	echo "Flushing current iptables rules"
	# Flush the current rules
	iptables -F
	iptables -X
	iptables -t nat -F
	iptables -t nat -X
	iptables -t mangle -F
	iptables -t mangle -X
	iptables -P INPUT ACCEPT
	iptables -P FORWARD ACCEPT
	iptables -P OUTPUT ACCEPT
}

start () {
	echo "Adding new iptables rules for Privoxy"
	# Allow privoxy to connect to DansGuardian
	iptables -t nat -A OUTPUT -p tcp --dport $DANSPORT -m owner --uid-owner $PRIVOXYUSER -j ACCEPT
	iptables -t nat -A OUTPUT -p tcp --dport $HTTPPORT -m owner --uid-owner $PRIVOXYUSER -j ACCEPT

	# Redirect users who access $HTTPPORT to $PRIVOXYPORT
	iptables -t nat -A OUTPUT -p tcp --dport $HTTPPORT -j REDIRECT --to-ports $PRIVOXYPORT

	# Keep users from connecting to Squid and bypassing Dansguardian
	iptables -t nat -A OUTPUT -p tcp --dport $SQUIDPORT -j REDIRECT --to-ports $PRIVOXYPORT
}

stop () {
	echo "Restoring iptables rules from $LOCATION"
	# Restore the old rules
	iptables-restore < $LOCATION
}


case "$1" in
	start)
	flush
	start
	;;

	restart)
	stop
	flush
	start
	;;

	stop)
	stop
	;;

	*)
	echo "usage: start|stop|restart"
	;;

esac
exit 0
```

Now, if you want to add it to startup (on Ubuntu), just run:
```
sudo update-rc.d transproxy defaults
```

(On Arch, add the script to /etc/rc.d/ and add the name of the file to your DAEMONS array in /etc/rc.conf)

That should do it. :)

---

