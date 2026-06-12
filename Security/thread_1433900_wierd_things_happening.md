---
title: "wierd things happening"
date: 2010-03-19
forum: Security
---

### Post by fragileandys on 2010-03-19
a week ago or so when my wife would attempt to access facebook.com, her browser would take her to myspace.com (she runs win 7 on her laptop).  I figured this was some type of malware or something so I ran several different virus and malware scanners on her cpu but she still has this issue.

BUT, last night when trying to access youtube.com on my laptop running ubuntu 9.1 i was being directed to myspace.com.  then today when trying to go to [www.google.com](www.google.com) i was brought to a "this is probably not the site you are looking for" page saying i was attempting to go to [www.google.com](www.google.com) but the server was identifying itslef as another address.

I messaged some other people who live in the same town and are on the same ISP as me, and they are able to access google.com just fine.  

Any ideas here?

I just ran rkhunter and chkrootkit and everything came back fine.

---

### Post by lisati on 2010-03-19
Someone playing practical jokes with redirecting your browser via your router? One of my routers has an option to redirect pages via its parental controls, one way to check if this is happening is to see if it happens on all machines connected via that router, or just one.

---

### Post by wirelessmonkey on 2010-03-19
This is almost certainly something to do with DNS.... are you using something other than your home router for DNS settings?

---

### Post by fragileandys on 2010-03-19
> Someone playing practical jokes with redirecting your browser via your router? One of my routers has an option to redirect pages via its parental controls, one way to check if this is happening is to see if it happens on all machines connected via that router, or just one.

I checked all settings on my router and nothing looked out of the ordinary

> This is almost certainly something to do with DNS.... are you using something other than your home router for DNS settings?

No, I don't use anything other than the router.  And I hadn't made any changes recently either.

I went ahead and reset my router, and it works fine now.  I have a pretty good password with remote access disabled on the router.  I have the wireless access permitted to only my laptop, my wifes and my palm pre via the mac addresses.  Not sure what the deal is, but i guess I'll post again if we run into this issue again.

thanks for the replies

---

### Post by cdenley on 2010-03-19
```

dig facebook.com
dig google.com
dig myspace.com

```

Try changing your DNS servers to:
208.67.222.222
208.67.220.220

Make sure there isn't anything funny in /etc/hosts
```

cat /etc/hosts

```

---

### Post by OpSecShellshock on 2010-03-19
Sounds a bit like client side DNS rebinding. I've never actually heard of that being implemented in production, though. Everything I've read has been theoretical. Um, change all of your passwords now that your router's been reset.

---

### Post by wirelessmonkey on 2010-03-20
There have been a few compromises for certain routers recently.... maybe this was one of them.  Make sure your router firmware is up to date!

---

### Post by slowth5 on 2010-03-21
> **fragileandys said:**
> I have the wireless access permitted to only my laptop, my wifes and my palm pre via the mac addresses

Hope that's not all you're relying on, because MAC addresses are easily spoofed. Once someone is on your network, all bets are off.

---

### Post by CharlesA on 2010-03-21
> **wirelessmonkey said:**
> There have been a few compromises for certain routers recently.... maybe this was one of them.  Make sure your router firmware is up to date!

This is usually good advice, but the latest firmware for my router breaks my VoIP service. Way to go Dlink! :)

Always read the release notes/google around before doing a firmware update, and it's generally best to only update if you are having problems (same goes for BIOS updates).

---

### Post by lisati on 2010-03-21
> **slowth5 said:**
> Hope that's not all you're relying on, because MAC addresses are easily spoofed. Once someone is on your network, all bets are off.

+1. MAC filtering on its own isn't enough - some kind of encryption as well is probably a good idea. WPA is usually better than WEP.

---

### Post by CharlesA on 2010-03-21
> **lisati said:**
> +1. MAC filtering on its own isn't enough - some kind of encryption as well is probably a good idea. WPA is usually better than WEP.

This. I don't even bother with MAC filtering, and just use WPA2 AES with a 64-bit key. Good luck cracking that bugger.

---

### Post by OpSecShellshock on 2010-03-21
The router is certainly a good place to start. The relevant logs are probably gone, though. However, the fact that it doesn't seem to have happened to all of the devices at the same time has me worried that it was something else. From what I understand, it started with one computer, and a while later the other one followed suit. That's why I think it started with DNS poisoning on the client side and was ultimately passed to the router from the "victim zero" machine. Something like that wouldn't necessarily require malware in order to work. It could just be a manipulation of cached data in the browser itself.

---

### Post by Jive Turkey on 2010-03-21
> **CharlesA said:**
> This. I don't even bother with MAC filtering, and just use WPA2 AES with a 64-bit key. Good luck cracking that bugger.

$30 and 30 min once an attacker has the packet capture.

---

### Post by CharlesA on 2010-03-21
> **Jive Turkey said:**
> $30 and 30 min once an attacker has the packet capture.

For WPA2? What are they running, CUDA?

Source, please.

---

### Post by blueridgedog on 2010-03-21
> **cdenley said:**
> [CODE]
Try changing your DNS servers to:
208.67.222.222
208.67.220.220


+1  First step to rule out DNS erros

---

### Post by Jive Turkey on 2010-04-06
> **CharlesA said:**
> For WPA2? What are they running, CUDA?

Source, please.

I was mistaken, I went back looked it up and its a dictionary style crack so it won't work on long random keys.

from [http://www.wpacracker.com/faq.html](http://www.wpacracker.com/faq.html)
> But I use WPA2 so it's cool right?

Actually, while WPA2 introduced CCMP mode as a replacement for the problematic TKIP, when run with authentication based on Pre-Shared Keys (PSK), it is still vulnerable to dictionary attacks. Our service works against both WPA and WPA2 when PSK is being used.

---

### Post by CharlesA on 2010-04-06
Thought so. Thanks!

---

