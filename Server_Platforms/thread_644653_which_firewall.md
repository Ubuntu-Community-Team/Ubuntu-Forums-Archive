---
title: "which firewall ????"
date: 2007-12-19
forum: Server Platforms
---

### Post by olddocks on 2007-12-19
ok, i have installed ubuntu on my laptop and connected to internet with pppoeconf. I am very worried that it is unsafe without firewall. 

which firewall to install for home ubuntu? i am thinking about apf-firewall but again i dont know which ports to block?

i am not a pro in ubuntu just a novice user. Any suggestions or advice much appreciated :)

Thanks :)

---

### Post by OrangeCrate on 2007-12-19
> By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up. Remember that open ports provide services that hackers can connect to, and only if they can connect to these services can they be potentially abused and exploited.

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by stmurray on 2007-12-19
I'm not sure who is saying there is no ports open by default, but it isn't true on my installation of Ubuntu (Gutsy).  It has Avahi ports open for mdns and (for some reason) it's implementation of the dhcp client keeps a listening port open as well;

udp        0      0 0.0.0.0:32768           0.0.0.0:* 5558/avahi-daemon:  
udp        0      0 0.0.0.0:68              0.0.0.0:*   4297/dhclient3      
udp        0      0 0.0.0.0:5353            0.0.0.0:*  5558/avahi-daemon:  


  These are UDP ports, so typical nmap-type scanning (TCP or SYN scans) won't show them as open, but they do accept connections, so they are potential risk.  

Also, very often you can install packages later on that open ports as well. (remote access software, samba, etc)

I would install a firewall.  firestarter has a intuitive interface.

---

### Post by stmurray on 2007-12-19
As a follow-up to my last post, i just installed Hardy Desktop as a VM.  It's a clean install.  Blow is the results of an nmap udp scan (nmap -sU) against that 

PORT     STATE         SERVICE
68/udp   open|filtered dhcpc
5353/udp open|filtered zeroconf

---

### Post by HermanAB on 2007-12-19
Install Firestarter or Shorewall.  There is nothing magical about these things, they just set up a few iptables rules.

Cheers,

Herman

---

### Post by OrangeCrate on 2007-12-19
The OP tells us that he is a novice who has just installed Ubuntu, so, the advice I gave him is sound. Here's another reference on the need of configuring a firewall on a default install:

> By default, Ubuntu includes a firewall, iptables, but by default nothing is engaged. This is reasonable as a default Ubuntu install opens zero ports to the outside world, so a firewall is redundant.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

A scan by Shields UP! will show no open ports.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

After spending time to read both provided links in my posts, to gain an understanding of Linux security, if the OP does decide to install a firewall, or at some point decides to install any server software, then he can use Firestarter to configure iptables. The Firestarter documention is here:

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by kustomjs on 2007-12-19
if you got a old pIII laying around install smoothwall because that what I use it works good.

---

### Post by stmurray on 2007-12-19
OrangeCrate,

I guess we just disagree.  I know that on the versions of Ubuntu I have installed, I have open UDP ports.  If i had a laptop that I may plug into a foreign network (hotel room, cyber cafe, etc), and/or is directly connected to the Internet, I would install a firewall.  

We do agree that firestarter is a good choice to use.

---

### Post by OrangeCrate on 2007-12-22
^,

There's really no disagreement between us. In fact, because I'm curious as to how it works, I do have a firewall engaged, but I would feel quite comfortable to not have one. Ubuntu is quite secure right out of the box.

For new users, one of the first things they need to overcome, is the Windows mindset of computer security. Things just work differently on Linux, and security is approached from a different direction.

A great overview on these issues is provided in the second link above by bodhi.zazen, and new users should definitely spend some time reading there.

> If you are coming from a windows background you are used to terms like antivirus, spyware, and firewalls. Linux is different and these are not as important. They are discussed first because these are FAQ on the forums. Unfortunately, it is sometimes difficult for new users to wade through some of the FUD (some of which is produced by anti-virus companies) ...

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by bwhite82 on 2007-12-22
> **kustomjs said:**
> if you got a old pIII laying around install smoothwall because that what I use it works good.

I second that, I just set up a smoothwall box (a computer I was going to throw in the trash) and I must say: it rawks my socks.

---

### Post by rsw686 on 2007-12-22
> **Soldierboy said:**
> I second that, I just set up a smoothwall box (a computer I was going to throw in the trash) and I must say: it rawks my socks.

You should check out pfSense as an alternative to SmoothWall. Anyway I agree that a hardware firewall is the best way to go. Although if that is not an option than yes a software firewall is a good idea.

---

### Post by asnd16 on 2007-12-23
well just did a sheilds up and recived the following . . .GRC Port Authority Report created on UTC: 2007-12-23 at 05:41:35

Results from scan of ports: 0-1055

    0 Ports Open
 1052 Ports Closed
    4 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

Ports found to be STEALTH were: 25, 135, 139, 445

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

---

