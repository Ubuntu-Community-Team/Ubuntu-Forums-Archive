---
title: "Is this a safe idea and/or good one?"
date: 2009-01-20
forum: Security
---

### Post by stopie on 2009-01-20
Was torn between Networks forum and this one...but since the most important concern out of the three that I have is a 'safety thing,' I figured this thread belongs here - sorry if I annoy anyone.

**The Situation**
I currently have my External HDD shared on my home network so I can access it whenever I want, and so my mini 9 has a 350G HD ;). I want to switch my Gateway over to Ubuntu so I may rid my life of windows (sine I love Ubuntu on my mini so much), and I would still like to have my HDD ghetto-mounted to the network. Sicne the HDD doenst have an ethernet port, all of the research I've done says that I can't directly mount it to the network - I have to leave the Gateway on 24/7 and have it connected to the network 24/7.

**The Set Up**

[LIST]
[*]Gateway MA3
[*]Western Dig Ext HD (only USB connector - no ethernet)
[*]Netgear Routher
[LIST]
[*]"Secure password"
[*]"Unprotected" Broadcast
[*]Use MAC filter to only allow specific machienes to connect
[/LIST]
 
[/LIST]
[B]
The Question(s)[/B]

[LIST]
[*]Being that this is a home network that is somewhat protected by the router, and that the 'hosting' cpu would run ubuntu, would the current set up be safe?
[LIST]
[*]If its not safe, is there a way to make it safe?
[*]What would those ways be?
[/LIST]
 
[*]Is there a better way to share the External HDD on the network?
[*]Any other recomendations?
[/LIST]
Thanks for your time and input!

---

### Post by bgerlich on 2009-01-20
1. Your current networking setup is highly insecure. Use WPA with at least 10 char long passphrase instead of "unprotected". MAC verification is not a security feature, it's used for identification.

2. If you don't want to leave your computer on all the time get a NAS (network storage) with a usb port. It is quiet, cool and will allow you to expand your storage space by installing a sata/ide disk later if you need it. You can also upgrade your router to one that will allow you to plug in an USB disk.
If you don't mind your computer staying on all the time, there should be no problem with using it to share your network drive on the network.

---

### Post by stopie on 2009-01-20
Thanks for the advice!

For the sake of learning: How is a MAC filtered router vulnerable? (keeping in mind my security knowledge = 0.0000001 if you round up)

---

### Post by bgerlich on 2009-01-20
It's hard to say about vulnerability, MAC filtering can not be treated as a security feature. What your computers do rhight now is something like that:
1. Laptop connects to router by shouting its name (MAC).
2. Router allows it to connect
3. Laptop and router keep sending information to one another by means of shouting.
Anybody in range can hear quite well what is the laptop's name (MAC) and every other information you are sending between your laptop and the internet, including all passwords that aren't secured otherwise (Https, SSL for example). 

If someone wants to use your internet connection, considering the person already can have access to almost everything you do on the internet, a single command is all it takes to change the network card name and connect to your router: sudo ifconfig wlan0 hw ether 00:00:00:00:00:00, where the zeroes are a MAC address of one of your computers (remember that the address is broadcasted to anyone who cares to listen, just like anything else you do on the internet).

---

### Post by stopie on 2009-01-21
Thanks - thats a great way of explaining it. Now to go find a hexadecimal generator for WPA key...

---

### Post by bgerlich on 2009-01-21
If you want to go for the hex key you can, I myself use a longish passphrase i.e.: "goToThestoreandget6Tomatoes" easy to remember and reasonably secure :)

---

### Post by stopie on 2009-01-21
I myself can be paranoid - especially since I use the network for online everything (from banking, to insurance, to shopping, to what have you) - and I was under the impression that MAC filter was safe, as thats how our high school prevented my PSP from connecting (if I only found linux then...). 

So with that paranoia, I used a random number gen, then converted it as hex into letters and numbers, then used three different random wpa keygen sites to come up with 2 keys each, and then in a txt file, mixed and matched parts and chunks of each for a full 63 (I think thats the max) character long randomness. I also disabled SSID broadcast, seeing is that most people around my area probably think linux is a band or something, so they probabally arent leet haxors. If someone can get through all of that...they can have what they find :P

---

### Post by yamazaki1 on 2009-01-22
I find WPA to be just fine typically for securing wireless based connections, but it is still single factor authentication, meaning it *can* be brute forced...theoretically and assuming someone cares to take the time to do so (AirCrack can ony do some 30-60 words per second, where the amount of possible WPA-PSK password combos are in the many many billions).  

Even if they did crack your WPA-PSK and join your wireless network they'd still have to deal with all the traffic being encrypted between your hosts.  Best they could do at that point would be to:

1) Scan the network for available services
2) Find your SMB(?) server
3) Brute force the password to get the share (assuming there is a password)

So yeah, WPA is generally good enough for me if the password is not a "guessable" one.

If you're really really paranoid you can enforce kerberos authentication between your machine and the ubuntu box before you allow the file sharing protocol to occur.  This is, of course, provided that both machines can implement kerberos.  Kerberos is multi-factor authentication, which is practically impossible for someone to brute force as they won't have your private key on their box.

Implementing kerberos can be fairly long and involved, and probably out of scope of this forum though, so I'll just point you here:

[http://web.mit.edu/Kerberos/](http://web.mit.edu/Kerberos/)

if you're interested :)

---

### Post by hyper_ch on 2009-01-22
if you want to be secure, then you won't even consider to use wireless.

---

