---
title: "SD card reader doesn't work"
date: 2008-05-23
forum: System76 Support
---

### Post by mdozurk on 2008-05-23
Hi,
I have a relatively new gazelle value with a clean install of Hardy running on it.  I plugged in the SD card of my camera in the card reader and nothing happened.  I did a tail -f /var/log/message and no new messages are displayed when I insert the card.

To describe in detail.  I took out the sony memory stick pro duo (magic gate mark 2) 8 gb card out of my camera and put it into the sony memory stick duo adaptor (MSAC-M2).  The symbol on the adaptor matches the symbol next to the card reader so I assume they are compatible.  I stick in the card into the PC and feel that it fits into place.  The card is halfway in.

Any ideas?

Mustafa

---

### Post by jdb on 2008-05-23
I don't know about the gazelle, but on the daru2 half way in is not far enough.
Half way in there is some resistance like it's coming up against a spring.
Keep pushing it will go almost all the way in.
When released the card comes back out a little so about 1/8 inch is exposed.
To release it push again & it will come back out.

jdb

---

### Post by mdozurk on 2008-05-23
There is no spring mechanism in gazelle.  It feels like if I push any harder (after halfway) I might break something.

---

### Post by thomasaaron on 2008-05-23
I just checked on my GazV5, and the card reader works under Hardy. Also, I don't believe it is supported by the System76 driver; it works out of the box with Ubuntu.

A standard SD card slides in MORE than 3/4 of the way. So, if you are saying that your *adapter* only slides in half way, that is probably correct (as it is pretty long). You should try to just insert a standard SD card. If the standard card works, you know there is some sort of compatiblity/functionality problem with the adapter.

---

### Post by jdb on 2008-05-23
If you can't get the adaptor to work you might try a memory card reader that connects via a usb cable.
They have gotten really cheap and have slots for just about any kind of memory card your likely to come across.

jdb

---

### Post by jeamer on 2008-05-23
Any way you could try on a Pangolin running 64bit Gutsy? I've got a PanV3 and if it's reading the card I can't find it. I know I'm using the right kind of card, too; the logo on the card matches one of the logos right beside the card reader opening.

Now that I've gotten very accustomed to my compy, a review is on the way...

---

### Post by thomasaaron on 2008-05-23
jeamer,

Under Gutsy 64-bit, the card reader is supported by the System76 driver. Please go to System > Administration > System76 Driver > Install Tab > Install Button.

Then reboot your computer.

Then go to a terminal and enter: ```
tail -f /var/log/syslog
``` and press enter.
Does your computer mount the card? If not, what is the output in the terminal?

---

### Post by jeamer on 2008-05-23
Wow, there's mud on my face. If that's even how the saying goes.

I thought I had already installed the latest driver, but apparently not. Everything works great now, shows up on desktop instantly after inserting the card. I've now got a s76 launcher on my AWN to remind me. Thanks Tom.

---

