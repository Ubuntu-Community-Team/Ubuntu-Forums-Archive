---
title: "Network intrusion"
date: 2008-02-11
forum: Server Platforms
---

### Post by Mikecore on 2008-02-11
I need some advice. I have been setting up a home file server. It is connected to a Linksys WRT54G v2 wireless router through an ethernet connection. ( wired I'm mean to say ). My wireless network was setup with MAC filtering to only permit my families laptops to connect to it. And I have the broadcast essid set to off, remote admin was turned off and the default password changed. however I did not have any security setup like wep/wpa. I have never had an issue with anyone connecting before. Anyhow Saturday night I stayed up till 2 AM configuring my new file server ( AMD64 Gusty fresh server install ) with ssh, ftp, and samba. After getting everything talking ( all my families laptops Mixed OS's linux and Winsucks alot ) I went to bed the next morning I get up around 10 AM and get back on to complete setting up my server I happen to double check last night work and notice I couldn't connect to my server through my samba share. After playing around for a while I did a smbtree command from one of my laptops and find that at some point a computer named "TODD" was on my network. It came back and said it could either contact it anymore or there was a bad 
comm of some type. At that point I shut everything down. Please note my server wasn't outside of my local network. no port forwarding or DMZ. so it was completely hidden ( as far as I know )

I have since updated the router firmware to the latest out. Changed to security settings to WPA personal with a long and complicated key, Changed the admin Password ( again long and compilcated )
and again setup MAC filtering to permit only my families computers 
from connecting to my router. I changed all the passwords on my laptops and scanned the linux ones with chkrootkit and scanned the windows one for viruses, ( didn't find any problems ). I also setup my router to log incoming and outgoing traffic. I also have all my laptops fire walled. 

Up until now I have never really worried about anyone connecting to my wireless router because I thought with the small measures I did take most ( 99% ) of the people around me would not be able to connect to my network without really being a cracker. or atlest a smart kid with a lot off time. I live in a good area and most of my hood is older retires and no kids. Am I thinking that for this person to connect to my network 
1) they would have had to scan for hidden networks ( I know this is not a problem "Kismet" and others software but they would have had to been close to my house to actually make the connection. Point is I would have noticed I live on a conner lot.

How could they bypass the mac filtering? without the router password and remote admin turned off?  

And finally with all the new security do you think I will be fine in the future if not what would you recommend?

---

### Post by x3roconf on 2008-02-11
1. Sniff for allowed mac adresses. (airodump-ng)
2. Change your adress to allowed mac adress.
3. Connect! :D

---

### Post by cdenley on 2008-02-11
Some wireless cards can be switched to radio mode so they can read all traffic from all networks within range. This means they were able to capture all your traffic unencrypted, and as x3roconf said, have access to all your mac addresses. A mac address can easily be changed, even in Windows. You would be surprised how far someone can connect to your network with the right antenna.

If you enabled WPA encryption, I wouldn't worry about it anymore. However, as long as you are using wireless networking, there is always the potential that someone is doing something. WPA2 has some security improvements.

---

### Post by Mikecore on 2008-02-11
I wasn't using wep or wpa before because years ago when I set up my router ndiswrapper didn't play nice with them. I see from how easy it was to setup my linux laptops with wpa that doesn't seem to be the case anymore. Cool I feel a little bit better. Thanks for the replies.

---

