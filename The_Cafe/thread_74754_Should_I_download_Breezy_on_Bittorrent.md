---
title: "Should I download Breezy on Bittorrent?"
date: 2005-10-12
forum: The Cafe
---

### Post by blastus on 2005-10-12
I'm on dialup and have never used Bittorrent before. I've heard of Bittorrent but just decided today to read up on it. I have a couple of questions...

1. Is Bittorrent practical or recommended for dialup users?
2. Is Bittorrent secure?

The reason I ask is because I'm leery of connecting to someone else's insecure PC running who knows what on it and also allowing someone else's insecure PC running who knows what on it to connect to my machine. There are most certainly compromised, modified, or fake Bittorrent clients out there. A hash goes a long way but is it enough? :???:

---

### Post by Stormy Eyes on 2005-10-12
If you're on dialup, don't bother with bittorrent. Sorry.

---

### Post by xequence on 2005-10-12
Well, it shouldent make much of a difference for dial uppers.

With the mirrors I got 90 KBPS download speed. With bittorent I got 300 KBPS. (WIth breezy, yesterday).

I use torrents alot and I have always got the file I wanted, no corruptions.

---

### Post by raublekick on 2005-10-12
What bittorrent client are you using? I'd try [Azureus]("http://azureus.sourceforge.net/"), it's for both Windows and Linux. 

As far as dial-up goes I can't really say for sure one way or the other. It's not going to be super fast but it might be better than a normal HTTP or FTP download. But who knows, it might take longer than just waiting for a ship-it cd to arrive :)

---

### Post by xequence on 2005-10-12
Azureus is definitally the best torrent client. Only bad thing is, its java, which is slow.

---

### Post by gflores on 2005-10-12
I'd just stick with using a download manager and downloading straight from the Ubuntu servers (and mirrors).

---

### Post by Takis on 2005-10-12
Whichever way you go, just make sure to double check the md5 sum when the download's finished. If just a single byte is wrong, the md5 sum changes completely so you'll know if you have a valid iso image or not.

