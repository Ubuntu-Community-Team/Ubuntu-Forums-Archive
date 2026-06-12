---
title: "60 minutes story on vulnerabilities of WEP"
date: 2007-11-25
forum: The Cafe
---

### Post by kevdog on 2007-11-25
Just saw 60 minutes story on vulnerabilities of WEP encryption in regards to TJ Maxx debacle last year.  I was surprised how many retailers use WEP to transmit credit card data.  I thought the vulnerabilities of WEP was old news.

I knew of program named kismet, but was surprised to see the program named kismac.

---

### Post by Blutack on 2007-11-25
I once installed a BT Business Broadband system for a customer (basically a wireless modem with a pretty picture of hardworking employees smiling on the front).
As default 64 bit WEP.  They market this thing to small businesses as a blackbox solution.
I kid you not.  Aircrack would have been in in about 20 minutes.
There is a moral to that story.  (Apparently BT are also advertising IT support.  Wonder if it includes site security checks).

---

### Post by rfruth on 2007-11-25
I saw the 60 minute segment, hope it opens some eyes ...

---

### Post by p_quarles on 2007-11-25
> **kevdog said:**
> Just saw 60 minutes story on vulnerabilities of WEP encryption in regards to TJ Maxx debacle last year.  I was surprised how many retailers use WEP to transmit credit card data.  I thought the vulnerabilities of WEP was old news.

I knew of program named kismet, but was surprised to see the program named kismac.
Didn't realize that retailers were using WEP. Frankly, I find it completely insane that anyone would use *wireless* to transmit credit card numbers. I mean, if they have to, WPA2 would be perfectly safe, but are these credit card machines supposed to be mobile? Do that many stores have checkout stands that are relocated to random places every day? 

Plus, it seems completely obvious to me that any sensitive data should be encrypted before transmitting it over a network of any kind. It's been 10 years since I've worked in retail, so I don't know what the norms are, but this kind of worries me.

---

### Post by some_random_noob on 2007-11-25
Yes, dodgy indeed. Not to mention that someone could browse illegal porn via your connection *shiver*.

I should be safe though, I changed the default SSID and then made sure it doesn't broadcast it. So now the only way to hack it is to use packet sniffers. I also do MAC filtering. Even if someone hacks it it's no big deal for me, my brother is the one who uses wireless.

Oh yeah, and there are heaps of unprotected networks around anyway, which make for great cannon fodder! I'd be the last person in my neighbourhood to be hacked.

---

### Post by Palmyra on 2007-11-25
Yep.  I just saw it too.  Looks like I won't be going back to TJMAX (I sometimes shop at TJMAX) or any other place that uses WEP.  I'd prefer  a place that doesn't use a wireless connection at all.

Can't believe they would be that reckless.  I use WPA2 at home, and I'd figure that they'd be smart enough to do some homework.  If you watched the entire segment, it showed that a high level person at TJMAX actually weighed the options of switching to a more strong encryption.  He decided using WEP was worth the risk.  Well, screw you...you've lost a customer here.

---

### Post by Colro on 2007-11-25
I still use WEP out of laziness to switch all of my computers. I live out in the middle of nowhere, I can spit farther then my router's range, and no one around here would have a clue how to even connect to a wireless network in the first place, let alone crack into a WEP encrypted one. Major coperations still using it, though, is kind of sad to see.

---

### Post by n3tfury on 2007-11-25
> **some_random_noob said:**
> Even if someone hacks it it's no big deal for me

> **some_random_noob said:**
> Not to mention that someone could browse illegal porn via your connection *shiver*.



still not a big deal?

---

### Post by kevdog on 2007-11-25
After seeing that story I kind of want to go to the Home Depot parking lot and see if I can get into their network.  Maybe once in, I can do some illegal downloading of songs.  It would be great if the RIAA would actually bust the store for this.  

Seriously...The whole story is a joke.  Ive shopped at TJMaxx maybe two times in the past 10 years, and something tells me that my information was probably obtained.  Those hacks were obtaining data for 1.5 years before someone actually discovered what they were doing.

