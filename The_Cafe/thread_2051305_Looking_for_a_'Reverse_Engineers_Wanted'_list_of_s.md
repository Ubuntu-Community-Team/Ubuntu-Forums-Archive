---
title: "Looking for a 'Reverse Engineers Wanted' list of sorts"
date: 2012-09-01
forum: The Cafe
---

### Post by REgrunt on 2012-09-01
Does anybody know of any todo-lists with protocols/file formats for bored reverse-engineers with too much free time? Ideally something a bit more accessible and in demand than old DOS business apps or the image format for some medical scanner (been there).

I know the first suggestion always is to 'scratch your own itch', but everything I use is either open source or at least open standards - so no itches. Over the years, I've cracked the encryption and analyzed the netcode of a handful of apps and games/MMOs, wrote viewers for their proprietary file formats, etc. and always greatly enjoyed doing that but that was usually just for me personally and I'd love to see someone actually benefit from this.

Maybe just some file converter for some proprietary Windows app or something.

---

### Post by tartalo on 2012-09-01
One area that in my opinion is lacking in Linux is the synchronization with portable devices like phones and tablets, there are lots of half-backed projects, perhaps you can help there.

---

### Post by effenberg0x0 on 2012-09-01
I'm not sure if this is the kind of reverse engineering you have in mind but, in my opinion, making open source drivers for VGA cards (NVidia, ATI) work as good as proprietary drivers requires a lot of hacking, studying the hardware, etc. If you apply your skills to that you will be making *many* Linux users happy. Not to mention you will be actively helping Linux adoption grow in share in end-users desktops (I know VGA is not the only factor, but it's a relevant one).

Regards,
Effenberg

**EDIT:** I forgot one thing: Microsoft Office files. No matter how much we love LibreOffice, it still has many problems understanding complex Excel spreadsheets and PowerPoint presentations. Maybe there's work to be done in understanding MS Office proprietary file format. And, of course, there's WINE too.

---

### Post by forrestcupp on 2012-09-01
I'm sure the ReactOS team would love to have some help from a good reverse engineer. Wine, too.

---

### Post by JDShu on 2012-09-01
Nouveau and Lightspark probably need help.

---

### Post by Lucradia on 2012-09-02
> **forrestcupp said:**
> I'm sure the ReactOS team would love to have some help from a good reverse engineer. Wine, too.

The ReactOS team needs **_clean-room_** reverse engineers, not just plain ones.

---

### Post by HermanAB on 2012-09-02
> **Lucradia said:**
> The ReactOS team needs **_clean-room_** reverse engineers, not just plain ones.
Engineers that take a shower once in a while?

---

### Post by sffvba[e0rt on 2012-09-02
"Cracking" encryption and reverse engineering of proprietary software etc. does happen, but is more often than not illegal and not supported on the forum

*Thread **closed**.*


404

---

### Post by s.fox on 2012-09-04
Thread reopened.

---

### Post by forrestcupp on 2012-09-04
Thanks for reopening this thread. I think there are a lot of areas that the community could really use a good clean-room reverse engineer who is eager to help out. :)

Of course we're not going to point anyone toward pirating and illegal activities. There are enough legal things that can be done to help out. ;)

---

### Post by sffvba[e0rt on 2012-09-04
> **forrestcupp said:**
> Thanks for reopening this thread. I think there are a lot of areas that the community could really use a good clean-room reverse engineer who is eager to help out. :)

Of course we're not going to point anyone toward pirating and illegal activities. There are enough legal things that can be done to help out. ;)

My bad... carry on :)


404

---

### Post by Artemis3 on 2012-09-05
Yes, recent phoronix entries talk about success in reverse engineering video decoding/encoding in some SoC ARM solutions, such as the one in the raspberry pi. That would allow full hd playback without proprietary blobs.

Also different countries see reverse engineering in different ways, most allow it, a few need the so called "clean room" method, etc.

So if you are bored and want to, go with hardware; thats where the most urgent needed help is. Projects like nouveau are always welcoming help, for instance.

---

### Post by quequotion on 2012-09-05
If you're into games, there's a whole lot of work to be done in the emulation scene.

Some people consider this work to be illegal, but with little specific precedent or law supporting that opinion they are often extending the idea of copyright infringement, as it applies to games, to the entire concept of emulation where it does not apply whatsoever.
In fact, most of this work can be seen as necessary for posterity, research, education, and the last resort of dedicated fans who have no hope for parts or service for their ancient machines; and the work can definitely be done "clean room".

