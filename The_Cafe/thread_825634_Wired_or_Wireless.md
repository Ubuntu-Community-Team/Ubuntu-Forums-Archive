---
title: "Wired or Wireless ?"
date: 2008-06-11
forum: The Cafe
---

### Post by hellmet on 2008-06-11
Umm.. I did see similar topics but none match exactly.. 

My uncle is setting up his office in this new location in a few months from now. We are quite confused between choosing Wired/Wireless networks. There'll be eventually 30 employees - max.
Data exchange between computers will be minimal - mostly documents and pdfs- no multimedia or streaming anything.

Our opinions :
Wired - Secure - physical connection needed to tap into network
         - Reliable - No frequency interference 

Wireless - Quite secure if SSID broadcast is turned off, and security is turned on. 
             - New generation routers and cards capable of 108Mbps are nearly as fast or   
               faster than 100Mbps Ethernet.
             - Extreme mobility. Workstations can be placed and moved even after all 
               wiring is done. Get connected from any part of the office.

But these conclusions are from the limited experience that we have in this field.
Right now, we are favoring Wireless over Wired networks for all workstations, while wiring the printer and the server for reliability's sake.

But, I want to know what you guys think of having a Wireless setup in an office environment. Do you think we should also have CAT5 laid just in case?
How secure and reliable is Wireless? Are these 108Mbps routers and cards a safe bet- do they really give 108Mbps? etc.

Thanks for the patience in reading through this long question:).
And I appreciate your response!

---

### Post by sakid on 2008-06-11
Wired where ever possibe - especially in a business environment.

Wireless should only be used by laptops and even then I believe in using wired if possible.

---

### Post by Jim! on 2008-06-11
I disagree with the above opinion. I believe wireless to be a better choice, It's cheaper than installing a wired connection and much easier too, there are also plenty of security protocols that if followed will make it almost as secure if not just as secure as a conventional wired network.

---

### Post by gameryoshi600 on 2008-06-11
IMHO, Wired for desktops if you got 1 if more then 1 go wireless
Laptops always should be wireless and wired if your at someones house and they do not have wireless then go wired. ;)

---

### Post by Kevbert on 2008-06-11
Both. Wired for desktops which are less likely to be moved and wireless 802.11g/n for laptops.  Wireless can be configured to allow only certain PCs to log on via their MAC codes.

---

### Post by ilrudie on 2008-06-11
I would say wired.  If you want to go wireless you must treat internal traffic as though it were external.  There is no way to properly secure a wireless access point.  MACs can be spoofed easily.  Hidden SSID is worthless.  WEP is easy to crack.  WPA and WPA2 will have flaws although they are much better options.  Your business could also face legal trouble if someone uses your wireless to do something illegal.  It wont stick but it'd would be better if you did not incure the cost of defending your buisiness.  Wired is the way to go for buisinesses in my opinion.

If you are serious about wireless make everyone connecting to the work network and the internet go through a VPN.  Thats your best bet.

---

### Post by ivze on 2008-06-11
I confirm that WEP is very weak (see [www.aircrack-ng.org](www.aircrack-ng.org)).
But what threats WPA-protected networks, if passwords are choosen correctly?

---

### Post by rickyjones on 2008-06-11
A combination.

All computers should have a wired connection if possible. A switch will give dedicated speeds to each computer that is wired. This is not true with wireless. A wireless network may broadcast at 108Mbps but you'll never reach that. A wireless network is just like a hub, the more computers connecting over it the slower it will be for everyone. Not exactly true with a switch.

If the budget allows then install a network jack at each desk and more throughout the building in case of future moves. Install a wireless network as well that laptops can use when moving around the office.

Another thing that you will notice is that going all wireless will present performance issues if you have say, an Active Directory domain. I've noticed that I have to let the computer bake for a few minutes at the login screen so that the wireless network has time to connect and sync up.

Wireless is a great technology but it should not be your only method of connectivity. You get what you pay for in terms of network performance.

Sincerely,
Richard

---

### Post by billgoldberg on 2008-06-11
> **hellmet said:**
> Umm.. I did see similar topics but none match exactly.. 

My uncle is setting up his office in this new location in a few months from now. We are quite confused between choosing Wired/Wireless networks. There'll be eventually 30 employees - max.
Data exchange between computers will be minimal - mostly documents and pdfs- no multimedia or streaming anything.

Our opinions :
Wired - Secure - physical connection needed to tap into network
         - Reliable - No frequency interference 

Wireless - Quite secure if SSID broadcast is turned off, and security is turned on. 
             - New generation routers and cards capable of 108Mbps are nearly as fast or   
               faster than 100Mbps Ethernet.
             - Extreme mobility. Workstations can be placed and moved even after all 
               wiring is done. Get connected from any part of the office.

But these conclusions are from the limited experience that we have in this field.
Right now, we are favoring Wireless over Wired networks for all workstations, while wiring the printer and the server for reliability's sake.

