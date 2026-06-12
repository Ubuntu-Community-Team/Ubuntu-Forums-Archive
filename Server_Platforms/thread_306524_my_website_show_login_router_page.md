---
title: "my website show login router page"
date: 2006-11-25
forum: Server Platforms
---

### Post by SilvioTO on 2006-11-25
Hi, I have a Ubuntu Dapper server with a website. I open the 80 port on nat section of my router (zyxel 660HW-D1), but when I try to open website I'm redirected to login page of router configuration... Where I wrong? Thanks.
Silvio.

---

### Post by PilotJLR on 2006-11-25
It sounds like your router does not support loopback... some questions for you:
- When you reached your router login page just now, did you type your PUBLIC ip address in the browser?
- When you type the server's PRIVATE address in the browser from inside your lan, does the website work properly?

If those 2 items are a yes, then verify the site is working externally... i.e. have someone outside your own network test this for you!

Many soho routers, when presented with their own WAN ip address internally, will direct the packet to the lan interface, which is the management interface. Routers with loopback will instead send the packet to the WAN interface, at which point your port forward or ACL is applied.

---

### Post by MJN on 2006-11-25
I don't think it necessarily sounds like a loopback issue, but rather that the router's built-in web server is listening on port 80. To resolve this, either turn it's server off (might not be possible) or change the port it listens on (e.g. to 8080) and ensure that you're forwarding port 80 to your server (it sounded like you may have done this, but I couldn't be certain from your wording).

Mathew

---

### Post by PilotJLR on 2006-11-25
> **MJN said:**
> I don't think it necessarily sounds like a loopback issue, but rather that the router's built-in web server is listening on port 80. To resolve this, either turn it's server off (might not be possible) or change the port it listens on (e.g. to 8080) and ensure that you're forwarding port 80 to your server (it sounded like you may have done this, but I couldn't be certain from your wording).

Mathew

Most routers by default do not accept management interface requests on the wan interface, for security reasons... 
If he is using the WAN ip addrs internally, then loopback is explicitly required.
Without loopback, the port forward is not applied, therefore you hit port 80 on the lan interface... this is why I asked the 2 questions above...

---

### Post by MJN on 2006-11-25
I see where you're coming from now.

A Google search reveals it does support loopback however many Zyxel routers appear not to enable it by default. It seems there's a rather convoluted way of enabling it and this requires a 3rd party Windows tool - []("http://forums.whirlpool.net.au/forum-replies-archive.cfm/347939.html")[http://zyxmon.3daffex.com/settingse.php](http://zyxmon.3daffex.com/settingse.php).

Using the Telnet access (I wonder if this requires the above tool?) if you go into Section 24 (System Maintenance) and choose Command Interpreter Mode then execute **ip nat loopback on**.

What a palaver just to set a commonly-required function. Why would anyone *want* it disabled?

Mathew

---

### Post by PilotJLR on 2006-11-25
Nice find! It's nice it can at least be made to support loopback. I would assume you could telnet to it without any additional windows apps... but I don't have this router, so I don't know that for sure.

Worst case, just add your server's local address to /etc/hosts and call it a day  ;)

---

### Post by MJN on 2006-11-25
That may be the best option, as it would also appear that the config changes (or at least the loopback one) is not permanent and must be entered into some form of boot file in the router.

Makes my trusty D-Link 604 seem rather archaic... although this supports loopback out of the box so perhaps not! ;)

Mathew

---

### Post by SilvioTO on 2006-11-25
First, thanks for your answers... one puntualization: the server work with dyndns service, and the site respond to this url: [www.artenuovadimensione.dnsalias.com](www.artenuovadimensione.dnsalias.com). Try yourself if the router access login appears.
if, in Firefox, I type [http://192.168.1.34](http://192.168.1.34) the site work regularly
if, in Firefox, I type [www.artenuovadimensione.dnsalias.com](www.artenuovadimensione.dnsalias.com) I can see only the router administration login page.
The ping command of the url from console work fine.
Tanks again for your precious help!

Silvio.

---

### Post by MJN on 2006-11-25
It doesn't work from here (are you still at 151.37.170.209?) - no response.

However, assuming this is just a transient problem, from what you've clarified it looks like your router is not currently supporting loopback. So, either trawl through the links mentioned above or do as PilotJLR suggests and put a suitable mapping in /etc/hosts e.g. **192.168.1.34 [www.artenuovadimensione.dnsalias.com]("http://www.artenuovadimensione.dnsalias.com") **- this will mean that whenever your type your URL from machine it'll obtain the internal server address as opposed to going out onto the Internet and retrieving the router's WAN address via the DNS.

Mathew

---

### Post by PilotJLR on 2006-11-25
Yeah, same here...
Make sure your dnsalias account is updated properly... if your dnsalias account says your IP is the same as this: [www.whatismyip.com](www.whatismyip.com)
then that would mean your port forward is not configured correctly on the router.

The fact you get your website with the private address means you're over half to way there!  :-)

---

### Post by SilvioTO on 2006-11-26
My dnsalias account say my ip adress is the same of [www.whatismyip.com](www.whatismyip.com)

Ping from my server to my website:

PING artenuovadimensione.dnsalias.com (192.168.1.34) 56(84) bytes of data.
64 bytes from artenuovadimensione.dnsalias.com (192.168.1.34): icmp_seq=1 ttl=64 time=0.201 ms

ping [www.artenuovadimensione.dnsalias.com](www.artenuovadimensione.dnsalias.com)
PING artenuovadimensione.dnsalias.com (151.37.170.209) 56(84) bytes of data.
64 bytes from adsl-209-170.37-151.net24.it (151.37.170.209): icmp_seq=1 ttl=254 time=0.722 ms


This is the file /etc/hosts of my server:

127.0.0.1	localhost
192.168.1.34	artenuovadimensione.dnsalias.com	artenuovadimensione

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


This is my nat configuration on router:

SUA Only
Active Network Address Translation(NAT) checked 
(other option is full features)

Port forwarding tab:
 	 Default Server Setup
 
Default Server: 0.0.0.0

 	 Port Forwarding
Service name: WWW  start port: 80  end port: 80  server ip address: 192.168.1.34

Any idea where my error?

Thanks...

---

### Post by MJN on 2006-11-26
Just to clarify, you can access your site from within your LAN by going to 192.168.1.34 but you can't get there with artenuovadimensione.dnsalias.com (incidentally, you ought to also put the [www.art]("http://www.art")... alias in /etc/hosts too) ?

In fact, would I be right in thinking you're still trying to reach your server with *www*.art..? If so, you need to put that as an alias as mentioned above.

Mathew

---

### Post by PilotJLR on 2006-11-26
I think so too... the ping to [www.(longname).dnsalias.com](www.(longname).dnsalias.com) went to your public ip addrs, so you need to add the www. domain to /etc/hosts

The site isn't working externally... your network appears to not have port 80 open.

Is port 80 blocked at the router? If not, do you have a separate hardware firewall that could be blocking the port?
Lastly, do you know if your ISP blocks port 80? Mine does by default, so I have to fill out a form to get them to un-block it.

---

### Post by MJN on 2006-11-26
That's interesting about the form...

My ISP doesn't block any ports however I'd always assumed that those that did just blocked them and that was that. I didn't realise they'd reopen them on request - I take it you have to agree to certain conditions? Or is it more that they'll open them up if asked but just want to know in advance?

Mathew

---

### Post by PilotJLR on 2006-11-26
It's really more like a waiver... for example, with my ISP, you have to complete the form in order to use port 25 outbound. They block the port so that you can't hurt anything if your computer gets a worm and starts spamming. If you basically accept responsibility for not becoming a spammer, then they let you use port 25.
I'm not sure what the rationale is for port 80, since they usually block that to force people to buy more expensive "business" connections.  :-)

But it is at least worth looking into... waivers can sometimes get some ports un-blocked.

---

### Post by SilvioTO on 2006-11-27
I find the solution, but don't understand how modify my hosts file...
The problem is my router that don't support internal loopback. Solution is here: [https://www.dyndns.com/support/kb/archives/loopback_connections.html](https://www.dyndns.com/support/kb/archives/loopback_connections.html) but I don't understand, at the end of file, this line:

192.168.0.1	router.example.com
192.168.0.2	[www.example.com](www.example.com)
192.168.0.3	foo.example.com

How to modify my server file? What's "foo" (ip of my client.artenuovadimensione.dnsalias.com)?
And dhcp server on router? I turn it on or off? Actually are off. And, suppose, I delete dns of my isp from router... or not?

Thanks in advance...
Silvio.

---

### Post by MJN on 2006-11-27
Slow down! You were almost there before (I think)
 
Can you access your site using artenuovadimensione.dnsalias.com from within your LAN? If so, and it's just [www.artenuovadimensione.dnsalias.com]("http://www.artenuovadimensione.dnsalias.com") that's not working then you just need to add [www.artenuovadimensione.dnsalias.com]("http://www.artenuovadimensione.dnsalias.com") to the 192.168.1.34 line in /etc/hosts i.e.:
 
127.0.0.1 localhost
192.168.1.34 [www.artenuovadimensione.dnsalias.com]("http://www.artenuovadimensione.dnsalias.com") [COLOR=#bd5900]artenuovadimensione.dnsalias.com[/COLOR]
 
As mentioned above, your router **does** support loopback but you need to enable it. I don't think you need to go the hassle of doing this as tweaking your hosts file will have the same effect for all intents and purposes.
 
Mathew

---

### Post by SilvioTO on 2006-11-27
You suggested option "127.0.0.1 localhost
192.168.1.34 [www.artenuovadimensione.dnsalias.com](www.artenuovadimensione.dnsalias.com) artenuovadimensione.dnsalias.com" give me unable to access to the server, I used live cd for correct this:
~$ sudo reboot
sudo: unable to lookup artenuovadimensione via gethostbyname()

Now that is my hosts file: 
127.0.0.1 localhost
192.168.1.34 [www.artenuovadimensione.dnsalias.com](www.artenuovadimensione.dnsalias.com) artenuovadimensione

in both cases I browse "http://www.artenuovadimensione.dnsalias.com" and "http://artenuovadimensione.dnsalias.com" i get my router login page.
Only if I browse "http://192.168.1.34" i get full access to my website.

---

### Post by SilvioTO on 2006-11-27
In the support pages on the Zyxel website at this url: [http://www.zyxel.com/web/support_knowledgebase_detail.php?KnowledgeBaseID=749&pid=20050105140750](http://www.zyxel.com/web/support_knowledgebase_detail.php?KnowledgeBaseID=749&pid=20050105140750)
I find the solution:

1 - open a terminal:
2 - type: telnet 192.168.1.1 (default ip of the router Zyxel 660HW-D1) and enter acces password;
3 - from the "ras>" prompt type: "ip nat loopback on" (without quote) and press return;
now nat loopback work.

Now I can access on my website typing [www.artenuovadimensione.dnsalias.com](www.artenuovadimensione.dnsalias.com)
do you can too?

---

### Post by MJN on 2006-11-27
No, nothing. Is your IP address 151.37.245.151? As that's what the DNS is saying...
 
I'm curious that it's working for you... What's the contents of your /etc/hosts file? If you've enabled NAT loopback then you should remove the extra entries that we've put in (otherwise you won't be using NAT loopback at all but rather going directly to the server via its LAN address).
 
Mathew

---

### Post by SilvioTO on 2006-11-27
151.37.245.151 is correct, the site respond at ping command and browse fine in Fifefox for me. Try now, I'm delete "www." from second line.

my hosts file:

127.0.0.1	localhost
192.168.1.34	artenuovadimensione.dnsalias.com	artenuovadimensione

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by MJN on 2006-11-27
Sorry, nothing.
 
I'm now thinking your ISP blocks port 80...
 
Incidentally, you **should **have [www..](www..). in your hosts file if that's a name you're going to be using to connect! (and I suspect it is)
 
Mathew

---

### Post by SilvioTO on 2006-11-27
I deactivate the router firewall... try now please...

---

### Post by MJN on 2006-11-27
Yep - it's working!

Now that you've activated the NAT loopback you ought to remove the 192.168.1.34 line from /etc/hosts so then you're viewing the same DNS namespace as everyone else (strictly speaking it doesn't matter however leaving config like this hanging around can often be the cause of a great deal of head-scratching problems when you update the DNS yet still seem to be resolver to the original server!).

Mathew

---

### Post by SilvioTO on 2006-11-27
Hi, I'm back now from english course... :D  Good news! Now I have firewall deactivate; it's not a good thing. I need to reactivate this and create a rule for port 80. You suggest me to delete from hosts file the ip? Like this example? Show me examples please, I understand quickly and best.

from...
127.0.0.1 localhost
192.168.1.34 artenuovadimensione.dnsalias.com artenuovadimensione

to...
127.0.0.1 localhost
artenuovadimensione.dnsalias.com artenuovadimensione

I understand well? This tactic evade possible problems of dydns service, exactly? Strange, I read that the ip address is necessary for server work.
For now I have activate the firewall and created this rule:

packet direction: wan to lan
source ip: any
destination ip: 192.168.1.34
service: http port 80
action: permit

The site work with this change too? For me yes.

Thanks, you have a greate patience...
Silvio.

---

### Post by MJN on 2006-11-27
Sorry, not working. :(

With regards to the /etc/hosts file get rid of the whole line, i.e. just leaving you with:

127.0.0.1 localhost localhost.localdomain

(I know you didn't have the last name in, but do)

As for having patience, one has to when it comes to Linux! ;)

Mathew

---

### Post by MJN on 2006-11-27
Working again! [22:54 GMT]

---

### Post by SilvioTO on 2006-11-27
I think this router is not good product... with my atlantis land router I never had problems; tomorrow I'll go at the shop and change it. Never Zyxel again... [-( 

Bye and thanks again.
Silvio

---

### Post by PilotJLR on 2006-11-27
> **MJN said:**
> No, nothing. Is your IP address 151.37.245.151? As that's what the DNS is saying...
 
I'm curious that it's working for you... What's the contents of your /etc/hosts file? If you've enabled NAT loopback then you should remove the extra entries that we've put in (otherwise you won't be using NAT loopback at all but rather going directly to the server via its LAN address).
 
Mathew

Yeah... with loopback, the /etc/hosts entries are okay, but superfluous.

The website still doesn't work for me... if your IP addrs in dnsalias is correct, then the problem is probably either:
 - bad port forward
 - firewall on router
 - ISP blocking port 80

---

### Post by PilotJLR on 2006-11-27
> **SilvioTO said:**
> I think this router is not good product... with my atlantis land router I never had problems; tomorrow I'll go at the shop and change it. Never Zyxel again... [-( 

Bye and thanks again.
Silvio

Good luck!
Just be aware you need to put the /etc/hosts entries back in, if the router you buy doesn't have loopback. No biggie!

---

### Post by SilvioTO on 2006-11-29
End of the story: the new router I changed has the same problem, but... I phoned to the assistance of Atlantis Land that show me that is not a problem, is the chipset of router that is so build, and my site is visible outside of my lan. The only difference is that I must use the internal lan adress of my server for manage website; they suggest me to try to change the default port 80 in 8081. I'll try, or, temporary, I use the telnet command for enable the internal loopback, but if I restart router this option return to default (internal loopback off).
In any way, I'm satisfied, because I learned something new...

Hi!
Silvio.

---

### Post by MJN on 2006-11-29
What's your new router? Not the same make I hope! I'm not surprised the new one doesn't support loopback either... it seems that many don't (the DLink DI604 certainly does if you're after something that definitely does).

If you check out the links I provided I'm sure one of them mentions how to make the ip nat loopback command permanent - can't remember how exactly (something to do with modifying the startup file) but I've definitely read it.

Or, as we've discussed above, just edit your hosts file to include mapping between your domain and internal LAN address - we can all see it from the outside so the potential absence of NAT loopback need not matter... it's just a pain when it's the unknown cause of a problem (but now you know about it so you're alright!)

Mathew

---

### Post by SilvioTO on 2006-11-30
I change it with Atlantis Land WebShare 141W and it's good for me; it has great italian phone support also.
I administer the site via local lan ip and, if I need to access to website, type in telnet the command ip net loopback on... It's not a problem for me.

Bye! :p

---

