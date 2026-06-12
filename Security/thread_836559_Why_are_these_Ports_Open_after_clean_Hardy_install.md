---
title: "Why are these Ports Open after clean Hardy install and How can I close them???"
date: 2008-06-21
forum: Security
---

### Post by Mark.H on 2008-06-21
Hey all

I'm a relative newbie to Ubuntu, and I am having a real issue with something!

That something is various open Ports.

I have ran a port scan on my routers IP address and my PC's IP address and they both show identical open ports.
This confuses me a little because I thought Ubuntu closed all ports when it is first installed???

I am using the new Ubuntu Distro' Hardy 8.04 and also Firestarter as my Firewall.

I have spent ages trawling through various search engines and forums looking for a solution to why these ports are open and HOW can I close them. With absolutely NO success!!

The Router I am using is a Sagem F@st 2504 Sky one and the open ports which are giving me such a headache are as follows:

Port  /   Protocol
 
21       ftp
23       telnet
53       domain
80       www
1863     msnp
1864     unknown
4443     unknown
5190     aol
5431     unknown
5566     unknown
30005    unknown

I hope there is somebody here who can help me make sense of this and possibly give me a solution??

Cheers for now..

Mark Hogan

---

### Post by Pjotr123 on 2008-06-21
This is why ports are open by default:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

Try ufw for a change, instead of firestarter.

---

### Post by ramjet_1953 on 2008-06-21
Don't forget that when you are behind a router, sites like Shields-Up report the port status of your router's firmware firewall, not the configuration of iptables. 

Regards,
Roger :cool:

---

### Post by ddales on 2008-06-22
There are literally hundreds of ports that will be open by default even with a new installation.  This is by design and many of them are needed in order for the system to run properly.

However, just because a port is open or available does not necessarily mean that it's usable.

To close ports that you don't want to have open comment them out of your /etc/services file and reboot.

Just be very careful which ports you close or your system may produce unwanted behavior or stop working all together.

---

### Post by Mark.H on 2008-06-22
Hey all thank's for all your helpfull reply's...

especialy ddales I think that may just be the answer i have been searching for!!!

you said 'To close ports that you don't want to have open comment them out of your /etc/services file and reboot'...

This is interesting.

So my next step is to look into my /etc/services file??? and comment them out!

How do I look into my /etc/services file?? and then comment the desired points out?

where would be a good place to start learning about the above??

Cheers again

Mark..

---

### Post by Jonne on 2008-06-22
I wouldn't recommend messing with system files, but this is how you do it:
open a terminal
type 'sudo gedit /etc/services'

