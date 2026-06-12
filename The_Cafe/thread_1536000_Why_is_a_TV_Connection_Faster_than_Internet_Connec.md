---
title: "Why is a TV Connection Faster than Internet Connection?"
date: 2010-07-21
forum: The Cafe
---

### Post by emagine on 2010-07-21
Hello everyone,

Basically, I want to know why when you use your tv service the channels show up instantly, even in hd.  But when you use an internet connection on hulu or youtube, the video must buffer.  Are tv and internet coming through different lines?  I was just curious.  Any help will be appreciated.

---

### Post by whiskeylover on 2010-07-21
The TV channels aren't being transmitted on TCPIP.

---

### Post by emagine on 2010-07-21
> **whiskeylover said:**
> The TV channels aren't being transmitted on TCPIP.
How are they being transmitted?  Do they use a more efficient type of transmission that is incompatible with regular internet transmission?

---

### Post by Cuddles McKitten on 2010-07-21
Partial answer:

Cable is a one-way protocol.  They send you information, you receive  it.  There's no acknowledgement or authentication required, so the line  doesn't have to devote any resources to allowing you to send/acknowledge  information.  The data you get from cable doesn't have any packet  headers since a small loss of information won't ruin your TV viewing  (whereas loss of a couple of bytes could easily ruin transmission of a  binary, for example).  

The biggest reason is that there are no middlemen.  "Buffering" is usually done to allow for changes in download speed.  If, say hop #10 on your way to YouTube gets bogged down with traffic for ten seconds, your video might slow down and halt if you haven't buffered.  When you're connected directly to the cable company, you don't have to worry about this.

---

### Post by emagine on 2010-07-21
> **Cuddles McKitten said:**
> Partial answer:

Cable is a one-way protocol.  They send you information, you receive  it.  There's no acknowledgement or authentication required, so the line  doesn't have to devote any resources to allowing you to send/acknowledge  information.  The data you get from cable doesn't have any packet  headers since a small loss of information won't ruin your TV viewing  (whereas loss of a couple of bytes could easily ruin transmission of a  binary, for example).  

The biggest reason is that there are no middlemen.  "Buffering" is usually done to allow for changes in download speed.  If, say hop #10 on your way to YouTube gets bogged down with traffic for ten seconds, your video might slow down and halt if you haven't buffered.  When you're connected directly to the cable company, you don't have to worry about this.
Ok, that makes sense.  Thank you!

---

### Post by juancarlospaco on 2010-07-21
> **Cuddles McKitten said:**
> Partial answer:

They send you information, you receive  it.  There's no acknowledgement or authentication required, so the line  doesn't have to devote any resources to allowing you to send/acknowledge  information.

No.
an** UDP Multicast** Stream is also like that.

---

