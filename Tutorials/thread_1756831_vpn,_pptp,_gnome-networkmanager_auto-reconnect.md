---
title: "vpn, pptp, gnome-networkmanager auto-reconnect"
date: 2011-05-12
forum: Tutorials
---

### Post by Cornelius.Pseudonymous on 2011-05-12
Greetings

I was presented with the problem of my vpn connection and pptp dropping on me over time, sometimes being over a period of days or hours. I needed some sort of solution to have my vpn reconnect, automatically. I felt vulnerable, running p2p or whatever else during the night and not knowing if it would drop while I was asleep or away.

I did a lot of research, found a few promising scripts and plug-ins, but couldn't get anything to work right, like many of people I read about. 

SOLUTION:
I made a bash script-
Requirements- networkmanager, openvpn/pptp, nmcli (which i believe is packaged with networkmanager)

name this whatever you like 
ex. vpn-auto.sh
make it executable and open privileges 
I added mine to my autostart file 
```

#!/bin/sh
while [ "true" ]
do
    vpnck=$(nmcli con status uuid 3e46a1d0-ab02-4d69-bd36-31dfcc01af6d)
    if [[ $vpnck == *cryptocloud* ]]
    then
    else
      (sleep 1s && nmcli con up uuid 3e46a1d0-ab02-4d69-bd36-31dfcc01af6d)
    fi
    sleep 20
done

```Replace "*cryptocloud*" with your vpn name
Replace "3e46a1d0-ab02-4d69-bd36-31dfcc01af6d" with your uuid of the vpn you want to auto reconnect.

To find out your uuid type
```

nmcli con

```in your terminal

The downside to this is you have a bash script that checks every 20 seconds, or whatever you change that to, but imo this is better than a lot of bloated scripts and plug-ins I've seen circulating.

If there are any optimizations that anyone has please share.
Thanks

---

### Post by MagicThinker on 2011-10-25
G'day,

Awsome, Thank you very much I have been searching for something like this for a long time now.

Cheers

---

### Post by relgames on 2012-06-13
When I try to run it, it prompts an error:

./startvpn.sh: [[: not found

What is wrong??

---

