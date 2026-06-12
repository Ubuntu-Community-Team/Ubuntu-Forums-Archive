---
title: "[SOLVED] Attempted wireless hack . . . ."
date: 2008-04-04
forum: Security Discussions
---

### Post by wannadumpwindows on 2008-04-04
I have my own home wireless network, it's secured with WPA2 and my passkey doesn't have any dictionary words in it. Someone in my neighborhood is spoofing the mac of one of my wireless clients and is probing/sniffing the network. I noticed one day when I fired up kismet to  see what was floating around. I check now and then. I happened to see him using his mac originally, and then it goes back and forth between using his and spoofing mine. I was just curious if there's anything I can do to stop it. He hasn't accessed my network at all, and there's only been one de-auth attempt to my knowledge, I've been keeping an eye on all the logs, but as I'm sure you can understand, I'm paranoid as hell. I know I know, just turn off wireless. But I don't think I should have to do that just because some little idiot wants to learn how to crack. Anyone have any tips or tricks on anything I might be able to do to deter it. Any help would be appreciated. Thank you in advance.

---

### Post by tgalati4 on 2008-04-04
Spy Versus Spy.  Now is a good time to dust off that tool box and find out what you can use to find out more about your wireless voyeur.  Build yourself a coffee can antenna and weaken the signal in his direction.  

Once kismet is set up, you can attach a USB gps and walk around the neighborhood with your laptop in your bag and capture a decent wireless signal strength profile.

Set up a honeypot (by lowering your defenses) and leave some gifts behind.  Be sure to isolate your network.  Once he's in, then you can do some interesting things in reverse.

If you can get root of his machine before he gets yours then I would say that's a win.

---

### Post by netlogic on 2008-04-04
let me guess...
Let's think about WPA-PSK
you are a paranoid that slacker macOSX hipster can break a 256 bit key?
Let me think... Let's say the possible typeable character combinations for keys of an eight character length is just above six quadrillion (that's 94 to 8th power). 

My math might be off, so let's assume his OSX LAPTOP can crack 45 hashes a second... How long would it take? Around 4 million years? If he doesn't work for the government and has an access to specialized custom mainframes, I think you are safe. I don't even think RIAA or MPAA has access to them.

are you ok?

Let me guess... You just feel like breaking something, right?

---

### Post by tamoneya on 2008-04-04
Why dont you just go over and tell him to cut it out or youll call the police. Its got to be someone near by.  It cant be that hard to figure out.

---

### Post by wannadumpwindows on 2008-04-04
I know I'm being paranoid, but hat's what got me looking into wireless security in the first place. I also know it's unlikely to be cracked. But I'd still like to be able to do SOMETHING. I've been thinkin about the honey pot idea on and off too. I have a couple old boxes layin around I could put in the DMZ and see what he's capable of, but I still need to let him in in order to do that, which is what I'm trying to prevent in the first place. So you guys really think I'm just overly paranoid, and it's not much to worry about?

---

### Post by netlogic on 2008-04-04
If you want cracker jack tricks, you are on a wrong forum brother...
There are plenty of IRCs dedicated to cracker jacks.

---

### Post by tamoneya on 2008-04-04
there is always the upsidedown internet hack with a squid proxy server.  Just google for it and you will get plenty of results.

---

### Post by wannadumpwindows on 2008-04-04
And apparently it's now wrong to ask questions about how I may be able to prevent cracking attempts on my own network? I was just curious if there were any simple deterrents, that's all!

---

### Post by Lacrimstein on 2008-04-04
You have no control over the cracking *attempts* on your network; As long as you are connected to the internet, you will have those; However, that doesn't matter. What matters is the success rate of those attempts, which for you are so far, as I understand, 0.

---

