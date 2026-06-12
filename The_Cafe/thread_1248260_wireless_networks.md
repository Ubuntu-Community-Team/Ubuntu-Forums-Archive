---
title: "wireless networks"
date: 2009-08-24
forum: The Cafe
---

### Post by sandyd on 2009-08-24
can someone give me a quick rundown about wireless network security, and the different encryption protocols, and which one is best? (and no, im NOT going to turn images upside down for people who steal my wifi, like that kid on digg did. i just want then out.)

---

### Post by pwnst*r on 2009-08-24
[http://en.wikipedia.org/wiki/Wireless_security](http://en.wikipedia.org/wiki/Wireless_security)

don't bother with WEP, go with at LEAST WPA but preferably WPA2.

---

### Post by macogw on 2009-08-24
and use AES/CCMP, not TKIP.

---

### Post by pwnst*r on 2009-08-24
roit

---

### Post by gletob on 2009-08-24
> **macogw said:**
> and use AES/CCMP, not TKIP.

Use WPA2 with TKIP and AES

---

### Post by macogw on 2009-08-24
> **gletob said:**
> Use WPA2 with TKIP and AES

No, AES.  If you set "TKIP/AES" it'll just go with the more-likely-compatible one...ie. TKIP.  Boo. TKIP is a stream cypher and thusly sucky on block-like packets.  AES is a block cypher, so stick with it.

---

### Post by calrogman on 2009-08-24
Don't use WEP.  WEP sucks.  You can crack it in less than 10 minutes.

---

### Post by LookTJ on 2009-08-24
WPA2 with AES, as AES is very strong compared to TKIP

---

### Post by t0p on 2009-08-24
If you choose WPA/WPA2 with AES/CCMP, it's unlikely anyone will even try to crack your wireless security.  Even TKIP will dissuade most would-be crackers.  The encryption on WPA2 cannot currently be cracked - the only way in is if someone guesses or brute-forces your passphrase.  If you use a strong passphrase (64 "random" characters including special characters like $ and *), no one's going to crack it any time soon... like before the heat-death of the universe!

WEP is a waste of time.  WEP stands for "wired equivilent privacy", meaning it was designed to be as secure as a wired network.  And everyone knows how secure a wired network tends to be...

So, use WPA2 with AES/CCMP.  Use a long "random" passphrase inbluding special characters.  And for heaven's sake, don't write it down anywhere that any other living being is ever going to see it!  A great many security cracks occur because some clever soul writes the passphrase on a Post-It note and sticks it on the monitor or under the keyboard...

---

### Post by pwnst*r on 2009-08-24
speaking of passwords, use this:

[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

---

### Post by macogw on 2009-08-24
> **t0p said:**
> Even TKIP will dissuade most would-be crackers.  The encryption on WPA2 cannot currently be cracked - the only way in is if someone guesses or brute-forces your passphrase.  
It takes 12 minutes to crack TKIP because it's a stream cypher being used on packets (blocks).  Just sayin'

---

### Post by dragos240 on 2009-08-24
WPA. Great choice. NOT WPA2, wpa2 is hard to configure via the terminal, although, wpa is easy.

---

### Post by Swagman on 2009-08-24
Paranoid people.

I use WEP because my daughters  DS's need WEP

It's no problem

---

### Post by dragos240 on 2009-08-24
Or if you want, RAIDIUS..... To my knowledge, it's the most secure.

---

### Post by Tristam Green on 2009-08-24
> **Swagman said:**
> Paranoid people.

I use WEP because my daughters  DS's need WEP

It's no problem

WPA2 with a backend Cisco ACS Server with PEAP Authentication.

Become the NORAD you know you want to be.


I recommend usage of a MAC access list, reserved IP addresses for your devices, turn off DHCP, and WEP, WPA, or WPA2.  Take your pick, your average next-door neighbor looking to gank some free wireless will give up after not correctly guessing the password anyway.

---

### Post by cartman640 on 2009-08-24
Personally I use WPA2 with AES only, and have a MAC filter with a decent length pass phrase. Some devices won't connect to it, but neither will my next door neighbour ;) If I lived in a busy area I'd probably have a hidden SSID too, although that won't stop anyone who's really looking.

---

### Post by pwnst*r on 2009-08-24
> **dragos240 said:**
> WPA. Great choice. NOT WPA2, wpa2 is hard to configure via the terminal, although, wpa is easy.

yes, dumb down your security because it's a manual pain in the @$$ to configure via a method that's not needed.

---

### Post by t0p on 2009-08-24
> **macogw said:**
> It takes 12 minutes to crack TKIP because it's a stream cypher being used on packets (blocks).  Just sayin'

Could you refer me to some docs about this?  I'm certainly not aware of TKIP being so easily defeated.

**EDIT:** Okay, I found [this episode of Security Now]("http://media.grc.com/sn/sn-170-lq.mp3") which discusses the TKIP vulnerability in some detail.  There's also a transcript [here]("http://www.grc.com/sn/sn-170.htm").  I'm having a shuftie at it now.  I'll be in a better position to discuss this a bit later.

---

### Post by &#32 Greg on 2009-08-24
If someone actually cares enough to break through encryption, then let them.

---

### Post by t0p on 2009-08-24
> **&#32 Greg said:**
> If someone actually cares enough to break through encryption, then let them.

Not the greatest idea.  If you have an encrypted network, and the police discover it's been used to access child pornography, they will blame *you*.

Anyway, encryption is how you defend your sensitive info from all those 3v1l h4x0rs out there.  So it's a good idea to make your network's security as hard as possible.  "Letting them" break in is the last thing you want to do.  Well, the last thing *I* want to do anyway...

---

### Post by pwnst*r on 2009-08-24
> **t0p said:**
> Not the greatest idea.  If you have an encrypted network, and the police discover it's been used to access child pornography, they will blame *you*.

Anyway, encryption is how you defend your sensitive info from all those 3v1l h4x0rs out there.  So it's a good idea to make your network's security as hard as possible.  "Letting them" break in is the last thing you want to do.  Well, the last thing *I* want to do anyway...

^^this.

when people ask me "why do you go through so much 'trouble' to harden your network", i mention unwanted pedos possibly using it and they shut right up.

---

### Post by &#32 Greg on 2009-08-24
There are plenty of things that can happen to you, honestly, the off-chance of someone deciding to break through my encryption, look at child pornography, and then get me caught are pretty small.

Seriously '64 random character (including special characters) passphrase with WPA2 encryption, and AES not TKIP..." I suppose whatever helps you sleep at night, but I'd find the hassle of entering that in every time someone visiting wants to use their laptop to be a little much.

---

### Post by t0p on 2009-08-26
> **&#32 Greg said:**
> There are plenty of things that can happen to you, honestly, the off-chance of someone deciding to break through my encryption, look at child pornography, and then get me caught are pretty small.

Maybe so.  Maybe you don't bank online either, or pass other sensitive info over your network to the internet.  But if you do, and you've got crap security, maybe someone will sniff the traffic, get your credit card numbers and run up some serious debts.  Or grab a few passwords and recruit your box for a botnet.  Or... you get the idea (hopefully).

> **&#32 Greg said:**
> 
Seriously '64 random character (including special characters) passphrase with WPA2 encryption, and AES not TKIP..." I suppose whatever helps you sleep at night, but I'd find the hassle of entering that in every time someone visiting wants to use their laptop to be a little much.

Who said anything about typing?  You could put it on a usb stick.  Technology is so helpful.

---

### Post by t0p on 2009-08-26
> **macogw said:**
> It takes 12 minutes to crack TKIP because it's a stream cypher being used on packets (blocks).  Just sayin'

Okay mac, I've looked at various info about the vuln you're referring to and I haven't seen anything to suggest it's possible to crack WPA/TKIP like you're suggesting.

If I'm wrong then please please supply a link to show me.  Because I like to think I'm relatively *au fait* re security issues.

---

### Post by macogw on 2009-08-26
> **t0p said:**
> Okay mac, I've looked at various info about the vuln you're referring to and I haven't seen anything to suggest it's possible to crack WPA/TKIP like you're suggesting.

If I'm wrong then please please supply a link to show me.  Because I like to think I'm relatively *au fait* re security issues.

[http://news.softpedia.com/news/WPA-Encryption-No-Longer-Secure-97418.shtml](http://news.softpedia.com/news/WPA-Encryption-No-Longer-Secure-97418.shtml)
> NetworkWorld reports that, according to Dragos Ruiu, the PacSec organizer, in order to crack the TKIP (Temporal Key Integrity Protocol) key, the researchers found a way to trick the router into sending them large amounts of encrypted data. Combining this with what Ruiu calls a “mathematical breakthrough”, the attack time was reduced to a matter of minutes, between 12 and 15. 

---

### Post by t0p on 2009-08-26
> **macogw said:**
> [http://news.softpedia.com/news/WPA-Encryption-No-Longer-Secure-97418.shtml](http://news.softpedia.com/news/WPA-Encryption-No-Longer-Secure-97418.shtml)

Thanks, I shall have a shuftie at that later.

---

### Post by t0p on 2009-08-26
Well, reading that article at **Softpedia** led me to do some googling, which led me to a pdf of the paper "Practical attacks against WEP and WPA" by Martin Beck and Erik Tews (the discoverers of the vulnerability).  If you want to have a read of it, you can download it from [here]("http://ihatehate.wordpress.com/2009/08/26/beck-tews-and-their-wpa-attack/").

Interesting stuff.  It's certainly a kick up the butt for all of us who've grown rather lazy trusting WPA like it's bullet-proof or something.  WPA is certainly *not* bullet-proof!!

---

### Post by Skripka on 2009-08-26
> **t0p said:**
> Well, reading that article at **Softpedia** led me to do some googling, which led me to a pdf of the paper "Practical attacks against WEP and WPA" by Martin Beck and Erik Tews (the discoverers of the vulnerability).  If you want to have a read of it, you can download it from [here]("http://ihatehate.wordpress.com/2009/08/26/beck-tews-and-their-wpa-attack/").

Interesting stuff.  It's certainly a kick up the butt for all of us who've grown rather lazy trusting WPA like it's bullet-proof or something.  WPA is certainly *not* bullet-proof!!

Nothing is "bullet-proof".

You can lock your bike up with a U-lock and a Kryptonite chain lock, and someone will just pull out their diamond-coated circular saw.

If someone wants to crack your wireless net, they will.  The only question is how much work you make it.  The odds are that if someone has the know-how to beat a simple MAC whitelist, that your WEP or WPA or WPA2 etc security won't pose that much of a challenge either...of course your odds of ever having someone even ABLE to beat even a simple MAC whitelist to try to break into your network are quite low.


What is neat is that people have used multiple NVidia GPUs to crack WPA2 in a matter of hours simply by brute force.  Yea...all that effort to secure your wireless and it can still be beat in a matter of hours with a brute-force style attack.

[http://arstechnica.com/security/news/2008/10/company-puts-nvida-gpus-to-work-cracking-wireless-security.ars](http://arstechnica.com/security/news/2008/10/company-puts-nvida-gpus-to-work-cracking-wireless-security.ars)

---

### Post by t0p on 2009-08-26
> **Skripka said:**
> 
If someone wants to crack your wireless net, they will.  The only question is how much work you make it.  The odds are that if someone has the know-how to beat a simple MAC whitelist, that your WEP or WPA or WPA2 etc security won't pose that much of a challenge either...of course your odds of ever having someone even ABLE to beat even a simple MAC whitelist to try to break into your network are quite low.


You're really simplifying this.  Beating a MAC filter is trivial.  Defeating WPA2/CCMP is far from trivial.

> **Skripka said:**
> 
What is neat is that people have used multiple NVidia GPUs to crack WPA2 in a matter of hours simply by brute force.  Yea...all that effort to secure your wireless and it can still be beat in a matter of hours with a brute-force style attack.

[http://arstechnica.com/security/news/2008/10/company-puts-nvida-gpus-to-work-cracking-wireless-security.ars](http://arstechnica.com/security/news/2008/10/company-puts-nvida-gpus-to-work-cracking-wireless-security.ars)

That arstechnica "article" simplifies these matters even more than you.  (I write "article" in quotes because it's more like an ad.)  And [if you look at Elcomsoft's own publicity]("http://www.elcomsoft.com/distributed_password_recovery.html"), you'll see even more dubious claims and hand-waving.  Using a CPU, brute-forcing a strong WPA2 passphrase would take many thousands of years.  Elcomsoft's GPU-harnessing techniques might be able to reduce that to a century or two.  It will *not* defeat WPA2 security in "a matter of hours".

Of course, as the technology improves, so too will the cracker's tools.  But security systems will improve along with them.  When it becomes possible to break WPA2 within a reasonable timeframe, we'll have WPA3 or 10 or whatever.

Don't get me wrong, I'm not claiming that security software is unbeatable.  But the fact is that the weak point is the human.  The idiot who uses his ex-girlfriend's name as a passphrase instead of a random 64-character string will find his sytem pwned no matter what wondrous technology he's bought.  Whereas the sensible user will have a network so secure that most crackers won't even bother trying.

---

### Post by bodhi.zazen on 2009-08-26
> **carlee said:**
> can someone give me a quick rundown about wireless network security, and the different encryption protocols, and which one is best? (and no, im NOT going to turn images upside down for people who steal my wifi, like that kid on digg did. i just want then out.)


IMO if you are broadcasting your packets for all to hear, the expectation for privacy is unreasonable.

If you wish to feel better, use WPA, but best to assume it is insecure.

---

### Post by doas777 on 2009-08-26
I'm trying to decide on a practical means to isolate a wifi net for things like ds's and cell phones, but without exposing my internal network itself. I don't worry nearly so much about someone accessing my internet, as i do about them accessing my boxes.

---

### Post by pwnst*r on 2009-08-26
> **doas777 said:**
> I'm trying to decide on a practical means to isolate a wifi net for things like ds's and cell phones, but without exposing my internal network itself. I don't worry nearly so much about someone accessing my internet, as i do about them accessing my boxes.

Linksys WRT54GL (or equivalent), DD-WRT, VLANS or segregated hot spot.

---

### Post by doas777 on 2009-08-26
> **pwnst*r said:**
> Linksys WRT54GL (or equivalent), DD-WRT, VLANS or segregated hot spot.

VLANs would be a good bet, if I can split my wifi interface into differant lans.  not sure if that is possible, but might work

---

### Post by pwnst*r on 2009-08-26
> **doas777 said:**
> VLANs would be a good bet, if I can split my wifi interface into differant lans.  not sure if that is possible, but might work

you can with DDWRT and a Linksys WRT54GL :D

---