### Post by bwhite82 on 2007-12-23
> **asnd16 said:**
> well just did a sheilds up and recived the following . . .GRC Port Authority Report created on UTC: 2007-12-23 at 05:41:35

Results from scan of ports: 0-1055

    0 Ports Open
 1052 Ports Closed
    4 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

Ports found to be STEALTH were: 25, 135, 139, 445

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

Ouch, what firewall are you using? Its not doing a good job for you. The fact that it was able to ping ICMP is particularly troubling -- that leaves you open to a ICMP flood attack. A good firewall will stealth ALL of your ports.

---

### Post by asnd16 on 2007-12-23
fixxed now . . I was not using any . . .never really needed to care much before but was watching the traffic today. . ..  INTERESTING . . . so I just installed firestarter

---

### Post by bwhite82 on 2007-12-23
Are you sure its fixed? I could do a remote audit on your machine (nessus) if you'd like to test it out, just need your external IP. :biggrin:

---

### Post by OrangeCrate on 2007-12-23
> **Soldierboy said:**
> **Ouch, what firewall are you using? Its not doing a good job for you**. The fact that it was able to ping ICMP is particularly troubling -- that leaves you open to a ICMP flood attack. A good firewall will stealth ALL of your ports.

The Shields UP scan results posted by asnd16 is the results you would see for a standard Ubuntu install. All ports are closed by default. A firewall has not yet been configured on his box.

To be able to shut ping off, and stealth all ports, you have to install a GUI, like Firestarter, to configure iptables, or I suppose, your suggested option of Smoothwall.

If a user chooses Firestarter, as soon as it is installed, another scan will show all ports stealthed, and to turn off pinging, the user just needs to customize the ICMP filtering rules in the preferences area.

[http://www.fs-security.com/docs/preferences.php](http://www.fs-security.com/docs/preferences.php)

In his later post, it appears that asnd16 has done that, and his new scan by Shields UP, will be the same as mine...

GRC Port Authority Report created on UTC: 2007-12-23 at 10:35:00

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

Edit:

Post your test results from Smoothwall, I'd be curious to see how it performs.

Back to the OP's question...

Linux is not Windows. By default, Windows has listening services running on many ports. By default, Ubuntu has none. So, unless you're running a mail server, the default install of Ubuntu is quite safe, and I wouldn't worry too much about configuring a firewall. But, they're fun to play with, and I suppose they do add an additional layer of security, and on a slow day, you can sit there and watch all the hits.  ;)

---

### Post by bwhite82 on 2007-12-23
> Post your test results from Smoothwall, I'd be curious to see how it performs.

Can you post a link to the scan?

---

### Post by rsw686 on 2007-12-23
> **Soldierboy said:**
> Can you post a link to the scan?

Smoothwall, pfSense, or other based firewalls will show all ports as stealth unless you have ports opened for services.

---

### Post by The Cog on 2007-12-23
Gutsy does **not** have all ports closed by default. You can see what's listening with the command:
**sudo netstat -plntu**
No need to worry about ones listening on 127.0.0.1 - they can't be got to remotely.

---

### Post by stmurray on 2007-12-23
> **OrangeCrate said:**
> .

GRC Port Authority Report created on UTC: 2007-12-23 at 10:35:00

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

)

There are two issues with the scan:
1) It only scans 1056 ports.  There are 65536 possible TCP ports
2) It doesn't scan UDP ports.  UDP scanning is problematic (as it is connectionless and there is no "handshake" to create a connection), and it appears GRC doesn't try to scan for them.  For a good overview of scanning of various types you can see [www.insecure.org](www.insecure.org) , which is the home of nmap.  

Therefore, using GRC as your only scan may be leading you into a false sense of security.  

As I said earlier in the thread, my installation of Gutsy and now Hardy each have two UDP ports open (for avahi and for the dhcp client). As far as I can tell, this is the default installation. (Am I correct in this??)

---

### Post by bwhite82 on 2007-12-23
Yeah, Ubuntu's default security is excellent, but for the security-anal (me), I wanted to go that extra step and set up a hardware firewall. I also use tor+privoxy when browsing to certain sites.

---

### Post by The Cog on 2007-12-24
I confirm that it's avahi and dhcpclient that hold the open UDP ports. I don't remember if avahi had just one open, or if it had two open though. I think it was just one, but I'm not sure. The DHCP client only opened one.

---

### Post by bryncoles on 2008-01-14
hi folks. just a quick question from a n00b (one week and counting now... yay!). 

i still have a windows security mindset, so i dont quite understand all this firewallishness thats going on with ubuntu.i have installed firestarter because it makes me feel happy. piece of mind and all that. 

what i'd like to know is, do i need to play with the settings or can i sit back and start being smug at all my windows-based friends now? also: does it automatically start when i boot up, or do i need to set it up some more?

thanking you all in advance, and loving this OS!

---

### Post by grekomind on 2008-01-14
I will Agree With HermanAB..Test these firewalls!

---

