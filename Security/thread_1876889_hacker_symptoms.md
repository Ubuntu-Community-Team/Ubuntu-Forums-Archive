---
title: "hacker symptoms"
date: 2011-11-07
forum: Security
---

### Post by Cu Rua on 2011-11-07
Somebody told me he could hack my wireless from his laptop in under 30 seconds, which I took to be a promise he would. Since then, during shut down, my computer runs an increasing number of network debugging lines across the screen just before it turns off. I'm not sure what it means, but I have a strong feeling this hacker may be behind it. Any thoughts? Suggestions?

---

### Post by OpSecShellshock on 2011-11-07
I get a whole lot of messages on the screen when shutting down as well. They go by quickly, so I'm not sure how to suggest going about listing them here. Most likely they have nothing to do with someone saying they can hack your wireless (which itself could mean several things).

If you've allowed your friend to connect to your access point, then there's no need for any hacking, so the first thing to do is confirm you haven't done that. Then there are some other things you can do. Find out what kind of wireless router you have, and download the manual from the manufacturer's website. It will tell you how to access its administration console. Connect to it directly with a cable (not over wireless) and access that page. Follow instructions to reset the administration password. Note that this will be different than the password you enter to connect to the wireless access point.

After resetting the password, go to the section of the administration page where you can configure the wireless itself. For encryption, select WPA2. If that isn't listed, then at least select WPA. You'll need to create an encryption key/password. It will allow up to 63 characters, so use them all. This key will be stored in your computer after the first time you enter it, so it's not something you'll have to constantly remember. Keep track of the key (writing it down is fine, but be sure to store it in a place only you can get it).

I strongly suspect that at most your friend was talking about cracking the password for the wireless access point, which under some conditions can be done fairly quickly, at which point someone has access to your network and will be able to intercept your web traffic over the air between your computer and your access point. That's true with any open wi-fi as well, so it's still pretty bad but is a risk many people accept every day at coffee shops and things. And again, it probably is not related to the messages on your screen when shutting down.

---

### Post by Drenriza on 2011-11-07
Why does he think he can crack the network security in the first place? What network security are you using? If you use WEP change to WPA2, and it is close to impossible, if you also use a strong keyword.

---

### Post by Dangertux on 2011-11-07
> **Cu Rua said:**
> Somebody told me he could hack my wireless from his laptop in under 30 seconds, which I took to be a promise he would. Since then, during shut down, my computer runs an increasing number of network debugging lines across the screen just before it turns off. I'm not sure what it means, but I have a strong feeling this hacker may be behind it. Any thoughts? Suggestions?

I would say if you're using WEP (which is probably what he's referring to) he could gain access to the network in ~30 seconds. I find it highly unlikely he could gain access to your personal machine that quickly. Unless of course he happens to know your credentials for SSH or VNC if you're using that. 

As was already stated I really think it has nothing to do with the "messages" appearing when you shut down your system though.

---

### Post by drdos2006 on 2011-11-07
From the terminal, run "ifconfig"
This will give you your MAC address and your router allocated IP address.

Then log in to your router and see if anybody else is connected to your router. Your MAC address should show in "Attached Devices". 

If any other MAC addresses are showing and you are the only one that you are aware of connected to your router, then you may have a problem.

regards

---

