---
title: "Wireless Security?"
date: 2007-04-09
forum: Server Platforms
---

### Post by NSR500 on 2007-04-09
I typically refrain from using wireless, but may have the need to occasionally enable my router because I cannot run cable in my apartment. Is there a way or tool('s) that I can use to make sure my system is not compromised?

I have read the tutorial here: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
and I have also looked at the tools here: [http://ubuntuforums.org/showthread.php?t=9836](http://ubuntuforums.org/showthread.php?t=9836)

I understand much of what is in those discussions and am looking for guidance in what to watch out for.

Plain and Simple...

1. What network monitoring tool can I use to see if someone has compromised my system and is syphoning off packets?

2. What tool, if any, from this thread: [http://ubuntuforums.org/showthread.php?t=9836](http://ubuntuforums.org/showthread.php?t=9836) would I use?

It seems that most of the discussions are based on auditing and looking for holes, but assuming that you have put forth your best efforts; what do you use to monitor your traffic against snoopers?

Thanks for the help guys!

---

### Post by moffa on 2007-04-10
Since you're using a router, the easiest way would be to go to the router's page and see the MAC address of any clients that have connected.

---

### Post by johnnymac on 2007-04-10
First off, if your using wireless and do not want anyone so get on:

1.  Don't broadcast your ssid
2.  Use WEP or WAP
3.  Use MAC filtering and only allow certain MAC addresses to connect.

If you do those three things...only someone with ALOT of time and effort can crack it.  Once they crack the WEP key (which will be quite difficult since you'd be filtering MAC addresses), they have to figure out how to clone your MAC to even be able to use the access point.  At some point they'll just give up and go find someone who didn't secure their stuff.

---

### Post by NSR500 on 2007-04-10
Thanks Guys!

I have been employing those practices for quite some time now and regularly check my logs. My main concern is a "Near-Real Time" or "Real Time" method or tool I can use to see if someone is doing something. For example... How do I know if someone is using Airsnort, Aircrack, or some other appllication on me? 
I've setup a test rig and tried it on myself and I did not notice anything abnormal until it was cracked and I logged on with the keys. I've thought of monitoring traffic for packet injection, etc... but its a bit challenging if I'm dl'ing a torrent and maxing out my bandwith.

---

### Post by az on 2007-04-10
> **johnnymac said:**
> 
If you do those three things...only someone with ALOT of time and effort can crack it.  Once they crack the WEP key (which will be quite difficult since you'd be filtering MAC addresses), 

When you sniff packets from wireless, you are not associated with any ssid.  So restricting mac addresses, not broadcasting your ssid are irrelevant.  Cracking your WEP becomes a matter of time and packets sniffed.

Unfortunately, today's home wireless techology is not secure.  You should not have the expectation of security over wireless.  WEP, WPA, etc all make it inconvenient for a cracker, but it is far from impossible.

---

### Post by johnnymac on 2007-04-10
So, by far my favorite IDS has been SNORT.  Bad thing is...there isn't much in that arena for wireless.  But they are starting to put it together...

[http://snort-wireless.org/](http://snort-wireless.org/)

You can be adventurous and try it out.

Also...some people can be QUITE over-bearing on wireless security.  If you are using strong WEP encryption, 99% of the people will just move on to an unsecured access point (they are plentiful).  For the remaining 1% who has the urge to do it....he's in some downtown area breaking into government records or banks :)

---

### Post by huygens on 2007-04-11
If one think WEP is enough a security, then one should read this: [http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/](http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/)
:-)

And if you can read French: [http://sid.rstack.org/blog/index.php/2007/04/04/180-les-clous-sont-la-mais-vous-aviez-oublie-la-couronne](http://sid.rstack.org/blog/index.php/2007/04/04/180-les-clous-sont-la-mais-vous-aviez-oublie-la-couronne)

---

### Post by johnnymac on 2007-04-11
No one is saying WEP is enough security.  You want secure wireless - don't use it.  All you can do is take enough precautions to give someone a hard time trying to crack your wireless.  No one is going to spend the time needed to break your WEP key and|or figure out how to spoof their way through MAC address filtering...why would they when they could go a block down the road and find an access point that is not secured.  Now, if someone is able to sniff their way through grabbing your information as your surfing...hopefully your not doing anything like bank transactions, online purchasing or anything like that wireless - that would just be foolish.

---

### Post by jaheds on 2007-04-11
You can always leave your wireless network open and implement a Virtual Private Network (VPN) between the server that is connected to the wireless router and your main server/internet.  There are plenty of VPN implementation that work well in Ubuntu, and I think VPNs are considered secure by many.

You can even protect your wireless network using a WPA key, instead of leaving it open to add a bit more to your VPN protection;  but then you'd be encrypting twice and face the performance issues associated with that (it's not that bad.)

I used OpenVPN, and it was very easy to work with.  It has a nice client for Mac OS X and windows, as well as for Linux.  It doesn't use usernames and passwords if I remember correctly.  It uses certificates instead, so you just click "connect" and wait to be connected to your virtual network; and generating and issuing these certificates is easy enough using OpenSSL.

It's all about reaching a security balance.  For me that balance was just a simple WPA key on my router and no VPN.  For you, it might be different.

---

### Post by NSR500 on 2007-04-11
Thx Jaheds!

---

### Post by cookfromfrozen on 2007-04-11
Do not bother with MAC address filtering or SSID hiding, they provide no security and only cause more hassle.

To secure a wireless network, all you need to do is enable WPA and use a strong passphrase.  Preferably, the password should be the maximum length permitted by WPA (which is 63 ASCII characters or 64 hexadecimal digits) and be as random as possible.

My preferred way to generate a 63 character pseudo-random string is to use the Automated Password Generator.  It is available in the repositories (the package name is apg), and you can use it to generate a WPA passphrase like so:
```
apg -m63 -x63
```

This produces passphrases like this:

```
WoifDopAcelAgDatzyWownubbudbeyctupsadnalgEtUdwoslefNagidsojCish
MycsyitkergIakFowhoujikaQueijapDacZobdyggavjojdyapyaskOtDatonIr
ecHoygsUntOcNatulErupAycsIvOvRicAkJacIcUdbacHikOvOobOfCabgeidOp
Gosbuf7ClyufVuhejIjicEsarlOvJuexNutGenthivOymOdchephyuctEdkuWij
VobAgyaydyirrItsevnaDryelWuHeewQuiDrenfosgegtashyidaywotIpikWue
```

If you want even more security, you can use a passphrase with symbols too, though some crap routers don't support it.

Save this into a text file and transfer it to the computers you want on your wireless network, either by wired network, USB key, CD etc.  Paste this in to your wireless client.  Your network is now secure.  

The only known attack against WPA is the dictionary attack, and you have made it infeasible for an attacker to brute-force due to the sheer length of the passphrase.

---

### Post by MJN on 2007-04-11
All sound advice, but if the only known attack is dictionary based then presumably you can achieve 'sufficient' security with simply using a lengthy passphrase? Specifically I mean one you can remember/retype? Of course, the use of numbers/symbols massively help in this regard and if we're getting above 8-10 characters I am assuming this makes it impractical to attempt to break?

I'm not saying you're wrong with the random passphrase suggestion, just wondering if my approach is flawed? My preference for this is due to the occasional visitor I have to my network which I wish to allow - and they're often devices (PDA's etc) which can make the physical transfers of passphases problematic. However, that reasoning aside presumably there are merits in minimising the relative complexity of whatever security we introduce...

Mathew

---

### Post by cookfromfrozen on 2007-04-12
Another approach might be to use a passphase of 6  or 7 Diceware words.  That way you can remember it but still have  a secure passphrase.

On the other hand, even  20 pseudo-random characters will still make brute-forcing the key infeasible but  it also makes entering the key by hand much easier.

---

### Post by coxy on 2007-04-12
There are a few steps that you can follow to secure your wireless connection and they have all been mentioned.

1. Hide you SSID (even when hidden they are easy to find, but it still helps)
2. Use MAC address filtering (any Unix/Linux box can spoof a MAC address, but again it helps)
3. Use a 63 random character pass phrase and store it on a USB key or similar storage media
4. Do not use WEP; use WPA for your encryption and use your random 63 character key

WEP can be cracked in under 15 minutes (I have seen it done in less than 3) if you know how and have done it before. If you want to be very paranoid then you can change your random 63 character key at random intervals but that is not really necessary.

---