[MESS]("http://www.mess.org/") and [MAME]("http://mamedev.org") have as much work do be done as there are machines to emulate in the known universe.

[Yabause]("http://yabause.org") is an open-source Sega Saturn emulator.
The system was years ahead of it's time, a long time ago.
It was the only system at the time, and for the following decade, with dual processors.
Unfortunately, it wasn't well documented even in its heyday and has always been difficult to develop on; now it's quite a challenge for a few dedicated fans to bring back to life to keep playing their old games even after the original hardware breaks down. 

[lxdream]("http://www.lxdream.org/") is another open-source Sega emulator, for the Dreamcast.
Of particular interest for a reverse engineer would be the [GD-ROM]("http://en.wikipedia.org/wiki/GD-ROM") disk format, which is a high-density CD-ROM format which used *standard CD-ROM hardware* to read disks with 1.2 GB capacity. The system had custom firmware to spin the disk at a lower speed while utilizing Constant Angular Velocity to read the higher-density disks. Attempts have been made to add native support to linux with limited success.
This system also carried a Windows CE logo and has a rather functional linux distribution available.

[bsnes]("http://byuu.org/bsnes") is a good example of how emulation can be done well. Nearly 100% complete, the primary author of this open-source SNES emulator has sought to reproduce the behavior of each part of the original hardware precisely, while maintaining strict coding practices to keep it clean and simple. The result is an extremely functional emulator that requires a great deal more resources than the hackish ones of yesteryear.
Reverse engineering the system proved a challenge, as each game introduces unique hardware into the system. To properly emulate chips which haven't been manufactured by companies that no longer exist since the mid 90's, game cartridges had to be disassembled, their chips removed and individually "uncapped" - a process by which the plastic casing of a chip is melted off with acid, then each layer of silicon inside the chip is scanned at high resolution before melting down to the next. This is also being done to chips needed for MESS and MAME.

---

### Post by Lucradia on 2012-09-06
iirc, it's not legal to play a console emulator unless it can play the intended media and you currently own that system being emulated (whether or not the real life version is destroyed or not.)

---

### Post by forrestcupp on 2012-09-06
> **Lucradia said:**
> iirc, it's not legal to play a console emulator unless it can play the intended media and you currently own that system being emulated (whether or not the real life version is destroyed or not.)

