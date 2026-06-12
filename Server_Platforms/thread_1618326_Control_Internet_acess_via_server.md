---
title: "Control Internet acess via server?"
date: 2010-11-10
forum: Server Platforms
---

### Post by felix_mc on 2010-11-10
I have a Ubuntu server, that among other things, acts as a DHCP server. One networking port is connected to a dsl modem, and the other to a switch to which about 20 computers are connected. Internet is shared from the DSL modem to the switch through the Ubuntu server. Automatic addressing is disabled, so each computer is set up to have a specific static IP address which is known to the server admins (which includes me). Is there a way to disable the internet connectionfor a specific computer, via the computer's IP address? This is meant to be used in a highschool networking class as a means to reduce random web browsing and increase productivity. For example if Johny did not turn all his labs in, I'd like the teacher to be able to disable his internet connection by simply knowing that his IP is 192.168.1.23 and adding it to a blacklist or something of that sort. Anyway is this possible with my current set up?

---

### Post by SeijiSensei on 2010-11-10
Something like this perhaps:

```

BLACKLIST=$(cat /etc/firewall/blacklist)

for addr in $BLACKLIST
do
    iptables -I INPUT -s $addr -j REJECT
done


```

Using the -I switch puts all the blacklisting rules at the top of the INPUT chain.

---

### Post by endotherm on 2010-11-10
well there are a couple things that come to mind, but it seems like a proxy server like squid is your best bet. if the kid is bad, lock his access to the proxy. setting it up will probably been a bit of an exercise (I haven't tried squid before, so could be a breeze, just not sure).

another option is dns filtering with tools like the openDNS client, but that probably won;'t work for your approach to DNS serving.

---

### Post by SeijiSensei on 2010-11-10
Squid's more work than it's worth in this case, I think, and would require creating ACL rules in /etc/squid/squid.conf.  It would also only block web traffic, so a knowledgeable kid could point his browser at a remote proxy site and end-run the blocking.  

Using iptables enables you to turn off **all** access to the network.

---

### Post by felix_mc on 2010-11-11
IP tables seems like the way to do it..however, is there a way to turn off **only** internet access and not network access as well? The reason for that is that the server also acts like a local web/file server and its used by students to view their current grade, as well as download lessons/assignments to their own computer and all that. 

We already have openDNS set up on the network. As long as there's internet, kids always seem to find a way around things.

---

### Post by SeijiSensei on 2010-11-11
> **felix_mc said:**
> IP tables seems like the way to do it..however, is there a way to turn off **only** internet access and not network access as well?

Let's assume your local network subnet is 192.168.1.0/24. Then,

```

BLACKLIST=$(cat /etc/firewall/blacklist)
LOCALNET="192.168.1.0/24"

for addr in $BLACKLIST
do
    iptables -I INPUT -s $addr -d $LOCALNET -j ALLOW
    iptables -I INPUT -s $addr -j REJECT
done

```

allows access to the local network, but not the Internet.

---

### Post by felix_mc on 2010-11-17
Thank you! I used a variation of the script you provided and it worked for a while, but then some students discovered they can change their IP address to an address that is not yet in use to get online. Is there a way to block internet traffic from all IPs, except for specific ones? As in instead of having a list of blocked IPs to have and list of allowed IP's rather?
Since all computers in the room have static IPs based on the their physical location in relation to the front of the room, it would be quite easy to manage

---

### Post by SeijiSensei on 2010-11-17
Clever, aren't they? :D  You can see why I didn't think a Squid proxy would be effective against them.

How about this:

```

WHITELIST=$(cat /etc/firewall/whitelist)
LOCALNET="192.168.1.0/24"

# everyone can see the local network
iptables -A INPUT -s $LOCALNET -d $LOCALNET -j ALLOW

# only IPs in whitelist can see the Internet
for addr in $WHITELIST
do
    iptables -A INPUT -s $addr -j ACCEPT
done

# block all other traffic from the LOCALNET
iptables -A INPUT -s $LOCALNET -j REJECT 

```

Notice I'm using the "-A" option to append rules here rather than -I above.  Just make sure you put this block of code in the right part of your ruleset.

If you're distributing IP addresses via DHCP, you can exert some control over changing them by using static assignments based on MAC addresses.  That won't stop them from creating static IPs on their machines within the local subnet, though. You might want to permit only a small subnet of the local network block.  For instance, a netmask of 255.255.255.224, or "/27" in CIDR-notation, creates a 30-host subnet; 255.255.255.240 or /28 creates a 14-host subnet.  (The first and last addresses in a subnet cannot be assigned to hosts because the first is the network address and the last is the broadcast address.)

So, for instance, if you limited everything to 192.168.1.0/27, you'd be supporting only 192.168.1.1 through 192.168.1.30 rather than 192.168.1.1-255 which you get from a full "class-C" subnet with network mask 255.255.255.0 or /24.

Another technique you can try is using another box to "eat" the otherwise unused addresses.  Hide a Linux box somewhere on the network and use interface aliasing to allow that box to represent all the unused addresses.  Let's say you decide to use 192.168.1.0/27, but don't have any machines assigned to .27 through .30.  Give the hidden box the first of these addresses and have it respond to the remaining ones like this:

```

ifconfig eth0:0 192.168.1.28
ifconfig eth0:1 192.168.1.29
ifconfig eth0:2 192.168.1.30

```

Now if someone tries switching his computer to 192.168.1.28 it will have an address conflict with the hidden Linux box.

---

