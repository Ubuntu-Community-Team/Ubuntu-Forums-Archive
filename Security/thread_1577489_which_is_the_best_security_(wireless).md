---
title: "which is the best security (wireless)"
date: 2010-09-18
forum: Security
---

### Post by ubuntu27 on 2010-09-18
Hello everyone.
I just got my new Internet which currently it is using WEP. I want to use something more secure. I [have]("http://www.dslreports.com/forum/remark,14248880") [been]("http://******************/?Wireless-Networking-Security:-WPA-to-WPA2&id=138759") [reading]("http://www.cisco.com/en/US/products/ps10047/products_qanda_item09186a0080a39161.shtml") different articles and I am quite confused on what to use.


It seems that my modem supports the following:

WEP(Wired Equivalent Privacy) 64-bit encryption
WEP(Wired Equivalent Privacy) 128-bit encryption
WPA-PSK(Wi-Fi Protected Access Pre-Shared Key)
WPA
WPA2-PSK(Wi-Fi Protected Access 2 Pre-Shared Key)
WPA2
WPA-PSK / WPA2-PSK Mixed

An my network card has:

```
sudo iwlist wlan0 auth
wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP

```

What is the best option? I am a newbie regarding wireless network. ><;

---

### Post by CharlesA on 2010-09-18
Use WPA2 CCMP (AES) if you can. Otherwise use WPA.

WEP is trivial to crack.

---

### Post by ubuntu27 on 2010-09-18
Thank you Charles.

I have a question. What is CIPHER-TKIP and CIPHER-CCMP? I don't see it in the Modem's Configuration page.


If I choose WPA or WPA2 at modem's configuration page. It ask me for a Radiu's IP address, Radiu's port, and Radiu's key. 

"**WPA2-PSK**(Wi-Fi Protected Access 2 Pre-Shared Key)" , "**WPA-PSK / WPA2-PSK Mixed**," and "**WPA-PSK**(Wi-Fi Protected Access Pre-Shared Key)"  dosn't ask me for Radius, but it ask me for a "Pre-Shared Key". SO, that seems to be easier.

Are those compatible with my card? And which one is securer?

---

### Post by CharlesA on 2010-09-18
CCMP is probably listed as AES.
TKIP is listed as TKIP.

Use WPA2-PSK and see if it has something for AES.

---

### Post by ubuntu27 on 2010-09-18
> **CharlesA said:**
> CCMP is probably listed as AES.
TKIP is listed as TKIP.

Use WPA2-PSK and see if it has something for AES.

WPA2-PSK dosn't contain any info nor a camp on AES.
It only contains a box where it ask for _Pre-Shared Key_: (8-63 characters or exactly 64 hex digits)

None of the options list AES.

---

### Post by CharlesA on 2010-09-18
Where are you looking?

---

### Post by ubuntu27 on 2010-09-19
> **CharlesA said:**
> Where are you looking?

NETGEAR Gateway: [http://192.168.0.1](http://192.168.0.1)
At "Wireless Setings"

---

### Post by CharlesA on 2010-09-19
What model? You could check the manual to see what wireless security it supports.

---

### Post by ubuntu27 on 2010-09-19
> **CharlesA said:**
> What model? You could check the manual to see what wireless security it supports.

Netgear CGD24G

I don't know if it is accurate, but [SpeedGuide.net]("http://www.speedguide.net/broadband-view.php?hw=290") list the following as supported

WEP-64bit
WEP-128bit
WPA (TKIP)
WPA-PSK (TKIP)
WPA2-PSK (AES)
Wireless MAC Address filtering

_____

So, WPA2-PSK is AES? It didn't mention it at the modem/router's config Web site.

---

### Post by CharlesA on 2010-09-19
Looks like the one listed as "WPA2-PSK" is what you want.

Here's the manual I found:

[http://www.charter.com/customers/GETBINARY.xbin?ID=2232](http://www.charter.com/customers/GETBINARY.xbin?ID=2232)

---

### Post by ubuntu27 on 2010-09-19
> **CharlesA said:**
> Looks like the one listed as "WPA2-PSK" is what you want.

Here's the manual I found:

[http://www.charter.com/customers/GETBINARY.xbin?ID=2232](http://www.charter.com/customers/GETBINARY.xbin?ID=2232)


Perfect! Thank you Charles.

Thank you so much.

EDIT: It woks well! WOohoo!

---

### Post by CharlesA on 2010-09-19
No prob.

<Insert gripe about router/modem combo devices here> :)

---

