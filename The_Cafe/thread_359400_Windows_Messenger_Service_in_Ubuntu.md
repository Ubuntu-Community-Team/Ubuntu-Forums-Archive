---
title: "Windows Messenger Service in Ubuntu"
date: 2007-02-11
forum: The Cafe
---

### Post by esaym on 2007-02-11
Ok this is going to be the weirdest question out there...

I noticed in my firewall logs that I am getting 1000's (there are several 1000 people on my network subnet..) of blocked udp connection attempts on ports 1026,1027, and 1028.  I am guessing this is windows messenger spam.  Yet for some reason I want to view it!  I haven't had one of those annoying message pop ups in years.  I kinda want to bring back old memories you know?  And maybe even restock my illegal viagra supply..

So are there any programs in linux that will allow this?  If so I am sure the novelty of it will wear off quickly and that program will get a quick aptitude remove.  But I am still curious as to what all this is floating around on the network I am plugged into (thanks road runner...) :lol:

---

### Post by esaym on 2007-02-13
Hmm nobody with any info?  Maybe I will just use ettercap or something to sniff the packets and see if I can get anything that way...

Update:
Ok I forwarded the ports to my linux machine and got ettercap sniffing for udp packets.  Within a few minutes I was getting packets with messages like this one:

```
CRITICAL ERROR MESSAGE! - REGISTRY DAMAGED AND CORRUPTED.

To FIX this problem:
Open Internet Explorer and type:  www.registrycleanerxp.com
Once you load the web page, close this message window

After you install the cleaner program you will not receive any more reminders or pop-ups like this.

VISIT www.registrycleanerxp.com IMMEDIATELY!
```

```
STOP!
Registry Cleaner Recommended!

To download and scan computer for Registry Errors,
1. Please visit http://www.regwinclean.com
2. Download and install Registry Cleaner
3. Scan computer for any possible errors.
4. Register to complete scan corrections.

Registry cleaners can improve system performance and stabalize system..
```

Pretty worthless.  I think I am through wasting time on this... lol

---

### Post by esaym on 2007-03-01
I hate to bump an old thread but just something I found out today:

You can actually get a working windows messenger service on ubuntu.  Kopete comes with the plug in called "winpopup".  That is what you need and you need to have samba configured.  Thats it!  Of course this would only be of use in a corporate environment and even in those places I have never seen windows messenger used...

---

### Post by Boomy on 2007-03-01
I got a bunch of those exact packets when I was experimenting with Ethereal and bypassed my hardware firewall. They started almost instantly after setting my router to DMZ. There's a alot of crap out there targeted at windows users; just one more reason not to use it.

I have used gaim for an msn client.

---

### Post by AndyW on 2007-03-02
I remember when we figured this out at school. We would just spam each other. It was funny to copy and past a message dozens of times that said this is a virus and send it to an unsuspecting victim.:)

---

