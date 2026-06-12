---
title: "ufw error message twice a minute -means?"
date: 2014-12-30
forum: Security
---

### Post by Dreamer Fithp Apprentice on 2014-12-30
Running Trusty with plain Openbox as DE (like a stripped down Lubuntu), 64 bit.

ufw is logging messages that repeat twice each minute like this (some substrings substitued as indicated because I'm  not clear what part of this output is potentially sensitive): 

I've broken this up with line feeds that aren't in the original to make it easier to read:
```

Dec 23 15:22:10 m kernel:
[5_digits_different_each_repetition.6_digits_different_each_repetition]
[UFW BLOCK] IN=eth0 OUT=
MAC=alphanumeric_string_with_a_colon_as_every_third_character
SRC=numerals_and_decimals_looks_like_an_ip_address
DST=224.0.0.1 LEN=32  TOS=0x00 PREC=0x00
TTL=1 ID=5_digit_string PROTO=2

```

Or here it is in the original form:
```

Dec 23 15:22:10 m kernel:  [5_digits_different_each_repetition.6_digits_different_each_repetition]  [UFW BLOCK] IN=eth0 OUT=  MAC=alphanumeric_string_with_a_colon_as_every_third_character  SRC=numerals_and_decimals_looks_like_an_ip_address DST=224.0.0.1 LEN=32  TOS=0x00 PREC=0x00 TTL=1 ID=5_digit_string PROTO=2

```

The interval between time stamps at the beginning of the repeated sequence
alternates between 26 and 34 seconds resulting in entries alternating between
10 and 36 seconds after the minute.

My ufw status:

```
me@m:~$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip
me@m:~$

```

This stops when I physically disconnect from the internet but resumes  when I reconnect. So what does this mean? Is it a security concern?

Thanks for any thoughts you can share.

Best wishes to all for 2015.

---

### Post by Doug S on 2014-12-30
It is nothing to worry about. Something is looking for all multicast capable hosts on the network.
see also: [http://tldp.org/HOWTO/Multicast-HOWTO-2.html](http://tldp.org/HOWTO/Multicast-HOWTO-2.html) ; [http://ubuntuforums.org/showthread.php?t=2231716&highlight=224.0.0.](http://ubuntuforums.org/showthread.php?t=2231716&highlight=224.0.0.) ; [http://ubuntuforums.org/showthread.php?t=1886913](http://ubuntuforums.org/showthread.php?t=1886913)

---

### Post by Dreamer Fithp Apprentice on 2014-12-31
Thanks. That at least gives me a good place to start reading. I'll have to understand this a little better before I'm comfortable with it. If nothing else, it looks like something is wasting resources failing at the same task over and over again.

---

### Post by The Cog on 2014-12-31
IP protocol 2 is IGMP - Internet Group Management Protocol.
I guess your router is periodically asking if there are any boxes on the network who are interested in receiving multicast streams.
I think this is pretty normal part of the background babble you see on a LAN.

---

