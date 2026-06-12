---
title: "Bash script to email you your ip address"
date: 2011-10-18
forum: The Cafe
---

### Post by BennyBolton on 2011-10-18
I made a bash script to find your external ip address, and if it is different to the last time it checked it, it emails it to you.
It uses msmtp to send the email.

```
#/bin/bash

# email address which is sending the email
sender="user@domain.com"
# email address which is receiving the email
receiver="user@domain.com"
# delay time between checks in seconds
delaytime="1800"
# file to save previous ip address
oldip="/home/USER/.ip.address"
# temp file for email
tmpemail="/tmp/ip.mail"

touch $oldip
while true; do
	rm -f $tmpemail
	echo "To: $receiver" >> $tmpemail
	echo "From: $sender" >> $tmpemail
	echo "Subject: Your Ip" >> $tmpemail
	echo "" >> $tmpemail
	ipaddress=$(curl -s http://checkip.dyndns.org | sed 's/[a-zA-Z/<> :]//g')
	ipaddress2=$(cat $oldip)
	echo "Is: $ipaddress" >> $tmpemail
	echo "Was: $ipaddress2" >> $tmpemail
	echo $ipaddress
	echo $ipaddress2
	if [ "$ipaddress" != "$ipaddress2" ]
		then echo "There different!"
		cat $tmpemail | msmtp -a default $receiver
		rm -f $oldip
		echo $ipaddress >> $oldip
	fi
	echo "Continuing..."
	sleep $delaytime
done
```

This is the first bash script that i've published

---

### Post by Lars Noodén on 2011-10-18
Nice.  How do you plan on using it mostly?

---

### Post by aeiah on 2011-10-18
to do away with a dynamic dns service, i presume.

its a nice script, although i wouldn't have put it in a loop. id have made it do a single pass and repeatedly call it from cron.


also, "**they're** different" ;)

---

### Post by CharlesA on 2011-10-18
> **aeiah said:**
> to do away with a dynamic dns service, i presume.

its a nice script, although i wouldn't have put it in a loop. id have made it do a single pass and repeatedly call it from cron.


also, "**they're** different" ;)

This.

I just use dyndns since it's easier to remember a domain name instead of having to look up an ip address.

---

### Post by Lars Noodén on 2011-10-18
> **CharlesA said:**
> I just use dyndns since it's easier to remember a domain name instead of having to look up an ip address.

dyndns is an easy way.  I use it, too.  There are also other similar services:

[http://dnslookup.me/dynamic-dns/](http://dnslookup.me/dynamic-dns/)

---

### Post by CharlesA on 2011-10-18
> **Lars Noodén said:**
> dyndns is an easy way.  I use it, too.  There are also other similar services:

[http://dnslookup.me/dynamic-dns/](http://dnslookup.me/dynamic-dns/)

Yep. I've used no-ip too.

---

### Post by kelbizzle on 2012-07-13
I just thought about this and before writing it I attempted to search for it. 

It's going to be useful for me because I can remember my ip as it doesn't change often. But when it does it's inconvenient. Also, my dyndns name seems to always expire from lack of use. This is just easier for me because I don't need to use it as often.

BTW thanks!

---

