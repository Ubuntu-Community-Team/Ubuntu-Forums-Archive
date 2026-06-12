---
title: "ltsp rdesktop load balancing"
date: 2008-10-01
forum: Server Platforms
---

### Post by bbaer on 2008-10-01
I have created an LTSP server under Hardy and am attempting to create seamless RDP clients via PXE to my windows 2k3 terminal servers.  I have two of these as I have about 80 workstations and need to balance to load not to mention have some redundant services, just in case.  My problem is that I can't find a way to balance the load.  the win 2k3 servers are the standard editions so I can't use any of m$'s solutions.  I was hoping that there was an easy way to add two or more server addresses to the screen script provided and have it select one from the array or something of that nature.  My coding abilities are limited.  Does anyone have a suggestion for me?

Thanks in advance,
Bryan

---

### Post by lykwydchykyn on 2008-10-01
I found through some experimentation that lts.conf will actually expand shell variables and commands just like a bash script.  I've used this to create a scenario where the thin client auto logs-in with its hostname:
```

LDM_USERNAME = $(hostname)

```

Instead of hardcoding the RDP_SERVER setting into lts.conf, you could use the same sort of technique to assign it by the output of a script, like so:
```

RDP_SERVER = $(/usr/local/bin/server_selector)

```

server_selector would be a small script that randomly output the name or ip of one of your servers.  You'd have to chuck this in /opt/ltsp/i386/usr/local/bin and then rebuild your client image.

Here's a bash script that might work:
```

#!/bin/bash
servers=('server1' 'server2')
number=$RANDOM
let "number %=2"
echo ${servers[$number]}

```

That's kind of hacky, I know.  But it'd do the trick.  And at some later date if you want to do some more sophisticated load balancing, you just update that script to do something more than random selection (maybe test ping times, or retrieve a load value published by the server, etc).

---

### Post by bbaer on 2008-10-01
That's great, I'll take that and run with it.  Thanks so much!

-Bryan

---

### Post by aacable on 2010-07-16
[COLOR=Blue][SIZE=4]So simple & worked like a charm ! many thx buddy ...[/SIZE][/COLOR]


> **lykwydchykyn said:**
> I found through some experimentation that lts.conf will actually expand shell variables and commands just like a bash script.  I've used this to create a scenario where the thin client auto logs-in with its hostname:
```

LDM_USERNAME = $(hostname)

```Instead of hardcoding the RDP_SERVER setting into lts.conf, you could use the same sort of technique to assign it by the output of a script, like so:
```

RDP_SERVER = $(/usr/local/bin/server_selector)

```server_selector would be a small script that randomly output the name or ip of one of your servers.  You'd have to chuck this in /opt/ltsp/i386/usr/local/bin and then rebuild your client image.

Here's a bash script that might work:
```

#!/bin/bash
servers=('server1' 'server2')
number=$RANDOM
let "number %=2"
echo ${servers[$number]}

```That's kind of hacky, I know.  But it'd do the trick.  And at some later date if you want to do some more sophisticated load balancing, you just update that script to do something more than random selection (maybe test ping times, or retrieve a load value published by the server, etc).

---

