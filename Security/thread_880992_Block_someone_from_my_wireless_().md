---
title: "Block someone from my wireless (?)"
date: 2008-08-05
forum: Security
---

### Post by RavUn on 2008-08-05
Someone seems to be using my wireless and I'd like to block them.  If I have their IP address and they're currently connected to my router is there a way to get their Mac address and block them completely?

Also, is there an effective way to block outside access completely?  It's already encrypted with WPA.  And, could I possibly find who it is that's connected to us?

---

### Post by y@w on 2008-08-05
Does your router allow you to view the DHCP lease table? That'd be the easiest way I know of to find out the MAC address. There's probably an option to blacklist their MAC address in your wireless access point then.

The much better way would just be to setup WPA to encrypt it with a password...

---

### Post by RavUn on 2008-08-05
Yea, i've been looking for a dhcp client list but couldn't find it.  It's already encrypted with WPA.

I need to figure out how to do this:
[http://www.ex-parrot.com/~pete/upside-down-ternet.html](http://www.ex-parrot.com/~pete/upside-down-ternet.html)

:P


EDIT: Oh, I found the MAC filter and it has a list.  I had to turn on the filter first... whoops.  Well, the person's not currently connected so I'll have to check again later on.

---

### Post by y@w on 2008-08-05
Their lease should still be valid. Typically it's something like 2 days. So.. someone hacked your WPA network? Was the password guessable?

---

### Post by issih on 2008-08-05
WPA is more secure than WEP, but it too is vulnerable to attack. I believe wpa2 is a lot more secure if your hardware supports it.

Personally I just run a mac filter...more admin when theres something new to add to the list, but pretty much impossible to hack.

---

### Post by y@w on 2008-08-05
> **issih said:**
> 
Personally I just run a mac filter...more admin when theres something new to add to the list, but pretty much impossible to hack.

If someone has hacked the WPA network, they know how to change their MAC address. It's not hard...

---

### Post by issih on 2008-08-05
Very true, they can change their mac address, but they have to guess one of the valid ones that you have on your network...now that is a whole hell of a lot harder than hacking a wpa network :)

EDIT..

Hmmn now I think about it, i'm not sure how easy it might be to harvest connected mac addresses for an access point, which would compromise the security of a mac filter totally...I'll have to investigate that

---

### Post by lisati on 2008-08-05
The wireless router I use has an "attached devices" option which lets me see what's connected (and sometimes what is trying to connect)

The MAC filtering on my router is a permission-based one, rather than a "blacklist" - I tell it which devices I want to allow based on MAC address, everyone else gets blocked.

Is checking the router logs an option?

---

### Post by y@w on 2008-08-05
Ah, you want to whitelist only the ones you want in. I was under the impression you wanted to blacklist the "bad" ones. There's a definite trade-off there.. convenience vs. "security". Is using WPA2 an option?

---

### Post by cdenley on 2008-08-05
> **issih said:**
> Very true, they can change their mac address, but they have to guess one of the valid ones that you have on your network...now that is a whole hell of a lot harder than hacking a wpa network :)

EDIT..

Hmmn now I think about it, i'm not sure how easy it might be to harvest connected mac addresses for an access point, which would compromise the security of a mac filter totally...I'll have to investigate that

No guessing necessary, they just need to capture your traffic. Some wireless adapters support "radio mode" which will allow you to see all traffic it receives regardless of whether you are connected to their network. MAC filtering is not a replacement for encryption, but couldn't hurt if used in addition to encryption.

I have a cisco card that supports "radio mode" at home. It's been a while since I used it. I'm not sure if you can get the mac address from encrypted traffic, but if you're using encryption it doesn't matter much.

As far as mac filtering, or advanced DHCP settings, that entirely depends on your router. The DHCP solution you linked to is not a solution, since your neighbor can simply assign themselves a static address instead of using the assigned DHCP address. Practical jokes such as that require you to have a Linux router, gateway, or bridge.

---

### Post by pseudo-random on 2008-08-05
Before you block them, install wireshark and packet sniff them. It's your network so you're legally allowed to intercept their data. You may even find something juicy like a login to a website with a login/user name identifying the hacker to you. Just a suggestion ;)
> sudo apt-get install wireshark

---