Ive really gotten into gpg/truecrypt recently.  As a previous poster stated, you would think the transmited data would be encrypted and then sent using a relatively secure wireless encryption algorithm such as WPA2.  I'm sure WPA will likely be broken in a few years, however hopefully something better will be out at that time.  

It just kind of sucks the great lengths I go to attempt to secure my data at home (and honestly if most of it were stolen it probably wouldn't matter), but how friviously stores act on your behalf to protect your data once you give it to them.

I'm not sure what the best course of action would be to hold stores to a higher standard.  I'm really against lawyers, congress since yeah that might take 10 years and really never produce anything with teeth.  Boycott -- but yeah -- I'm sure they don't care about me.  It just bugs me -- that is all.

---

### Post by n3tfury on 2007-11-25
> **kevdog said:**
> After seeing that story I kind of want to go to the Home Depot parking lot and see if I can get into their network. 

i hope you get caught and tossed into jail.  i'm joking of course, but then again, so are you.

of course, this is extreme, but still:  [http://www.securityfocus.com/news/10138](http://www.securityfocus.com/news/10138)

---

### Post by p_quarles on 2007-11-25
> **kevdog said:**
> It just kind of sucks the great lengths I go to attempt to secure my data at home (and honestly if most of it were stolen it probably wouldn't matter), but how friviously stores act on your behalf to protect your data once you give it to them.
Seriously, good point. It was just a few years ago that there were all kinds of fears about online shopping and data security. Now it turns out that it's *more *dangerous to give your credit card to a person. (and, yes, I realize that online stores could use unsecured protocols as well, but between SSL and VeriSign you at least have some evidence that they're *thinking* about security).

---

### Post by n3tfury on 2007-11-25
> **p_quarles said:**
> Seriously, good point. It was just a few years ago that there were all kinds of fears about online shopping and data security. Now it turns out that it's *more *dangerous to give your credit card to a person. (and, yes, I realize that online stores could use unsecured protocols as well, but between SSL and VeriSign you at least have some evidence that they're *thinking* about security).

it's ALWAYS been dangerous to give to a person.  we've been giving credit card numbers to people for years (waiters/waitresses for example) and they take it from you and use it out of your view alot of the time.  nobody thinks about that though.

---

### Post by kevdog on 2007-11-25
> **n3tfury said:**
> i hope you get caught and tossed into jail.  i'm joking of course, but then again, so are you.

of course, this is extreme, but still:  [http://www.securityfocus.com/news/10138](http://www.securityfocus.com/news/10138)

I read that story -- one thing I do not get.  The accomplice pleaded guilty for checking his email using Lowe's network.

So you mean to tell me that if I went to Home Depot - broke their WEP encryption, gained access to their wireless network (because that is all its going to give me at first), and I check my gmail account, I in some way have committed a crime??

How is this any different than jumping on my neighbor's unencrypted wireless network and checking my e-mail??  Something just doesn't seem right here!!

And yes I know I'm getting off track a little bit -- sorry to stray from the topic!

---

### Post by n3tfury on 2007-11-25
> **kevdog said:**
> I read that story -- one thing I do not get.  The accomplice pleaded guilty for checking his email using Lowe's network.

So you mean to tell me that [COLOR="Red"]**if I went to Home Depot - broke their WEP encryption, gained access to their wireless network **[/COLOR](because that is all its going to give me at first), and I check my gmail account, I in some way have committed a crime??

How is this any different than jumping on my neighbor's unencrypted wireless network and checking my e-mail??  Something just doesn't seem right here!!

And yes I know I'm getting off track a little bit -- sorry to stray from the topic!

how is your statement in bold red above NOT a crime?

---

### Post by p_quarles on 2007-11-25
> **n3tfury said:**
> it's ALWAYS been dangerous to give to a person.  we've been giving credit card numbers to people for years (waiters/waitresses for example) and they take it from you and use it out of your view alot of the time.  nobody thinks about that though.
Yeah, I actually remembered the stories about the portable card scanners just after I posted that. 

To make matters worse, many people are opting for these RFID credit/debit cards now. Apparently, the future of "convenience" largely means convenience for criminals. 

I do think about this, though. I had my debit card "cloned" a couple years ago. I got all my money back, but never figured out how the card number got stolen. My best guess comes from what a bank employee told me: it's possible to place a fake ATM panel over a real one. The fake ATM looks and acts just like the real thing, but instead of contacting your account, it records your card's info and responds with "network down." I'd gotten a similar message about a week before the incident. :/

---

### Post by n3tfury on 2007-11-25
> **p_quarles said:**
> Yeah, I actually remembered the stories about the portable card scanners just after I posted that. 

To make matters worse, many people are opting for these RFID credit/debit cards now. Apparently, the future of "convenience" largely means convenience for criminals. 

I do think about this, though. I had my debit card "cloned" a couple years ago. I got all my money back, but never figured out how the card number got stolen. My best guess comes from what a bank employee told me: it's possible to place a fake ATM panel over a real one. The fake ATM looks and acts just like the real thing, but instead of contacting your account, it records your card's info and responds with "network down." I'd gotten a similar message about a week before the incident. :/

yeah i've read about the cloners and the ATM panels before.  and i LOL at people that jump on RFID.  good luck, i say.

---

### Post by kevdog on 2007-11-25
So let me get this straight -- just a question -- it is illegal to crack WEP and use the cracked network for benign purposes??? 

And as far as the Lowe's story as linked to above, the guy didn't even have to crack a WEP network.  The network was open.  The accomplish pleaded to a misdemeanor checking his email on Lowe's network.  How is this a crime??  Millions of college students must be committing a crime everyday if using someone else's network is actually a crime!

---

### Post by n3tfury on 2007-11-25
> **kevdog said:**
> So let me get this straight -- just a question -- it is illegal to crack WEP and use the cracked network for benign purposes??? 

And as far as the Lowe's story as linked to above, the guy didn't even have to crack a WEP network.  The network was open.  The accomplish pleaded to a misdemeanor checking his email on Lowe's network.  How is this a crime??  Millions of college students must be committing a crime everyday if using someone else's network is actually a crime!

i wasn't referring to the article.  i was referring to your last post.  it's illegal to crack a business network.  i'm not sure why that's so hard to believe.

---

### Post by kevdog on 2007-11-25
I'm learning here.

Just a follow-up question

Is it illegal to crack a home network?? What if I run a home-based business?  Would this be considered a business or personal network?

And I guess just to sum it all up --
It is illegal for me to crack a wireless WEP encrypted network?? I'm not trying to be a smart-*** here, but I guess I've never thought about it before.  I always thought of wireless encryption as an "optional" safeguard with user-be-warned.  If the network is cracked, then it would be my fault (the owner of the network) and not the fault of the hacker.

---

### Post by p_quarles on 2007-11-25
From what I've read (IANAL), it's not clearly illegal in the U.S. to use an open wireless network without permission. Cracking an encrypted network without permission is definitely illegal, but connecting to an open network without asking is a gray area. Several people have been "convicted" for doing so, but my understanding is that this has to do with the judge's interpretation of the vague laws pertaining to the issue. 

According to a recent Slashdot article, it *is *clearly illegal to use an open network without permission in the UK.

---

### Post by p_quarles on 2007-11-25
> **kevdog said:**
> It is illegal for me to crack a wireless WEP encrypted network?? 
If you own the network in question, then it would be legal to crack it. If you attempt to crack a network without the permission of its owner -- even if it's easy -- you could be prosecuted.

---

### Post by kevdog on 2007-11-25
> **p_quarles said:**
> If you own the network in question, then it would be legal to crack it. If you attempt to crack a network without the permission of its owner -- even if it's easy -- you could be prosecuted.

Guess I didnt know that!!  And just to further clarify -- it would probably be use of the network that would be considered illegal.  If I scanned a network and obtained the WEP key, but never used the key, I would guess this wouldn't be illegal.  

Again I'm not trying to get technical here, but there are so many aircracking suites that are available, however the creators of these packages are not being prosecuted.  In fact its probably the same software that the network hackers use as the FBI.  I guess all the software being produced is intended for me to check the vulnerability of my own network :)

---

### Post by p_quarles on 2007-11-25
> **kevdog said:**
> Again I'm not trying to get technical here, but there are so many aircracking suites that are available, however the creators of these packages are not being prosecuted.  In fact its probably the same software that the network hackers use as the FBI.  I guess all the software being produced is intended for me to check the vulnerability of my own network :)
[standard caveat about getting legal advice at UF.org]

There's nothing fundamentally illegal about cracking software, since it can be used for perfectly legitimate purposes, such as security testing.

And that wouldn't be limited to only your own network. If someone hired you to test their security, you would be within your rights to use any cracking software available to attempt to crack their system. There are incorporated businesses in the U.S. that offer this as a service. As I understand it, it's just a question of permission: if someone asks you to crack something, you can legally use any app you want in order to accomplish that.

---

### Post by kevdog on 2007-11-25
Sorry for getting off track here -- I guess I learned something tonight!

---

### Post by Dr. C on 2007-11-25
Why not simply pay cash at retailers and avoid the whole issue of credit card information over unsecured wireless connections?

---

### Post by Fbot1 on 2007-11-25
> **FineE said:**
> Why not simply pay cash at retailers and avoid the whole issue of credit card information over unsecured wireless connections?

convenience

---

### Post by Dr. C on 2007-11-25
> **Fbot1 said:**
> convenience

Then one must accept the risk of identity theft associated with the chosen method of payment. Personally I see little point in using credit of debit cards to pay for a cup of coffee or similar small transactions when using a $5 bill is just as convenient, and in most cases much faster. 

On the other hand for that $500 payment credit or debit may make sense, but if the store is using an unsecured connection then paying cash may be the way to go.

---

### Post by Fbot1 on 2007-11-25
> **FineE said:**
> Then one must accept the risk of identity theft associated with the chosen method of payment. Personally I see little point in using credit of debit cards to pay for a cup of coffee or similar small transactions when using a $5 bill is just as convenient, and in most cases much faster. 

On the other hand for that $500 payment credit or debit may make sense, but if the store is using an unsecured connection then paying cash may be the way to go.

I think credit card owners are usually aware of them.

---

### Post by aysiu on 2007-11-25
Not ashamed to say we use WEP in our household.

Despite Mac fanatics' claims to the contrary (everything apparently "just works"), my wife and I have been unable to get WPA to consistently work on her G4 Powerbook. If we use WPA, the connection drops every three or four minutes. If we use WPA2, her Powerbook cannot connect to it at all.

So we use WEP, even though it's not secure.

---

### Post by Dr. C on 2007-11-25
> **Fbot1 said:**
> I think credit card owners are usually aware of them.

I would say say **some** credit and debit card owners are aware of the risks but many are not, otherwise why do we have the growing problem of identity theft with multi billion dollar fraud related to credit and debit transactions?

---

### Post by kevdog on 2007-11-25
aysui

Sounds like a driver problem to me!!

I have no idea about bsd, but I thought it could run ndiswrapper.  I know you deplore ndiswrapper, however depending on the chipset of the device (and the windows driver), I would think wpa2 should work for you.  

I might not have any clue what I'm talking about however.  My last MAC I purchased with a Macintosh SEII (the one piece machine).  I havent turned it on in years.  I thought the 2000 millenium bug would kill it, but when I last turned it on in 2002 (my first time since 1999), the date was still accurate. Wow amazing.

---

### Post by aysiu on 2007-11-25
Yeah, we've done a lot of research on the net, but we have the latest drivers installed. I'm not sure how *ndiswrapper* would help...?

---

### Post by kevdog on 2007-11-25
I'm kind of talking out of my rear end, but I would think it would give you another option to try.  Assuming your hardware supports WPA (not exactly sure what chipset we are talking about here), I would think ndiswrapper would give you windows drivers that would provide for wpa2 capability -- unless the drivers are really old.  Perhaps I shouldn't stir the pot since I don't really know what I'm talking about when it comes to BSD,MAC OSX.  Its all just a hypothesis!

---

### Post by aysiu on 2007-11-25
> **kevdog said:**
> I'm kind of talking out of my rear end, but I would think it would give you another option to try.  Assuming your hardware supports WPA (not exactly sure what chipset we are talking about here), I would think ndiswrapper would give you windows drivers that would provide for wpa2 capability -- unless the drivers are really old.  Perhaps I shouldn't stir the pot since I don't really know what I'm talking about when it comes to BSD,MAC OSX.  Its all just a hypothesis!
Well, the thing is--the hardware is *supposed to* support WPA natively in Mac OS X.

Unfortunately, my wife and I have already spent many hours researching this, and she doesn't want to futz around with her computer any more. She just wants to use it. She'd rather have an insecure wireless network than spend any more time trying to get WPA to work.

---

### Post by Dr. C on 2007-11-26
I do not know about ndiswrapper on a MAC, but you may wish to take a look at  this 

[http://www.apcc.com/resource/include/techspec_index.cfm?base_sku=WMR1000G&tab=models]("http://www.apcc.com/resource/include/techspec_index.cfm?base_sku=WMR1000G&tab=models")

If the MAC has Ethernet then this router can be used as an access point for the MAC to a wireless network and it does support WPA.

---

### Post by aysiu on 2007-11-26
> **FineE said:**
> I do not know about ndiswrapper on a MAC, but you may wish to take a look at  this 

[http://www.apcc.com/resource/include/techspec_index.cfm?base_sku=WMR1000G&tab=models]("http://www.apcc.com/resource/include/techspec_index.cfm?base_sku=WMR1000G&tab=models")

If the MAC has Ethernet then this router can be used as an access point for the MAC to a wireless network and it does support WPA.
I appreciate the input, but that seems a bit too involved. I'm not really looking for a workaround any more. I was just explaining why we use WEP, despite its vulnerabilities.

---

### Post by kevdog on 2007-11-26
Sorry for stirring the pot -- I should have just kept to myself on this one -- way off topic!

---

### Post by sammydee on 2007-12-02
Aysiu - there's an easy way of making sure all traffic transmitted over the wireless network is totally secure, and stop anybody else using it at the same time, even if it is wep.

You'll need one other computer, doesn't matter how old it is. You have to put them like this:

Laptop------wifi-------access point----wired-----linux pc-----internet/modem

Close all ports on the linux pc except ssh. It is trivially easy to set up a ssh so that the linux pc acts as a proxy. Then it doesn't matter how insecure the wifi is, all traffic is secured and nobody can use it for internet access.

You can use putty for easily setting up a dynamic port forwarding tunnel. then just tell the browser on the laptop to connect to localhost on whatever port you specified and use it as a proxy. Done!

I use this method to ensure my traffic is encrypted when I use open or wep secured access points in cafe's etc.

Sam

---

### Post by kevdog on 2007-12-02
I know this is possible -- however I cant say Ive used ssh port forwarding in this manner -- IT WOULD BE GREAT if you wrote up a how-to with exact details how to do this!!  I know this would take you some time, however I think it would be a great edition for everyone.

---

### Post by n3tfury on 2007-12-02
> **kevdog said:**
> I know this is possible -- however I cant say Ive used ssh port forwarding in this manner -- IT WOULD BE GREAT if you wrote up a how-to with exact details how to do this!!  I know this would take you some time, however I think it would be a great edition for everyone.

i don't use ubuntu much outside of my house (work is windows/vpn) but it'd be nice to have a short write up on this.

---

### Post by kevdog on 2007-12-02
I guess sammydee has left the building......

---

### Post by sammydee on 2007-12-04
nope still here

I'm sure there was already a howto about it...

however, if there isn't, i'd be happy to write one.

What forum do I put it in?

sam

---

### Post by n3tfury on 2007-12-04
> **sammydee said:**
> nope still here

I'm sure there was already a howto about it...

however, if there isn't, i'd be happy to write one.

What forum do I put it in?

sam

[http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)

but post a link in this thread please :)

---

### Post by kevdog on 2007-12-04
Just write the how-to and place it in the Networking forum.

---

### Post by n3tfury on 2007-12-04
> **kevdog said:**
> Just write the how-to and place it in the Networking forum.

you're slow.

---

### Post by sammydee on 2007-12-04
Ask and ye shall receive...

Ta daaaaaaaaa!

[http://ubuntuforums.org/showthread.php?t=631290](http://ubuntuforums.org/showthread.php?t=631290)

---

### Post by n3tfury on 2007-12-04
you rock sammy, i'm going to get this going this weekend, thanks!!!

---

