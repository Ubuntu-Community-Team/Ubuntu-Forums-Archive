---
title: "Wifi Hacking Made Easy?"
date: 2011-02-28
forum: Security
---

### Post by _joecrawford on 2011-02-28
I just had a though:

why would anyone try to break WEP or WPA encryption?  I would guess that 95% of people never put an admin password on their router settings, where most of the network security is housed.  Why would people take the time to crack WEP or WAP when they can just run through the top 10 manufactures of routers, access the admin page and just reset to no encryption and then run FireSheep or whatever they want?

I am not condoning wifi hacking, it was just a thought that came to mind and I am trying to see if I am missing something here.  I can't imagine this hasn't been discussed before. Seems like a huge vulnerability that I don't know the answer to.

---

### Post by Sef on 2011-03-01
> why would anyone try to break WEP or WPA encryption? I would guess that 95% of people never put an admin password on their router settings, where most of the network security is housed. Why would people take the time to crack WEP or WAP when they can just run through the top 10 manufactures of routers, access the admin page and just reset to no encryption and then run FireSheep or whatever they want?

1) WEP is so thoroughly broken that the password can be found out in a few minutes.

2) WPA has been broken too, but not as badly as WEP (so far.)

3) People usually crack them to hide what they are doing, which is often illegal.

---

### Post by mimor on 2011-03-01
To access the admin you need to be on the network already.
So eigher, you need to be pugged in trough the wire, or you have to crack the key to connect to the router over the wireless...

---

### Post by pricetech on 2011-03-01
For some people it's just to show they can do it.

Too much time on their hands I guess.

---

### Post by brian_p on 2011-03-02
> **Sef said:**
> 
2) WPA has been broken too, but not as badly as WEP (so far.)


Would you elaborate on that? All the claimed WPA cracks I've read about have either been theoretical or of such complexity as to be unusable within any sensible timeframe.

---

### Post by sammiev on 2011-03-02
Been some good reads about WPA hacking at Backtrack. WPA can be done but it does take a little time but a very strong password can really help. GL :)

---

### Post by brian_p on 2011-03-02
> **sammiev said:**
> Been some good reads about WPA hacking at Backtrack. WPA can be done but it does take a little time but a very strong password can really help. GL :)

At

[http://http://www.aircrack-ng.org/doku.php?id=cracking_wpa](http://http://www.aircrack-ng.org/doku.php?id=cracking_wpa)

I read:

> The only time you can crack the pre-shared key is if it is a dictionary word or relatively short in length. Conversely, if you want to have an unbreakable wireless network at home, use WPA/WPA2 and a 63 character password composed of random characters including special symbols.

I wonder how successful the method described would be with ***wpaismostdefinitelyverysecure ?

---

### Post by stlsaint on 2011-03-02
> Would you elaborate on that? All the claimed WPA cracks I've read about have either been theoretical or of such complexity as to be unusable within any sensible timeframe.


Some dedicated processor resources and a database setup with pre-configured tables will do in shorter time than trying to brute your way thru!! It also takes way less time with the same processor resources and database to crack WEP than it does to crack WPA!

---

### Post by brian_p on 2011-03-02
> **stlsaint said:**
> Some dedicated processor resources and a database setup with pre-configured tables will do in shorter time than trying to brute your way thru!! It also takes way less time with the same processor resources and database to crack WEP than it does to crack WPA!

I'm not concerned about WEP. I'm concerned about the unsubstantiated claims that WPA is broken is some manner that we should all be concerned about. Your using processor resources and a database doesn't sound much different to brute forcing to me.

---

### Post by cariboo on 2011-03-02
@brian_p

Maybe this is what you are looking for?

[http://arstechnica.com/security/news/2008/11/wpa-cracked.ars](http://arstechnica.com/security/news/2008/11/wpa-cracked.ars)

---

### Post by sammiev on 2011-03-02
> **brian_p said:**
> I'm not concerned about WEP. I'm concerned about the unsubstantiated claims that WPA is broken is some manner that we should all be concerned about. Your using processor resources and a database doesn't sound much different to brute forcing to me.

You can download a large database to try to find the WPA key or send them the packets to examine for you at a price. WPA2 with a strong key made up of all different chars will likely be unbreakable at this point. GL :)

---

### Post by brian_p on 2011-03-02
> ** said:**
> @brian_p

Maybe this is what you are looking for?

[http://arstechnica.com/security/news/2008/11/wpa-cracked.ars](http://arstechnica.com/security/news/2008/11/wpa-cracked.ars)

Thanks, cariboo907. I'd seen similar articles but not this one. Close your eyes if you dislike extensive quoting of a selective nature!

> Now let's back up a little. The early coverage of this crack indicated that TKIP keys were broken. They are not. "We only have a single keystream; we do not recover the keys used for encryption in generating the keystream," Tews said.

No keys recovered - no access.

> Tews pointed out that "if you used security features just for preventing other people from using your bandwidth, you are perfectly safe," which is the case for most home users. Someone can't use this attack to break into a home or corporate network, nor decipher all the data that passes.

Couldn't be clearer. could it?

> Tews said that the basics of network security are still valid, too: for WPA with TKIP or AES, choosing a long network key, perhaps 20 characters that are relatively random, can defeat all known brute-force key cracking methods.

So - WPA is broken is far from reality. And yet I see it being repeated time and time again when WiFi is mentioned.

---