### Post by lisati on 2008-08-05
My current setup uses a combination of MAC filtering and WEP. Yes,`I know WPA2 is better than WPA which is better than WEP, but the wireless adapter on my desktop was (is) a pain to get working properly with WPA2 under Windows, Ubuntu was happy enough using WPA2 with it, I'm looking to replace it sometime anyway.
No major risks here where I live: my neighbour (whom I used to hook into my wireless) has his own connection now, and I'm not aware of any other wireless users in the area - mostly government-subsidised rental for low-income families.

(BTW: the park over my back fence and the school at the bottom of the street were used as locations in the movie "Eagle vs Shark")

---

### Post by brian_p on 2008-08-05
> **RavUn said:**
> Someone seems to be using my wireless and I'd like to block them.  If I have their IP address and they're currently connected to my router is there a way to get their Mac address and block them completely?

Also, is there an effective way to block outside access completely?  It's already encrypted with WPA.  And, could I possibly find who it is that's connected to us?

There is a cast iron, guaranteed way of preventing anyone connecting to your wireless router. Use a 63 character random passphrase and be done with the fiffing and faffing about with dhcp and MAC filtering.

---

### Post by brian_p on 2008-08-05
> **issih said:**
> WPA is more secure than WEP, but it too is vulnerable to attack. 

Under what circumstances is WPA encryption vulnerable?

---

### Post by y@w on 2008-08-05
Personally.. at this point, I'd run a wire :)

---

### Post by issih on 2008-08-05
If you want to know about wpa vulnerabilities, then I'd suggest you look into it via the magic of google, no point making it any easier than it has to be for the less polite members of society..

Some forms of wpa are fairly secure, some aren't

---

### Post by brian_p on 2008-08-06
> **issih said:**
> If you want to know about wpa vulnerabilities, then I'd suggest you look into it via the magic of google, no point making it any easier than it has to be for the less polite members of society..

What did you want? A 'please'?

> Some forms of wpa are fairly secure, some aren't

All forms of WPA are very secure. Passphrases of adequate length and randomness don't get cracked in a timeframe which makes sense to the cracker. I'll make it easy for you, you could do with a modicum of guidance:

[http://www.dslreports.com/forum/wsecurity](http://www.dslreports.com/forum/wsecurity)

While you're there, reassessing your understanding of the security provided by MAC filtering wouldn't be a waste of time.

---

### Post by AndyCee on 2008-08-06
The brief answer to your question *"Under what circumstances is WPA encryption vulnerable"*, for those reading the thread and not familiar with WPA, is that it is possible for a malicious user to gain the passkey if it is not of adequate length and based on a dictionary word.

I realise you know this, Brian. WPA is very secure. It's implementation isn't always.

But a 63 character random passphrase? Who's hacked his network - the FBI? Wouldn't a sentence be adequate? eg. "I dare you to hack this network, b***h!"

---

### Post by slowth5 on 2008-08-07
> **AndyCee said:**
> But a 63 character random passphrase? Who's hacked his network - the FBI? Wouldn't a sentence be adequate? eg. "I dare you to hack this network, b***h!"

I don't understand the logic here.  You are only required to input the passphrase once if everything is working properly, so why not use the full potential of wpa?  

Also, spoofing a MAC address is trivial, since even I've achieved that while testing my own network.

---

### Post by Proton Soup on 2008-08-09
just change your network name to "ThisIsAVirus"

---

### Post by y@w on 2008-08-09
> **Proton Soup said:**
> just change your network name to "ThisIsAVirus"

I personally like to use "p00p" :)

---

### Post by AndyCee on 2008-08-12
> **slowth5 said:**
> I don't understand the logic here.  You are only required to input the passphrase once if everything is working properly, so why not use the full potential of wpa?  


Generally true. I have a hidden SSID, and have friends come over for network gaming, so the passphrase gets used more than once at my place.

---

### Post by hyper_ch on 2008-08-12
a hidden SSID is not really hidden at all...

---

### Post by AndyCee on 2008-08-15
I know, I've been reading up on it. I'm considering broadcasting, but I haven't gotten around to it. As it is currently hidden, I need to manually enter my password sometimes.

---

### Post by AndyCee on 2008-08-18
FYI:
My new password is "Holly Golightly has lost her shoe. It's in the pot-plant!"

[My wife is an Audrey Hepburn fan]

---

### Post by ds[de] on 2008-09-01
I hope you're joking.

You're worried about some people bypassing your wireless connection and you post your password here?

If someone has actually been inside your network and sniffed traffic, don't you think they could have seen your HTTP connection(s) to ubuntuforums.org and found out who you are by now?
You may call it paranoid but posting a password is never a good idea, even if you think nobody knows who you are.


Regards,
ds[de]

---

