---
title: "[SOLVED] Can log into wireless network, but can't surf"
date: 2008-03-07
forum: System76 Support
---

### Post by tuebinger on 2008-03-07
Hello, I have a Darter Ultra model #1221.  I'm having a problem connecting to my wireless network.  I can log in with my password to our WEP network, and the networking icon shows I am connected, but I can't bring up any websites.  

This problem seems to be related to our recently giving DSL a try.  We hooked up our DSL but found it too slow, so we went back to  our cable hookup again, which I had been connected to wirelessly before with no problems.  Same password and everything, just now I can't surf.  I've tried changing the password and just setting up the network with no security, but still can't surf.  

Do you know what I might be doing wrong?  

Thanks.

---

### Post by mozetti on 2008-03-07
Can you ping any websites?

Try:```
ping google.com
```

Press Ctrl-C to stop.

If you get a response, then your DNS settings are correct and working. If you don't get a response, try:```
ping 72.14.207.99
```

If you get a response here, but not from the first one, then it means you're connected to the internet but your DNS settings aren't correct and don't work.

---

### Post by thomasaaron on 2008-03-07
Your network manager is probably not configured properly. I've see this occasionally when network manager's configuration is not EXACTLY like your router's.

If you router is set to 64-bit Hex / WEP / Open System, then network manager should be as well. Otherwise, there is a chance that it will connect but not allow you to surf.



The other possibility is that you are connecting to your Router, but your router is either improperly connected to your modem, or your modem is not connecting with your provider.

Pinging, per the previous posting will let you know if this is the case.

---

### Post by tuebinger on 2008-03-07
Here's what I've tried.  

I pinged goggle and got:  ping: 

unknown host google.com

I pinged 72.14.207.99 and got:  

From 10.0.1.1 icmp_seq=1 Destination Host Unreachable
(this repeats with seq=2, 3, etc...)

I've tried going into the Network Manager and changing the settings manually but that doesn't work.

I know that my router is connecting to my modem and my modem is communicating with my provider because I'm typing this on our macbook.  

As for the router being set to 64-bit Hex / WEP / Open System, I know it is set for WEP 128 bit ascii encryption, but I don't know about the 64-bit Hex.  I don't recall there being an option for this.  I assume it's Open System.  How do you know?   The router is an Apple Airport and has an abundance of options.  

So it works for the macbook (probably because it's an apple product) but not for the daru2.  However, it worked fine before.

Any ideas what I should do next?

---

### Post by tuebinger on 2008-03-21
Solved... sort of!  There must have been something wrong with our old Apple Airport router. After two weeks of trying to troubleshoot this problem, and hours on the phone with various tech support, we bit the bullet and bought a Netgear router.  Everything's fine now.  No connectivity issues.

Still don't know what the original problem was, but now we have a groovy round, flying saucer-shaped Apple paperweight!  :)

Our 'new' paperweight :(... next to our new router.

---

