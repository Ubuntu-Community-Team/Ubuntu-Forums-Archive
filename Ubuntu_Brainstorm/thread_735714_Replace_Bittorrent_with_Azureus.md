---
title: "Replace Bittorrent with Azureus"
date: 2008-03-25
forum: Ubuntu Brainstorm
---

### Post by WarMonkey on 2008-03-25
I think most people would rather use Azureus than bittorrent. Azureus is more user friendly, and seems to have faster download speeds for most people compared to the default bittorrent client.

---

### Post by andyho on 2008-03-25
I used azureus, abc, and utorrent on my windows machine before.. I finally settled on utorrent. I use ktorrent now though. :)

---

### Post by smartboyathome on 2008-03-25
By the way, Transmission is now the default bittorrent client in Hardy, and Azureus is not for ubuntu imo, it uses java which iis slower.

---

### Post by Asham on 2008-03-26
**Is Java really THAT slow?** I thought it was more due to the fact that Azureus is kinda bloated, or at least anything but lightweight.

---

### Post by bruce89 on 2008-03-26
Good luck fitting Java on the CD.

---

### Post by Asham on 2008-03-27
The Java runtime is about 20 Mb large so I don't really see your point.

---

### Post by Lord Illidan on 2008-03-27
I'd rather use Deluge any day over the bloated application that is Azureus. Don't get me wrong, it's a good application, but space on the CD is limited, and yes, adding Java into the mix will have an effect.

There's 20MB for Java, and 11 Mb for Azureus. 31 MB..

Transmission and Deluge both clock in at under 5 mb, their dependencies are already included in Ubuntu.

---

### Post by celliott on 2008-03-27
I use TorrentFlux. I find it way better then any of the other applications. Plus i install it right on my media server and i can download everything right to it via web browser.

Check it out, very cool.

[http://www.torrentflux.com/]("http://www.torrentflux.com/")

Cheers

---

### Post by Asham on 2008-03-27
It was a long time ago I gave up on Azureus, mostly for its bloat and memory footprint.  I like Transmission and especially Deluge for the plugins and its UI is very familiar to uTurrent which I use when on Windows.

Still I hope Sun's JRE is included in Ubuntu some day. Java is not as bad as many make it out to be. Though it could be improved on in some aspects but I'd say that goes for most software.

---

### Post by madmetal on 2008-03-27
> **Lord Illidan said:**
> I'd rather use Deluge any day over the bloated application that is Azureus. Don't get me wrong, it's a good application, but space on the CD is limited, and yes, adding Java into the mix will have an effect.

There's 20MB for Java, and 11 Mb for Azureus. 31 MB..

Transmission and Deluge both clock in at under 5 mb, their dependencies are already included in Ubuntu.

simple and nice..
i think the discussion about the default bittorrent client is too old and since transmission is the default from now on is also pointless..

also when making a suggestion always think of factors like cd space limit , community and trends  ;)

---

### Post by bruce89 on 2008-03-28
> **Asham said:**
> The Java runtime is about 20 Mb large so I don't really see your point.

Here are the compressed sizes (i386):

openjdk-6-jre = 212k
openjdk-6-jre-headless = 23.5M
libaccess-bridge-java = 423k
openjdk-6-jre-lib = 4938k
tzdata-java = 140k

Considering the fact that there is only a few MB left on the CDs on some architectures, Java will never be installed by default.

---

### Post by Asham on 2008-03-28
Ok, first I hope you can accept my apologies if I came of as being rude. Sorry about that. 


Why not ship the JRE from Sun instead; it's smaller, "only" 18 Mb all in all. And even if it's still early, how about the new JRE a.k.a the Java Kernel? It should be just a couple of (likely 2-4) mega bytes large and it's scheduled to be released in the summer if I am not mistaken. But it may not be ready for general use just yet. I wouldn't know since I've never used it. It sounds promising though. :)

---

### Post by neodarksaver on 2008-03-28
the requirement to have Java in order to use azureus just added the factor of possible instability to azureus... transmission is a good choice.

---

### Post by bruce89 on 2008-03-28
> **Asham said:**
> Why not ship the JRE from Sun instead; it's smaller, "only" 18 Mb all in all. And even if it's still early, how about the new JRE a.k.a the Java Kernel? It should be just a couple of (likely 2-4) mega bytes large and it's scheduled to be released in the summer if I am not mistaken. But it may not be ready for general use just yet. I wouldn't know since I've never used it. It sounds promising though. :)

OpenJDK is Sun's GPLed Java. The kernel thing would be useful in fact.

---

