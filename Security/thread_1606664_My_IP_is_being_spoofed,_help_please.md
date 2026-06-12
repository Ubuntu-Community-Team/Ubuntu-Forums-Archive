---
title: "My IP is being spoofed, help please?"
date: 2010-10-26
forum: Security
---

### Post by nrenniks on 2010-10-26
My IP is being spoofed by someone and I suspect it is being used for malicious purposes(possibly illegal ones). How can I stop someone from using my IP? I'm using a dynamic IP but obtaining a new IP seems to be useless. Changing my wireless password will probably just as useless I guess. So yea please help anyone? Much thanks. If this has already been posted, sorry, but if it has could you direct me to the solution? Alright, I guess that's all. Please help.

---

### Post by Iowan on 2010-10-26
Your ISP should be your first stop. I'm a bit confused, though - I'm not really sure how to ask...if you get a dynamic IP, how do you know yours is being spoofed, and where it's being used?

 If you don't get adequate response, use the Report Abuse button to request the thread be moved to Security Discussions.

---

### Post by nrenniks on 2010-10-26
Okay I was a bit nervous at first so maybe I entered some crap. But let me explain as fully as I can.

I use rapidshare, depositfiles etc. and it said I couldn't download because of parallel downloads. That is, my IP was already downloading a file. Since it's only my computer this is impossible. Hence, someone else must be using my IP. Another reason is that I was banned from 4chan for posting CP when I did not even go on 4chan for a week. Nor did I ever post such disgusting content. Which is what worries me the most, that someone is using my IP to do illegal activities. 

I thought an IP spoof is when someone else is using your IP through some means other than a rootkit or having your internet password.

Let me fully state that no one else besides me is using my IP address in my home. I do not use a shared IP address, it is a home network setup for just me. No one else but me can use it.

I change my IP quite frequently out of paranoia so I know that I could have ran into an IP that already had been blocked by 4chan but the rapidshare and depositfile situations make me worry that someone else is using my IP.

I do not use any unsafe websites or anything. I just think my IP is being hijacked.

I've checked several times for rootkits on my Ubuntu box and there wasn't anything up with it.

So I guess I'm just a paranoid wreck at this point so I just need some advice, help, etc.
I hope it's not me just being stupid. I know IP spoofs are viable and aren't all that hard(relatively speaking I guess).

Edit: My ISP is pretty much useless they really, really don't get what's happening. E.g. they said it was a virus in the download, a) I use Ubuntu(unlikely that it is a virus or worm, etc.) and b) I didn't execute any scripts, etc. just loaded a web page.

---

### Post by Iowan on 2010-10-26
Moved to Security Discussions.
Hopefully this will draw more response.
Good Luck!

---

### Post by lisati on 2010-10-26
One possibility is that the person who was previously assigned the IP address you now have started a download but didn't complete it.

---

### Post by nrenniks on 2010-10-26
It could be that possibly I suppose but the thing is it happened on two separate occasions with two seperate IPs. Unlikely or probable?

Yea I should have posted it in security but I can't really pick categories good ha. INTP much right? :P

---

### Post by anomie on 2010-10-26
[QUOTE=nrenniks]I use rapidshare, depositfiles etc. and it said I couldn't download because of parallel downloads. That is, my IP was already downloading a file. Since it's only my computer this is impossible. Hence, someone else must be using my IP. Another reason is that I was banned from 4chan for posting CP when I did not even go on 4chan for a week. Nor did I ever post such disgusting content. Which is what worries me the most, that someone is using my IP to do illegal activities.[/QUOTE]

Allow me to apply Occam's Razor here and throw out a couple alternative possibilities: 

Idea one - you have a process holding open a connection for your download application (easy to verify with netstat), and you did indeed post some objectionable content on 4chan (not really accusing you of that; just humor me). 

Idea two - someone has jumped onto your wifi network (WEP, perhaps?) and is operating from behind your nice little AP/router/NAT device. 

-------

I don't see any evidence here that your "IP is being spoofed". If your 'net-facing IP were being spoofed, you'd at least be having intermittent connection problems. If your host (private, non-routable network) IP were being spoofed, your OS would be throwing a fit about duplicate IPs.

---