Wow! This is what [Nintendo's web site](http://www.nintendo.com/corp/legal.jsp#emulator)) says about the matter:
> Can I Download a Nintendo ROM from the Internet if I Already Own the Authentic Game?

There is a good deal of misinformation on the Internet regarding the backup/archival copy exception. It is not a "second copy" rule and is often mistakenly cited for the proposition that if you have one lawful copy of a copyrighted work, you are entitled to have a second copy of the copyrighted work even if that second copy is an infringing copy. The backup/archival copy exception is a very narrow limitation relating to a copy being made by the rightful owner of an authentic game to ensure he or she has one in the event of damage or destruction of the authentic. **Therefore, whether you have an authentic game or not, or whether you have possession of a Nintendo ROM for a limited amount of time, i.e. 24 hours, it is illegal to download and play a Nintendo ROM from the Internet.**(Bold added)

They also go on to say that it's still illegal to download ROMs even if the game is no longer commercially available. I hate hearing this.

---

### Post by mevun on 2012-09-06
I don't get the fascination with reverse-engineering most software products.  For a company that is trying to build a product replacement, it might make sense, but I am not sure what an individual will gain from it.

Still, if I had to offer something that could be done, I would suggest reverse-engineering the protocol for Cisco Raw Data Record (RDR) packets.  Actually, I am not even sure if they are opposed to giving out the format.  I wrote a parser for Radius and DHCP RDR packets, although parts of the header were opaque.  I actually don't think Cisco would have a problem telling others their packet format and some of the fields are already documented on their website.  BTW, to do this reverse-engineering you probably need a whole networking lab.

My overall suggestion (probably unwelcome) though would be to help with open-source projects instead of reverse-engineering closed products.  I notice that the OP has not returned to the thread though.

---

### Post by quequotion on 2012-09-06
> **forrestcupp said:**
> They also go on to say that it's still illegal to download ROMs even if the game is no longer commercially available. I hate hearing this. Indeed. Unfortunately for Nintendo, their opinion doesn't really have enough actual case law behind it to constitute legal fact.

Of course, with things like the Digital Millennium Copyright Act in effect, the law is now subject to postmodernism as far as those in power are concerned: 

The law means, and is, what they believe it to mean, and be *regardless of what it actually means or is*, at least as far as copyright law as pertaining to the games.

Working on an emulation program itself is another matter.

In most countries, while it probably violates the terms of service between you and the manufacturer, it isn't illegal to take apart a machine you own and attempt to repair, replace, or replicate the parts as long as you don't intend to manufacture a commercial product. 

[I]Unfortunately a few manufactures have illicitly done just that using code from open-source emulators, unaccredited, in violation of the law, nintendo's patents, and the GNU General Public License.

[/I]Perhaps I should add that my views are my own and are not associated with or representative of any other person, persons, or organization.

---

### Post by forrestcupp on 2012-09-06
Another great project for a good software reverse engineer would be to help make LibreOffice's support for Microsoft's XML formats less crappy.

> **quequotion said:**
> Indeed. Unfortunately for Nintendo, their opinion doesn't really have enough actual case law behind it to constitute legal fact.

Of course, with things like the Digital Millennium Copyright Act in effect, the law is now subject to postmodernism as far as those in power are concerned: 

The law means, and is, what they believe it to mean, and be *regardless of what it actually means or is*, at least as far as copyright law as pertaining to the games.

Yeah. It's a pretty big gray area. I have a harder time accepting the legality of ROMs for Dolphin than I do for original NES ROMs.

---

### Post by mips on 2012-09-06
> **forrestcupp said:**
> Another great project for a good software reverse engineer would be to help make LibreOffice's support for Microsoft's XML formats less crappy.


As far as I know MS's own implementation of XML is rather crappy or should I say non-standard...

---

### Post by forrestcupp on 2012-09-06
> **mips said:**
> As far as I know MS's own implementation of XML is rather crappy or should I say non-standard...

That depends on how you look at it. If the majority of people use MS's XML file formats, that kind of makes it the industry standard. It's not LibreOffice's fault that MS doesn't open the specs, but it would still be nice if they could get their implementation a little more compatible.

---

### Post by mips on 2012-09-06
> **forrestcupp said:**
> That depends on how you look at it. If the majority of people use MS's XML file formats, that kind of makes it the industry standard. **It's not LibreOffice's fault that MS doesn't open the specs**, but it would still be nice if they could get their implementation a little more compatible.

I'm not saying it is at all. What I'm saying MS OOXML was supposed to be an open standard that was steamrolled through the standards bodies with lots off opposition and look at the state of affairs now. If the standard was so open & universal it should be easily adopted by all without interoperability issues.
[http://en.wikipedia.org/wiki/Office_Open_XML#Standardization_process](http://en.wikipedia.org/wiki/Office_Open_XML#Standardization_process)

---

### Post by vexorian on 2012-09-06
> **mips said:**
> I'm not saying it is at all. What I'm saying MS OOXML was supposed to be an open standard that was steamrolled through the standards bodies with lots off opposition and look at the state of affairs now. If the standard was so open & universal it should be easily adopted by all without interoperability issues.
[http://en.wikipedia.org/wiki/Office_Open_XML#Standardization_process](http://en.wikipedia.org/wiki/Office_Open_XML#Standardization_process)
Ah memories.

This is hilarious in retrospect.

I still find it hard to believe so many standard bodies would think that a format that requires you to see through 6000 pages of ambiguous text was good for an open standard. Worse if there was already an standard to do exactly the same.

Oh well, MS can sure work magic.

---

### Post by forrestcupp on 2012-09-06
> **mips said:**
> I'm not saying it is at all. What I'm saying MS OOXML was supposed to be an open standard that was steamrolled through the standards bodies with lots off opposition and look at the state of affairs now. If the standard was so open & universal it should be easily adopted by all without interoperability issues.
[http://en.wikipedia.org/wiki/Office_Open_XML#Standardization_process](http://en.wikipedia.org/wiki/Office_Open_XML#Standardization_process)
I know it's ridiculous. But they're Microsoft, and that's what we have to deal with.

---

### Post by quequotion on 2012-09-07
> **forrestcupp said:**
> I know it's ridiculous. But they're Microsoft, and that's what we have to deal with.I like this quote. I like it a lot.

---

