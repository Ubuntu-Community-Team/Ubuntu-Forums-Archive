---
title: "Returning external ip address using miniupnpc"
date: 2017-01-29
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2017-01-29
Hi all

Have a Bash script which detects any change to the external IP address of a server and then updates the DNS at Namecheap only if a change detected.

Planning to replace ```
ipnew="$(curl ident.me)"
``` in the script with ```
ipnew="$(external-ip)"
```The script currently runs every 5 minutes on a cron job to avoid excessive 'polling' of ident.me and perhaps its unavailability, but would like to run the script every 1 or 2 minutes to improve response rates.

So are there any 'gotchas' in using the alternative method, please?

TIA

Chris

---

### Post by SeijiSensei on 2017-01-29
I don't know how you're getting the address.  I use this on 14.04:

```
ADDR=$(/sbin/ifconfig | grep 'inet addr' | head -n 1 | awk '{print $2}' | sed 's/addr://g')
```

The format of ifconfig results are slightly different on later distros.  The word "addr:" has been deleted.  On those distros you need only

```
ADDR=$(/sbin/ifconfig | grep inet | head -n 1 | awk '{print $2}')
```

You could run your script once per minute and have little effect on performance.  Most of the time the address will remain unchanged, and the script will do nothing.

---

### Post by ChrisRChamberlain on 2017-01-30
SeijiSensei

Many thanks for your reply.

Both your code snippits return '127.0.0.1' or am I missing something?

---

### Post by Habitual on 2017-01-30
curl icanhazip.com
will always show the external ip.

Just sayin'

---

### Post by SeijiSensei on 2017-01-30
Use "ifconfig eth0" or whatever name has been assigned to the public-facing interface.

ifconfig returns information about the interfaces in alphabetical order.  Since servers are generally connected by wired Ethernet, the "eth0" interface typically appears first ahead of "lo".  The "head -n 1" command uses the first line with the word "addr" in it which would then be eth0.

Is it possible you're connecting this machine via wifi, so the wlan0 interface comes after lo?  If so, buy yourself an Ethernet cable and connect the machine with that.

> **Habitual said:**
> curl icanhazip.com
will always show the external ip.

The OP said he wanted to avoid polling remote web sites that provide this service.

---

### Post by Habitual on 2017-01-30
> **SeijiSensei said:**
> The OP said he wanted to avoid polling remote web sites that provide this service.
Not to argue, but that is incorrect, he specified excessive 'polling' of ident.me

icanhazip.com won't care about 2 hits ever few minutes.
used in conky for years.

I'm out,.
Peace.

---

### Post by The Cog on 2017-01-30
I think external-ip gets its info by using UPnP to query the local router. If this works (probably will in a home network), it should avoid any polling of web sites. Try the command by hand and see if it gives the right answer.

---

### Post by ChrisRChamberlain on 2017-01-31
The Cog

The routers in question are Netgear DG834x and 'external-ip' works as expected.

Didn't know if 'external-ip' was also using external 'polling', hence the question.

As it appears it does not, reducing the frequency of checking of the external ip address by using 'external-ip' appears to provide a solution for this class of router.

Many thanks to all who contributed to the thread - as ever, a lot was learned.

Chris

---

