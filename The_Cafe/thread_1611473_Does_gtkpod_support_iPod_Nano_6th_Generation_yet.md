---
title: "Does gtkpod support iPod Nano 6th Generation yet?"
date: 2010-11-01
forum: The Cafe
---

### Post by devondashla on 2010-11-01
I'm looking to get the newest Nano, since my Classic no longer works.

---

### Post by gavdari on 2010-11-26
Maybe to late to answer your question, but I have an iPod Nano 6G and it doesn't work with any native software in linux. I've tried gtkpod, rhythmbox, banshee and amarok so far and none of them are working. Each has some error at some point which I guess is because of new firmware that is not supported yet. I would like to know if any one finds a good solution to get it to work under maverick.

---

### Post by alaukikyo on 2010-11-26
> **gavdari said:**
> Maybe to late to answer your question, but I have an iPod Nano 6G and it doesn't work with any native software in linux. I've tried gtkpod, rhythmbox, banshee and amarok so far and none of them are working. Each has some error at some point which I guess is because of new firmware that is not supported yet. I would like to know if any one finds a good solution to get it to work under maverick.

try itunes in wine

---

### Post by Rave Gloves on 2010-11-26
i just bought a Fuze made by sandisk. It is far superior to ipods. The sound quality is amazing and best of all it works 100% with ubuntu. I've had to much bother with ipods and ubuntu so i felt it was time to change.

---

### Post by gavdari on 2010-12-01
> **alaukikyo said:**
> try itunes in wine
Well, it didn't work. Are you sure iTunes works in maverick and Wine 1.2?

---

### Post by TakeLifeEasy on 2010-12-11
Can someone point me in the right direction where to find further updates on this and who are the developers?

---

### Post by peternickson on 2010-12-12
Still no support using any programs.  gtkpod detects music, but crashes.  Banshee detects that the ipod contains content, but doesn't detect it as music.  Rhythmbox detects the music, but you cannot add music to ipod.

---

### Post by gnomeuser on 2010-12-12
I have recently been involved in triaging all the iPod bugs in Banshee, and the answer is no.

