---
title: "&quot;cfg80211: Current regulatory domain updated by AP to: US&quot; - what???"
date: 2010-05-04
forum: Security
---

### Post by mango42 on 2010-05-04
```
 ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  4 15:30:09 xx kernel: [   36.080969] cfg80211: Calling CRDA for country: US
May  4 15:30:09 xx kernel: [   36.083219] cfg80211: Regulatory domain: US
May  4 15:30:09 xx kernel: [   36.083221] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May  4 15:30:09 xx kernel: [   36.083225] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
May  4 15:30:09 xx kernel: [   36.083229] cfg80211: Regulatory domain: US
May  4 15:30:09 xx kernel: [   36.083230] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May  4 15:30:09 xx kernel: [   36.083234] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  4 15:30:09 xx kernel: [   36.083237] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
May  4 15:30:09 xx kernel: [   36.083240] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  4 15:30:09 xx kernel: [   36.083243] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  4 15:30:09 xx kernel: [   36.083246] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
May  4 15:30:09 xx kernel: [   36.083250] cfg80211: Regulatory domain: 98
May  4 15:30:09 xx kernel: [   36.083252] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May  4 15:30:09 xx kernel: [   36.083255] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May  4 15:30:09 xx kernel: [   36.083269] cfg80211: Current regulatory domain updated by AP to: US
May  4 15:30:09 xx kernel: [   36.083271] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May  4 15:30:09 xx kernel: [   36.083274] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
```


This is a new one to me! How come my 'regulatory domain' is the US when I live in Europe?

It seems the net is becoming a monster thanks to the recent demands of the US Senate and the 'entertainment industry', IMO.

---

### Post by cdenley on 2010-05-04
The regulatory domain is about radio frequencies, not about the entertainment industry. I don't use wireless so I can't test it, but you can try:
```

echo options cfg80211 ieee80211_regdom=EU|sudo tee /etc/modprobe.d/regdom.conf

```
then reboot

Depending on what country you are in, there may be a country-specific regulatory domain you should use.

---

### Post by mango42 on 2010-05-05
Many thanks for the exploratory code, **cdenley**. Once I've checked what **sudo tee** does, I'll give it a whirl.

It's the 'entertainment industry' which first brought intense lobbying pressure to bear on Washington to get the net 'regulated' (in their favour!) - then Senator Rockefeller started to realise that all his family's nefarious criminal enterprises were being exposed on the net - and now it's reached the stage of 'cyber-warfare' and 'full spectrum dominance' and other such mind-bending paranoia and greed-driven idiocy.

The net was such a positive, helpful place before Go00ogle emasculated Deja News - hey ho, ten years of public domain information, not to mention extraordinarily useful algorithms, down the cyber drain...

---

### Post by OpSecShellshock on 2010-05-05
In this particular case it's just about the use of over-the-air frequencies. 80211 is a set of wireless data standards, and "regulatory" just means the sets of protections against interference in communications. The "AP" in the string stands for access point, which to me suggests that it's not local to your computer at all, but rather is being determined by the wireless access point that your computer is connecting to. Depending on whether or not you own the access point, you may be able to log in to the administration interface and see if there are other regulatory guidances that are more local to where you live. Check the manual of the router.

---

### Post by mango42 on 2010-05-07
> **OpSecShellshock said:**
> In this particular case it's just about the use of over-the-air frequencies.

Thanks for your explanation, **OpSecShellshock** - perhaps the paranoia was getting to me, too ;-)

---

