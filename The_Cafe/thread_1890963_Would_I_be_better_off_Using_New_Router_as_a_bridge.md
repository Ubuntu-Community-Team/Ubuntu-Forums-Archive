---
title: "Would I be better off Using New Router as a bridge?"
date: 2011-12-04
forum: The Cafe
---

### Post by mamamia88 on 2011-12-04
I just ordered a Netgear WNR2000 that appears to be version 2 so it can run dd-wrt.  It appears to only be using the mini version though.   Right now I am using my modem that also does wireless to broadcast all over my house.    But, it doesn't do N.   I am curious though what would see a better performance gain for surfing/gaming?   Using it as a N router (which my current router only goes up to g) or using it as a bridge to connect my consoles too?  My 360 has a n adaptor built in and is on the lower floor of the house on opposite end.  Any help would be appreciated.

---

### Post by Old_Grey_Wolf on 2011-12-04
If you are going to use it as a bridge to your wireless-G modem, then you will still get the 54 Mbps wireless-G speed even on the Netgear router; unless, you plan to connect the wireless-N to the modem with an Ethernet cable.

I had a house that was a very large 2 story. I had to use a bridge to be able to connect from anywhere in the house. I had a wireless-G bridge connected wireless to a wireless_G router connected to my modem. When I got a wireless-N router, I found that it world work throughout the house without using a bridge. Modem connect with a 2 meter Ethernet cable to the wireless-N router.

You will have to experiment with the router configurations to determine what works best for you. 

I was able to retire my wireless-G router and bridge when I got my wireless-N router.

---

### Post by CharlesA on 2011-12-04
Unless it is a wireless bridge, you would still get wireless-N speeds. all you would have to do is hook the new router into the current network via one of the LAN ports on the back.

---

### Post by mamamia88 on 2011-12-04
> **CharlesA said:**
> Unless it is a wireless bridge, you would still get wireless-N speeds. all you would have to do is hook the new router into the current network via one of the LAN ports on the back.

Let me see if I understand this.    If I use the router as a bridge it will pick up the wifi signal from my ssid and let me connect my 360 via ethernet?  That is my assumption on what a bridge does.   I get around 66% signal strenth in my basement and want to get a more reliable/stronger signal if possible.  I bought the router on sale so even if it's not very useful I won't feel too bad.    I'm just curious if I would get a more reliable setup by placing the router in the basement as a bridge and connecting via ethernet or just by connecting my 360 via entering the ssid details.

---

### Post by CharlesA on 2011-12-04
[It depends on how you set it up]("http://www.dd-wrt.com/wiki/index.php/Client_Bridged"), but it can work like that.

I just plug the router into the network via cable and leave it as an access point, but that's just me.

---

### Post by mamamia88 on 2011-12-04
> **CharlesA said:**
> [It depends on how you set it up]("http://www.dd-wrt.com/wiki/index.php/Client_Bridged"), but it can work like that.

I just plug the router into the network via cable and leave it as an access point, but that's just me.

you see that is the thing.  The computer that the router would be by doesn't have wifi so I would have too connect it via ethernet.  Meaning that I can't move it any closer to my consoles.  I could use extra ethernet ports in the basement but I also want any improvements n might provide.  If I was to pick up a wifi bridge in the future I would be able to get the full n speed through a g bridge right?  My network doesn't even come close to maxing out the max speed of a g bridge ethernet port.  Guess I have a lot to think about

---

### Post by Old_Grey_Wolf on 2011-12-04
> **mamamia88 said:**
> Let me see if I understand this.    If I use the router as a bridge it will pick up the wifi signal from my ssid and let me connect my 360 via ethernet? 

The Netgear can pick up the wireless signal from your wireless-G modem; however, it will get wireless-G speed (54 Mbps). To get a higher speed, you will have to connect the Netgear wireless-N router to the wireless-G modem using an Ethernet cable.
 
> I'm just curious if I would get a more reliable setup by placing the router in the basement as a bridge and connecting via ethernet or just by connecting my 360 via entering the ssid details.

It is possible that the wireless-N router connected via Ethernet to the modem will provide coverage for your entire house. The signal strength may be lower but wireless-N doesn't need the same signal strength to work reliably.

---

### Post by Old_Grey_Wolf on 2011-12-04
> **mamamia88 said:**
> ...If I was to pick up a wifi bridge in the future I would be able to get the full n speed through a g bridge right?  

The wireless connection doesn't work any faster than the slowest component in the data path.

To get a wireless-G router to work with a wireless-N router at wireless-N speeds you have to use an Ethernet cable.

---

### Post by mamamia88 on 2011-12-04
> **Old_Gray_Wolf said:**
> The Netgear can pick up the wireless signal from your wireless-G modem; however, it will get wireless-G speed (54 Mbps). To get a higher speed, you will have to connect the Netgear wireless-N router to the wireless-G modem using an Ethernet cable.
 


