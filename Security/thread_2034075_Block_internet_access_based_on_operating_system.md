---
title: "Block internet access based on operating system"
date: 2012-07-27
forum: Security
---

### Post by deadtom on 2012-07-27
All of the computers in our home are running kubuntu. I have myself and our teenager set up to dual boot into winxp for gaming and I don't use the winxp side for anything but gaming. No browsing, no chatting, no nothing. I just don't trust windows any more.

I can't seem to impress this upon my teenager however. Currently I have both of our kids set up so that the firewall redirects all traffic over port 80 to port 8118, where privoxy does a fairly decent job of content filtering. 

I've been trying to find some way to get either iptables or privoxy to detect, by reading the user-agent, which OS is in use and either block or redirect traffic if it finds the word 'windows' in there.

I've had no luck finding anything in privoxy that will do this, possibly someone here knows a trick to make that work. However, I was hoping that by using the --string switch in iptables, I might be able to block it that way.

Now I am pretty clueless when it comes to iptables so I have no idea if this is even possible. Here's what I've thrown together for this:

```
 -A OUTPUT -p tcp -d kids.ip.address.xxx -m string --string 'Windows' --dport 80 -j DROP
```From what I've read here, this should work although I'm not entirely sure of the syntax: [http://www.netfilter.org/documentation/HOWTO//netfilter-extensions-HOWTO-3.html#ss3.18](http://www.netfilter.org/documentation/HOWTO//netfilter-extensions-HOWTO-3.html#ss3.18)

However when I try to run it, this is the error I get:

```
iptables v1.4.4: STRING match: You must specify `--algo'
Try `iptables -h' or 'iptables --help' for more information.
```Of course, the --help gives me no clue at all here.

Any ideas here? Or is this just not possible to do this way?

Thanks!

---

### Post by Ms. Daisy on 2012-07-27
You could use the windows firewall to block outgoing to ports 80 and 443. You may have to install some other firewall (like comodo or something) on the Windows partition to achieve that.  My default XP Pro firewall would not give me fine-grained control to do this.


edit: I don't game- I guess this only works if the games don't use those ports.

---

### Post by deadtom on 2012-07-27
> **Ms. Daisy said:**
> You could use the windows firewall to block outgoing to ports 80 and 443...

Thanks but that's something he could very easily turn off himself.

---

### Post by CharlesA on 2012-07-28
parental supervision ftw?

---

### Post by deadtom on 2012-07-29
> **CharlesA said:**
> parental supervision ftw?


Yes, I could check in on him repeatedly throughout the day, peeking in via VNC while I'm at work during the day and then making hourly trips to his room to peek at his monitor, thereby violating his privacy and irritating both him and myself.

Good plan.

-or-

I could use this fascinating thing we call modern technology and eliminate the problem all together. 


...ftw...

---

### Post by Zorael on 2012-07-29
Hmm. Have you looked into the iptables **osf** module? I have never used it myself, mind.

From iptables' man page, with some slight manual formatting;
```
**osf**
    The osf module does passive operating system fingerprinting. This modules
    compares some data (Window Size, MSS, options and their order, TTL, DF,
    and others) from packets with the SYN bit set.

    [!] **--genre** string
        Match an operating system genre by using a passive fingerprinting.

    --ttl level
        Do additional TTL checks on the packet to determine the operating
        system. level can be one of the following values:

    · 0 - True IP address and fingerprint TTL comparison.
        This generally works for LANs.

    · 1 - Check if the IP header's TTL is less than the fingerprint one.
        Works for globally-routable addresses.

    · 2 - Do not compare the TTL at all.

    --log level
        Log determined genres into dmesg even if they do not match the
        desired one. level can be one of the following values:

    · 0 - Log all matched or unknown signatures

    · 1 - Log only the first one

    · 2 - Log all known matched signatures

    You may find something like this in syslog:

    Windows [2000:SP3:Windows XP Pro SP1, 2000 SP3]: 11.22.33.55:4024 ->
    11.22.33.44:139 hops=3 Linux [2.5-2.6:] : 1.2.3.4:42624 -> 1.2.3.5:22
    hops=4

    OS fingerprints are loadable using the nfnl_osf program. To load finger-
    prints from a file, use:

    **nfnl_osf -f /usr/share/xtables/pf.os**

    To remove them again,

    **nfnl_osf -f /usr/share/xtables/pf.os -d**

    The fingerprint database can be downlaoded from
    [http://www.open-bsd.org/cgi-bin/cvsweb/src/etc/pf.os](http://www.open-bsd.org/cgi-bin/cvsweb/src/etc/pf.os) .
```

I think you need to modprobe **xt_osf** before you can use it.

I gave it a brief attempt as a local rule but it seems like it can only match INPUT, PREROUTING and FORWARD hooks (and not OUTPUT for traffic generated by local processes).
```
$ sudo mkdir -p /usr/local/share/xtables
$ sudo wget 'http://www.openbsd.org/cgi-bin/cvsweb/~checkout~/src/etc/pf.os?rev=1.25;content-type=text%2Fplain' -O /usr/local/share/xtables/ps.of
$ sudo modprobe xt_osf
$ sudo nfnl_osf -f /usr/local/share/xtables/ps.of
$ sudo iptables -A FORWARD -p tcp --dport 80 -s kids.ip.address.xxx -m osf --genre Windows --ttl 1 -j DROP
```
Something like that? Maybe? I'm not really forwarding any traffic so I can't try it out.

---

### Post by CharlesA on 2012-07-29
> **deadtom said:**
> Yes, I could check in on him repeatedly throughout the day, peeking in via VNC while I'm at work during the day and then making hourly trips to his room to peek at his monitor, thereby violating his privacy and irritating both him and myself.

Good plan.

Supervision does not mean spying.

Trying to filter via user agent is a bad idea because it is easy to change the user agent being reported.

Read these:
[http://www.netfilter.org/documentation/HOWTO/netfilter-extensions-HOWTO.html#toc3.18](http://www.netfilter.org/documentation/HOWTO/netfilter-extensions-HOWTO.html#toc3.18)
[http://www.webhostingtalk.com/archive/index.php/t-1139081.html](http://www.webhostingtalk.com/archive/index.php/t-1139081.html)
[http://serverfault.com/questions/395845/limiting-and-redirect-port-access-with-useragent](http://serverfault.com/questions/395845/limiting-and-redirect-port-access-with-useragent)

Zorael: That might work, but how does it tell the fingerprint of the OS?

---

### Post by Zorael on 2012-07-29
> **CharlesA said:**
> Zorael: That might work, but how does it tell the fingerprint of the OS?
I'm far from knowledgeable in the field, so I can only shrug and guess that what's described in the first paragraph of the quoted man page section is enough to get a reasonably accurate fingerprint. I'm also unsure what a good --ttl setting would be, so I'd suggest some trial and error there (well, overall).

---

### Post by dodo3773 on 2012-07-29
> **deadtom said:**
> 
```
 -A OUTPUT -p tcp -d kids.ip.address.xxx -m string --string 'Windows' --dport 80 -j DROP
```From what I've read here, this should work although I'm not entirely sure of the syntax: [http://www.netfilter.org/documentation/HOWTO//netfilter-extensions-HOWTO-3.html#ss3.18](http://www.netfilter.org/documentation/HOWTO//netfilter-extensions-HOWTO-3.html#ss3.18)

However when I try to run it, this is the error I get:

```
iptables v1.4.4: STRING match: You must specify `--algo'
Try `iptables -h' or 'iptables --help' for more information.
```Of course, the --help gives me no clue at all here.

Any ideas here? Or is this just not possible to do this way?

Thanks!

--help will not tell you that much. If you read the man page though it tells you that --algo can be either bm or kmp. 

The way I would probably do this would be to spoof the mac address early in the boot sequence (something persistent) on the kubuntu side so that on your network they would look like 2 different computers depending on which operating system is booted. Seems like that would make this easier to me.

---

### Post by deadtom on 2012-07-29
> **dodo3773 said:**
> The way I would probably do this would be to spoof the mac address early in the boot sequence...

Now THAT is a great idea! I think that is the route I'll take with this.

I know that steam and windows update need to get out over port 80 so I can set permit rules in privoxy to allow access to those sites and block the rest. 


Thanks every body for your input!

---