edit the file ('commenting out' means putting a # in front of the line in question)

Be careful! Make sure you understand what any service does before you disable it, or you'll break something.

---

### Post by fsmithred on 2008-06-22
You shouldn't need to mess with /etc/services, and I'd recommend against it, unless you have specific instructions for a specific purpose. What you first need to do is configure your router so that you don't have any open ports that you don't need. 

But before you even do that, consider how you obtained your information. If you scanned your router from a computer on your local network, then what is showing as open might not be the same as what shows as open from the outside. If you figure out how to close all of these, I suspect your router will stop working.

Go to grc.com, follow the links to Shields Up, and do a port scan there. Then you'll know what's open to the outside on your router. If you want to see what's open on ubuntu (hint: nothing is open by default) then you need to either disable the firewall in your router or connect the computer directly to the modem without the router and scan again, or scan it from another computer on your local network. If you don't like the results, install a firewall program.

---

### Post by ddales on 2008-06-22
If you want to learn more about securing or "hardening" your system, this is a good place to start.  Especially chapters 4 and 5.  But like I said, as well as with the other comments, be careful or you may screw up your system.

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

As with anything else, make sure you do the appropriate preparation to make sure you know exactly what you're doing before undertaking any such changes.

---

### Post by Mark.H on 2008-07-03
Hey all...

Hi my name is mark and I am having a real dilemma with something!!
I have posted threads on Launchpad and received replies, but being a bit of a novice I am still a little unsure of how to rectify a problem I've had since I made a clean install of the new Ubuntu 8.04 Hardy Distro'.

 I have always been concerned with PC and On-Line security and this is the main reason I migrated to using Ubuntu!.

After the clean install I decided to run a couple of security checks on my firewall. The firewall i use is Firestarter. 

I ran two separate port scans on my own system. I used GRC's ShieldUp and Gnome-Nettool to scan both my PC IP address and my routers IP address.
The output of the two scans were exactly the same!.
It showed that I indeed have open ports, 
The output that ShieldsUp gave me was:

21 ftp
23 telnet
53 domain
80 www
1863 msnp
1864 unknown
4443 unknown
5190 aol
5431 unknown
5566 unknown
30005 unknown

As you can see the ports which read unknown are not even stealthed.
This is really concerning me, and I would once and for all like to sort this out...

Am i right to be so concerned??
 i wrote port 30005 into google and one site said that this port is used, or is a Backdoor Trojan.

My router is a Sagem 2504 SKY router. and I can find no manual in how I can close the problematic PORTS!!.

Is there anyone here who can possibly Help me.  

 It is really concerning me!!

---

### Post by Mark.H on 2008-07-03
Hi all..

 I have asked a similar question to this a little while ago, and I did recieve some helpfull answers but I never did get the problem I have completely sorted.

I am going to have another shot at getting the solution I am looking for. So i will add a bit more detail to my problem...

I have a Sagem f@st 2504 SKY router and I am using Ubuntu 8.04 Hardy as my O/S.
I have always been a little concerned with the pitfalls of PC and On-Line security which is one of the main reasons I moved to Ubuntu.
So after I upgraded to the new 8.04 distro'. I decided to run a couple of security checks on my new installation including a Port scan using GRC's ShieldsUp and Gnome-Nettools Network tools to run a port scan on my routers IP address and my PC's IP address.

 The two separate port scans gave me the same output,
That I do indeed have some open ports.
Some are stealthed. but Six ports are indeed completely OPEN!!

 The ports which I am concerned about are listed below:

21 ftp
23 telnet
53 domain
80 www
1863 msnp
1864 unknown
4443 unknown
5190 aol
5431 unknown
5566 unknown
30005 unknown

There are 6 ports that are completely OPEN and are NOT even Stealth.

The Six Ports are: 1863 , 1864 , 4443 , 5190 , 5566 , and 30005

 Am I right to be concerned about this??

 I hope maybe there is someone clued up about this. Who might be able to shed a little light on my issue??

 Kind regards.

  Mark...

---

### Post by kevdog on 2008-07-03
By default on your Linux box, all ports are open, however if there is no listening process on the port there is no security risk.  Just an FYI.  If still super paranoid -- although for no reason -- use IPtables to set the default policy of your INPUT ports to DROP, so then your ports will appear stealthed.

The command to do this is easy:

sudo iptables -P INPUT DROP 

After doing this all incoming ports are closed and it will appear to be stealthed or filtered.  Its overkill however.

---

### Post by bryncoles on 2008-07-03
dunno anything about those ports, but i gather that by default no ports are supposed to be open in ubuntu. so if they're open now, it mighht mean you have installed some sort of server program?

anyway, 

[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

should help you configure the built in firewall (ufw) to close those ports again. also typing 'man ufw' into the terminal should get you some rather technical-jargon-esque info about what ufw is. 

hopefully someone more useful (knowledgeable) than me will see this thread and provide more useful tips!

*edit*

oh yeah, for future reference, try and give your threads specific titles. it'll help people on the forums spot problems they can help with, and your issues will be resolved quicker! something like 'why are these ports open?' would be good for this one!

lets hope the problem can be solved quickly ;-)

---

### Post by Mark.H on 2008-07-03
Hey Kevdog..

Thanks for your reply..

I think that is the answer i was looking for.

Can I ask you what FYI means and why do you think the command is overkill?

Where do you suggest is a good place for me to learn a bit more about your solution??

Cheers again Kevdog??

---

### Post by jimv on 2008-07-03
Well, those ports aren't going to be open if you didn't have something set up using them.  So are you running apache, an ssh server, an ftp server, etc?

Also, if you check your router, are those ports forwarded through the router?

I just ran both those checks on my system at home and nothing was open (at least not on the standard ports :)

EDIT:

Here's some free research:
Port 1863 - MSN Messenger
Port 1864 - MSN Messenger
Port 4443 - Yahoo File Sharing and Transfers
Port 5190 - AOL Instant Messenger
Port 5566 - Seems like something randomly generated
Port 30005 - Saw some references on Google to video game servers or Windows trojans.

I wonder if perhaps you have PnP enabled on your router...that would automatically open a port on the router when your computer requests it.  I keep it turned off on my router so I know what ports are open.

---

### Post by cdenley on 2008-07-03
> **Mark.H said:**
> Hey Kevdog..

Thanks for your reply..

I think that is the answer i was looking for.

Can I ask you what FYI means and why do you think the command is overkill?

Where do you suggest is a good place for me to learn a bit more about your solution??

Cheers again Kevdog??

FYI = for your information

That command is overkill because I'm pretty sure it will block ALL incoming traffic, including traffic you initiated such as web browsing. You're probably banging your head against the wall right now trying to figure out how to get this page to load.
```

sudo iptables -P INPUT ACCEPT

```

What is your IP address? Do you have a router?
```

ifconfig

```
I'm guessing the port scanning service you used is picking up another server on your LAN. Either that, or it warns you that connections were rejected instead of dropped. As long as you have no servers listening for connections on those ports, you're fine.
```

netstat -lnt

```

---

### Post by Mark.H on 2008-07-03
Hey again Kevdog...

Funnily enough my browsers working fine...

after running your first command suggestion, I ran a port scan on my pc ip address using the two port scanners gnome-nettool and shields up.

The gnome-nettool scan did not show any open ports after running the first command.

But the second scanner I used, ShieldsUp STILL showed the same open ports even when I scan my PC address, The same IP address which Gnome-nettol s NO longer shows OPEN...

I must admit i'm still confused by this...

The output after running the ifconfig command is:

eth0      Link encap:Ethernet  HWaddr 00:50:04:a1:b2:e3  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fea1:b2e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3096066 (2.9 MB)  TX bytes:502182 (490.4 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83244 (81.2 KB)  TX bytes:83244 (81.2 KB)

I havr not got a clue how to read this output. (Hoping you can clarify it for me???)..

Cheers Mark...

Anyway,

---

### Post by cdenley on 2008-07-03
I guess when that iptables rule is used in conjunction with ufw's, it doesn't filter established connections. I can tell from your IP address (192.168.0.2) that you are using a router. With a typical router configuration, it would be acting as a firewall. Is it configured to forward ports to another server? I would use nmap to scan your computer from another computer in your LAN.
```

nmap 192.168.0.2

```
Then I would find your WAN IP address
```

wget -q -O - http://www.whatismyip.org/ && echo

```
and scan your router (preferably from outside your LAN)
```

nmap [wan ip]

```

---

### Post by Mark.H on 2008-07-03
No I have not installed antyhing like that.

I ran the two port scans as soon as Made a clean install Ubuntu 8.04.
I ran a suugested command and got this output:
the command was: sudo netstat -tupl


Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:ipp           *:*                     LISTEN      4918/cupsd      
tcp        0      0 localhost:smtp          *:*                     LISTEN      5173/exim4      
udp        0      0 *:50112                 *:*                                 4777/avahi-daemon: 
udp        0      0 *:bootpc                *:*                                 5486/dhclient   
udp        0      0 *:mdns                  *:*                                 4777/avahi-daemon: 
mark@mark-desktop:~$ sudo netstat -l -t
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:smtp          *:*     

i have NO clue waht so ever what to make of this?
Can anyone shed a little light??

---

### Post by Shazaam on 2008-07-03
Sounds like Sheilds Up! is seeing open ports on your ROUTER/modem, not your pc. Firestarter/iptables has no effect on a router/modem. Secure your router/modem and you will be fine.

---

### Post by steveneddy on 2008-07-03
I agree. My router is first in line for defense of my home network.

I always do everything I can do to secure my router and everything always works out OK.

---

### Post by Dr Small on 2008-07-03
I always skip firewall rules on the local lan, since I have a router / firewall at the gateway. Saves alot of time and hassle to get the computers on the network to talk to each other :D

---

### Post by kevdog on 2008-07-03
Where is darkghost?

---

### Post by Dr Small on 2008-07-03
> **kevdog said:**
> Where is darkghost?
The hostname of my computer :D
```
[drsmall@darkghost ~]$
```

---

### Post by kevdog on 2008-07-03
darkghost -- in reference to something? or just made up?

---

### Post by Mark.H on 2008-07-04
Hey al. Thank's again for all your replies..

 Things are a little clearer now..

This is where I am struggling to get a clear insight into how to configure my Router.
I have a Sagem f@st 2504 SKY router and (Not through lack of searching)
I can not find any manuals etc to clearly state how to configure the routers firewall. To close the ports which do not need to be open...
It's getting quite annoying..

Has anybody body had a similar problem??

and how did you rectify it?? 

Cheers

Mark...

---

### Post by Dr Small on 2008-07-04
> **Mark.H said:**
> Hey al. Thank's again for all your replies..

 Things are a little clearer now..

This is where I am struggling to get a clear insight into how to configure my Router.
I have a Sagem f@st 2504 SKY router and (Not through lack of searching)
I can not find any manuals etc to clearly state how to configure the routers firewall. To close the ports which do not need to be open...
It's getting quite annoying..

Has anybody body had a similar problem??

and how did you rectify it?? 

Cheers

Mark...
Basically, here is a guide how to open ports, for your router:
[http://www.portforward.com/english/routers/port_forwarding/Sagem/Fast2504/HTTP.htm](http://www.portforward.com/english/routers/port_forwarding/Sagem/Fast2504/HTTP.htm)

And a complete list for everything:
[http://www.portforward.com/english/routers/port_forwarding/Sagem/Fast2504/Fast2504index.htm](http://www.portforward.com/english/routers/port_forwarding/Sagem/Fast2504/Fast2504index.htm)

It shouldn't be too hard to figure out how to close ports from there.


@kevdog:
darkghost was the hostname I created for my computer after my Dad bought me a new, shiny, black, Antec Sonata III Case. I couldn't keep the old name "selftech" any longer, so I had to find something more suitable that matched the look of my system :D

---

### Post by brian_p on 2008-07-04
> **Mark.H said:**
> Hey all...

Hi my name is mark and I am having a real dilemma with something!!

[Snip]

> I ran two separate port scans on my own system. I used GRC's ShieldUp and Gnome-Nettool to scan both my PC IP address and my routers IP address.

You do understand GRC looks at your router from the outside (the internet) and Gnome Nettool looks it from the inside (your network)? The results can be (and often are) quite different.

> The output of the two scans were exactly the same!.

I'm having a little difficulty accepting this but am prepared to be corrected.

> It showed that I indeed have open ports, 
The output that ShieldsUp gave me was:

21 ftp
23 telnet
53 domain
80 www
1863 msnp
1864 unknown
4443 unknown
5190 aol
5431 unknown
5566 unknown
30005 unknown

As you can see the ports which read unknown are not even stealthed.
This is really concerning me, and I would once and for all like to sort this out...

My puzzlement is how you got those data from GRC. It will only custom scan blocks of 64 ports at a time so to get up to port 30005 in a methodical way would mean about 500 inputs. Is that what you did?

GRC has a User Specified Custom Port Probe. What do you get for each port status when you put those port numbers in? OPEN or CLOSED?

---

### Post by brian_p on 2008-07-04
> **ddales said:**
> To close ports that you don't want to have open comment them out of your /etc/services file and reboot.

/etc/services is consulted by inetd and /etc/inetd.conf is an empty file on a default Ubuntu install. In fact, looking in /etc/init.d it does not appear the inetd daemon is even started. What is the basis for your offering this advice?

---

### Post by cjv8888 on 2008-07-05
After reading the above, I went to GRC and did a port scan.  I also have a fairly new install of ubuntu Hardy.
The result showed that all ports are stealthed.
I have a wireless router where a few ports are forwarded for bittorrent.
However these are in the 50 thousands and GRC did not pick it up.

---

### Post by Mark.H on 2008-07-05
Hey..

I have posted a couple of threads before and had some helpfull replys, but i am a relatively newcomer to ubuntu and i am looking to know how i can close afew ports i don't think should be open..

I am using ubuntu 8.04 and Firestarter and UFW.
Is it a bad idea to run two firewalls?

and if I am running two firewall. If I change rules in one firewall. Would the other firewall cancel them out. Because it's rules are unchanged?
Or do I need to change rules in both firewall?

I have mentioned this before, but I made a clean install and ran a port scan on my own system using Gnome-nettols and shieldsUP.
This pointed out that i have some open ports and six of them are not even staealthed!!

I now know that it is my router that is the problem. and I have searched high and low for a relatively straight forward instructions or even a manual for my router which is a Sagem f@st 2504 SKY.
 SKY being that it is the broadband provider SKY who pipe my internet and satelitte TV etc. Because it is sky who supply my router it has its own firmware version. Not the original Sagem firmware version, and this is why I can't seem to get a manual for my router because SKY don't want customers flashing the router to the original firmware version. this would void the terms and conditions blah blah blah.

The troubling ports are 

21 ftp
23 telnet
53 domain
80 www
1863 msnp
1864 unknown
4443 unknown
5190 aol
5431 unknown
5566 unknown
30005 unknown

I do know that not all ports need to be closed.
It is port number 1863, 1864, 4443, 5190, 5566, 30005.
That are concerning me because these are showed as open and not even stealthed.

Is there any body who can explain to me in laymans terms how to close the desired ports through my routers Firewall??

Thank's all Mark..

---

### Post by brian_p on 2008-07-05
> **Mark.H said:**
> Hey..

I have posted a couple of threads before and had some helpfull replys, . . . . 

You have indeed, Mark, and it is becoming a little confusing when you use more than one forum to seek help for the same problem. At present there is a thread started by you in the Security forum where a post of mine asking some questions is as yet unanswered.

> The troubling ports are 

21 ftp
23 telnet
53 domain
80 www
1863 msnp
1864 unknown
4443 unknown
5190 aol
5431 unknown
5566 unknown
30005 unknown

I'll be blunt: How did you obtain that list from GRC? Would you say exactly and in detail what you did?

---

### Post by Mark.H on 2008-07-05
Thak's for bringing that to my attention!

I thought if i post it in different forums it would get seen by more people thus get more replys.
I will no longer do that..

OK back to you last reply.

The below was done after a completely clean install of Ubuntu 8.04 Hardy...

I used Gnome nettools network tools port scan originally on my routers IP address AND my PC IP adress.
This gave me the same output:
which was:

21 ftp
23 telnet
53 domain
80 www
1863 msnp
1864 unknown
4443 unknown
5190 aol
5431 unknown
5566 unknown
30005 unknown

so my next step was to run a port scan using ShieldsUp which said I had true stealth an everything was hidden.
this at first concerned me because my original scan showed that there was indeed open ports.

the next step was to scan the above port numbers that showed in my Gnome-Nettols scan. Using shieldsUp user specified port scan on the above prot numbers.
This gave the same output as nettols port scan!!.

this i dont mind admitting really confused me...

After using this forum I have learned that I need to configure my Roters Firewall. But I can not find any help on this... Not even a manual for my router..

mark...

But after posting a threadon this forum I found that shields up scans my router ip address

---

### Post by Mark.H on 2008-07-05
if this helps, this is the text output from the shieldup user specified port scan results: 

GRC Port Authority Report created on UTC: 2008-07-05 at 15:07:20

Results from scan of ports: 21, 23, 53, 80, 1863, 1864, 4443, 
                            5190, 5431, 5566, 30005

    6 Ports Open
    0 Ports Closed
    5 Ports Stealth
---------------------
   11 Ports Tested

NO PORTS were found to be CLOSED.

Ports found to be STEALTH were: 21, 23, 53, 80, 5431

Other than what is listed above, all ports are OPEN.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

Cheers

Mark...

---

### Post by brian_p on 2008-07-05
> **Mark.H said:**
> The below was done after a completely clean install of Ubuntu 8.04 Hardy...

Ok.

> I used Gnome nettools network tools port scan originally on my routers IP address AND my PC IP adress.
This gave me the same output: . . . .

I assure you this is impossible from a completely clean install, but we will return to it at a later time. What were the two addresses? [B]If the PC IP address does not start 192 do not post it here.
[/B]


>  . . . . which was:

21 ftp
23 telnet
53 domain
80 www
1863 msnp
1864 unknown
4443 unknown
5190 aol
5431 unknown
5566 unknown
30005 unknown

For the router these data are fine. The open ports can be seen from the INSIDE. They are inaccessible from the internet. Do not worry about them.

Repeating myself, none of these ports can be open on your PC.

> so my next step was to run a port scan using ShieldsUp which said I had true stealth an everything was hidden.
this at first concerned me because my original scan showed that there was indeed open ports.

the next step was to scan the above port numbers that showed in my Gnome-Nettols scan. Using shieldsUp user specified port scan on the above prot numbers.
This gave the same output as nettols port scan!!.

this i dont mind admitting really confused me...

It would confuse anyone! Would you please go here:

[http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

Put the port numbers 21, 23, 53 etc one by one into 'Scan a single port number' and report what you get. Make a note of the IP number while you are at it.

---

### Post by lswb on 2008-07-05
First off I have to say that IMHO you are needlessly worried. With that out of the way, I would also strongly advise you to run ONLY ONE firewall and figure out how to configure it the way you like. Remember the firewall on you computer will not affect your router.

Since you are connecting through a router, using the GRC site for a port scan is going to show the ports that your ROUTER exposes to the internet. The router would have to be configured to pass any communications on those ports through to the computer. 

Most consumer/residential type router configurations nowadays are accessed through a web browser by pointing it at a specific ip address. Often the factory default is 192.168.1.1 or something close to this. It should be relatively easy to find out by googling your router make & model and a few keywords like "configuration" or "setup". I doubt that the ISP would change the default before shipping the router, but you never know. You can also try running the command "route" in a terminal, it will give some output. Look for a line with an ip address and a * in the column below Gateway, and try putting that ip address in your web browser address bar.

---

### Post by Mark.H on 2008-07-05
Hi brian_p.

I have done as asked.
Do i need to check all the available boxes before doing the scans???

---

### Post by brian_p on 2008-07-05
> **Mark.H said:**
> Hi brian_p.

I have done as asked.
Do i need to check all the available boxes before doing the scans???

No. Put 21 in the 'Scan a single port number:' box and click 'Scan Port' next to it. Then 23, 53 and so on.

---

### Post by Mark.H on 2008-07-05
OK done the asked for scans (without checking all the extra option boxes_
And the scan is for my PC IP address which starts with the number 90....

This is the output i got:
 For Ports

21  isn't responding on port 21 (ftp).
23 isn't responding on port 23 (telnet).
53  isn't responding on port 53 (domain).
80  isn't responding on port 80 (http).

1863 is responding on port 1863 (msnp). !!!!
1864 is responding on port 1864 (paradym-31port).!!!
4443 is responding on port 4443 (pharos).!!!
5190 is responding on port 5190 (aol).

5431 isn't responding on port 5431 (park-agent).

5566 is responding on port 5566 (udpplus).!!!
30005 is responding on port 30005 ().!!!

this is the scan on my pc's ip address and definately not my routers.

I would also like to add that i have actually cleanly installed Ubuntu 8.04 hardy Twice using two separate install disks
One was posted from Shipit and is an original disk.
The second was a downloaded .ISO from Ubuntu itself.
They both stilll gave the same scan results after using the two port scanners I mentioned in earlier posts.

Thank's for your help so far...
I feel like im actually getting somewhere with this!!

---

### Post by bodhi.zazen on 2008-07-05
> **Mark.H said:**
> Hey all

I'm a relative newbie to Ubuntu, and I am having a real issue with something!

That something is various open Ports.

I have ran a port scan on my routers IP address and my PC's IP address and they both show identical open ports.
This confuses me a little because I thought Ubuntu closed all ports when it is first installed???

I am using the new Ubuntu Distro' Hardy 8.04 and also Firestarter as my Firewall.

I have spent ages trawling through various search engines and forums looking for a solution to why these ports are open and HOW can I close them. With absolutely NO success!!

The Router I am using is a Sagem F@st 2504 Sky one and the open ports which are giving me such a headache are as follows:

Port  /   Protocol
 
21       ftp
23       telnet
53       domain
80       www
1863     msnp
1864     unknown
4443     unknown
5190     aol
5431     unknown
5566     unknown
30005    unknown

I hope there is somebody here who can help me make sense of this and possibly give me a solution??

Cheers for now..

Mark Hogan

Mark H:

Please do not start multiple threads on the same topic. I merged 4 threads all asking the same question. Multiple threads cause confusion and duplication of effort.

First, no you should not run both UFW and firestarter at the same time.

Let me start at the beginning :

See this thread for Security :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

OK, now for firewalls :

What is you expect a firewall to do for you anyway ?

The firewall in Linux is IP Tables. Everything else, firestarter UFW, are configuration tools.

Firstarter : Firestarter is "OK" but it is out dated. If you use firestarter, you should configure your firewall then CLOSE FIRESTARTER. You do not need firestarter to be running for your firewall to be active. Firestarter runs as root and is a security risk.

UFW : UFW is IMO a better tool. 

See : [http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)
[uhelp]8.04/serverguide/C/firewall.html[/uhelp]
[[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")

==========

To answer your question :

A default installation on Ubuntu has no servers installed so IPTables is set to be permissive or as you say "open". There is nothing wrong with this.

If you install a sever you need to learn to secure it and a firewall may be  apart of your security.

If you want to block all traffic use ufw :

```
sudo ufw --help
```

Now close firestarter and do the following :

```
sudo ufw disable
sudo iptables -F #This command removea all rules

sudo ufw enable
sudo ufw default deny
```

Now all connections, all 65,000 +, are blocked.

To open a port (ie 80):

```
sudo ufw allow http
```

and on.

To list your firewall rules :

```
sudo iptables -L
```

For more information on iptables :

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables)

---

### Post by brian_p on 2008-07-05
> **Mark.H said:**
> OK done the asked for scans (without checking all the extra option boxes_
And the scan is for my PC IP address which starts with the number 90....

I'd be surprised if your PC's IP began with 90. The majority of ISPs hand out one IP and it has to go the router (to the part it facing the internet).

For your PC's IP do

```
/sbin/ifconfig
```

in a terminal. What is the number immediately after 'inet addr:'


> This is the output i got:
 For Ports

21  isn't responding on port 21 (ftp).
23 isn't responding on port 23 (telnet).
53  isn't responding on port 53 (domain).
80  isn't responding on port 80 (http).

1863 is responding on port 1863 (msnp). !!!!
1864 is responding on port 1864 (paradym-31port).!!!
4443 is responding on port 4443 (pharos).!!!
5190 is responding on port 5190 (aol).

5431 isn't responding on port 5431 (park-agent).

5566 is responding on port 5566 (udpplus).!!!
30005 is responding on port 30005 ().!!!

this is the scan on my pc's ip address and definately not my routers.

We'll wait and see what inet addr: says!

You have six ports responding on the router but as lswb implies any communication from the internet will stop there and not get through to your computer so there is no danger. I am not familiar with what they do or why they are there. It could be a manufacturer/ISP thing.

---

### Post by Mark.H on 2008-07-05
the address that shows after 'inet addr:' is 192.168.0.2 

i will just say that as soon as i entered the site you suggested there was already an IP address in the box to be scaned by T1, the address was not my routers address, it was my pc address. 90..

The addres at the top of this post the 192.168.0.2 was the address that showed in terminal when I ran the /sbin/ifconfig command.

If I want to look at my router web page to change settings etc I have to enter 192.168.0.1

---

### Post by brian_p on 2008-07-05
> **Mark.H said:**
> the address that shows after 'inet addr:' is 192.168.0.2

**192.168.0.2 is your computer's address.**

> i will just say that as soon as i entered the site you suggested there was already an IP address in the box to be scaned by T1, the address was not my routers address, it was my pc address. 90..

**The number 90.. is the address of the part of the router (the external interface) which communicates with the internet.**

> The addres at the top of this post the 192.168.0.2 was the address that showed in terminal when I ran the /sbin/ifconfig command.

Yes.

> If I want to look at my router web page to change settings etc I have to enter 192.168.0.1

Yes again.

BUT - a router has two bits (two interfaces). One faces the internet and has to be addressed by 90.., and one faces inside and has to be addressed by 192.168.0.1, which is what you did with your browser because it is on the inside.

Your problem in interpreting the results from GRC and other scans you have done arise from this.

---