It is possible that the wireless-N router connected via Ethernet to the modem will provide coverage for your entire house. The signal strength may be lower but wireless-N doesn't need the same signal strength to work reliably.thank you.  I'll let you know how it works out when it comes in the mail.  I can't wait.

---

### Post by mamamia88 on 2011-12-04
edit just ran speetest.net speedtest from right next to router,connected via ethernet to routher, as well as right in front of consoles on netbook.  speed test results where all nearly identical with wifi a higher ping by about 6ms in front of ps3.  knowing this i will probably just use it as a bridge for a netflix enabled blu ray player in other room.

---

### Post by CharlesA on 2011-12-04
Note: Your internet connection is probably slower then even a Wireless-g connection, so speedtest results will not show any difference.

---

### Post by 1clue on 2011-12-04
When I tried this my g router was one of the early apple airport "UFO" models. It turns out I wasn't getting even close to g max speeds. More like 5 Mbps. 

I messed with it for awhile and then just eliminated the old equipment. My n gear suddenly worked better, and easily covered not only my house but the garage and a significant chunk of yard on the other side. 

I messed with dd-wrt on my linksys wrt610nv2 but eventually gave up on it. The features I was trying to use evidently aren't used in combination very often because I was getting crashes and bizarre behavior every so often. I reverted to the stock firmware and am living with a little less control.

---

### Post by jjex22 on 2011-12-04
This is marginally off topic but may help the OP - we had that router up until april, (from virgin media) we found that it worked well as an N router, and well as a G router - it sucked as a G/N mixed router! we upgraded everything to N apart from an old mac that couldn't take a better airport card - tried running it on mix with dd-wrt and it was a nightmare - drop outs, crashes; endless having to restart the blooming thing! as soon as we set it to N or G only all the hassle we had went away. In the end we got a second hand N router and used that one as a bridge to the mac so the whole network was N. Just thought it might be worth baring in mind if you've got mixed devices!

---

### Post by mamamia88 on 2011-12-05
> **jjex22 said:**
> This is marginally off topic but may help the OP - we had that router up until april, (from virgin media) we found that it worked well as an N router, and well as a G router - it sucked as a G/N mixed router! we upgraded everything to N apart from an old mac that couldn't take a better airport card - tried running it on mix with dd-wrt and it was a nightmare - drop outs, crashes; endless having to restart the blooming thing! as soon as we set it to N or G only all the hassle we had went away. In the end we got a second hand N router and used that one as a bridge to the mac so the whole network was N. Just thought it might be worth baring in mind if you've got mixed devices!

I just remembered I had this madcatz n bridge.  Which says it's a n bridge but who really knows if it's n or not.    Anyway if I could gp all n on my network that would be great.   All I really need to connect is my ps3/360 and my netboook.  Is there a way to find out if my netbook supports n?  I could use the bridge for ps3 and the built in n adaptor for the 360.   Would the n router reduce ping for online gaming?    If I could get same speed and lower ping it would be worth it.    Also do you think dd-wrt is worth it on that router?  I read a review on newegg that said if using it as a router than OF is fine.  edit just looked up my wireless card on realteks website and it supports n so i'm golden.  worst case scenario is i go back to my old router and have an extra bridge laying around.   all in all not risking much for $20

---

### Post by 1clue on 2011-12-05
IMO tech works best with other tech of the same "generation". The notable exception in this case is Ethernet. Modern routers and switches hook up just fine with the oldest junk you can find, and the rest of the network seems to run at full speed. At least on Cisco/linksys, which is about all I buy now. 

I would absolutely put the newest tech closest to the Internet connection, speaking in terms of traffic. If you must use wireless to link these things then the oldest tech should handle the least traffic. Personally if I thought I needed that old router I would do anything possible to link it with Ethernet. 

You can buy a wireless n USB adapter but keep in mind older systems might not support it no matter what you do. I had a Mac like that, I still have the n card but not the Mac. 

Regarding speed, remember that you might be doubling up on traffic. Once you link wireless routers you now have a computer talking to a g router and then the g router talks to the n router on g protocol, with the g router using the same radio for both transactions. On top of that the processor on some g routers is slow, adding further latency issues. Just because a router can talk on a protocol doesn't mean it can saturate the bandwidth. Simultaneous dual-band n systems are cheap enough now you could solve some of the problems by setting one radio up as g-only and the other as n-only. Then the g router could bind to the g radio and the n router passes the packets at normal speed on n, and the only packets that hit g are those regarding communication with the old box. 

That said, new computers are incredibly cheap right now so it would probably cost less to retire your old system and replace it with a new budget box.

---

