---
title: "ALFA AWUS036NH was working just up until now! Please help"
date: 2017-11-24
forum: Ubuntu/Debian BASED
---

### Post by emskie on 2017-11-24
Hello all,

I have a ALFA AWUS036NH, and have been using it for the past week with absolutely no issues. All of a sudden I turn on my VM and nothing shows up for wireless connectivity.
I have disconnected/connected it numerous of times from the VM and from the USB port itself with no luck. 

when typing iwconfig into terminal, this is what is displays

[IMG]https://imgur.com/Nc0VJdw[/IMG]
[IMG]https://imgur.com/Nc0VJdw[/IMG]
<img>https://imgur.com/Nc0VJdw<img/>

---

### Post by jeremy31 on 2017-11-24
Check to see if it is blocked
```
rfkill list
```

---

### Post by emskie on 2017-11-24
> **jeremy31 said:**
> Check to see if it is blocked
```
rfkill list
```


says wireless LAN
soft blocked: no
hard blocked: no

---

### Post by jeremy31 on 2017-11-24
See the wireless script link in my signature and post results

---

### Post by emskie on 2017-11-24
> **jeremy31 said:**
> See the wireless script link in my signature and post results

I can't
I don't even have access to a "wired connection"
sorry for not saying this earlier

have attached my VM network settings

am still learning the OS
[IMG]https://imgur.com/a/RhH2H[/IMG]

---

### Post by jeremy31 on 2017-11-24
*Thread moved to **Virtualisation**.*
What does ```
ifconfig
```
Show
I would also try ```
sudo iwconfig wlan0 txpower auto
```

Does ```
iwlist scan
```
Have any results?

---

### Post by emskie on 2017-11-24
> **jeremy31 said:**
> *Thread moved to **Virtualisation**.*
What does ```
ifconfig
```
Show
I would also try ```
sudo iwconfig wlan0 txpower auto
```

Does ```
iwlist scan
```
Have any results?

see attached

---

### Post by jeremy31 on 2017-11-24
*Thread moved to **Ubuntu/Debian BASED**.*
I don't know what to do in Kali

---

