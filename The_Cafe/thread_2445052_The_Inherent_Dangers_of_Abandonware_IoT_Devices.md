---
title: "The Inherent Dangers of Abandonware IoT Devices"
date: 2020-06-08
forum: The Cafe
---

### Post by DuckHook on 2020-06-08
[https://www.theregister.com/2020/06/08/smart_fridges_support_periods/](https://www.theregister.com/2020/06/08/smart_fridges_support_periods/)

Knowledgeable users may understand the inherent dangers in orphaned consumer devices, but consumers do not.

Many years ago, I made the mistake of buying a Western Digital MyBookLive device. To my disbelief and frustration, WD abruptly abandoned the device three years after my purchase. Note that this was specifically sold as an Internet&#8209;facing media&#8209;serving NAS. That's about as central and critical a role as a device can play in any given network environment. Their response to outraged queries (abridged): "We are committed to security. This device should only be used within a good firewall."

The really sad thing was not their lame, irresponsible response; it was how few consumers were sufficiently knowledgeable to be outraged.

Abandonware is already a big problem now. It's going to get much worse.

PS. I finally resurrected that WD NAS by nuking its lousy dead firmware from orbit and replacing it with OpenWRT. Once again, FOSS/Linux rides to the rescue.

---

### Post by EuclideanCoffee on 2020-06-08
I'm not sure how any company thinks it can maintain such ambitious projects in the first place. It's almost like it's designed to fail because consumers can host their own cloud cheaper while others could get free cloud storage anywhere.

---

### Post by DuckHook on 2020-06-08
This was back in the day when cloud was not as ubiquitous as it is today and there was still some question as to how it would develop. Indeed, this was WD's "answer" to the desire for self-hosted cloud devices.

The bigger problem is that WD did not consider this a "failure". As far as they are concerned, they sold millions of units, pocketed their profits, and are not responsible for all of the dead bodies lying around&#8212;I have no doubt that thousands of those units are now slaves in the massive botnets that are causing so much havoc in the net.

With respect to my original link, neither will Samsung, LG or any of these other fridge manufacturers. Consumers are enticed into paying huge premiums for "smart" fridges that can automatically restock themselves by placing orders with the online supermarket delivery service (ooo-ahhh), but are not warned that the fridge will be abandonware after two years (what's abandonware?).

---

### Post by grahammechanical on 2020-06-08
Planned obsolescence has been around for many decades. If we believe the American movie industry there are alien races right now scheming to invade earth because they have used up all the precious resources of their own planet. In my opinion they used up the resources building the massive invasion fleets. And then their equivalent of a certain smartphone/tablet reseller advertised their next model and could not meet the demand. So, the invasion fleet is launched.   :)

[https://en.wikipedia.org/wiki/Planned_obsolescence](https://en.wikipedia.org/wiki/Planned_obsolescence)

Regards

---

### Post by DuckHook on 2020-06-08
> **grahammechanical said:**
> …So, the invasion fleet is launched.   :) …
:lol: By far the best theory I've yet heard.

I do get the planned obsolescence business model. Whether I agree with it is another matter, but I'm not so naïve as to expect businesses to act otherwise. However, one would think that even this business model can only get away with so much cynicism: > …LG saying patches would be issued as required. Samsung said it would offer software support for a maximum of two years…
*Two years???*

The mischievous side of me wonders how Samsung would react if it got about that their fridges are only designed to last 2 years. :twisted:

---

### Post by mastablasta on 2020-06-09
> **DuckHook said:**
> 
The mischievous side of me wonders how Samsung would react if it got about that their fridges are only designed to last 2 years. :twisted:


i work in customer care for a large household manufacturer. i don't know what Samsung would say, but i do know our new bosses do not understand the concept of repair. so the products are made and dumped on market with no way to repair them after a year or two.

luckily the new law in Europe will force them to supply parts  so that appliance (not all appliance types yet) can function and be repaired for 10 years. i mean from consumer standpoint it makes a lot of sense. i am not sure how this will affect the IoT appliances they try to peddle. once i spoke with a marketing guy and IoT enthusiast. i mentioned that if you don't update one can hack and then the whole brand will look bad. he agreed that they need to figure out a solution for that. i don't think they ever did. they continue to sell these devices. 

i too would advise consumer to try and avoid such devices, at least until there are certain standards in place. if we had something similar to AMD64, UEFI and ATX standards, then at least consumers or repairmen could replace the OS later on with newer OS version or at least opensource software. 
until this si possible these items will basically be beyond repair and in EU they will receive lower grades on label. so as consumer you will see a label that will define how easily can it be repaired within certain period. then people will vote for money. no one will buy * star appliance if all others have 4* or 5*

i also hope this will move on to TV, smartphones and various hubs. manufacturers should be bound to at least some standards.

energy labels basically did just this. they forced manufacturers to really "go green". no one will buy an oven with D or C class energy efficiency if all others have A+, A++ and A+++ and they cost approximately the same. additionally i think you can see the savings on the labels (or rather you can calculate them). so who in their right mind would want to buy something that costs the same, yet is more expensive in the long run, makes more noise, doesn't dry as good etc.?!

---

### Post by The Cog on 2020-06-09
> Samsung said it would offer software support for a maximum of two years&#8230; 
For a cloud dependent IOT device, I read that as "We guarantee that this device will stop working within two years.". I really can't think why anyone would buy such an item.

---

### Post by kevdog on 2020-06-09
Do you really think abandonware products became "botnet farms"?

---

### Post by DuckHook on 2020-06-09
> **kevdog said:**
> Do you really think abandonware products became "botnet farms"?
[https://nakedsecurity.sophos.com/2018/11/12/botnet-pwns-100000-routers-using-ancient-security-flaw/](https://nakedsecurity.sophos.com/2018/11/12/botnet-pwns-100000-routers-using-ancient-security-flaw/)

This is just an example. There are similar stories weekly.

I subscribe to a number of security blogs and reading them is just depressing. So much so, that there are times I have considered unsubscribing. But ignorance is not really bliss, so I grit my teeth and stay informed.

Consider the case of the Western Digital MyBookLive in my first post.

[list=1]
[*]It was abandoned on kernel 2.x (I don't bother remembering which one precisely, but it was an ancient kernel anyway).
[*]It was designed and sold to be Internet facing with UPnP turned on by default.
[*]It was marketed as a consumer appliance that was just plug-and-play. A cloud device for dummies.
[*]I bought mine at Costco. There was a mountain of them in just the one store. If not millions, then at least hundreds of thousands were sold.
[*]Since its orphaning, thousands of CVEs have been discovered. Let's just exploit an infamous one: heartbleed.
[*]If I were a bad guy, I would prowl for old MyBookLives. They advertise their webservices freely and distinctively, so are easy to spot.
[*]Since it's a consumer device, many users who are just knowledgeable enough to be dangerous would have activated ssh without a second thought.
[*]Never mind heartbleed. Many of those same users would not have even bothered changing the ssh password from its factory default (they were all the same, root ssh was enabled and the password was available with any web search).
[/list]
There is absolutely zero doubt in my mind that a hefty proportion of those MyBookLives are now pwned.

Botnet farms, DDoS bots, cryptomining bots… some form of bot anyway. Why on earth would a scumbag refrain from taking advantage of such easy pickings?

---

### Post by TheFu on 2020-06-09
We need laws to mandate "Truth In Packaging" like we have for Food items with the Nutrition Labels.  

I've thought a little about what should be on the box side for any internet dependent devices AND software:

[LIST]
[*]    Support EoL date
[*]    Free upgrade schedule and paid "extended support" schedule.
[*]    Patch schedule - monthly, quarterly.
[*]    What works without internet connectivity?
[*]    What requires internet connectivity to work?
[*]    List of all {domains|IPs}:{ports} required for each network connection
[*]    List of protocols used for each external connectivity
[*]    2FA standards supported
[*]    How new firmware is updated – USB flashing, network load, something else?
[/LIST]

If I'd known that Google was going to EoL my $450 phone 2 yrs later, I'd never have bought it.  Seems many companies think 3 yrs of support is fine. I find it strange that Apple seems to do the best job, by far, of all the IoT makers.

Some devices that people buy without thinking about life times.
[LIST]
[*]Remember Plays For Sure from MSFT?
[*]Thermostats like Nest v1 (pre-Google)
[*] Door locks / Garage doors
[*]Any internet cam/video
[*]Phones / Tablets
[*]TVs
[*]Media Players
[*]Routers
[*]Kitchen appliances with IoT stuff
[*]IoT controllers that tie into Google / Amazon / Apple "home" controllers.
[*]Software - how long will WoW be available or Quickbooks or Starflight or Apple Video purchases?
[*] Digital cameras with connectivity
[/LIST]

BTW, almost all consumer routers get 2-3 yrs of support, no more.  I'm always amazed when people are running 10 yr old Belkin/Buffalo/Linksys routers that have never been patched.  If you care about security in your house, there are 3 choices:
[LIST=1]
[*]Get a recent small business router like Mikotek or Ubiquiti which are well regarded for quick patching
[*]Build your own x86-64 device that runs one of the small business router distros which are known to be well-maintained. pfSense, OPNSense, some Linux versions like smoothwall, sonicwall, ... 
[*]Build your own x86-64 device that runs a small Linux distro that YOU setup as a firewall + router.
[/LIST]
I suppose people could just buy a new router every 3 yrs.

---

### Post by kevdog on 2020-06-10
It seems like a better solution for the IoT crap would be at the router/firewall level -- however if your router is 10 years old likely this isn't going to work.  I agree that making internet facing devices that have an EOL date or planned obsolescence does introduce a very big risk. I like the truth in Packaging idea however why am I skeptical that will never happen.  Industry keen on selling new devices with security taking a backseat.

---

### Post by TheFu on 2020-06-10
> **kevdog said:**
> It seems like a better solution for the IoT crap would be at the router/firewall level -- however if your router is 10 years old likely this isn't going to work.  I agree that making internet facing devices that have an EOL date or planned obsolescence does introduce a very big risk. I like the truth in Packaging idea however why am I skeptical that will never happen.  Industry keen on selling new devices with security taking a backseat.

Nutrition labels didn't happen voluntarily. They were required by the FDA in the Federal Food, Drug, and Cosmetic Act

SMART for HDDs didn't happen voluntarily. They were required by a govt purchasing department.

Something similar has to happen for network connected devices. Probably the FTC or EU will need to force it.  We'll never get anything if it isn't mandated.

---

### Post by DuckHook on 2020-06-10
> **TheFu said:**
> Nutrition labels didn't happen voluntarily… Something similar has to happen for network connected devices. Probably the FTC or EU will need to force it.  We'll never get anything if it isn't mandated.
I would like to see things go one step further, as mastablasta has outlined: a minimum support period imposed so that IoT products last for more than a measly couple of years. As a corollary issue, we have a real e&#8209;waste problem in our society and two-year planned obsolescence cycles not only rip off consumers, but are socially irresponsible.
> **The Cog said:**
> For a cloud dependent IOT device, I read that as "We guarantee that this device will stop working within two years.". I really can't think why anyone would buy such an item.
Cogent observation that strikes at the heart of the matter.

[list=1]
[*]I'm afraid that most people haven't the foggiest notion of the dangers of dead software, though to be fair, these are not the easiest of concepts to understand.
[*]Unfortunately, a significant contingent also don't care (we even get those on our forums from time to time).
[*]Manufacturers are very aware of consumer ignorance and will opt for product churn over sustainability because that's where the profits are.
[*]If we have to live in a world where product churn is inevitable, I suppose a partial solution might be to charge a recycle fee up front. But this does not solve the security issue.
[/list]
The problem is both recurrent and tough to tackle. Knowledgeable users don't drive the agenda. The agenda is being driven by this miasma of consumer ignorance and a profit motive that is more than willing to exploit that ignorance.

Uninformed users not only get ripped off, but don't know that they are being ripped off even after their devices lose support. There are millions of users still using Android KitKat, unknowing or uncaring of the danger they pose not only to themselves, but to the larger computing community.

---

### Post by grahammechanical on 2020-06-10
In the European Union there is the WEEE legislation. Waste Electrical & Electronic Equipment.

> The first WEEE  Directive ([Directive  2002/96/EC]("https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32002L0096"))  entered into force in February 2003. The Directive provided for  the  creation of collection schemes where consumers return their WEEE free of   charge. These schemes aim to increase the recycling of WEEE and/or  re-use.

The company that sold the equipment should have a scheme to allow the buyer to return the product without charge. This kind of legislation is all well and good if the items are actually recycled. They are instead most likely put in a shipping container and dumped in Africa or Asia where some small child is given a hammer and told to bash the motherboard to get what little precious metals there are. Oh, let us not mention the hazardous materials present.

Well, why not. It is done with plastic. Is it not?

Regards

[https://ec.europa.eu/environment/waste/weee/index_en.htm](https://ec.europa.eu/environment/waste/weee/index_en.htm)

---

### Post by mastablasta on 2020-06-11
let's not even talk about peeping Toms on the net connected easy to use and setup IP camps. not only they had problem with security patching, many people left the default password. i've read that you can see many strange things on certain sites that streamed this video.

---

### Post by DuckHook on 2020-06-11
> **mastablasta said:**
> …peeping Toms on the net connected easy to use and setup IP camps…you can see many strange things on certain sites that streamed this video.
[https://www.csoonline.com/article/3342418/meet-the-man-in-the-room-attack-hackers-can-invisibly-eavesdrop-on-bigscreen-vr-users.html](https://www.csoonline.com/article/3342418/meet-the-man-in-the-room-attack-hackers-can-invisibly-eavesdrop-on-bigscreen-vr-users.html)

I know you said "Let's not even talk about…" but I couldn't resist.

---

