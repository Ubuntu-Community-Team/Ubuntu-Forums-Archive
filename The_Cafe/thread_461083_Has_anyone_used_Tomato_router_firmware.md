---
title: "Has anyone used Tomato router firmware?"
date: 2007-06-01
forum: The Cafe
---

### Post by matthinckley on 2007-06-01
I have been using Tomato for my Linksys WRT54G for about a month now and I love it.  It has awesome QoS settings and a real-time bandwidth monitor.

It can be found here: [http://www.polarcloud.com/tomato/]("http://www.polarcloud.com/tomato/")

I've posted some screenshots of the bandwidth monitor and QoS graphs

---

### Post by starcraft.man on 2007-06-01
Only other firmware I've dabbled in (than default) is [DDWRT]("http://www.dd-wrt.com/dd-wrtv2/index.php") and I was/am really happy with it :). I'm not sure the exact features, it prolly has all that (I can't be bothered to look :p). I'm a basic guy so I don't use em all anyway >.>.

Oh and I really like the DDWRT theme.

---

### Post by matthinckley on 2007-06-01
I used DDWRT before I used Tomato.. I also like DDWRT and it does offer many features that Tomato does not such as VLANS and setting up as a hotspot with registration page and all..

What I like most about Tomato is the QoS features..  I have Vonage at home and I found whenever I am running torrents I couldn't use my phone.. I could hear people talking but they couldn't hear me because torrents were using all of my available upload bandwidth.

DDWRT allowed me to set QoS up by port or MAC which would be fine except my computer running torrents also runs an apache server and Ampache to stream my music.  so when I throttled back that PC my music streaming was hampered as well.

Tomato Firmware allows me to set up QoS by MAC, IP, Protocol, and ports.  I am able to set my ports being used by bittorrent to low priority and give my Apache server higher priority, while my Vonage router has the highest priority.  

One thing I liked about DDWRT was when I was using my server as my router, I could move the WAN port of my WRT54G into the LAN, effectively making it a 5 port switch with a wireless access point.. I can't do this with Tomato, but I found it easier for my network to just have the WRT54G be my router anyways.

---

### Post by calraith on 2007-06-01
I'm happy as a pig in poop with Tomato.  I'm running it on two WRT54G's in AP + WDS mode.  This way I can keep my cable modem and main router up on top of my bookshelf, but still plug the occasional wired client into my second router and use it as a wired switch without running wires across doorways or having to crawl into the impossibly tiny attic access hole to run a new network drop.  My laptop will also automatically use the AP with the highest signal strength, so I can take it out onto the porch, which I couldn't do before.

The QoS thing is excellent as well.  It ensures my wife can still access her online classes uninterrupted while I've got a torrent running and am listening to a Shoutcast stream, and I don't have to configure anything client-side.

The SVG graphs were fun for the first couple of days, but I rarely use them anymore.  It's still nice to know I can play with them if I want.  I think I will now.

---

### Post by jiminycricket on 2007-06-02
Tomato kept crashing my router every few hours for some reason, so I had to go back to DD-WRT.  DD-WRT has a similar theme option to it if that's part of what attracted you to Tomato.

---

### Post by qpieus on 2007-06-02
I haven't tried it yet, but I might give it try. I run dd-wrt on a Buffalo WHR-G54S router. It runs perfectly but the dd-wrt has a billion features I don't need. Not that that is a problem since I just don't mess with the settings I don't need. But maybe the simpler interface of tomato would be good to try.

I just got a second buffalo router to set up a wireless bridge. I assume tomato can handle this task? The other feature I like with the dd-wrt is the ability to assign a static IP to my PCs based on their MAC addresses. Can tomato do this? I'm gonna go read up tomato's features, but if you happen to know if these 2 features are supported please add your experiences here.

---

### Post by calraith on 2007-06-02
> **qpieus said:**
> I just got a second buffalo router to set up a wireless bridge. I assume tomato can handle this task? The other feature I like with the dd-wrt is the ability to assign a static IP to my PCs based on their MAC addresses. Can tomato do this? I'm gonna go read up tomato's features, but if you happen to know if these 2 features are supported please add your experiences here.

I drew you a picture showing you how I have my two routers set up.  I worked hard on it so don't laugh. ;)
[IMG]http://xs216.xs.to/xs216/07226/ap_wds.gif[/IMG]

In answer to your other question, yes, you can assign static IP's based on client MAC address.  That's how my wife's and my desktop are set up.

---

### Post by matthinckley on 2007-06-02
Awesome picture calraith!

---

### Post by calraith on 2007-06-02
Thanks!  I thought so too.  Insignificant side note: the main router is named "tomato" because of the Tomato firmware.  The secondary router is named "pumpkin" because I have orange hair and my wife calls me Pumpkin.  I'm not sure whether Pumpkin was an intentional correlation between my hair color and a common pet name lovers call each other, but as a name for a router, it works on so many levels.  Glad you asked!

But yeah, I had considered dropping around a hundred bucks for sumn like an Xbox wireless ethernet interface that I could plug into a megabit switch so I could have multiple computers connected via ethernet, but feed that switch a wireless signal from the main router.  Turns out I was on eBay at just the right time to win this second WRT54G v2 for around 25 bucks.  In retrospect, the Xbox wireless ethernet interface probably would've handled only one IP address anyway, so I probably would've spent a hundred bucks for nothing.

Tomato's AP + WDS functionality saved me about 75 bucks.  The QOS is the whipped cream on top, but some kind of 5-star restaurant whipped cream, not that crap that comes from a spray can.  I'm hungry.

---

### Post by qpieus on 2007-06-04
Thanks calraith, nice pic. I can see how hard you worked at it ;)
Can you use WPA with that setup?  I read a couple tutorials that said WEP was being used - I don't want that.

---

### Post by calraith on 2007-06-04
The example given in the FAQ specifically uses WPA for WDS.

[http://www.polarcloud.com/tomatofaq#how_do_i_use_wds](http://www.polarcloud.com/tomatofaq#how_do_i_use_wds)

---

### Post by roadkilla on 2007-06-05
I'm programming firmware mods for Tomato [http://rapidshare.com/files/35133458/Tomato_1.07.1040VPN.7z](http://rapidshare.com/files/35133458/Tomato_1.07.1040VPN.7z)
btw when updating from dd-wrt you must do a hard nvram reset.

---

### Post by matthinckley on 2007-06-05
> **roadkilla said:**
> I'm programming firmware mods for Tomato [http://rapidshare.com/files/35133458/Tomato_1.07.1040VPN.7z](http://rapidshare.com/files/35133458/Tomato_1.07.1040VPN.7z)
btw when updating from dd-wrt you must do a hard nvram reset.
I didn't.. worked fine for me

EDIT: btw what is this firmware you have linked.. is it different than the regular Tomato? what is different about it?

---

### Post by Rede on 2007-06-05
> **calraith said:**
> Thanks!  I thought so too.  Insignificant side note: the main router is named "tomato" because of the Tomato firmware.  The secondary router is named "pumpkin" because I have orange hair and my wife calls me Pumpkin.  I'm not sure whether Pumpkin was an intentional correlation between my hair color and a common pet name lovers call each other, but as a name for a router, it works on so many levels.  Glad you asked!

But yeah, I had considered dropping around a hundred bucks for sumn like an Xbox wireless ethernet interface that I could plug into a megabit switch so I could have multiple computers connected via ethernet, but feed that switch a wireless signal from the main router.  Turns out I was on eBay at just the right time to win this second WRT54G v2 for around 25 bucks.  In retrospect, the Xbox wireless ethernet interface probably would've handled only one IP address anyway, so I probably would've spent a hundred bucks for nothing.

Tomato's AP + WDS functionality saved me about 75 bucks.  The QOS is the whipped cream on top, but some kind of 5-star restaurant whipped cream, not that crap that comes from a spray can.  I'm hungry.

I've set up WDS using DDWRT on two routers. I found it was better than having no signal strength, but it really seems to have reduced the overall network speed. Out of curiosity, did you experience any slowdowns?

---

### Post by calraith on 2007-06-05
> **Rede said:**
> I've set up WDS using DDWRT on two routers. I found it was better than having no signal strength, but it really seems to have reduced the overall network speed. Out of curiosity, did you experience any slowdowns?

Yeah, divide your bandwidth by 2 per router.  So if you have 3 set up for 802.11g, your bandwidth for LAN transfers will be 54 / 2 / 2 = 13.5mbps.  I'm quite drunk, so my math could be off.  How much more frequently do you do LAN transfers versus PC <-> Internet, anyway?

---

### Post by larytet on 2008-02-07
up here. 
using tomato too

installation - no problem, smooth on the WRT54GL v 1.1
tomato took my previous settings. 

QoS work for HTTP and Skype. for Skype i chose to use alternative ports 80 and 443)

QoS is not perfect. i do have ability to browse and talk by Skype under heavy P2P traffic, but delay increases - I wait for the "picture" longer. But in any case this is significant improvement over Linksys original firmware.

GRE (PPTP) still fails or very slow under heavy traffic, probably because time outs or delays and I use VPN+remote desktop lot . I will look into it.

Static DHCP and local host name resolution (DNS) work flawlessly. Now I can connect to my local servers using names instead of IP addresses and still I can control all IPs in the network. This was important in my setup.

I am using WEP. I did not try WAP.

Some cool features (comparing to the Linksys original FW)
- SSH 
- monitoring of the connections and bandwidth
- QoS based on the protocol type+port+address+data size
- static DHCP entries
- and much more

JS in the WEB interface is really cool and I know what I am talking about. The UI is minimal, but very functional. Help is probably missing. I had to google around to figure out what some of the netfilter options exactly do.

---

### Post by larytet on 2009-01-21
Update.
I switched to the latest Tomato firmware. still no problems. 

One tip regarding static DNS entries and OpenDNS

to edit static DNS entries connect to the router using ssh (you will probably need to enable SSH access first via WEB interface)
```

ssh root@192.168.18.1

```
After that look for wan_dns line
```

# nvram show | grep wan_dns 
wan_dns=192.168.0.2
# 

```
Write this line down somewhere.

Now go to the [http://www.opendns.com/](http://www.opendns.com/)  click "Start using now" link on the page, click router, click any router, copy IP address, for example

208.67.222.222
208.67.220.220

now you should write 
```

# nvram set wan_dns='208.67.222.222 208.67.220.220'
# nvram commit

```

That's it. From now on you are using OpenDNS servers instead of your ISP DNS. You can use both by checking box on the page Advanced->DHC/DNS page in the WEB interface.


Second tip is related to WiFi. Choose to send beacon every 91 or 97 or 101 any other number which is not 100 and is not divided by 100. Choose channel as far as possible from the occupied channels. For example if channel 6 is occupied choose 11 for your access point.

---

### Post by ssam on 2009-01-21
> **calraith said:**
> 
[IMG]http://xs216.xs.to/xs216/07226/ap_wds.gif[/IMG]

you should upload that to
[http://www.ratemynetworkdiagram.com/index2.php](http://www.ratemynetworkdiagram.com/index2.php) :-)

---

