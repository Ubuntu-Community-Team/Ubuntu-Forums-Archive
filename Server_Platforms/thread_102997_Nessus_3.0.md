---
title: "Nessus 3.0"
date: 2005-12-13
forum: Server Platforms
---

### Post by KingBahamut on 2005-12-13
Tenable Security has announced the release of Nessus 3.0. Nessus is an enterprise level vulnerability scanner and this new version brings a complete rewrite of the Nessus engine redesigned for increased speed and efficiency running on the average, twice as fast as Nessus 2. From the release: *"In addition to gaining dramatic improvements in performance, Tenable also provides an optional Direct Feed subscription service for Nessus 3.0 which provides immediate access to new vulnerability checks and entitles Nessus 3.0 users to commercial support from Tenable. The Tenable Plugins include support for a rating methodology called Common Vulnerability Scoring System (CVSS) that can be used to express the criticality of a discovered vulnerability or threat."*

----

Has anyone compiled yet? Tested on Breezy?

---

### Post by sysmin on 2005-12-13
KingBahamut,

I have gotten Nessus 3.0 to work in Breezy using the Debian package available from the Nessus web site. There is no compiling, because Nessus is now a closed source project. I haven't done any speed comparisons yet, but it is supposed to be considerably faster. One thing you will notice right away is the lack of a GUI. You have to download the GUI separately, and that is source code. The NessusClient code can also be downloaded from the Nessus web site as well. It compiled on my system just fine. One note is that I have all of the necessary libraries installed, and I am running a custom 2.6.14.3 kernel built from vanilla source. The GUI looks different as well. I am going to have to give it a good test drive, but there are no apparent problems so far.

---

### Post by cactus on 2005-12-13
I, for one, will not be using nessus anymore. 
Go openvas!
[http://www.openvas.org/doku.php?id=](http://www.openvas.org/doku.php?id=)

slightly off topic: [http://lists.grok.org.uk/pipermail/full-disclosure/2005-October/037923.html](http://lists.grok.org.uk/pipermail/full-disclosure/2005-October/037923.html)

A very interesting post. :)

---

### Post by KingBahamut on 2005-12-13
You know dunno about you guys, but all I ever needed to route out network problems were a minimalist cd , PHLAK usually, a command line , tcpdump, tcpflow, iptraf, arping, and some MAC documentation.

---

### Post by cactus on 2005-12-13
heh. most problems can be figured out with tcpdump (ethereal), ping, maybe telnet, and an old school hub.. 
rawr!

---

### Post by KingBahamut on 2005-12-13
j00 r s0 r33t c4ctu5

---

### Post by sysmin on 2005-12-13
[QUOTE=cactus]I, for one, will not be using nessus anymore. 
Go openvas!
[http://www.openvas.org/doku.php?id=](http://www.openvas.org/doku.php?id=)

slightly off topic: [http://lists.grok.org.uk/pipermail/full-disclosure/2005-October/037923.html](http://lists.grok.org.uk/pipermail/full-disclosure/2005-October/037923.html)
[/QUOTE]
I know that people are mad because they decided to close the source of the project and that is understandable. However, I see quite a few companies taking the Nessus source code, repackaging it and charging a small fortune for it. That isn't right either. Also, there is a very big misconception out there that because something is open source it is not secure. People should learn lessons from proprietary encryption algorithms, just because it's secret does not mean it's secure. So, when trying to get in to certain environments they may turn their nose up at an open source project. 

There is no doubt that the community made Nessus great. The question is, will the community still continue to work with Nessus or will they really rally around something like OpenVAS. When using a vulnerability in a business setting it is important to have something that is trusted, has been tested, and hopefully the customer has heard about, all of which Nessus is. Currently, even though they are built on Nessus, the other projects are not at that point. I really hope one of these other open source projects gets to that point, but in the meantime I am going to continue to use Nessus. I also think that many people who use the scanner will just continue to do so since it is still free. It will be very interesting to see what the future holds.

---

### Post by cactus on 2005-12-13
[QUOTE=KingBahamut]j00 r s0 r33t c4ctu5[/QUOTE]

hahaha!
I wish. 

oh wait... 
leet speak. 
you were probably being sarcastic. 
:???:

oh well.. 
/me moves on

---

### Post by KingBahamut on 2005-12-14
Still, Im very interested to see whether or not nessus will keep up.

---

### Post by g-a-c on 2005-12-15
You do realise, Bahamut, that Nessus isn't a network troubleshooter? I don't know if your post was made in a sarcastic tone, it's too early in the morning for me to tell correctly :)

And as for the whole Nessus free/non-free thing, if it really is the case that being open source meant they just got ripped off by people packaging up Nessus and passing it off as their own work then fair play to them on closing it. From what I gather they got roughly nothing contributed from the community when it was open sourced anyway.

Just as an aside, do Debian packages commonly work in Ubuntu releases? Is Nessus the exception, or the norm?

---

### Post by KingBahamut on 2005-12-15
There a here and there theory, and the after the original post about all I need is  was a poke =).

---