### Post by jjex22 on 2011-12-05
> **mamamia88 said:**
> I just remembered I had this madcatz n bridge.  Which says it's a n bridge but who really knows if it's n or not.    Anyway if I could gp all n on my network that would be great.   All I really need to connect is my ps3/360 and my netboook.  Is there a way to find out if my netbook supports n?  I could use the bridge for ps3 and the built in n adaptor for the 360.   Would the n router reduce ping for online gaming?    If I could get same speed and lower ping it would be worth it.    Also do you think dd-wrt is worth it on that router?  I read a review on newegg that said if using it as a router than OF is fine.  edit just looked up my wireless card on realteks website and it supports n so i'm golden.  worst case scenario is i go back to my old router and have an extra bridge laying around.   all in all not risking much for $20

I'd agree if you just want to use it as a standard home router, standard options it's not worth the time of adding dd-wrt. But you would need to add it if you wanted to use it as a bridge, as I'm pretty sure that's the reason we added it in the first place. It also gives you more options to configure what each device is able to do etc, but of course it's just what you want to do with it, most modern wireless routers are pretty sensibly configured for standard home networking tbh!

---

### Post by mamamia88 on 2011-12-05
> **1clue said:**
> IMO tech works best with other tech of the same "generation". The notable exception in this case is Ethernet. Modern routers and switches hook up just fine with the oldest junk you can find, and the rest of the network seems to run at full speed. At least on Cisco/linksys, which is about all I buy now. 

I would absolutely put the newest tech closest to the Internet connection, speaking in terms of traffic. If you must use wireless to link these things then the oldest tech should handle the least traffic. Personally if I thought I needed that old router I would do anything possible to link it with Ethernet. 

You can buy a wireless n USB adapter but keep in mind older systems might not support it no matter what you do. I had a Mac like that, I still have the n card but not the Mac. 

Regarding speed, remember that you might be doubling up on traffic. Once you link wireless routers you now have a computer talking to a g router and then the g router talks to the n router on g protocol, with the g router using the same radio for both transactions. On top of that the processor on some g routers is slow, adding further latency issues. Just because a router can talk on a protocol doesn't mean it can saturate the bandwidth. Simultaneous dual-band n systems are cheap enough now you could solve some of the problems by setting one radio up as g-only and the other as n-only. Then the g router could bind to the g radio and the n router passes the packets at normal speed on n, and the only packets that hit g are those regarding communication with the old box. 

That said, new computers are incredibly cheap right now so it would probably cost less to retire your old system and replace it with a new budget box.
So since evertyhing I want to use on the web has the capability of using N I would benefit most from using exclusively n and turning off g broadcasting?   I'm just curious if I would reduce latency for online gaming using n?  Thats about the only advantage I could possibly see to using the router as a router and not a bridge for other devices such as a blu ray player I own without wifi that can do netflix.  but then again i have enough netfix devices.  also would my kindle be able to connect to n?

---

### Post by 1clue on 2011-12-05
I suspect that you would get better performance by turning off g entirely or at least by hooking the g router to the n router with a cable. But again I think if you're careful about placing your routers in the middle of the computer cluster you might be able to have both routers pretty close and cover all your bases. 

Try an experiment by running your cable modem to the middle of the house. Hook your n router to that with Ethernet. Hook g to n with a short cable and spread them out so they're as apart as is reasonable.  Then turn everything on and see what happens. 

You may need to experiment. N has more range and higher speed. 

If you have games or media going it makes sense to put that on its own net. Stop buying g gear. Consider hardwiring where possible and USB n adapters for the devices that support it.

---

### Post by mamamia88 on 2011-12-06
> **1clue said:**
> I suspect that you would get better performance by turning off g entirely or at least by hooking the g router to the n router with a cable. But again I think if you're careful about placing your routers in the middle of the computer cluster you might be able to have both routers pretty close and cover all your bases. 

Try an experiment by running your cable modem to the middle of the house. Hook your n router to that with Ethernet. Hook g to n with a short cable and spread them out so they're as apart as is reasonable.  Then turn everything on and see what happens. 

You may need to experiment. N has more range and higher speed. 

If you have games or media going it makes sense to put that on its own net. Stop buying g gear. Consider hardwiring where possible and USB n adapters for the devices that support it.
unfortunately that's not really possible  because i would be tripping on wires no matter how i wire it.  also the pc it's hooked up too doesn't have a wireless. card.

---

### Post by 1clue on 2011-12-06
> **mamamia88 said:**
> unfortunately that's not really possible  because i would be tripping on wires no matter how i wire it.  also the pc it's hooked up too doesn't have a wireless. card.

So you're using the g router as a substitute wireless card?

Regardless this was just supposed to be an experiment. It doesn't really matter if you trip on wires for an hour or two. What I was trying to point out is the speed difference between mixed mode or pure n.

Again if you retire your old box or find an n adapter that works with it then you no longer need to worry about g at all.

---