Scroll down to the bottom and have a look at the MD5 sum for which image you download:
[http://us.releases.ubuntu.com/releases/5.10/](http://us.releases.ubuntu.com/releases/5.10/)

You can check the MD5 sum using winMd5Sum:
[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)
(it's licensed similarly to, although fair more briefly than, the GPL)

---

### Post by BWF89 on 2005-10-12
[QUOTE=xequence]Azureus is definitally the best torrent client. Only bad thing is, its java, which is slow.[/QUOTE]
I prefer BitTornado. Which is also Windows and Linux
[http://bittornado.com/](http://bittornado.com/)

---

### Post by RastaMahata on 2005-10-12
damn, am I the only one using ubuntu's default bittorrent client? :(

---

### Post by GreyFox503 on 2005-10-12
If you're on dial-up, there's no point in using bittorrent.  It won't go any faster (and you probably won't want to stay on for hours (or days) seeding back whatever you downloaded).

If you get broadband or use it somewhere else, then bittorrent is great.  I cast another vote for Azureus, though that may just be out of ignorance (never used bitcomet/bitlord/bittornado).  Azureus gives you an insane amount of information and options about your downloads, although it feels kinda slow (blame java!).

And yes, as far as I can tell, it does not prevent a security risk.  Bittorrent protocol has hash-checking built into it, and as someone else pointed out, you can also run an md5sum against the final download anyway.

---

### Post by Lovechild on 2005-10-12
[QUOTE=RastaMahata]damn, am I the only one using ubuntu's default bittorrent client? :([/QUOTE]

no, I use it as well - but it's not without flaws

---

### Post by MechR on 2005-10-13
On the Windows side, [µTorrent](http://www.utorrent.com) is amazingly small (91Kb currently), and just a couple features away from perfection :)  Closed-source, though...

---

### Post by Pablo_Escobar on 2005-10-13
[QUOTE=RastaMahata]damn, am I the only one using ubuntu's default bittorrent client? :([/QUOTE]
You're not the only one :) I'm dowloading Breezy using standard Gnome Torrent Client. I get better speeds than Azureus. :KS

---

### Post by mr_mop on 2005-10-13
[QUOTE=RastaMahata]damn, am I the only one using ubuntu's default bittorrent client? :([/QUOTE]

No I use it as well! It works, why get something else? :confused:

---

### Post by flaming_monkey on 2005-10-13
Downloading ~700Mb over dial-up will take a long time, I know, I use to have dial-up. Try asking a friend who has broadband or maybe go to the local library or university, the I.T department people are usual very happy to help Linux fans and I'm sure they'll burn you a copy. You could always order the CD-Rom from Ship-it but you will have to wait a few months before it arrives.

If you're determined to download the ISO over dial-up then Takis was right in saying you should run a md5sum check once the files been downloaded.

The one bonus about using bit-torrent is that the file is constantly hash checked, meaning that downloaded file it guaranteed to be uncorrupted.

---

### Post by tedius on 2005-10-13
I've never used bit torrent before, so I've just looked at the bit torrent site.

Now before I start I need to open ports 6881 to 6889.

It then mentions I might have to change the IP address that's being reported.  I'm behind a LinkSys NAT firewall, will I have to change the IP address that the default torrent program sends to the tracker and if so how do I do it.

Thanks for the help.

---

### Post by phrozen on 2005-10-13
[www.portforward.com](www.portforward.com)
it should get you going for everything, and if you still want to download ubuntu either use a download accelerator (make sure you get a fulll version so you get maximum speed), it will flood your internet connection for a few days, but using bittorent should be just as quick, i get quicker speeds thru normal internet but i have a 5mbs connection so slow for me is under 100kbs, and i would consider that very slow

---

### Post by BoyOfDestiny on 2005-10-13
[QUOTE=blastus]I'm on dialup and have never used Bittorrent before. I've heard of Bittorrent but just decided today to read up on it. I have a couple of questions...

1. Is Bittorrent practical or recommended for dialup users?
2. Is Bittorrent secure?

The reason I ask is because I'm leery of connecting to someone else's insecure PC running who knows what on it and also allowing someone else's insecure PC running who knows what on it to connect to my machine. There are most certainly compromised, modified, or fake Bittorrent clients out there. A hash goes a long way but is it enough? :???:[/QUOTE]

Yeah the hash is enough (SHA1 I believe).

My recommendation is go for mirrors. 

From a terminal use 
wget -c  [http://us.releases.ubuntu.com/releases/5.10/ubuntu-5.10-install-i386.iso](http://us.releases.ubuntu.com/releases/5.10/ubuntu-5.10-install-i386.iso) and that will do the trick. 
The -c means continue so that wget allows resumes. 

If you prefer a gui go to Add Applications and choose gwget.

After the file is done, check the MD5 sum. If it is damaged (AFAIK there are no par files for ubuntu you could get). 

Fire up bittorrent and it will repair/replace the missing pieces, and ensure you have a "perfect" file. :razz:

---

### Post by BoyOfDestiny on 2005-10-13
[QUOTE=tedius]
It then mentions I might have to change the IP address that's being reported.  I'm behind a LinkSys NAT firewall, will I have to change the IP address that the default torrent program sends to the tracker and if so how do I do it.

Thanks for the help.[/QUOTE]

No. (I'm behind a linksys router too) Just open the ports... Anyway bt can use more (or maybe it's just azureus), from 6881-6999. 
Those 9 you opened should be enough though (if you had more machines to forward to on your network, those ports are there.)

---

### Post by BWF89 on 2005-10-13
[QUOTE=flaming_monkey]Try asking a friend who has broadband or maybe go to the local library or university, the I.T department people are usual very happy to help Linux fans and I'm sure they'll burn you a copy.[/QUOTE]
And you get to meet other Linux users or if they don't even know explain to them what Linux is.

---

### Post by Jenda on 2005-10-13
[QUOTE=BWF89]And you get to meet other Linux users or if they don't even know explain to them what Linux is.[/QUOTE]
i.e. meet or create GNU/Linux Users...

Any idea why my Azureus downloads rarely top 10 kB/s, when I can get over 100 kB/s with Limewire et al?

---

### Post by jeffreyvergara.NET on 2005-10-13
i did not configure my ubuntu's default bit torrent client, and it works fine. and as flaming_monkey said, "the file is constantly hash checked, meaning that downloaded file it guaranteed to be uncorrupted." that what I liked in torrents, especially when downloading huge files like .iso, i tested it before when I downloaded Hoary twice, both failed in md5sum check. but using torrent, everything went smooth, so I recommend torrent.

---

### Post by GreyFox503 on 2005-10-13
[quote=Jenda]
Any idea why my Azureus downloads rarely top 10 kB/s, when I can get over 100 kB/s with Limewire et al?[/quote]

I don't think Limewire even uses the bittorrent network, does it?

Torrent swarms are fastest when they are the most popular.  If what you're downloading is old/niche and not many people are on, then yeah it could take a while.

---

### Post by jyank on 2005-10-13
[QUOTE=RastaMahata]damn, am I the only one using ubuntu's default bittorrent client? :([/QUOTE]

That is just frontend for BitTornado for gnome :cool: 

But, I use it as well because bittornado doesn't seem to work as good as it does in windows

---

### Post by Jenda on 2005-10-13
Thanks. I was thinking it might be a configuration thing.
Limewire doesn't use torrents, I just said that so that you know why I deem it strange that Azureus is so slow.
And it does that even when ther's tons of peers - it doesn't connect to enough of them IMO.

---

### Post by xequence on 2005-10-13
> damn, am I the only one using ubuntu's default bittorrent client?

I used to, before I got azureus working in linux. It is much faster then the windows version for some odd reason.

> I prefer BitTornado. Which is also Windows and Linux
[http://bittornado.com/](http://bittornado.com/)

Didnt that have some error reporting back to the tracker or something? Or that might have been bitcomet.

> Any idea why my Azureus downloads rarely top 10 kB/s, when I can get over 100 kB/s with Limewire et al?

It just depends on how many people are seeding. I have gotten between 1 KBPS and 350 KBPS with it. Normally, the more people in the torrent the better. Some tracker sites have 10Mbit uploaders and you will get really fast downloaded from them.

---

### Post by blastus on 2005-10-13
Thanks everyone for the replies! It seems the consensus is that Bittorrent is secure but is designed for broadband only.

I'm using WebDownloader for X. I started downloading Breezy last night and let it go all night and all day today. I already have 277MB so I'm almost half-way there. It usually takes me about 2-3 days to download an ISO depending on if I can let it go all night/day.

---

### Post by skoal on 2005-10-13
Where's all the 'kubuntu-5.10-install-i386.iso' loving at on bit torrent?

I was snagging ~8kB/s earlier, but with my 2Mbps pipe I promptly put that torrent's head on my ctrl-c chopping block.  I will seed myself eventually, but the kubuntu torrent korn field seems to be quite barren at the moment.  Where the farmers at? 

\\//_

---

### Post by stoeptegel on 2005-10-14
The kubuntu dvd download is slow for me too, i downloaded 50MB in half a day :(   But now the tracker is also down...:confused:

EDit
And up again.
EDit
The slow speed could be caused by ktorrent for me, bittornado does better now.

---

### Post by magomago on 2005-10-14
[QUOTE=skoal]Where's all the 'kubuntu-5.10-install-i386.iso' loving at on bit torrent?

I was snagging ~8kB/s earlier, but with my 2Mbps pipe I promptly put that torrent's head on my ctrl-c chopping block.  I will seed myself eventually, but the kubuntu torrent korn field seems to be quite barren at the moment.  Where the farmers at? 

\\//_[/QUOTE]

I've been seeding Ubuntu since it came out ;)  Both thirty two and sixyfour bit, maxing out my 10mbit connection :D

MY goal is to seed up about a ratio of 100 and then stop...unless i get disconnected first ;)

---

### Post by AllenGG on 2005-10-14
Hi Blastus , something is really wrong !  Quote:&quot;&quot; It usually takes me about 2-3 days to download an ISO depending on if I can let it go all night/day.&quot;&quot; previously on dial-up I could d/l large files, LATE AT NIGHT, rarely taking over 2-3 hours. Look over all the &quot;mechanicals&quot; first. Some modems aren't worth a **** ! Having been in the computer sales biz, it was obvious that all modems are not equal. Winmodems being at the top of the &quot;rotten&quot; list. Good luck with A-Open for some reason.  Remember on Bittorrent ot Tornado you're relying on other participants, some may want to &quot;shutdown&quot; in the middle of your d/l. Here, my current DSL is ver-r-ry slow sometimes during the day. luck ! AGG

---

### Post by benplaut on 2005-10-14
[QUOTE=MechR]On the Windows side, [µTorrent](http://www.utorrent.com) is amazingly small (91Kb currently), and just a couple features away from perfection :)  Closed-source, though...[/QUOTE]

only 91Kb? surely you can guess the source :cool:

---

