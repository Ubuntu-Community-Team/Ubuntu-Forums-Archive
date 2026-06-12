---
title: "Request: HBCI support for Gnucash"
date: 2006-03-25
forum: Ubuntu Backports
---

### Post by tiomo on 2006-03-25
For those of you who might not know: HBCI is a online-banking standard used in Germany. Gnucash is a very powerful application and with the support of HBCI it becomes even more powerful as you can do online transactions from within the application, you can import data from your bank and so on.

I have to admit i was a bit shocked to see this is not being supported and as i learned from the german ubuntu community it was supported in a previous release of ubuntu. Why was this support dropped? This is essential to a lot of gnucash users (sorry that everyone not from Germany is left out here but that's not our fault) and i'm sure it wouldn't be a lot of work to integrate this. I came from Gentoo to Ubuntu and on Gentoo it was no problem getting the HCBI support. I'm sure almost every other linux distro has support for this too so please think about it and do something about it.

Thanks.

---

### Post by s3ppel on 2006-04-03
Jipp, I would be overjoyed to find Gnucash working out of the Box with HBCI. However I'm not so sure about other Distros supporting it. I tried SuSE as it is (was) a German Distribution, but had no real luck to get Gnucash-HBCI working there either. I at least got it to install on SuSE, while somehow I cant get Gnucash to even compile on Breezy, some dependency I fail to resolve.
However I'm still clueless how to get Gnucash working together with my Chipdrive, even on SuSE.
I really hope the forthcomming 2.0 release of Gnucash will make things easier, as onlinebanking is really all that keeps me from dumping Windows alltogether.

Greetings

---

### Post by dpm on 2006-04-12
[quote=tiomo]
I have to admit i was a bit shocked to see this is not being supported and as i learned from the german ubuntu community it was supported in a previous release of ubuntu. Why was this support dropped? [/quote] 
Having a look at the ubuntu packages site, it seems that the gnucash-hbci package was present on Warty and Hoary. From Breezy onwards there are no gnucash packages providing HBCI support out of the box. Unfortunately, it seems that there won't be support for HBCI on Dapper either.

For a possible explanation on why the HBCI support was dropped, have a look there (in German language):

[http://www.linuxwiki.de/GnuCash#head-529c1383e6c34427ed3fc4ffa444475509ed55a3]("http://www.linuxwiki.de/GnuCash#head-529c1383e6c34427ed3fc4ffa444475509ed55a3")

It basically says that from version 1.8.10 onwards gnucash switched to the AqBanking family of HBCI libraries (which replaced the older openhbci libs). Apparently unrelated to this, it seems that there are licensing issues with the gnucash-hbci package, and it cannot therefore be hosted on debian repositories. That's my understanding of why there isn't a gnucash-hbci package anymore (although I must say the explanation provided on that page was not very clear to me).

Anyway, I would also very much like to see a deb package with HBCI support, but I don't think we'll get to see it as a backport because there simply isn't any package to backport from. So I think it's up to us to find it somewhere else or compile gnucash from source with HBCI support.

You were saying you were shocked to see that HBCI support on the gnucash ubuntu package... Well, what I personally was shocked about is that no-one seems to be using HBCI in ubuntu. Doing a search on the ubuntu forums for HBCI returned only 4 threads, of which one of them is a duplicate... Common, are German people not doing online banking or what? 

I guess most people are using the web interface rather than doing it through a personal finance program. I'll have to give kmymoney another go some of these days, although after a quick play with it, it only seems to support OFX and not HBCI.

(sigh)

---

### Post by bdoetsch on 2007-10-03
FYI: As I needed HBCI myself, I just compiled gnucash 2.2.1 for Gutsy. You can find the exact links to the debs here:

[http://doetsch.info/2007/10/03/gnucash-221-mit-hbci-in-ubuntu-710-gutsy-gibbons/](http://doetsch.info/2007/10/03/gnucash-221-mit-hbci-in-ubuntu-710-gutsy-gibbons/)

If you ever want to compile this for yourself, there's an excellent guide available at the gnucash wiki: [http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian)

Cheers,
B

Update: I've recompiled using the latest sources as there was an update today...

---

### Post by megandy on 2008-04-29
In case you compiled the newest version (2.2.5), it would be great, if you could provide it for download. As in hardy, there's unfortunatelly no hbci-version, yet.

Thank you very much for the old version!

---

### Post by undadecor on 2008-07-14
Here's 2.2.4 with HBCI and OFXDirectConnect support:  [http://ubuntuforums.org/showthread.php?t=854770](http://ubuntuforums.org/showthread.php?t=854770)

---

