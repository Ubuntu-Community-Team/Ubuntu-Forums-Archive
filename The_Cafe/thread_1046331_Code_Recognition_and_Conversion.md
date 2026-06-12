---
title: "Code Recognition and Conversion"
date: 2009-01-21
forum: The Cafe
---

### Post by Whelk on 2009-01-21
Hey folks,

I've got a mysterious user that posts on my personal family/friends forum every now and then in odd ways.  Last time it was easy enough to translate, since he/she/it posted in binary.

However, this time they posted something that I don't recognize.  It is as follows:

QW5kIEkgbG9va2VkIGFuZCBiZWhvbGQgYSBwYWxlIGhvcnNlIGFuZCBoaXMgbmFtZSB0aGF0IHNhdCBvbiBoaW0gd2FzIERlY
XRoIGFuZCBIZWxsIGZvbGxvd2VkIHdpdGggaGltICBBbmQgcG93ZXIgd2FzIGdpdmVuIHVudG8gdGhlbSBvdmVyIHRoZSBmb3V
ydGggcGFydCBvZiB0aGUgZWFydGggdG8ga2lsbCB3aXRoIGEgc3dvcmQgYW5kIHdpdGggaHVuZ2VyIGFuZCB3aXRoIGRlYXRo
IGFuZCB3aXRoIHRoZSBiZWFzdHMgb2YgdGhlIGVhcnRo

57686f20616d20493f0d0a576865726520616d20493f0d0a43616e20796f752074656c6c3f0d0a596f75206b6e6f77206d6520
77656c6c2e0d0a57686f2063616e20492062653f0d0a436865636b206d792069702e0d0a596f75276c6c206e6576657220677
56573732e0d0a596f75722073697465732061206d6573732e0d0a

I don't know if the line breaks are intentional or a result of my forum's formatting of the long lines.  I've tried to pick out and research a few common patterns, mostly in the second set (0d0a, 6c6c) but the only thing I've come up with is that it might be some kind of unicode and I have no idea how to convert it or even how to tell which language/set it's in in the first place.

I don't really know anything about code besides HTML and CSS, so any helpful hints would be appreciated.  I'm enjoying these little puzzles/challenges thrown my way.

---

### Post by Eisenwinter on 2009-01-21
The second one looks a lot like MD5.

---

### Post by tom66 on 2009-01-21
The top one *looks like* Base64. I fed it through a decoder, and voila:

> 
And I looked and behold a pale horse and his name that sat on him was Death and Hell followed with him  And power was given unto them over the fourth part of the earth to kill with a sword and with hunger and with death and with the beasts of the earth


Don't know about the other one. I took out the line breaks in the Base64.

---

### Post by Whelk on 2009-01-21
Excellent, thanks for the help so far.  That was quick.

Tom, may I ask what you used to decode the Base64?

---

### Post by tom66 on 2009-01-21
Alright, the bottom one is encoded in ordinary ASCII hexadecimal:

> 
Who am I? Where am I? Can you tell? You know me well. Who can I be? Check my ip. You'll never guess. Your sites a mess. 


Used this tool:
[http://www.yellowpipe.com/yis/tools/encrypter/index.php](http://www.yellowpipe.com/yis/tools/encrypter/index.php)

---

### Post by wmcbrine on 2009-01-21
The second one looks like straightforward hexadecimal encoding of ASCII. You can tell it's probably ASCII by the 0d0a sequences. Might be UTF-8 or something, though. Ignore the line breaks and spaces.

---

### Post by Whelk on 2009-01-21
You folks are great - thanks for all the help.  I'm responding in kind and wondering how to get more information out of an IP.  Checking the user's IP was the first thing I did, but it didn't match any used by people I know, and I don't have any sneaky IP-tracking skills.

---

### Post by tom66 on 2009-01-21
Try an IP geolocator-thingy. It'll give you the approximate location of the IP address, according to how ISPs distribute them. However, you can't guarantee it'll be accurate, and it'll only go down to about to city level.

---

### Post by Whelk on 2009-01-21
Thanks for the tip.  I've got an idea of who it might be now.

---

