---
title: "Wireshark sniffing"
date: 2008-11-17
forum: Security
---

### Post by DoubleMcLovin on 2008-11-17
I started playing around with wire shark recently, I'm noticing that it tracks sites that anyone on the network visits easily, but theres so much information its hard to keep track of. So theres filters, but I'm having a bit of trouble with those.

Could someone point me in the direction of a way I could set up a filter set to say look for the word "porn" or "sex" in the RAW output so that I could effectively monitor to see if people on my network are going places they shouldn't?

---

### Post by nesman89 on 2008-11-17
go to [http://revision3.com/hak5]("http://revision3.com/hak5")  they have 2 or 3 episodes about using Wireshark.  i found it quite helpful.

---

### Post by Kinstonian on 2008-11-17
'ip contains "porn"' will find all IP packets that contain "porn".  You can replace IP with TCP or UDP, or even higher protocols like HTTP or DNS if you want.  You can also use RegEx for example 'http matches "[Pp][Oo][Rr][Nn]"' will find all HTTP traffic containing the word "porn" regardless of case.

Checkout [WireShark's Display Filter Reference](http://www.wireshark.org/docs/dfref/) for more info on filters.

---