But, I want to know what you guys think of having a Wireless setup in an office environment. Do you think we should also have CAT5 laid just in case?
How secure and reliable is Wireless? Are these 108Mbps routers and cards a safe bet- do they really give 108Mbps? etc.

Thanks for the patience in reading through this long question:).
And I appreciate your response!

Wireless is the way to go, it's so much easier.

But wired can be more stable/secure.

---

### Post by aeiah on 2008-06-11
rickyjones gave a great argument, and one that i agree with. the inconvenience active directory, roaming profiles and email syncing caused when you have 10 people logging in all at once monday morning will be a nightmare. wire as much as possible and have wireless for guests and your road-worrior employees who arent in the office much

as a side note: not broadcasting the SSID is farely useless. its very easy to find a router's ESSID, you just monitor the airwaves and wait for someone to connect, on which point it broadcasts the name briefly. the same goes for MAC filtering, which is easy to spoof. the only thing that provides security without inconvenience is a very good WPA PSK password

---

### Post by billgoldberg on 2008-06-11
> **ivze said:**
> I confirm that WEP is very weak (see [www.aircrack-ng.org](www.aircrack-ng.org)).
But what threats WPA-protected networks, if passwords are choosen correctly?

[http://blogs.ittoolbox.com/wireless/networks/archives/cracking-wpapsk-6730](http://blogs.ittoolbox.com/wireless/networks/archives/cracking-wpapsk-6730)

I myself use wep.

I'm not concerned about people hacking it.

There are a dozen wireless networks I can pick up, half of them are open to the public.

Why would they take me? 

And if I get hacked, well, too bad.

Choosing wpa or a different wep key takes like 1 minute.

---

### Post by aeiah on 2008-06-11
yes but in an office setting you have to make things secure. id have thought that was obvious.

---

### Post by will1911a1 on 2008-06-11
My own network is set up in such a way that the desktops are wired and only our laptops need to worry about wireless.  

If you don't need the mobility, wired is the way to go.

---

### Post by RiceMonster on 2008-06-11
I would use wired if it was practical, but on my laptop it's not, so I use wireless. If I was using a desktop, I'd make sure I was using wired, because I much prefer it.

---

### Post by ilrudie on 2008-06-11
> **billgoldberg said:**
> [http://blogs.ittoolbox.com/wireless/networks/archives/cracking-wpapsk-6730](http://blogs.ittoolbox.com/wireless/networks/archives/cracking-wpapsk-6730)

I myself use wep.

I'm not concerned about people hacking it.

There are a dozen wireless networks I can pick up, half of them are open to the public.

Why would they take me? 

And if I get hacked, well, too bad.

Choosing wpa or a different wep key takes like 1 minute.

If your wireless network at home gets cracked it probably only affects you and the people who live in your house.  Its not great but there also isn't necessarily much to gain there either.  A business however might have some customers and employees.  If it does have customers it probably has contact information and credit cards / billing information,  It probably has tax information for its employees which may include Social Security numbers and other sensitive bits.  Losing customer/employee information and possibly customers/employees along with it just to save a little time/effort when setting up the office seems ill advised.  Wired is just better for serious business.

Regarding WPA:  If you choose a good key I am not aware of anything right now that can threaten you but WPA may have an unknown flaw in the standard waiting to be discovered and could certainly suffer from implementation flaws in your system.  Its just an extra risk for a business to take on IMO.

---

### Post by Fedz on 2008-06-11
Wired is by enlarge more secure but, wireless can and is highly secure if configured and monitored correctly with a maximum character (numbers, letters, upper-case, lower-case, extended character) password on WPA PSK.

Not broadcasting your SSID is all but useless except for the average Joe but, mac filtering is a line of defence as is not broadcasting your SSID.

The biggest protection will come from a good strong maximum character password and higher encryption than WEP :-)

I personally use the max. character password with mac filtering on WPA PSK but, I enjoy broadcasting my personalized SSID.

---

### Post by Robux the great on 2008-06-11
Allways wired with the wireless turned off on my router.

Regards

Rob

---

### Post by timcredible on 2008-06-11
> **hellmet said:**
> 
Our opinions :
Wired - Secure - physical connection needed to tap into network
         - Reliable - No frequency interference 

Wireless - Quite secure if SSID broadcast is turned off, and security is turned on. 
             - New generation routers and cards capable of 108Mbps are nearly as fast or   
               faster than 100Mbps Ethernet.
             - Extreme mobility. Workstations can be placed and moved even after all 
               wiring is done. Get connected from any part of the office.

 i have a ccnp and a cisco wireless certification, and i setup a 400+ access point network for a medium sized customer, and my personal opinions:

1 - wireless is half-duplex, shared bandwidth, wired switches are full-duplex, dedicated, so 108Mb/s 802.11n network is not as fast as 100Mb/s wired, it's not even close.  If you have more than 5 people on an access point, and they're doing a decent amount of traffic, then they're each getting about 10Mb/s equivalent throughput

2 - wireless is susceptible to interference, especially if you're in a large office building and other companies have wireless too.  i've also had problems in warehouses with large a/c units in the ceiling completely killing the wireless signals for hours at a time.  cordless phones, bluetooth devices, microwaves, etc. all interfere with wireless.

3 - i would recommend going wired only, but mobility is a nice feature, so you have to balance the technical view vs. the business requirements, and you'll probably end up with both wired and wireless.

4 - if wep and wpa are all you have to rely on, and you can't afford a centralized controller and a real wireless infrastructure (check out [cisco's wireless solutions]("http://www.cisco.com/en/US/prod/collateral/wireless/ps5678/ps430/prod_brochure09186a0080184925_ns337_Networking_Solution_Solution_Overview.html")), then you have to consider wireless only sort-of secure.

