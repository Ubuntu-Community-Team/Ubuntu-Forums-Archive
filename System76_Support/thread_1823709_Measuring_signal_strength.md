---
title: "Measuring signal strength"
date: 2011-08-12
forum: System76 Support
---

### Post by tc101 on 2011-08-12
I have an Starling netbook.  I have a big house and a wifi router.  I would like to be able to walk around the house with the netbook and see the signal strength in different rooms.  There is a little icon at the top of the screen with 4 columns that gives me some information.  As I walk around the house it changes from the highest column to the second highest column as I get farther from the wifi router.  Is there some way I could get more specific info, like an actual number for signal strength?  

Also, in the room farthest from the wifi I have a windows 7 desktop.  It tells me signal strengh is fair or poor (it fluctuates even though it is sitting still).  The ubuntu netbook tells me signal strength is pretty good (second highest bar).  I would like to figure out this difference by seeing some actual numbers on both computers.

---

### Post by zitch on 2011-08-12
Open up a terminal and run "iwconfig"?  I'm running Lucid and I get the following running with it right now:

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"brother"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:D4:78:87   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```

I'm only about 10 feet away from the AP, but I'd imagine you'd be interested in Link Quality and Signal level as you survey your house.

---

### Post by osx424242 on 2011-08-12
> I have a big house and a wifi router. I would like to be able to walk around the house with the netbook and see the signal strength in different rooms.

It's not *quite* what you're asking for, but you might be interested in building a heat map of signal strengths.  I used lewifi ([https://code.google.com/p/lewifi/](https://code.google.com/p/lewifi/)) to do this at my house a few years ago.  It doesn't give you the raw signal levels, I believe, but it does help you find the strong and weak signal areas pretty easily.

If I remember correctly, you have to do a screen capture of the picture it makes, because you can't recreate the picture from its data file.  So after you finish walking around your house, don't forget to take that screenshot!

> I would like to figure out this difference by seeing some actual numbers on both computers.

Of course, the antenna (including its orientation) on each WiFi card has a lot to do with signal strength.  So comparing signal strength between two computers at the same location will tell you more about the differences between their antennas than about the actual WiFi signal level at that location.  

> There is a little icon at the top of the screen with 4 columns

And of course, the way each version of software assigns signal levels to the bar differs, so 3 bars on one computer doesn't necessarily mean it has a stronger signal than the other computer with 2 bars; but you knew that and that's why you're looking to get actual signal levels! ;)

---

### Post by tc101 on 2011-08-12
> Of course, the antenna (including its orientation) on each WiFi card has a lot to do with signal strength.

I hadn't thought about that at all.  Can I buy a super antenna for my desk top and get a better signal?

---

### Post by osx424242 on 2011-08-12
> **tc101 said:**
> Can I buy a super antenna for my desk top and get a better signal?

Maybe, if its WiFi card has an external antenna connector (if it already has an external antenna, you may be able to unscrew the existing antenna and attach a larger one).  I've never done that, and don't know what kind of side effects that might have.

---

