---
title: "Ubuntu Linux for a Home server ???"
date: 2007-09-03
forum: Server Platforms
---

### Post by MrGando on 2007-09-03
Hi guys I study Computer Science in Chile ( South America ). I am a Apple user, most of my family are Apple users, here at home we have :

1 MacBook
1 MacBook pro
1 PowerBook G4

And a few weeks ago we had a G5, I got a very good offer for it ( one of those that you just can't reject because you know you will not get it again ). So I sold the G5.

The G5 was my Desktop at home, and it helped me to do a lot of stuff. Some of them where:

1- Ripping and Burning DvDs for backup or Car playing.
2- Downloading with Bit Torrent.
3- SSH/SFTP server ( for compiling )
4- WebServer
5- File Server
6- Print Server

I loved to be able to view DVD's stored in my G5 in realtime with other computers at home ( connected via cable to it ).

In my G5 I also stored all my Mp3's.

So the time has come to decide if I will finally buy a box to build a server at home.

I was thinking on :
 intel Core 2 Duo 2.33 ghz 1066 mhz frontside bus
2 gb ram patriot 800 mhz
A lot of HD space
Gigabit ethernet in the mother board ( I don't know if Ubuntu can work with this ??? )
and a Sata DVD writer reader.
Integrated video

Here are my questions.

1) Can ubuntu read/write an HFS partition ? ( that's mac os partitioning system ) ( maybe installing open FUSE can help ... I don't know )
2) Do you think ubuntu can fit my needs ?  I am used to the console, I use it all day long, so no problems with that.

Well, I am waiting to hear your input, or ideas, or suggestions about stuff that can go wrong.

Thanks a lot for this forums!!

---

### Post by scxtt on 2007-09-03
gigabit will work fine - i have 2 PCs w/ gigabit and feisty (1 has a PCI card, the other is integrated) ...

```
p   hfsplus                                           - Tools to access HFS+ formatted volumes
p   hfsutils                                          - Tools for reading and writing Macintosh volumes
```

---

### Post by MrGando on 2007-09-04
This seems to be great, I am pretty convinced now... The thing that I have to understand now , is how to connect my router to a Gigabit Switch, I just happen to have a regular D-Link router.

---

### Post by HermanAB on 2007-09-04
The Gigabit switch will likely step down to the lower speed of the home router.  Just plug in a cable and try it.  It should work.

---

### Post by scxtt on 2007-09-04
i have a gigabit switch plugged into a linksys router ... not sure what speeds i'm getting ... don't know if when i go [ gigabit <--> gigabit ] if the xfers are at top speeds, i'll have to check :p

---

### Post by MrGando on 2007-09-04
my internet connection is like 4Mbps,  the switch will be used in order to transfer big files so it will be used just for LAN, the router is mainly to give each computer a DHCP address. :)

Do you guys recommend some Hard drive in special to install the ubuntu OS ? Some fast drive or something ???

---

### Post by scxtt on 2007-09-05
> Do you guys recommend some Hard drive in special to install the ubuntu OS ? Some fast drive or something ???what?

---

### Post by MrGando on 2007-09-06
I meant some special kind of hard drive ... I finally went for a Western Digital raptor 10.000 rpm  36 gb, just for the OS , and I think I will go for seagate 7200.10 sata II drives for files.

What do you think ?

---

### Post by Brazen on 2007-09-07
You really don't need a fast harddrive for a home server.  If you were going to set up a database server accessed by hundreds of people, then a raptor would be useful, but for just sharing file with a couple other computer, any harddrive that has enough space would work just as good.

---

### Post by MrGando on 2007-09-08
Another question is what version of Ubuntu to use... I have seen many ppl using 6.06 or something but latest version is 7.04 ?

The server will have an intel 6550 core 2 duo processor , but I think I will install the i386 ubuntu version, I have heard bad stuff coming from the 64bit version.

What do you think about that ?

---

### Post by scxtt on 2007-09-08
my server runs 64-bit (AMD Athlon(tm) 64 X2 Dual Core Processor 3600+) - no problems ... it also runs 7.04, no problems there either ... it's mainly a VMware Server host, i'm very happy w/ it.

---

### Post by MrGando on 2007-09-09
oh , Nice to hear that 64bit version is getting better with the time. : ) .

I will love to hear if other ppl have used this version with  a server ?

---

### Post by mmtowns on 2007-11-13
I'm using 7.10 server on a test machine right now.  Seems to work fine so far.  It's an older P3-450 with 384 ram.

---

