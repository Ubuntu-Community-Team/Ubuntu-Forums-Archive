---
title: "how to clean up iptables?"
date: 2008-12-10
forum: Server Platforms
---

### Post by Shwick2 on 2008-12-10
My iptables script is getting bloated, redundant, and there's code duplication everywhere, how can I clean it up?

Use shell script functions?
Develop it in a different language, like python?

---

### Post by cdtech on 2008-12-10
Not sure what you mean?

**UPDATE::.**
My bad, I see your writing your own script. What lang are you using now?

---

### Post by Shwick2 on 2008-12-10
I'm using an sh script.  I'm just wondering if there is a generally accepted better way, or more object oriented way, to do this.

---

### Post by hictio on 2008-12-10
> **Shwick2 said:**
> I'm using an sh script.  I'm just wondering if there is a generally accepted better way, or more object oriented way, to do this.

I don't know, but, I think that, to the limit of what you can post, the only way to determine how to do that will be by taking a look at your current script.
If, by any chance, you want to take a look, I have posted in [this thread](http://ubuntuforums.org/showpost.php?p=6316875&postcount=3), sort of a template of the iptables script I use for servers/ workstations NOT routers.

You can easily add more chains for giving access to more services; on the script the only services are SSH, HTTP/ HTTPS & ping replies, but you get the idea.

One very important thing when applying firewall rules, be sure to have console access, or a work around in case you get blocked outside your own box!

---

### Post by Shwick2 on 2008-12-11
Thanks that looks good.

But I mean, I need to make a function out of this:
```

# Create LAN_ICMP_PROTECT chain to throttle ICMP
# Drop the packet if it was from an IP that connected at least twice in the past second
# Allow the packet while there are tokens left in the queue of size 10 that recharges at a rate of 6/s
iptables -N LAN_ICMP_PROTECT
iptables -A LAN_ICMP_PROTECT -m recent --set --name LAN_ICMP
iptables -A LAN_ICMP_PROTECT -m recent --update --seconds 1 --hitcount 3 --name LAN_ICMP -j DROP
iptables -A LAN_ICMP_PROTECT -m limit --limit 6/s --limit-burst 10 -j ACCEPT
iptables -A LAN_ICMP_PROTECT -j DROP

```

I have this same chain duplicated about 30 times, with slightly different numbers, for different services and interfaces.  I need to turn it into a function that takes a chain name, status name and some of those numbers.  I guess that would be a shell script function, however you do that.  It would end up saving me over a hundred lines of code probably.

---

### Post by cdenley on 2008-12-11
You can create functions with just about any language, including bourne or bash shell scripting. It all depends on your personal preference.
```

#!/bin/sh
do_func() {
        echo $1 $2
}
do_func val1 val2

```
I had to create a script that was much more dynamic, so I made a python script which would write rules to the standard input of the "iptables-restore" command.

---

