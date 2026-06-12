---
title: "Firewall?"
date: 2013-06-26
forum: Security
---

### Post by argvar on 2013-06-26
Windows had a firewall, but was plagued with viruses anyway.

Now that I have installed Ubuntu, should I consider some sort of firewall?

My router does have a firewall though!

---

### Post by Lars Noodén on 2013-06-26
There's not much need for a firewall, it is a technology that is overestimated.  But here is some reading:

[https://help.ubuntu.com/community/DoINeedAFirewall](https://help.ubuntu.com/community/DoINeedAFirewall)

If you still want one, you can turn on UFW.  It's there by default, but not turned on.  If you want a GUI for it then there is GUFW in the repositories which can be added with a few clicks.

---

### Post by Hungry Man on 2013-06-26
Firewalls reduce attack surface by limiting exposure of services that may accidentally be made public. If you are the only system behind your router it's just about 100% useless. If there is another system, i tcan protect you from a compromised system on there. If you are not behind a router it may be a good idea to use one.

---

### Post by argvar on 2013-06-26
THanks.

---

### Post by HermanAB on 2013-06-27
Linux pretty much *is* a firewall.  The default install doesn't need any special netfilter rules.

---

### Post by Blitzkriegz on 2013-06-29
> **HermanAB said:**
> Linux pretty much *is* a firewall.  The default install doesn't need any special netfilter rules.
In what way is Linux a firewall? If you connect your computer directly to the internet without a router than use a firewall.

---

### Post by CharlesA on 2013-06-29
> **Blitzkriegz said:**
> In what way is Linux a firewall? If you connect your computer directly to the internet without a router than use a firewall.

Ubuntu doesn't have any listening services by default, so there is nothing to access from the outside.

---

### Post by SeijiSensei on 2013-06-29
> **argvar said:**
> Windows had a firewall, but was plagued with viruses anyway.

Firewalls won't protect you from downloading malware.  However there are few such threats for Linux because of its small market share, its intrinsically better security (certainly compared to XP and earlier), and a more informed user population.

Not following links to unknown sites or in email helps a lot.  Looking at the destination of links is also useful.  Something that claims to be taking you to a bank's website but has a URL that points to who-knows-where is a good indication.  

The biggest threat to most peoples' computers is the person sitting in the chair.

---

### Post by uRock on 2013-06-29
If it makes you feel safe, then you may enable to UFW firewall by opening a terminal and pasting the following command ```
sudo ufw enable
``````
*****@*****:~$ sudo ufw enable
[sudo] password for *****: 
Firewall is active and enabled on system startup
*****@*****:~$ 

```If you find that you need to open ports for whatever reason, then you may want to install GUFW, which is a GUI for UFW.

Go here to learn more about UFW [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by HermanAB on 2013-07-01
Unfortunately a firewall is not a magic unicorn that can protect you against evil spirits.  The Linux network stack is pretty well debugged and doesn't need a firewall.  Most 'hardware' firewalls run Linux.  If Linux needed a firewall, then you would need to put a firewall in front of every firewall, recursively.  That will be very good for a hardware vendor, but not so good for your wallet.

If you need to protect a bunch of unmanageable Windows machines on a LAN, then set up a firewall on a Linux gateway.  If your Linux machine is the only one, then don't bother.

---

### Post by Soul-Sing on 2013-07-01
> **HermanAB said:**
> Unfortunately a firewall is not a magic unicorn that can protect you against evil spirits.  The Linux network stack is pretty well debugged and doesn't need a firewall.  Most 'hardware' firewalls run Linux.  If Linux needed a firewall, then you would need to put a firewall in front of every firewall, recursively.  That will be very good for a hardware vendor, but not so good for your wallet.

If you need to protect a bunch of unmanageable Windows machines on a LAN, then set up a firewall on a Linux gateway.  If your Linux machine is the only one, then don't bother.

An old pentium with pfsense is enough.

---

### Post by HarmonicaGuy on 2013-07-03
Just one question, 
I have udp ports in the "listing reports";
udp 4404 avahi-daemon 
udp 5353 avahi-daemon  
udp 68 dhclient
 udp6 33730 avahi-daemon
 udp6 5353 avahi-daemon.

I added udp 5353/udp as "deny in" to the gufw. Is this why udp 5353 and the udp6 5353 avahi-daemon are both showing in green?

Is this okay?

---

### Post by uRock on 2013-07-03
> **HarmonicaGuy said:**
> Just one question, 
I have udp ports in the "listing reports";
udp 4404 avahi-daemon 
udp 5353 avahi-daemon  
udp 68 dhclient
 udp6 33730 avahi-daemon
 udp6 5353 avahi-daemon.

I added udp 5353/udp as "deny in" to the gufw. Is this why udp 5353 and the udp6 5353 avahi-daemon are both showing in green?

Is this okay?

Yes. Green means deny and red means allow.

---

### Post by Soul-Sing on 2013-07-04
you can disable avahi.

---

### Post by HarmonicaGuy on 2013-07-06
How would I disable avahi? And should I?

---

### Post by Soul-Sing on 2013-07-06
gksu gedit /etc/default/avahi-daemon

add this:

AVAHI_DAEMON_DETECT_LOCAL=0

---

### Post by kleenex on 2013-07-07
Hi. Of course everything written above is true. But you can use e.g. simple iptables settings: [http://ubuntuforums.org/showthread.php?t=2144451&p=12652474#post12652474](http://ubuntuforums.org/showthread.php?t=2144451&p=12652474#post12652474)

---

### Post by HarmonicaGuy on 2013-07-08
Do I just copy and paste into the termimal even though I already set the rules listed below;

                        51413/tcp                  ALLOW       Anywhere
 

 51413/udp                 DENY        Anywhere
 

 5353/udp                   DENY        Anywhere
 

 5900/tcp                    DENY        Anywhere
 

 22                              DENY        Anywhere
 

 25/tcp                        DENY        Anywhere
 

 135,139,445/tcp        DENY        Anywhere
 

 137,138/udp              DENY        Anywhere
 

 110                            DENY        Anywhere
 

 2049                          DENY        Anywhere
 

 143                            DENY        Anywhere

---

