---
title: "covering my butt in the open"
date: 2008-05-10
forum: Security
---

### Post by Redneo on 2008-05-10
How do protect my self on open wifi like at Starbucks I read about Tor are there better options than Tor?

---

### Post by pveith on 2008-05-11
Depends on what you want to hide. There are "webwashing" plugins for firefox, which do not rely on sending packages throug a whole network.

You might want to try "PhProxy - InBasic 3.0.2C" from mozilla.org filed unter Firefox addons, this is also a webproxy, which gets good comments (direct link would be german, so here just the keywords).

By the way: Tor does not help you with attacks from the local network, so your bud is in the open in starbucks ;P ...

---

### Post by daschl on 2008-05-11
well, the real problem is that unsecured networks are unsecure (huh...). you can just try to make it "less unsecure" but not really secure.. if you are in the public you have to be aware of those who might want to steal your data and as an example i never do anything really personal at public internet hotspots.. for websurfing it is ok, and if the websites you want to use, use shttp it shouldnt be a problem either.. just think about pop,ftp,http,.. as they send all packages unencrypted

---

### Post by Uinluan on 2008-05-11
I have an ssh server set up at my home that I log into and then proxy all my traffic through that connection.  I originally set this up so that sites that are block at my work that I need to help me fix or repairs computer systems are still available to me.  This will encrypt your traffic and keep others from sniffing it.  However, it is always best to not visit any site where you have to put personal information in while on a public hotspot.  I hope this helps.  If you google socks proxy you can find step by step procedures to set this up.  I would explain it here but it would take a bit of space and I don't always explain things the best.  What makes sense to me doesn't always makes sense to everyone else.

---

### Post by kevdog on 2008-05-12
As alluded to above, here are the specific instructions how to tunnel your ssh connection (included DNS requests) over ssh back to either your home router (if using dd-wrt) or through an ssh daemon on your computer at home.  It does not include instructions how to set up the ssh daemon.  With this method even if you enter passwords and such they will not be sniffed:
[http://ubuntuforums.org/showthread.php?t=723025&highlight=wormser](http://ubuntuforums.org/showthread.php?t=723025&highlight=wormser)

---

### Post by Monicker on 2008-05-12
> **daschl said:**
> well, the real problem is that unsecured networks are unsecure (huh...). you can just try to make it "less unsecure" but not really secure.. if you are in the public you have to be aware of those who might want to steal your data and as an example i never do anything really personal at public internet hotspots.. for websurfing it is ok, and if the websites you want to use, use shttp it shouldnt be a problem either.. just think about pop,ftp,http,.. as they send all packages unencrypted

You still need to be careful about secure protocols such as https when using an unencrypted wifi connection.  Using tools like ettercap for a mitm attack, you can present your own certificate and thus view the encrypted traffic also.  The user will get a warning about the certificate not being correct, but some people just ignore that warning and proceed anyway.

And if the encryption being used for the wifi is WEP, you should still consider it wide open.  I've tested aircrack at home, and been able to get the correct WEP key on my router in as little as 2 minutes.

---

### Post by HermanAB on 2008-05-12
I run a SSH listener on port 80 on a server at home.  That way I can securely forward anything I want through there, since nobody even blocks port 80.

---

### Post by brian_p on 2008-05-12
> **Monicker said:**
> You still need to be careful about secure protocols such as https when using an unencrypted wifi connection.  Using tools like ettercap for a mitm attack, you can present your own certificate and thus view the encrypted traffic also.  The user will get a warning about the certificate not being correct, but some people just ignore that warning and proceed anyway.

This sounds interesting and I should educate myself about SSL certificates, but how far off the mark would I be if I thought

1. The MITM cannot possibly send a genuine certificate, and
2. No warning would indicate a genuine certificate so it would be ok to go ahead with a financial transaction?

I'm thinking along the lines that it is the ignoring of the warning which is the problem in what would otherwise be a safe communication.

> And if the encryption being used for the wifi is WEP, you should still consider it wide open.  I've tested aircrack at home, and been able to get the correct WEP key on my router in as little as 2 minutes.

WPA-PSK would be fine then? No possible MITM attack?

---

### Post by Monicker on 2008-05-12
Ettercap creates a spoofed certificate containing all of the information from the fields in the original certificate.  Its certficate is self signed though, which is why you will get a browser warning that something is wrong with it.

WPA-PSK is very strong as long as you use a good pre-shared key - not a dictionary word, and not too short.  You can use up to 63 characters for a psk.  Someone can still try a dictionary attack, but those operations are very time consuming.  I personally use a 35 character psk for my home wireless network.

---

### Post by brian_p on 2008-05-12
> **Monicker said:**
> Ettercap creates a spoofed certificate containing all of the information from the fields in the original certificate.  Its certficate is self signed though, which is why you will get a browser warning that something is wrong with it.

So a valid certificate is correctly signed and cannot be spoofed. Ignoring a warning (could it be spurious?) is definitely not in your best interests. Has a ssh tunnel any advantages over simply ensuring the certificate is kosher? I can see a possible disadvantage in that a machine has to be up and running at the other end of the tunnel.

> WPA-PSK is very strong as long as you use a good pre-shared key - not a dictionary word, and not too short.  You can use up to 63 characters for a psk.  Someone can still try a dictionary attack, but those operations are very time consuming.  I personally use a 35 character psk for my home wireless network.

I talked myself into a 63 random character one. I couldn't see why not.

---

### Post by FakeOutdoorsman on 2008-05-12
> **kevdog said:**
> As alluded to above, here are the specific instructions how to tunnel your ssh connection (included DNS requests) over ssh back to either your home router (if using dd-wrt) or through an ssh daemon on your computer at home.  It does not include instructions how to set up the ssh daemon.  With this method even if you enter passwords and such they will not be sniffed:
[http://ubuntuforums.org/showthread.php?t=723025&highlight=wormser](http://ubuntuforums.org/showthread.php?t=723025&highlight=wormser)

I second kevdog's router solution.  Very effective and power efficient.

---

