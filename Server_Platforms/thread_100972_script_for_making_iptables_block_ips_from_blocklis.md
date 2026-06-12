---
title: "script for making iptables block ips from blocklist?"
date: 2005-12-08
forum: Server Platforms
---

### Post by jamesford on 2005-12-08
ive been trying a lot of things but i cant get it working. im really just looking for a simple script that tells iptables to block the ips listed here [http://www.bluetack.co.uk/config/level1.txt](http://www.bluetack.co.uk/config/level1.txt) , after first downloading the list

ive no idea how to get it to work

also useful would be a script that downloads the same file ([http://www.bluetack.co.uk/config/level1.txt](http://www.bluetack.co.uk/config/level1.txt)) and converts it to ipfilter.dat format in other words from format 
ads.herald-sun.com ads:4.18.162.102-4.18.162.102
to 
4.0.25.146      - 4.0.25.148      , 0 , s0-0.ciscoseattle.bbnplanet.net (yeah i iknow th eips are different it was just an example)

---

### Post by LordHunter317 on 2005-12-08
Why in the world would you want to essentially block the entire Internet?

Some more details please, as IPtables is going to choke doing O(n) lookups on that mess without special modules, and there's bound to be abetter way no matter what.

---

### Post by tomchuk on 2005-12-11
As, LordHunter said, this won't work:
```

#!/bin/sh

wget http://dialspace.dial.pipex.com/town/pipexdsl/s/ashu56/bluetack/level1.txt
for RANGE in `awk -F":" '{sub(/\r$/,""); print $NF}' level1.txt`
do
    /sbin/iptables -I INPUT -m iprange --src-range ${RANGE} -j DROP
done

```

But this will print it out in the format you specified, with a side-effect of replacing ':' in the text portion with spaces.
```

awk -F":" '{sub(/\r$/,"");$NF sub(/-/," - "); printf ("%s , 0 , ", $NF); for(i=1; i<NF; i++) printf("%s ", $i); printf("\n")}' level1.txt

```

---

### Post by J.C. Denton on 2005-12-11
See if this produces what you want:
```
perl -ne 'if (($_ =~ m/^[^:]+?:([0-9\.\-]+)/) && ($_ !~ m/NET/)) { print "iptables -A INPUT -m iprange --src-range $1\n"; }' level1.txt | less
```
I didn't account for the stuff with NET in the line, but that could be easily added.  You may want to consider blocking supernets at this point, since this is somewhat inefficient.

[quote=LordHunter317]Why in the world would you want to essentially block the entire Internet?[/quote]Maybe he's paranoid ;)?

---

### Post by lcg on 2005-12-11
[QUOTE=J.C. Denton]Maybe he's paranoid ;)?[/QUOTE]
Then it would still be easier to just pull the network cable, wouldn't it? ;)

Lars

---

### Post by J.C. Denton on 2005-12-11
[QUOTE=lcg]Then it would still be easier to just pull the network cable, wouldn't it? ;)[/QUOTE]Not particularly.  I suspect what he's trying to do is "block everyone, with a few exceptions here and there."  In which case, the method used above is painfully inefficient.

---

### Post by lcg on 2005-12-12
[QUOTE=J.C. Denton]I suspect what he's trying to do is "block everyone, with a few exceptions here and there."  In which case, the method used above is painfully inefficient.[/QUOTE]
Isn't that how one usually designs a port filter?

You specify some kind of policy about what is allowed, implement this via netfilter/iptables and everything which is not explicitly allowed is dropped or better rejected at the end of your table ... And if something does not work, have a look at the log files and think about revising the policy.

At least that's how my firewall is implemented. Just my 0,02 &#8364;.

Lars

---

### Post by LordHunter317 on 2005-12-12
[QUOTE=lcg]Isn't that how one usually designs a port filter?[/quote]If you're excluding that many hosts, then no.  You switch to whitelisting.

Really, you should be whitelisting *anyway*, and only using a blacklist when you have traffic to a specific port you wish to deny to a small set of hosts.

---

### Post by lcg on 2005-12-16
[QUOTE=LordHunter317]If you're excluding that many hosts, then no.  You switch to whitelisting.

Really, you should be whitelisting *anyway*, and only using a blacklist when you have traffic to a specific port you wish to deny to a small set of hosts.[/QUOTE]
And that's exactly what I wrote. You define a policy about what is allowed and everything else is denied at the end of the table.

Lars

---

### Post by bionnaki on 2005-12-16
why not just install [peerguardian](http://www.ubuntuforums.org/showthread.php?t=95793&highlight=peerguardian) ?

---

### Post by Nutterpc on 2006-04-26
As far as I'm aware, there isn't an easy way to be able to get an iptables firewall script to automatically update with rules, apart from a program like snort, which has that functionality

Its one of the things I'm looking at trying to do for the iptables firewall which I've designed :)

---

