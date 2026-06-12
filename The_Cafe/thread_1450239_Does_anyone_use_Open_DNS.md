---
title: "Does anyone use Open DNS?"
date: 2010-04-08
forum: The Cafe
---

### Post by Shibblet on 2010-04-08
I've heard from a friend that was telling me that you can change your DNS settings to the OpenDNS settings, and it will keep people from being able to access "questionable" websites.

Does anyone use this?  And how well does it work?

---

### Post by juancarlospaco on 2010-04-08
I &#10084; OpenDNS
&#10004; It Works

---

### Post by handy on 2010-04-08
You heard right.

Just put the OpenDNS IP addresses into your router & away you go.

I used to use OpenDNS when I had a problem with Ubuntu loosing my DNS settings due to my ISP changing its DNS settings whenever it felt like it (which was quite often).

At least these days (though I use a different ISP) in Arch I can use the /etc/resolv.conf.head file to set my DNS address(es).

I expect that Ubuntu has found a way around this problem by now also.

---

### Post by Psumi on 2010-04-08
Tried it, didn't like it, switched back.

---

### Post by themarker0 on 2010-04-08
I use Google DNS

---

### Post by dmizer on 2010-04-08
I use OpenDNS and have for a very long while. It's fast and it works quite well, but it can interfere with local name resolution if you use them in your system settings instead of at your gateway/router.

> **Psumi said:**
> Tried it, didn't like it, switched back.

Care to elaborate on why you didn't like it? Just curious.

---

### Post by Psumi on 2010-04-08
> **dmizer said:**
> Care to elaborate on why you didn't like it? Just curious.

Made me felt every time I logged in, that my ISP would terminate my service.

---

### Post by Paqman on 2010-04-08
The content filtering aspect of OpenDNS works fairly well, but unfortunately their IP updater doesn't have a Linux version. That means that if your IP changes OpenDNS won't be able to filter your results correctly (although you're still using their DNS). The updater will run under Wine, but is a little flaky.

---

### Post by handy on 2010-04-09
I had no problems with OpenDNS at all a couple of years ago. & I used it for at least 6 months...?

---

### Post by sandyd on 2010-04-09
> **Paqman said:**
> The content filtering aspect of OpenDNS works fairly well, but unfortunately their IP updater doesn't have a Linux version. That means that if your IP changes OpenDNS won't be able to filter your results correctly (although you're still using their DNS). The updater will run under Wine, but is a little flaky.

what do you mean? you can use ddclient for that

---

### Post by Paqman on 2010-04-09
> **carlee said:**
> what do you mean? you can use ddclient for that

Yeah, looks like you can. Thanks for the tip!

---

### Post by Firestem4 on 2010-04-09
I've been using OpenDNS for almost 6 months. The service has been great. Very reliable, very responsive! Much faster than my ISP's (Time Warner) crappy DNS service.


> **Psumi said:**
> Made me felt every time I logged in, that my ISP would terminate my service.

An ISP can't terminate your service contract for using another DNS provider. Unless there is a specific clause you agreed to when you entered into your service contract (which is unheard of).

---

### Post by jfreak_ on 2010-04-09
Using OpenDNS for about 6 months. its great. its the only way I can connect to the net using my mobile.

---