---

### Post by NullHead on 2008-06-11
I highly recommend wired connections to the workstations. Wireless is over rated and 802.11**n** doesn't give you those actual speeds anyways .. I bought a 70$ 802.11**n** and I ***STILL*** have not connected as wireless N yet ..

I will say if you go the wireless rout; take a router that is MIMO enabled. If you don't end up connecting with the 802.11n connection type at least you can use MIMO 802.11g witch is what I'm currently using. 

In my situation wireless is needed to get internet to this particular computer. Wired is not an option here.

---

### Post by Tom--d on 2008-06-11
I would have all desktop's wired as you wont really move them, will you? 
Its secure and safe.

Wireless for laptop's which are always on the move. If the laptop is on a desk 24/7, have it wired.

Wireless: I would have a really good WPA key. And hide the essid (because you can  :D). MAC filtering always helps.
108mb/s, you will never reach that. When downloading, that always depends on the servers etc etc.

Hope this helped in anyway, 

Thanks,
Tom

---

### Post by hellmet on 2008-06-12
Thanks for the awesome response guys!! Each post was as helpful as the others!

Okay - I get that its better to use Wired for desktops, and wireless for the few laptops around. Will use all security possible - hide SSID, MAC filtering, and a strong WPA PSK pwd. I also get that Wireless 108Mbps gets divided among all computers. Wired 100Mbps doesn't.

But, I have a question. If I do have wireless in the office, and if the hacker gains access to the router by somehow cracking the wireless, then will he not be able to sniff all data being communicated between the Wired desktops too?

---

### Post by NullHead on 2008-06-12
> **hellmet said:**
> Thanks for the awesome response guys!! Each post was as helpful as the others!

Okay - I get that its better to use Wired for desktops, and wireless for the few laptops around. Will use all security possible - hide SSID, MAC filtering, and a strong WPA PSK pwd. I also get that Wireless 108Mbps gets divided among all computers. Wired 100Mbps doesn't.

But, I have a question. If I do have wireless in the office, and if the hacker gains access to the router by somehow cracking the wireless, then will he not be able to sniff all data being communicated between the Wired desktops too?

He won't be able to if you put the wireless router and the wired router/hub/switch on different VPNs.

---

### Post by BDNiner on 2008-06-12
I would go wired. If you plan on running a domain with any kind of backup solution then wireless could lead to data corruption in your backups. plus other electronic devices will interfere with the signal. so you may find areas in the office that have poor signal strength.

And you won't realised just how much sharing you will do once the network is in place. are you planning on using features like centralised e-mail or shared calendars?

---

### Post by damphoud on 2008-06-12
I would go wired all around, if it was not too great of an inconvenience for the notebooks. Do the notebook employees have their own desk/office? or do they setup on a boardroom table?

---

### Post by Lrdwilliams on 2008-06-12
> **Jim! said:**
> I disagree with the above opinion. I believe wireless to be a better choice, It's cheaper than installing a wired connection and much easier too, there are also plenty of security protocols that if followed will make it almost as secure if not just as secure as a conventional wired network.

Yep ... I agree with Jim. The future is wireless, so I'd say ... get rid of the wires now.
Cheers ... Les

---

### Post by timcredible on 2008-06-12
> **NullHead said:**
> He won't be able to if you put the wireless router and the wired router/hub/switch on different VPNs.
you mean vlans, not vpns, right?

also, to answer the question, a hacker won't get into your router, they will be grabbing the info traveling over the air with your wireless connections.  if they gain access to the network, they still haven't accessed the router, and won't be able to see packets on the wired network, only the wireless network.  but they will be able to attack any of your machines from an internal ip address.

---

### Post by NullHead on 2008-06-12
> **timcredible said:**
> you mean vlans, not vpns, right?

I guess either would work. VLAN would work better, but at our local library they use VPNs .. so I'm more familiar with those; my brother being the IT director of that particular library and all. 

Unfortunately the servers there are windows servers ](*,)

---

