---
title: "Get GPS Location from terminal"
date: 2010-08-07
forum: The Cafe
---

### Post by ronnielsen1 on 2010-08-07
You have to have curl installed


[http://foss-boss.blogspot.com/2010/08/bash-oneliner-get-gps-location-street.html](http://foss-boss.blogspot.com/2010/08/bash-oneliner-get-gps-location-street.html)

> The following code only works if:
- You run it in a root shell (Ubuntu users do: "sudo -i" then paste it)
- You are connected via Wifi to some access point
- Your wireless adapter is called wlan0 (otherwise replace it with the correct name)
- You're using a Linux system or something similar (i.e. Windows won't really work here)

Enter the following in a terminal. It should tell you your location
> 
/bin/echo '{"version": "1.1.0","host": "maps.google.com","request_address": true,"address_language": "en_GB", "wifi_towers": [{"mac_address": "' $( iwlist wlan0 scan | grep Address | head -1 | awk '{print $5}' | sed -e 's/ //g' ) '","signal_strength": 8,"age": 0}]}'  | sed -e 's/" /"/' -e 's/ "/"/g' > /tmp/post.$$ && curl -X POST -d @/tmp/post.$$ [http://www.google.com/loc/json](http://www.google.com/loc/json) | sed -e 's/{/\n/g' -e 's/,/\n/g> PS: If the returned information is wrong, or some kind of "unknown" ..  Consider yourself lucky, very lucky! That means Google does not (yet?)  know where your wifi AP is. For the rest of us .. tin-foil all the way 

---

### Post by Bachstelze on 2010-08-07
Good heavens, and people actually do *this*?  Hello? You're running a big blob of obfuscated code as root!

---

### Post by YuiDaoren on 2010-08-07
> **Bachstelze said:**
> Good heavens, and people actually do *this*?  Hello? You're running a big blob of obfuscated code as root!
BASH is weird, but I'd not go so far as to call it "obfuscated". It's obvious what it's up to, if you take the time to read it.

---

### Post by Bachstelze on 2010-08-07
> **YuiDaoren said:**
> BASH is weird, but I'd not go so far as to call it "obfuscated". It's obvious what it's up to, if you take the time to read it.

Of course it's obvious if you know, but I'd bet a lot of money most people who ran it don't, and would have run it even if it had a big rm -rf in it.

---

### Post by YuiDaoren on 2010-08-07
> **Bachstelze said:**
> Of course it's obvious if you know, but I'd bet a lot of money most people who ran it don't, and would have run it even if it had a big rm -rf in it.
Your opinion of people's willingness to run code aside, I'm glad you agree it's not obfuscated. :)

---

### Post by Bachstelze on 2010-08-07
> **YuiDaoren said:**
> Your opinion of people's willingness to run code aside

I wish it were just my opinion.  Sadly, in almost five years here, I've seen more such cases than I can recall.

---

### Post by YuiDaoren on 2010-08-07
> **Bachstelze said:**
> I wish it were just my opinion.  Sadly, in almost five years here, I've seen more such cases than I can recall.
That I agree that there are always a few folks who will run any old code on the promise of reward aside, the above single line shell script is still not obfuscated. :)

---

### Post by emil.s on 2010-08-07
Pretty good...
Much better than all "IP-locator" services, who says I'm in "Borlänge". A Different city 40km away from here.
However, this says I'm an  industrial area 1km from here (but in the same village.)

So I guess I can leave the foil hat off for another day. :D

---

### Post by renkinjutsu on 2010-08-07
checked the coordinates on google maps and the location was on the same corner of the block as my house!

---

### Post by Kdar on 2010-08-07
oops, I made mistype, let me try again.

---

### Post by toupeiro on 2010-08-07
> **YuiDaoren said:**
> That I agree that there are always a few folks who will run any old code on the promise of reward aside, the above single line shell script is still not obfuscated. :)

qft.

---

