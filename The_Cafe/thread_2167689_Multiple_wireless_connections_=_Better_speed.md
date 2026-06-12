---
title: "Multiple wireless connections = Better speed?"
date: 2013-08-14
forum: The Cafe
---

### Post by MasterNetra on 2013-08-14
I'm curious, would I have better download speeds if I have my internal wireless card & my usb adapter connected to the same public wifi signal? Haven't really thought about it until now. I mean I know of course it also depends upon the speed of the server downloading from, but still.

---

### Post by varunendra on 2013-08-15
With my not-so-great knowledge about it, I don't think it is fundamentally possible.

Multiple network interfaces can be configured for load balancing *(using a load-balancing router, I don't know if even that can be done within linux OS)*, but only one of them can be used at a time to get a particular stream of data. Multiple interfaces can't be used to get the same stream of data at the same time and combine it to increase the throughput.

---

### Post by PJs Ronin on 2013-08-15
..

---

### Post by rrnbtter on 2013-08-15
Greetings,
The concept isn't new! In the early 90's I had a twenty computer office and also a college classroom multiplexing dual USR 56k modems for a expoential speed of 150k.  The thing was really fast for that day. It required a server on the other end that supported multiplexing plus matching modems. In today's world with highspeed internet, and tremendous speed from NIC's and WIFI and with cable modems, not to mention 4G Cellular I don't see the necessity for the application. Most networks run faster than the source server depending on load. The idea is possible but with no demand the infrastructure wouldn't be there. So, no!

---

### Post by MasterNetra on 2013-08-15
I asked because I use my local library for its wireless internet access and sometimes I have to sit at places in it where the signal power is low with DL speeds associated with it. Been trying it and there does seem to be improvement with me connecting with both my internal wireless card and a usb adapter.

---

### Post by ian-weisser on 2013-08-15
You're talking about "bonding" two interfaces that are connecting to the same upstream gateway.
Yes, it will improve speeds...a bit.

See [http://ubuntuforums.org/showthread.php?t=1626536](http://ubuntuforums.org/showthread.php?t=1626536) for a working example.

---

### Post by Paqman on 2013-08-15
Wifi-n does something like this already. That's why 802.11n devices have multiple antennas.

---