### Post by nrenniks on 2010-10-26
Reason rules passion. I have WPA and from my neighbourhood(it's a small town) I personally know there is no way anybody has the skill to crack my connection. It sounds sort of arrogant of me to say that but trust me if you knew you'd agree. Hence, my mind is at ease. I didn't post anything rule breaking ha, take my word I suppose(?). Thanks for all the help, my paranoia is at an ease.

---

### Post by kreggz on 2010-10-26
Maybe your router has a rootkit

I'm just kidding but it is possible.

---

### Post by keewee on 2010-10-27
It could be that your ISP is using a transparent proxy, and that the filesharing sites are reading your ISP's proxy IP (shared by a lot of people) instead of your own IP.

---

### Post by tapas_mishra on 2010-10-27
I had a similar problem as Original Poster had.In such situations I would simply close my router and restart the modem again.Some times this used to work.

---

### Post by kerry_s on 2010-10-27
> **nrenniks said:**
> Reason rules passion. I have WPA and from my neighbourhood(it's a small town) I personally know there is no way anybody has the skill to crack my connection. It sounds sort of arrogant of me to say that but trust me if you knew you'd agree. Hence, my mind is at ease. I didn't post anything rule breaking ha, take my word I suppose(?). Thanks for all the help, my paranoia is at an ease.

:lolflag:
[http://www.wifi-predator.com/](http://www.wifi-predator.com/)

only requires pushing a button to crack you, when hooked up to say a old direct tv dish, the reach is far. :)

---

### Post by The Cog on 2010-10-27
When you say you have a dynamic IP address, I assume you mean the public IP address assigned by the ISP when you bring up your internet link. If you're using NAT and you mean the local IP address on your PC is dynamic, ignore this post.

I would point out that an IP spoof cannot be used in the way you seem to think it can. Uploading files or any other activity that requires a two-way TCP connection/conversation cannot be done with IP spoofing. If an imposter were to try and spoof your IP address from somewhere else, he would not be able to receive the responses from the server (they would be routed to your house). This would make it impossible for him to establish a full connection and hold a conversation with the server. So either the connection came from your house, or the server admin is mistaken about the IP address that committed the offense, or the server admin is mistaken about the time the offense was committed, or the ISP is mistaken about who was assigned that IP address at that time.

It is possible that the ISP's accounting is inaccurate. They have to try and keep track of which user is assigned which IP address at any time. This can go wrong occasionally, in which case when they try to figure out who had a given address at a given time, they get the wrong answer. Probably, the previous user of that address gets the blame. Changing your IP address frequently by resetting your router will only make this more likely.

It is possible that a mistake about the time of the offense gets the wrong person blamed. I remember reading about a schoolboy who was arrested for making a bomb threat to his school (telephone, not email) and phone records confirmed that he phoned the school at the time the bomb threat was made. Only a long time later was it discovered that one of the servers logging calls was an hour out due to daylight savings time, and he had actually called the school exactly one hour away from the time the threat was made. He had been checking on his homework assignment.

---

### Post by Kinstonian on 2010-10-27
You wouldn't happen to be using Tor by any chance would you?

---

### Post by wacky_sung on 2010-10-27
> **keewee said:**
> It could be that your ISP is using a transparent proxy, and that the filesharing sites are reading your ISP's proxy IP (shared by a lot of people) instead of your own IP.

I agreed with what you mention and that's what my ISP being using it.

---

### Post by Crazedpsyc on 2010-10-27
Try installing ettercap by running the following in a terminal:
```
sudo apt-get install ettercap-gtk
```
Then open ettercap from Applications>Internet>ettercap
open the Sniff menu and choose Unified Sniffing, then pick the appropriate interface (most likely "wlan0". Next open the Start menu and choose Start Sniffing. Finally go the the plugins menu,  select Manage the plugins, and double click on the plugins "find_ettercap" and "arp_cop". Watch the output box for anything suspicious and post everything in it here.

---

### Post by BigCityCat on 2010-10-27
> **kerry_s said:**
> :lolflag:
[http://www.wifi-predator.com/](http://www.wifi-predator.com/)

only requires pushing a button to crack you, when hooked up to say a old direct tv dish, the reach is far. :)

It says wep and wpa. I wonder if that includes wpa2.

---

### Post by endotherm on 2010-10-27
all else aside (there are numerous innocous examples of networking gone wrong, as others have mentioned), but  if you are convinced that someone is targeting you for this treatment, then they likely have a beachhead within your network and are operating through your equipment, rather than spoofing it. if you are seriously concerned, take your net down, and rebuild from scratch (router and all) examining each piece of network config as you go. 

if nothing else, if someone was spoofing your IP, it is unlikely that you would get any response from any of these sites in realtime, as the response would go to the spoofer, not to you. 

since this attacker likes and uses all the same sites you do though, I seriously start looking at friends and roommates, personal enemies, and former lovers.

---

### Post by kerry_s on 2010-10-27
> **BigCityCat said:**
> It says wep and wpa. I wonder if that includes wpa2.

yes, it does. :wink:

the thing is pretty awesome, my friend has it. at home he hooks it up to a huge dish, my friend is out in the boonies, there is no one around, you point that dish around he picks up all kinds of connections. he also uses it in his van, has a little rv type dish on the roof.

---

### Post by emarkay on 2010-10-27
> **The Cog said:**
> When you say you have a dynamic IP address, I assume you mean the public IP address assigned by the ISP when you bring up your internet link. If you're using NAT and you mean the local IP address on your PC is dynamic, ignore this post.

I would point out that an IP spoof cannot be used in the way you seem to think it can. Uploading files or any other activity that requires a two-way TCP connection/conversation cannot be done with IP spoofing. If an imposter were to try and spoof your IP address from somewhere else, he would not be able to receive the responses from the server (they would be routed to your house). This would make it impossible for him to establish a full connection and hold a conversation with the server. So either the connection came from your house, or the server admin is mistaken about the IP address that committed the offense, or the server admin is mistaken about the time the offense was committed, or the ISP is mistaken about who was assigned that IP address at that time.

It is possible that the ISP's accounting is inaccurate. They have to try and keep track of which user is assigned which IP address at any time. This can go wrong occasionally, in which case when they try to figure out who had a given address at a given time, they get the wrong answer. Probably, the previous user of that address gets the blame. Changing your IP address frequently by resetting your router will only make this more likely.

It is possible that a mistake about the time of the offense gets the wrong person blamed. I remember reading about a schoolboy who was arrested for making a bomb threat to his school (telephone, not email) and phone records confirmed that he phoned the school at the time the bomb threat was made. Only a long time later was it discovered that one of the servers logging calls was an hour out due to daylight savings time, and he had actually called the school exactly one hour away from the time the threat was made. He had been checking on his homework assignment.

Well written - and also remember that "My Cousin Vinny" almost got offed for a can of tuna...  :)

---

### Post by gamebusterzade on 2010-10-27
a common solution is to just restart the computer 

what will happen then is ur computer will link up with ur ISP and get a new IP adress from them 

trust me i had something similar happen to me

---

### Post by mainerror on 2010-10-28
> **gamebusterzade said:**
> a common solution is to just restart the computer 

what will happen then is ur computer will link up with ur ISP and get a new IP adress from them 

trust me i had something similar happen to me

Restarting your computer won't solve anything. He is hooked up with a router probably with a wireless access point. If anything he is going to get a new internal network address.

---

### Post by gamebusterzade on 2010-10-28
ya that i figured but ur u still need to talk to a server that has ur IPs on it because the router has 1 IP in it and that is from ur ISP 

it he/she is all that worried about that he/she should talk to his/hers ISP to see if they can change his IP network ID or his subnet but do NOT try to on ur oun.

FYI im behind two routers at home, and lots at collage

---

### Post by mainerror on 2010-10-28
> **gamebusterzade said:**
> ya that i figured but ur u still need to talk to a server that has ur IPs on it because the router has 1 IP in it and that is from ur ISP 

it he/she is all that worried about that he/she should talk to his/hers ISP to see if they can change his IP network ID or his subnet but do NOT try to on ur oun.

FYI im behind two routers at home, and lots at collage

This doesn't really make sense. If his ISP is assigning dynamic IP addresses which is very likely than only a reboot of his router would get him a new IP address or if the provider employs force disconnects.

---

### Post by endotherm on 2010-10-28
> **mainerror said:**
> This doesn't really make sense. If his ISP is assigning dynamic IP addresses which is very likely than only a reboot of his router would get him a new IP address or if the provider employs force disconnects.
even that doesn't work on many kinds of networks. my isp assigns the same dhcp address to me basically every time my router reboots. I have to reset my cable modem hard to get it to change.

---

### Post by mainerror on 2010-10-28
> **endotherm said:**
> I have to reset my cable modem hard to get it to change.

Which is what I actually meant.

---

### Post by gamebusterzade on 2010-10-28
> **endotherm said:**
>  I have to reset my cable modem hard to get it to change.

that will work as long as the router is dynamic also

---

### Post by Kinstonian on 2010-10-28
The chances that he was given an IP through DHCP where someone is coincidentally also currently downloading through rapidshare, etc., as well as someone posted child porn to a message board, which just so happens to be a place he frequents is pretty unlikely.  The most likely situation is that he, and others, are using the same Tor exit node.

---

### Post by gamebusterzade on 2010-10-28
@[nrenniks]("http://ubuntuforums.org/member.php?u=1175812") 

are u on the net with the net the computer that was spoofed 

if you are then it is not ur IP it might be something else

---

### Post by mainerror on 2010-10-28
> **gamebusterzade said:**
> that will work as long as the router is dynamic also

Would you please elaborate? I've worked for a ISP in Austria and I'm still not sure I understand what you mean? Do you mean static assigned IPs for their customers routers or what?

---

### Post by cmmckoy on 2010-10-29
I'm pretty sure what's going on is that someone is accessing your router, not spoofing your IP address or accessing your computer.  Try seeing everything that is connected to your router to see if there are devices connected that you don't recognize, or if there are more things connected than you can account for.

You'd be surprised who is able to gain access to things you wouldn't expect. Just because the old lady down the street can barely open a word processor doesn't mean that her sixteen year old nephew staying with her for the summer is the same way.

On my Linksys router, I go to [http://192.168.1.1](http://192.168.1.1) then enter my password, then go to Status > Local Network > DHCP Clients Table to see what is connected to my router, it may be something similar for you, and there are also other ways to find this information (I know, for example, the iPhone is able to identify everything connected to the same WiFi network at the phone)

In any case, I'd recommend changing your router's wireless password, just to be on the safe side.

---

### Post by gamebusterzade on 2010-10-29
> **mainerror said:**
> Would you please elaborate? I've worked for a ISP in Austria and I'm still not sure I understand what you mean? Do you mean static assigned IPs for their customers routers or what?


ya there are times people need static IPs for there routers but that is usualy found in small/home businesses. Static IPs are also always used in large businesses

(U should know this)

---

### Post by mainerror on 2010-10-29
> **gamebusterzade said:**
> ya there are times people need static IPs for there routers but that is usualy found in small/home businesses. Static IPs are also always used in large businesses

(U should know this)

Well I know this quite well but thats not the case here. Of course you ain't gonna get a new IP address if you pay for a static one but as stated it is a dynamic IP address so simply restarting your computer won't solve anything here.

---

### Post by gamebusterzade on 2010-10-29
> **mainerror said:**
>  simply restarting your computer won't solve anything here.

router can be static and computers be dynamic at the same time

  i should have stated that a cold start would be a good idea

that would make the computer forget its old IP and need a new one 

cold start = tuning off computer unplugging it for at least 10 minutes plugging back in and starting back up

[COLOR=Black]in the end i will agree with [/COLOR][cmmckoy]("http://ubuntuforums.org/member.php?u=731536") that would be the most logical idea yet

---

### Post by mainerror on 2010-10-29
> **gamebusterzade said:**
> i should have stated that a cold start would be a good idea

that would make the computer forget its old IP and need a new one 

cold start = tuning off computer unplugging it for at least 10 minutes plugging back in and starting back up

[COLOR=Black]in the end i will agree with [/COLOR][cmmckoy]("http://ubuntuforums.org/member.php?u=731536") that would be the most logical idea yet

Sorry for being pedantic but a cold start neither a warm start would ever help you with this problem as not the computer itself obtains the public IP address but the router in front of the computer. All you would do is to get your computer a new internal IP address at most. Routers nowadays tend to reassign IP addresses based on the computers MAC address so chances are high you will again just obtain the same internal IP address.

I just want to make you understand that rebooting your computer won't get you a new IP address. What you are referring to is that on PPPoE connections you have to kind of reconnect to your ISPs network and thus will get a new IP address but thats not the case for every ISP and network hardware configuration.

---

### Post by thegodfaza on 2010-10-29
> **kerry_s said:**
> :lolflag:
[http://www.wifi-predator.com/](http://www.wifi-predator.com/)

only requires pushing a button to crack you, when hooked up to say a old direct tv dish, the reach is far. :)

I need to get myself this future technology that can apparently crack AES256. And TKIP only has one security hole and it takes an hour to work. Set DHCP lease to 3600 seconds and your safe. My guess is this device is using the well known crack for WEP and is using rainbow tables for WPA2. Doubt it would get into my router as I use sentences for my passwords and it's using WPA2 AES256. Also before someone says "there is a newer attack by Martin Beck", that attack only lets you decrypt other users network traffic on the same encrypted network your currently connected to (the same thing that is built into the ethernet spec).

Also getting back to the original posters question. You said your using DHCP so obviously you got someone's IP who had abused those services before or your ISP like many ISPs is running all their subscribers traffic through the same IP ir a small number of IPs using a proxy to deal with the IP allocation issue (where IPv4 is running out of addresses that can be allocated). And from the times I've tried using rapidshare and the other file-sharing sites, they usually don't work well. I often get told that I'm currently downloading another file or the download link times out after I'm forced to wait an arbitrary amount of time. You could always try using a proxy, the Tor Network, or a VPN like [www.itshidden.com](www.itshidden.com).

---

### Post by gamebusterzade on 2010-10-30
> **mainerror said:**
> I just want to make you understand that rebooting your computer won't get you a new IP address. What you are referring to is that on PPPoE connections you have to kind of reconnect to your ISPs network and thus will get a new IP address but thats not the case for every ISP and network hardware configuration.


u know what, maybe i have some of my facts wrong

FYI my ISP uses PPPoE 

Iforgot about the other types

---

