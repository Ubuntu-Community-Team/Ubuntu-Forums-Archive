---
title: "script for counting packets?"
date: 2015-10-23
forum: Ubuntu Phone and Tablet
---

### Post by callmebruce on 2015-10-23
So I'm looking at my N5 with Ubuntu Touch 15.04r2 on it. I can see my wlan0 interface and my transmit and receive packets and TX and RX bytes. When I turn off wifi and turn on cell data, I see interface rmnet0 come up and can see it's ipv4 and ipv6 addresses. I can also see RX and TX bytes. The byte count gets cleared whenever I turn cell data off and on again. So I'm thinking if I want to get a rough idea about how much cell data traffic I'm using, I would want to look at RX and TX bytes on interface rmnet0 - probably look at then every 5 minutes. Get the starting value then store the delta.

I'm sure there must be a more elegant way to get the volume of cell data - any other choices?

I'm not interested in wlan0/wifi. I have a netflow server at home that counts that (but then I would be excluding wifi data when out and about connected to other waps). I'm mainly interested in rmnet0 interface - get base value, add delta and maybe a date or even a datetime timestamp, reset every month (or would I even need to do that, if I'm just doing deltas?)

*edit* so searching around, the following will get me some nice data: awk '/:/ { print($1,$3, $11) }' < /proc/net/dev
I would want to grab data from wlan0 and rmnet0. But before that, I need a nicer way to edit on my phone. Bluetooth doesn't work, so I can't use my bluetooth keyboard/mouse. Need to figure out if I can grab a slimport cable that would go hdmi to my monitor (using an hdmi to dvi adapter) and usb to a keyboard/mouse. Time to go cable shopping. Or just use ADB.

---

