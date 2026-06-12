---
title: "Wireless connected but no internet"
date: 2018-05-12
forum: Ubuntu/Debian BASED
---

### Post by chancuu on 2018-05-12
So I can see all the networks around me and it shows I'm connected to mine (which is a hotspot) but I have no internet still .Pages won't load and I can't ping anything besides 8.8.8.8. I'll also add that I'm using kali right now. I had ubuntu 16 before this and it worked fine but I installed kali about a week ago. I used my buddys hotspot when I first installed and it worked fine. Ever since I disconnected from his I haven't had any luck. I'm posting here since its more active and kali is debian based so. Any help would be much appreciated. I'll try and post terminal out puts the best I can seeing how I'm using my phone to post this. But I'm at a loss on what to do.

---

### Post by DarkAmbient on 2018-05-13
Hi, if you don't know how to solve this you really shouldn't run Kali. Kali is a distro with tools for penetration testing, which requires a lot of knowledge about networking and IT security. 

What is the content of your resolv.conf?
```
cat /etc/resolv.conf
```

It is has no line starting with nameserver (or if there is one) try add/set it to:

```

echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf

```

This is only to test if that was the issue, the change is temporarily, if you restart your network-manager it will be reset.

---

### Post by jeremy31 on 2018-05-13
*Thread moved to **Ubuntu/Debian BASED**.*

---

