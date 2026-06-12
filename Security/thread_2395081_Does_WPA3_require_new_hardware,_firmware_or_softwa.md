---
title: "Does WPA3 require new hardware, firmware or software?"
date: 2018-06-26
forum: Security
---

### Post by Paddy Landau on 2018-06-26
Now that the [Wi-Fi alliance has launched WPA3]("https://hexus.net/qaduyg"), does this require a hardware update or a firmware update, or can a WPA2-compatible device access WPA3 through merely an OS update?

---

### Post by #&amp;thj^% on 2018-06-26
I'm very glad you opened this thread, and it seems that all information is a bit vauge ATM.
Example: [https://forum.turris.cz/t/will-wpa3-work-on-existing-hardware/6158](https://forum.turris.cz/t/will-wpa3-work-on-existing-hardware/6158)

It's my understanding manufacturers will have to apply for WPA3 certification, and this is not feasible from business standpoint. So a way to force us to buy newer hardware.
Example: [https://community.spiceworks.com/topic/2111224-what-will-wpa3-require](https://community.spiceworks.com/topic/2111224-what-will-wpa3-require)

And a Quote form here: [https://www.howtogeek.com/339765/what-is-wpa3-and-when-will-i-get-it-on-my-wi-fi/](https://www.howtogeek.com/339765/what-is-wpa3-and-when-will-i-get-it-on-my-wi-fi/)
> Technically, WPA2 and WPA3 are hardware certifications that device manufacturers must apply for. A device manufacturer must fully implement the required security features before being able to market their device as “Wi-Fi CERTIFIED™ WPA2™” or “Wi-Fi CERTIFIED™ WPA3™”. 

Myself I'd be very surprised if it didn't require new hardware. 
But Too early to say, I would say it's likely new hardware will be required though.  (I kind of hope I'm wrong though :))

---

### Post by Paddy Landau on 2018-06-26
Thank you. It seems, then, that although we could in theory get updates via software and firmware, it won't actually happen.

Oh well, more money to be spent. Sigh.

I guess that it will be a few years before it fully rolls out.

---

### Post by uRock on 2018-06-27
I just bought a new router that doesn't support it. It might be ten years before that gets implemented in my household.

---

### Post by TheFu on 2018-06-28
My reading on this says that some old hardware will be able to have firmware upgrades to WPA3.

But if we've learned anything about wifi standards from the wifi-Alliance, it is that they don't get enough input from the true security experts before creating standards with less-than-great security.

For this reason, if you care about security, then you should always use a VPN if going over wifi networking or when using someone else's network.  Even at home, I use a VPN with my wifi devices to access my own network.  Wifi security just can't be trusted.   This is how reputable enterprises handle wifi access too.  They require 2FA and a VPN for any remote or wifi access.  You should too.

Don't believe me?  Ask any security expert with real security credentials.

---

### Post by Paddy Landau on 2018-06-29
> **TheFu said:**
> … if you care about security, then you should always use a VPN if going over wifi networking or when using someone else's network.
True, especially with public Wi-Fi, although you need a proper paid-for VPN. The free ones are unreliable and, according to what I've read, few of them take security seriously.

Using Wi-Fi on your own router with WPA2 (and later WPA3) should be OK, (unless you're handling state secrets), right?

---

### Post by TheFu on 2018-06-29
> **Paddy Landau said:**
> True, especially with public Wi-Fi, although you need a proper paid-for VPN. The free ones are unreliable and, according to what I've read, few of them take security seriously.

Using Wi-Fi on your own router with WPA2 (and later WPA3) should be OK, (unless you're handling state secrets), right?

You can run your own VPN server(s) if the goal is to protect your traffic, but not be slightly anonymous.
I use all three.
a) paid VPN for times when I want to appear to be somewhere else or in a different country.  I use AES-256  encryption, which is NOT usually the default for paid VPN providers. Normally, they default to much weaker ciphers. Many social and huge cloudy providers don't like these and break attempts to use them.

b) OpenVPN running from my home internet, for times when I'd like to appear to be from home OR when I want access to resources and/or files that are at home.  AES-256.

c) OpenVPN running on a $5/month VPS for when I'm doing work and need more control that a paid provider, but don't want to be tied to my home-location. AES-256. The downside is that the VPS leaves a direct trail and some services are blocked because VPS users aren't always nice internet people.

I don't trust **any** wifi regardless of their claimed security.  Been burned too many times. Heck, wpa2 had a major issue that was patched last fall but was available for over a decade.  Why trust that technology at all when it just isn't necessary? Same for WPA3. There will be issues with WPA3. It will be shipped with at least 5, probably 10 major problems. How long those problems remain hidden to most of the world is the real question, unless your data happens to be either a target or easy to access locations.  If you use wifi in an apartment setting, the risks are huge compared to someone living 20 miles from anyone else miles away from any major roads.  All wifi has a range farther than most people consider because they don't use good antennas. A directional antenna can vastly extend any RF - wifi, bluetooth, keyboards, mice, ...   

You might not want to give out your wifi network to family and friends either: [https://www.troyhunt.com/no-you-cant-join-my-wifi-network/](https://www.troyhunt.com/no-you-cant-join-my-wifi-network/)  Or put the wifi connection **outside** your network and treat it like you treat any foreign network.

IMHO.

---

### Post by Habitual on 2018-06-29
"It should be noted that both WPA3 and Wi-Fi Easy Connect will not hit the mainstream right away. In fact, it is going to be a many-years-long process that will require new routers and smart gadgets to support WPA3.

Therefore, WPA2 will not stop working any time soon, and devices with WPA3 support will still be able to connect with devices that use WPA2 for the working of your gadgets, but WPA3 support will eventually become mandatory as adoption grows.

WPA3 is set to roll out later this year and is expected to hit mass adoption in late 2019, when it eventually become a requirement for devices to be considered Wi-Fi certified, according to the WiFi Alliance."

says [https://thehackernews.com/2018/06/wpa3-wifi-security-standard.html](https://thehackernews.com/2018/06/wpa3-wifi-security-standard.html)

---

### Post by bodhin2 on 2018-06-29
interesting!  thanks for starting the thread.

---