[https://bugzilla.gnome.org/show_bug.cgi?id=631006](https://bugzilla.gnome.org/show_bug.cgi?id=631006)

Support your local libgpod developer, he may be able to reverse engineer support, till such a time as Apple learns to play with others.

---

### Post by mac9416 on 2010-12-25
According to a recent thread on the [GTKPod development mailing list]("http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTimPsMqVEr6Zh5-KtQAbwqATjc1G0dxdshD3ez2v%40mail.gmail.com&forum_name=gtkpod-devel") (the GTKPod folks write the software that allow Ubuntu to manage iPods):

> For now, the nano6g uses the same hash for the music database as the
iphone4 and the ipod touch 4, which unfortunately means someone needs
to reverse engineer this hash before the nano6g can be fully
supported. And reverse engineering this is pretty hard :-/

---

### Post by eneville on 2010-12-29
> **mac9416 said:**
> According to a recent thread on the [GTKPod development mailing list]("http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTimPsMqVEr6Zh5-KtQAbwqATjc1G0dxdshD3ez2v%40mail.gmail.com&forum_name=gtkpod-devel") (the GTKPod folks write the software that allow Ubuntu to manage iPods):

Apple must have taken a lesson from Microsoft Office file formats in the 90's.

---

### Post by luissil on 2011-06-12
June and nothing...?:(

---

### Post by Bandit on 2011-06-12
I have the most recent iPod Nano with video and it works like a charm.

---

### Post by Tuxi on 2011-06-12
Bandit,

Is it the squareish one?  This one [http://www.apple.com/ipodnano/]("http://www.apple.com/ipodnano/")?

Thanks.

---

### Post by Bandit on 2011-06-12
> **Tuxi said:**
> Bandit,

Is it the squareish one?  This one [http://www.apple.com/ipodnano/]("http://www.apple.com/ipodnano/")?

Thanks.

Wutt.. when did that come out?
[I got this one.]("http://support.apple.com/kb/HT1353#iPod_nano5G").

Looks like I got 5th gen one.. I thought I had the most recent since I just got it less then a year ago.. LOL o well..

---

### Post by Tuxi on 2011-06-12
I got the 6th gen one today as an early Fathers' Day present.  The database isn't updated within Ubuntu 11.04 (libgpod) atm.  I used SWMBO's Win box to load music today.  Looking into mediamonkey on my VBox version of XP. :-(

---

### Post by luissil on 2011-06-12
I used Itunes in Vbox, and I hate it! but it's the only way at this time... :-(

---

### Post by -Mudboy- on 2011-06-17
[URL="http://www.howtogeek.com/howto/24473/how-to-use-your-ipod-with-foobar2000/"]http://www.howtogeek.com/howto/24473/how-to-use-your-ipod-with-foobar2000/

[COLOR=Black]This program apparently runs under wine, i haven't tested it yet but anyone who wants to should go ahead as with the guide on the page i linked it apparently supports nano 6g[/COLOR]
[/URL]

---

### Post by clintonm on 2011-06-26
> **-Mudboy- said:**
> [URL="http://www.howtogeek.com/howto/24473/how-to-use-your-ipod-with-foobar2000/"]http://www.howtogeek.com/howto/24473/how-to-use-your-ipod-with-foobar2000/

[COLOR=Black]This program apparently runs under wine, i haven't tested it yet but anyone who wants to should go ahead as with the guide on the page i linked it apparently supports nano 6g[/COLOR]
[/URL]

I've read that wine doesn't support USB, in which case this won't be useful yes?

Also, I noticed in the changelog of the development version of libgpod, the library gtkpod uses, references to nano 6g serial numbers. Does this mean the nano 6g is becoming closer to being supported?

---

### Post by arealityfarbetween on 2011-06-30
not at all AFAIK, it just means that libgpod will recognise the device as something it will conceivably be able to control-once the libgpod guys manage to reverse engineer the hash that apple added to the database file on the iPod.

---

### Post by sebas9854 on 2011-07-30
Just so you know, I'm using gtkpod from the software centre with my new Nano, it works (so far)!

EDIT: Just disconnected the iPod, it didn't quite transfer the songs, it just pretended to.

Going to have to use Vbox on W7

---

### Post by tecywiz121 on 2011-10-17
I wonder if apple's hash has anything to do with their [patent]("http://appft1.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PG01&p=1&u=%2Fnetahtml%2FPTO%2Fsrchnum.html&r=1&f=G&l=50&s1=%2220100111292%22.PGNR.&OS=DN/20100111292&RS=DN/20100111292")

---

### Post by HDave on 2011-12-07
[Gtkpod's website]("http://gtkpod.org/wiki/Libgpod") still reports no 6G support as of today.  Does anyone know *when* support might be coming out?

---

### Post by Brejcha on 2011-12-27
Hopefully it gets support soon :-(

---

### Post by fyfe54 on 2011-12-28
> **devondashla said:**
> I'm looking to get the newest Nano, since my Classic no longer works.

Using iTumes in Virtualbox/Xp-Pro.  It's the only thnig that worked or me with 6th gen Nano.

FYI - Apple just replaced my 1st gen Nano with the latest model because of a bunch of bad batteries used in the original manufacture.  Check Apple's website for details.

---

### Post by wb8nbs on 2011-12-29
> **fyfe54 said:**
> Using iTumes in Virtualbox/Xp-Pro.  It's the only thnig that worked or me with 6th gen Nano.

FYI - Apple just replaced my 1st gen Nano with the latest model because of a bunch of bad batteries used in the original manufacture.  Check Apple's website for details.


FedEx just handed me a Gen 6 Nano as replacement for my Gen 1 that got recalled.  So I am also desperate for Linux support.  Will try Itunes with Wine but I don't have much confidence in that solution. :-(

---

### Post by Uppsala9496 on 2011-12-31
I am in this exact same situation.  Apple replaced my 1st gen nano with a 6th gen.  Nice that I now have double the space, but really, really crappy that I can't transfer over any songs from my media drive that is on my ubuntu machine.

---

### Post by tuneable on 2012-01-05
I found this thread through another message ([link]("http://askubuntu.com/questions/26353/how-can-i-sync-with-an-ipod-nano-6g")) on the same issue: no successful way to transfer mp3s to an iPod Nano 6th gen in native Linux apps (banshee, rhythmbox and the likes). I am still using Ubuntu 10.10, so things may look brighter on more recent releases.

That said, I can report the workarounds that did work for me:
[LIST=1]
[*]Virtualbox with a Windows Virtual Machine and iTunes
[*]Spotify for Linux
[/LIST]

Notes on Virtualbox: I did have to copy the mp3s to the Windows VM, because analysis of my library in iTunes took indefinite amounts of time when using a virtual share to my music library in Ubuntu (~/Music/).

Notes on Spotify: I have a free account and the Linux client. I  added the local files to the library and created a second playlist (called iPod) which I selected to sink to the iPod. Found this to be the only way to select the mp3s that end up on the iPod. Warning: Spotify erased my iPod before syncing. 

Either way works, but I'd still prefer to see a fix for libgpod/gtkpod.

---

### Post by erudite on 2012-01-11
I'm not sure this will ever be possible I'm afraid.  Apple have closed everything down by encrypting some hashes...

More here: [http://www.tuaw.com/2007/09/15/6th-gen-ipods-wont-work-with-linux-winamp/]("http://www.tuaw.com/2007/09/15/6th-gen-ipods-wont-work-with-linux-winamp/")

---

### Post by 80aless on 2012-01-22
I just managed to synchronize my Ipod nano 6g with Spotify for Linux! 
I confirm that banshee mounts the ipod and writes the files but the music does not appear

---

### Post by navafederico on 2012-01-23
Spotify is unfortunately not a solution for most European users.

Instead I recently found this java software, on the FAQ it's written it's possible to sync 6th gen ipod nano on linux, but I had no chance to test it since my replaced ipod is still on shipment. 

[http://www.jakpod.de/en/frequentlyaskedquestions/1-jakpod_faqs/14-supported_iPods](http://www.jakpod.de/en/frequentlyaskedquestions/1-jakpod_faqs/14-supported_iPods)

***"Attention!** JakPod does work with iPhones, iPod touchs and Nanos 6. Gen since version 2.0 but **only on LINUX machines**!"*

I hope this can be useful. I will test it as soon as I can.

UPDATE => no luck syncing the device with jakpod :(

---

### Post by luraze on 2012-01-31
I didn't get jakpod to work either. Kinda strange that he would write something like that. I do though have a feeling that he means 5g support, as I've read in his forums (written in German) that he doesn't even own a nano 6g to test.

I have tried Spotify with varying results. Far as I remember, it worked to write to the databse, but Spotify for linux is itself in beta stage, and therefore kinda buggy.

For now I dualboot with Windows, and use the oh so awful iTunes. Hoping for a quick fix, as the nano 6g is a wonderful little thing.

---

### Post by Ph1b on 2012-02-14
I got a iPod by the replacement program. This Apple is really annoying me, are there any updates with using iPod under Ubuntu?

---

### Post by DoctorLex on 2012-03-22
I am in the same situation: got a replacement 6th gen for my 1st gen nano, now I am trying to add some files in Linux to it and it proves impossible. I'd much rather have received a refurbished 1st gen even despite the fact that I now have 8GB instead of 4GB. As if it wasn't bad enough that I lost the ability to install Rockbox, now I can't even use the thing at all under Linux.

---

### Post by Ph1b on 2012-03-22
> **DoctorLex said:**
> I am in the same situation: got a replacement 6th gen for my 1st gen nano, now I am trying to add some files in Linux to it and it proves impossible. I'd much rather have received a refurbished 1st gen even despite the fact that I now have 8GB instead of 4GB. As if it wasn't bad enough that I lost the ability to install Rockbox, now I can't even use the thing at all under Linux.

I just sold that piece of apple-crap and bought a Sansa Clip+ for 20€ from UK. (living in gemany) Also reads my 32GB microSDHC and takes 16 hours with rockbox. :guitar:

---

### Post by Agent24 on 2012-03-24
I also now have an iPod Nano v6 (with firmware v1.2), due to the replacement\recall program.

I haven't found a way to use it in Linux yet either. BUT I have been able to use it in Windows with a program called "Mediamonkey"

I don't know if they have licensed something from Apple to make it work or what but it does work. I haven't tried it in Wine though.

---

### Post by wolfen69 on 2012-03-25
> **Ph1b said:**
> I just sold that piece of apple-crap and bought a Sansa Clip+ for 20€ from UK. (living in gemany) Also reads my 32GB microSDHC and takes 16 hours with rockbox. :guitar:

Finally, someone that took it upon them self to do something about the ipod dilemma. Don't use one if you want it to work in linux. Simple. Otherwise, feel free to stay with windows or apple for all your computing needs because of an mp3 player. ;)

---

### Post by perce on 2012-03-31
What never stops surprising me is that Apple made a device which can be interfaced only with ONE program of their choice, and people are still running to buy it, despite the many alternatives. What would people say if Microsoft had done the same?

---

### Post by Astinsan on 2012-04-05
It has to do with DRM. This is the only reason for doing this. It keeps you locked into their store. If apple can convince a record label or movie house that they have a secure way to distribute their IP it would be easier to get that publisher on board.  In the mean time it screws the customer. Specially when you send in your ipod for repair and get something else even when their website stated that you would get your exact model back... really irritating.

I suspect the hash maybe based off of the serial number.

---

### Post by Powergate92 on 2012-04-07
> **Astinsan said:**
> It has to do with DRM. This is the only reason for doing this. It keeps you locked into their store. If apple can convince a record label or movie house that they have a secure way to distribute their IP it would be easier to get that publisher on board.  In the mean time it screws the customer.
And that's why this lawsuit happened: [http://en.wikipedia.org/wiki/Apple_Inc._litigation#Apple_iPod.2C_iTunes_antitrust_litigation](http://en.wikipedia.org/wiki/Apple_Inc._litigation#Apple_iPod.2C_iTunes_antitrust_litigation)

---

### Post by danwood76 on 2013-04-16
If anyone gets to the end of this thread and wants a solution to using the Nano 6G with the libhashab.so I have one.

Basically I tried to get the original developper of the lib to send me a fixed version but he refused (he wanted money) so I set about reverse enginerring his code.
Fortunately I found a switch early on that tried (and failed) to detect the Nano 6G, I have modified the libhashab.so (changed 3 bytes) so that it always calculates the correct hash for the Nano 6G.

Attached is the library and some install scripts.
To use the library in 64-bit ubuntu you need to use a wrapper which I have written and is also included (as is the source) in the tar.gz.

All info is in the readme file, I hope this helps someone out!
I have tested this in Ubuntu 12.04 32 bit and 64 bit and can sync my Nano 6G with Rhythmbox, Banshee, and Clementine I'm sure anything that uses libgpod will work.

Basically extract it somewhere useful, read the readme, and then run one of the install scripts.

Kind regards,
Danny

---

### Post by Merk42 on 2013-04-16
Great, now I can close the thread for necromancy.

---