### Post by wannadumpwindows on 2008-04-04
Yeah, nothing successful, or even close. This is just the first time I've had to deal with anything of the sort, so my first reaction was extreme paranoia. But the longer I sit here and watch him probe and de-auth my clients, I'm starting to find his futile attempts rather amusing. I changed the name of my network to "your mac is **:**:**:**:**:**" of course, substituting his mac in there. So he should be very aware that I'm paying attention. If he chooses to keep it up, I'll just have to wait and see what happens I suppose . . . . . .

---

### Post by netlogic on 2008-04-04
> **wannadumpwindows said:**
> And apparently it's now wrong to ask questions about how I may be able to prevent cracking attempts on my own network? I was just curious if there were any simple deterrents, that's all!

This is how I translated you. Someone is shooting at your specialized location. You are annoyed by the gun sounds. We are telling you that hipster is just wasting his time. However, you are insisting on shooting back even it isn't necessary. Long as you have a very strong phasephrase, you are safe. WPA2 isn't WEP.

---

### Post by Lacrimstein on 2008-04-04
:lolflag:
I suggest you name your network in something that is insulting to him (he may not even know what an IP address is), like "Noob you suck at hacking"

---

### Post by wannadumpwindows on 2008-04-04
LoL. Thanks for the help guys. I now understand that I'm overly paranoid. And he's just wasting his time. And causing me to waste my own in the process. Thanks for the speedy and informative replies. I was just curious if there was any way to deter, not destroy. But, good lookin' out!

---

### Post by tamoneya on 2008-04-04
you could also stop broadcasting you SSID as well as change it so that he doesnt know what to connect to.

---

### Post by wannadumpwindows on 2008-04-04
I'll just settle my happy butt down and relax a little bit. I'll keep an eye on him. It just got me goin in the whole "OH MY GOD, I'M DOOMED" mentality. I'm ok now. LoL. Thanks. Rock On! :guitar:

---

### Post by netlogic on 2008-04-04
I'm not sure you know, but wpa/wpa2 keys aren't static keys like WEP.

Here is a link you should read
[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access)

Oh, by the way...
mac address filtering and turning off broadcast wouldn't matter. i wouldn't worry about those things. the goal is picking the right long random passphrase.

Only way to break your network is social engineering... Most crackers use social engineering and lie they got in through magic tricks. Most of the time, you cannot defeat the mathematics.

If you are worry your govt is after you, change it every week. They would need to burn a small town to get the power they need to compute. Of course, they might have a specialized math formula we all don't have... I am not a math geek, so I don't know too much about that.

---

### Post by wannadumpwindows on 2008-04-04
Thanks netlogic. That makes me feel A LOT better. And I know the mac filtering isn't gonna do anything, especially when he's already spoofing. And any good sniffer will decloak the hidden ones anyways. I use a nice long random key, so, best as I can tell, I have nothing to worry about. For now anyways . . . . . . Much appreciated!

P.S. If I was worried about our government (US) getting in, I wouldn't be connected to the net in the first place. I'm sure they've already seen anything of mine that would be of interest anyways. I've already had the full FBI background check. LoL.

---

### Post by tamoneya on 2008-04-04
SSID has nothing to do with WPA, WPA2 or WEP.  It is not part any encryption scheme

---

### Post by wannadumpwindows on 2008-04-04
No, the SSID doesn't. But hiding it keeps the honest people out. LoL.

---

### Post by netlogic on 2008-04-04
Here is a thing... Let's take it to the next level of paranoia.  Even he has a 100gigs Rainbow table (precomputed hash table).
Let's say he can increase his speed by 200x more than computing the has at 50/sec.... 200x came from 10 quadcore machines....
200x50=10,000/sec 
i am just guessing... what it will take...
25,000,000,000,000,000/10,000=250,000,000
250,000,000/60=4,166,666
41666668/24=1,736,111 days
1,736,111/365
4756 years...
so even he uses 10 quadcore pcs with a decent rainbow table, there is a chance it can take up 4756 years. Also there is a chance it might not contain your passphrase in the rainbow table.
of course, this is a brute force method.
so far that i know.  the brute force is the only way.

---

