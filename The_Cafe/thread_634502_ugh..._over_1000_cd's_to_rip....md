---
title: "ugh... over 1000 cd's to rip..."
date: 2007-12-07
forum: The Cafe
---

### Post by svtfmook on 2007-12-07
i should have stayed on top of this, but i've decided to do it now...

so what's the easiest way?

---

### Post by -grubby on 2007-12-07
buy 1000 CDROM drives and use them all at once?!

---

### Post by svtfmook on 2007-12-07
hmm... i would need 250 computers!

---

### Post by -grubby on 2007-12-07
> **svtfmook said:**
> hmm... i would need 250 computers!

maybe not the cheapest way to do it.....

---

### Post by blithen on 2007-12-07
> **nathangrubb said:**
> buy 1000 CDROM drives and use them all at once?!

xD! +1

---

### Post by gn2 on 2007-12-07
Good luck with that, I did 300 some years ago and it took a while but was worth it.

Grip is a good ripping program and you can set the bitrate. I prefer 192kb/s.
There's a box you can tick to stop spaces being changed to underscores in the  names and tags.

---

### Post by p_quarles on 2007-12-07
Ripping a thousand CDs is going to be tedious no matter what (and that's including if you had 1000 CD-ROM drives in 250 computers -- you'd still have to put them all in the trays).

If you have a 64-bit CPU and haven't upgraded to Ubuntu 64-bit yet, I would recommend doing that. Encoding is one of the areas where you'll notice a significant performance improvement. You'll still have a thousand CDs to rip, but it will go faster.

---

### Post by Scarath on 2007-12-07
pay a local urchin child to do it on ur computer while u go and sip lemonade?

enlist the help of friends and friends of friends and friends of friends of friends (etc)?

---

### Post by svtfmook on 2007-12-07
well, i think sound juicer only rips at 128kbps.

what ripper does 192??

---

### Post by crimesaucer on 2007-12-07
> **svtfmook said:**
> well, i think sound juicer only rips at 128kbps.

what ripper does 192??

Grip ripper does... just like gn2 suggested.


I really like Grip and all of it's features... except for how slow ripping is in Linux (for all rippers).


[http://nostatic.org/grip/](http://nostatic.org/grip/)
[http://nostatic.org/grip/doc/index.html#intro](http://nostatic.org/grip/doc/index.html#intro)

---

### Post by gn2 on 2007-12-07
> **svtfmook said:**
> well, i think sound juicer only rips at 128kbps.

what ripper does 192??

Grip, you can specify the desired bitrate by typing in the box I've marked with an arrow.

[IMG]http://i174.photobucket.com/albums/w109/gn1v/Grip.png[/IMG]

---

### Post by eljoeb on 2007-12-07
Beer makes it go faster.


It actually made it take longer for me, and I ended up ripping the same disc 23 times, but it got done.  Eventually.  100 CD's took a night.  Plus some of the morning to figure out why I had 23 copies of The Jungle Book soundtrack.

---

### Post by svtfmook on 2007-12-07
idk, grip doesn't seem to rip the tags and i like the way juicer organizes the files.

---

### Post by -grubby on 2007-12-07
> **eljoeb said:**
> 
... and I ended up ripping the same disc 23 times, but it got done.  ...figure out why I had 23 copies of The Jungle Book soundtrack....

:lolflag:

---

### Post by julian67 on 2007-12-07
I'd strongly suggest using [ripit]("http://www.suwald.com/ripit/ripit.html") for this.

> The program will do the following without user intervention:

  # gets the Audio CD Album/Artist/Tracks information from CDDB
  # rips the Audio CD Tracks
  # encodes to flac, mp3 or ogg
  # id3 tags encoded songs
  # Creates an playlist (m3u) file
  # Can generate a toc (cue) sheet for nice DAO burning
  # Can prepare and send a CDDB submission and save it locally
  # Can extract hidden songs and split ghost songs
  # May create md5sum files for all tracks
  # Run several encoder processes at the same time and same run


It's a command line application but very slick, it should only take a few minutes to set up and will save you a lot of time. When you're happy it's as you like in terms of encoder, output, tagging etc it can then be run with no user interaction other than feeding another CD into the tray when it auto ejects. Ripit will just keep going until you stop feeding it discs.

edit: it's in the ubuntu repositories, but I'd install it via apt (to get the dependencies installed easily) and then use the latest beta from the ripit site. I use it now in preference to any of the gui rippers I used before (sound-juicer, asunder, grip etc).

---

### Post by SonicSteve on 2007-12-07
How about just downloading the the music through a torrent or p2p. You have the CD's and in the end it will be the same anyway. I'm not sure it will be much faster but you at least won't have to insert 1000CD's plus eject 1000CDs that's an obscene number to be considering.

---

### Post by julian67 on 2007-12-07
> **SonicSteve said:**
> How about just downloading the the music through a torrent or p2p. You have the CD's and in the end it will be the same anyway. I'm not sure it will be much faster but you at least won't have to insert 1000CD's plus eject 1000CDs that's an obscene number to be considering.

yeah 1000 CDs of low quality 128 mp3 and aac with no tags/wrong tags/wrong filenames/no numbering/no playlists/missing tracks etc etc. 

yeeeuuuugghhhk!

---

### Post by n3tfury on 2007-12-07
> **svtfmook said:**
> i should have stayed on top of this, but i've decided to do it now...

so what's the easiest way?

not sure about easy, but you might want to take a look at this "average user" guide.  it's not linux specific, but there's alot of good info in there.

[[COLOR="DarkOrange"]guide[/COLOR]]("http://www.hydrogenaudio.org/forums/index.php?act=Attach&type=post&id=2938") (pdf)

---

### Post by n3tfury on 2007-12-07
> **SonicSteve said:**
> How about just downloading the the music through a torrent or p2p. You have the CD's and in the end it will be the same anyway. I'm not sure it will be much faster but you at least won't have to insert 1000CD's plus eject 1000CDs that's an obscene number to be considering.

lol do NOT do this

---

### Post by Mr.Auer on 2007-12-07
There are also other ripper options, like RipperX (in the repos) that rips to ogg, lame, flac if u have em installed, any bitrate the codecs support, will fetch cddb info as well.

And for secure, logged, error-repaired ripping RubyRipper, which is easy to install following directions here:
[http://wiki.hydrogenaudio.org/index.php?title=Rubyripper](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper)

RubyRipper is capable of similar secure ripping to Windows Exact Audio Copy (EAC). Rubyripper is capable of flac, ogg, mp3 all bitrates as well, and supports cddb.

---

### Post by n3tfury on 2007-12-07
> **Mr.Auer said:**
> There are also other ripper options, like RipperX (in the repos) that rips to ogg, lame, flac if u have em installed, any bitrate the codecs support, will fetch cddb info as well.

And for secure, logged, error-repaired ripping RubyRipper, which is easy to install following directions here:
[http://wiki.hydrogenaudio.org/index.php?title=Rubyripper](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper)

RubyRipper is capable of similar secure ripping to Windows Exact Audio Copy (EAC). Rubyripper is capable of flac, ogg, mp3 all bitrates as well, and supports cddb.

although i rip in windows with EAC, i have tried rubyripper in ubuntu and can vouch for the program's worth.  it does its job very well creating .flac (which is what i rip all my cd's to).  

OP:  i suggest making backups of your cd's to an uncompressed format of your choosing.  from there, you can encode to your heart's content.

---

### Post by p_quarles on 2007-12-07
I've used numerous ripping apps, and my personal favorite is K3b. In terms of options, speed, and reliability, nothing else I've used has been as good. It would definitely be my choice for a large, tedious project like this, since it just takes a couple clicks to get each new disk started.

EDIT: +1 on n3tfury's suggestion above. .flac files will take up more hard drive space (roughly 6x, I recall), but once you have them, you can re-encode them to other formats much more easily. Plus, they just sound better.

---

### Post by Depressed Man on 2007-12-07
Do it whenever your at the computer. If you have a dual core PC (and 64 bit?) it shouldn't slow your PC down that much. It'll slowly go through it all\. And one day you'll be doing the last.

---

### Post by Lostincyberspace on 2007-12-07
I have used grip to rip 4-500 cds i set it up to rip auto maticaly so all i have to do is put the disk in and away it goes takes less time to rip than encode though so set your # of .wav's to keep to a really high number 1-200

---

### Post by svtfmook on 2007-12-07
> **SonicSteve said:**
> How about just downloading the the music through a torrent or p2p. You have the CD's and in the end it will be the same anyway. I'm not sure it will be much faster but you at least won't have to insert 1000CD's plus eject 1000CDs that's an obscene number to be considering.
because i have a brother who owns a record store and get my music through his store.  i don't believe in p2p or torrents.  they are putting independently owned businesses out of business.

---

### Post by svtfmook on 2007-12-07
well, i did the 192kbps hack with sound juicer and it seems that they are ripping a lot faster as well.

---

### Post by kanem on 2007-12-07
I also endorse the Grip. In addition to what others have said you can set it up so that all you have to do is put the cd in. Period. When it's done ripping it can even eject it for you. So pop a cd in, go do something else, when you hear your tray open go put another one in.

Also, someone here said they didn't like the way it organizes the tags and files. That's totally customizable. It does it however you want.

And, in my experience, it's faster than SoundJuicer. 

1000 cds isn't so bad. Just don't try to do it all at once. When I ripped my collection I did it over the course of a couple of months. Too much at one time and you get sick of it.

---

### Post by LO Matt on 2007-12-08
> **julian67 said:**
> I'd strongly suggest using [ripit]("http://www.suwald.com/ripit/ripit.html") for this..

I prefer command line as well.  Still use abcde, but rarely as I don't get CDs much anymore . . .  Gonna look into ripit.  :guitar:

---

### Post by Dixon Bainbridge on 2007-12-08
Two suggestions:

Torrent the mp3's - might be quicker and less time consuming than manually sitting there and ripping them.  Queue them up and off you go. If you own the originals, there are no legal issues.

Or install audiograbber via wine - works a treat and is significantly quicker than any linux based ripper ive used.

---

### Post by bobbocanfly on 2007-12-08
I seriously recommend investing in a new hard drive and ripping as much as you can into Flac. After you do this you are free to rip it into whatever lossless encoding you want. It is also better than MP3 if you lose your CDs as you would still be at CD quality.

---

### Post by oldb0y on 2007-12-08
> **Dixon Bainbridge said:**
> If you own the originals, there are no legal issues.

Not quite sure about that, in the eyes of the recording industry, anything you don't pay for, you are stealing.

---

### Post by n3tfury on 2007-12-08
> **Dixon Bainbridge said:**
> Two suggestions:

Torrent the mp3's - might be quicker and less time consuming than manually sitting there and ripping them.  Queue them up and off you go. If you own the originals, there are no legal issues.



bad advice.

---

### Post by padams10001 on 2007-12-08
> **crimesaucer said:**
> Grip ripper does... just like gn2 suggested.


I really like Grip and all of it's features... except for how slow ripping is in Linux (for all rippers).


[http://nostatic.org/grip/](http://nostatic.org/grip/)
[http://nostatic.org/grip/doc/index.html#intro](http://nostatic.org/grip/doc/index.html#intro)

I've found ripping in Linux too be much faster than in XP.

> **kanem said:**
> 1000 cds isn't so bad. Just don't try to do it all at once. When I ripped my collection I did it over the course of a couple of months. Too much at one time and you get sick of it.

I agree. I've just finished ripping around 1000 CD's. I did about 10-15 each night after work anf=d that's enough for one day. Just make sure you know where you are up to in your collection as it can get very frustrating otherwise.

---

### Post by n3tfury on 2007-12-08
> **padams10001 said:**
> I've found ripping in Linux too be much faster than in XP.





all subjective.  it's going to boil down to how well your drive plays with your software, so an OS comparison is not really a valid point in regards to speed.

---

### Post by gn2 on 2007-12-08
> **oldb0y said:**
> Not quite sure about that, in the eyes of the recording industry, anything you don't pay for, you are stealing.

Depends on the law of the country you're in, it isn't the same everywhere.

---

### Post by julian67 on 2007-12-08
> **LO Matt said:**
> I prefer command line as well.  Still use abcde, but rarely as I don't get CDs much anymore . . .  Gonna look into ripit.  :guitar:

I think you'll like it. I tried all the rippers, gui and shell, from the repos and this is the king! Open a terminal, type ripit, press return and you're done...everything gets ripped, encoded, named, tagged, playlisted via the one simple command :) I love features like simultaneous encoding to different formats and sending the different encodes to different folders, even other networked PCs.

---

### Post by Dixon Bainbridge on 2007-12-08
> **n3tfury said:**
> bad advice.

Only if you're in the US. Thankfully, I'm not. :)

---

### Post by julian67 on 2007-12-08
> **Dixon Bainbridge said:**
> Only if you're in the US. Thankfully, I'm not. :)

can also land you in trouble in EU, particularly France has strong laws on this.  In UK you might get your contract with ISP terminated and be prosecuted.  With p2p you're not just downloading, you're also making the content available to others who may have no rights to it, that's where you get into trouble. I'm not saying I agree with the laws (I don't) but giving someone advice that may lead them to suffering extreme
 penalties is not a great idea.

---

### Post by n3tfury on 2007-12-08
> **Dixon Bainbridge said:**
> Only if you're in the US. Thankfully, I'm not. :)

no, i'm talking about the quality of the mp3's.  most of that crap out there have messy tags and the sound quality is usually less than desirable.

---

### Post by Dixon Bainbridge on 2007-12-08
> **n3tfury said:**
> no, i'm talking about the quality of the mp3's.  most of that crap out there have messy tags and the sound quality is usually less than desirable.

OIC. :)

Yeah true, but some creative searching can yield very good results.

---

### Post by n3tfury on 2007-12-08
and that "creative" searching then the subsequent downloading and most likely re-naming and re-tagging will be faster than ripping your own?  i doubt it.

---

### Post by julian67 on 2007-12-08
> **n3tfury said:**
> and that "creative" searching then the subsequent downloading and most likely re-naming and re-tagging will be faster than ripping your own?  i doubt it.

me too, cleaning up someone else's mess inevitably takes longer than ripping a CD how you like.

---

### Post by andrewabc on 2007-12-08
If you are going to rip the cds, do it properly and get proper bitrates. 192 constant bitrate is not the best, although 192 variable bitrate is good.

Please do not do 128 CBR you are shooting yourself in the foot and wasting your time. 128 was good back when napster was out, but audio standards have progressed since then.

Don't forget to use windows and use [Exact Audio Copy](http://www.exactaudiocopy.de/) for good quality.

:P

---

### Post by julian67 on 2007-12-08
> **andrewabc said:**
> If you are going to rip the cds, do it properly and get proper bitrates. 192 constant bitrate is not the best, although 192 variable bitrate is good.

Please do not do 128 CBR you are shooting yourself in the foot and wasting your time. 128 was good back when napster was out, but audio standards have progressed since then.

Don't forget to use windows and use [Exact Audio Copy](http://www.exactaudiocopy.de/) for good quality.

:P

??????

did you hear of free software and ogg vorbis and flac?

EAC usually has no advantage. It's sole advantage is if your cd drive caches audio data, but ruby ripper is pretty much as good for this.  EAC is also not perfect, I've had bad rips using secure mode when I used Windows. Burst mode with test & copy is often better, this surprises people who don't realise at all how the ripper works. I haven't had any problems with hundreds of rips using grip, sound-juicer, asunder, ripit etc. 

Bitrates are up to the OP, but ogg -q 6 or 7 will be superior to mp3 vbr around 192, probably around the same size or smaller too.

---

### Post by SonicSteve on 2007-12-08
> **svtfmook said:**
> because i have a brother who owns a record store and get my music through his store.  i don't believe in p2p or torrents.  they are putting independently owned businesses out of business.

You already own the music, you're just saving yourself the work of ripping it yourself. I don't believe in them either for the purpose of downloading music you don't own but if you do own it I don't see anything wrong with it. Yes you end up sharing it as you download it but the onus is not on you for that, it's on the person downloading who doesn't own it.

I buy all my music and I don't mind downloading the songs @128 even if the names are wrong as long as they aren't aren't ripped poorly. It all depends on how serious you are about your music. I suppose if you have 1000 albums you are probably quite serious about though right? 

On a separate note - forgive me if someone already asked this- how did you let you ripping get 1000 albums behind?

---

### Post by SonicSteve on 2007-12-08
> **andrewabc said:**
> If you are going to rip the cds, do it properly and get proper bitrates. 192 constant bitrate is not the best, although 192 variable bitrate is good.

Please do not do 128 CBR you are shooting yourself in the foot and wasting your time. 128 was good back when napster was out, but audio standards have progressed since then.

Don't forget to use windows and use [Exact Audio Copy](http://www.exactaudiocopy.de/) for good quality.

:P

I can't hear the diff between 128 and 192. In what way have the standards changed? 128 is still the same as it was 6 years ago, it's size hasn't really changed if at all and I don't see much benefit for justifying 192 and causing the files to grow 50% larger.

---

### Post by SonicSteve on 2007-12-08
> **oldb0y said:**
> Not quite sure about that, in the eyes of the recording industry, anything you don't pay for, you are stealing.

You can't steal something you already own. It's a matter of tomato, tomata if you rip them yourself or download them, as long as you own the music.

---

### Post by julian67 on 2007-12-08
If you use p2p to download copyrighted content you're also making it available and there's the risk.   Any brief look at recent high profile cases will confirm this.  You get sued/prosecuted not for downloading but for making the content available. It doesn't matter if you own the CDs or not, and the penalties are extreme. 

bitrates: anyone who can't hear the difference between 128k and a a high bitrate vbr or ogg encode needs a serious hearing test or their ears syringed to remove the wax :)  This is particularly true if you either have a high quality hi fi at home or you use very good earphones/headphones with a quality personal player.  And encoders have changed a lot over the years. For example the lame encoder for mp3 has been continuously developed, also the ogg encoder. They both give different and better results than several years ago, both in terms of audio quality and other factors like encoding speed, resource consumption for decoding (big effect on battery life for personal audio) and file size.

---

### Post by Spike-X on 2007-12-08
> **oldb0y said:**
>  in the eyes of the recording industry, anything you don't pay for, you are stealing.

And even if you do pay for it, you're probably planning to steal it anyway, and thus you should be treated like a potential criminal at all times.

---

### Post by SonicSteve on 2007-12-09
> **julian67 said:**
> If you use p2p to download copyrighted content you're also making it available and there's the risk.   Any brief look at recent high profile cases will confirm this.  You get sued/prosecuted not for downloading but for making the content available. It doesn't matter if you own the CDs or not, and the penalties are extreme. 

bitrates: anyone who can't hear the difference between 128k and a a high bitrate vbr or ogg encode needs a serious hearing test or their ears syringed to remove the wax :)  This is particularly true if you either have a high quality hi fi at home or you use very good earphones/headphones with a quality personal player.  And encoders have changed a lot over the years. For example the lame encoder for mp3 has been continuously developed, also the ogg encoder. They both give different and better results than several years ago, both in terms of audio quality and other factors like encoding speed, resource consumption for decoding (big effect on battery life for personal audio) and file size.

I'll try ripping at 192 again, perhaps my hearing isn't as good as it should be. I definitely could hear diff between 96 and 128 years ago.  96 sounded like a tin can. 128 sounded like it should, at least to me.

---

### Post by SonicSteve on 2007-12-09
> **Spike-X said:**
> And even if you do pay for it, you're probably planning to steal it anyway, and thus you should be treated like a potential criminal at all times.

What exactly are you saying? You can't paint everyone with the same color. In Canada our laws are different than yours. As far as being treated like a criminal at times, what exactly are you meaning?

---

### Post by julian67 on 2007-12-09
If you want to clearly notice the difference without the hassle of blind  listening tests then don't compare the 128 with 192 directly, but compare each with listening to the CD. You'll definitely notice a big difference between 128 and CD and more than likely notice some difference between 192 and CD.  Depends a little on your equipment and musical taste of course.

---

### Post by Mr.Auer on 2007-12-09
Id have to agree with that, being an audiophile and a musician myself.
I simply cant enjoy even 192 kbps music if its well-made ambient for example, the artifacts hurt my ear. In 128 kbps they are clearly audible, and to a lesser degree in 192 as well. I consider 192 ogg to be minimum.

If I rip to mp3 I use either alt preset extreme variable bitrate in LAME or 256 cbr. If I rip my own cds, I usually use FLAC.

---

### Post by Mr.Auer on 2007-12-09
> **andrewabc said:**
> 
Don't forget to use windows and use [Exact Audio Copy](http://www.exactaudiocopy.de/) for good quality.

:P

As I said earlier, theres no need for EAC. Just use Ruby Ripper, it does the same thing and rips to mp3, ogg and flac, logged, and repairs errors. You can set the amount of matches required for erroneus reads yourself.

[http://wiki.hydrogenaudio.org/index.php?title=Rubyripper](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper)

---

### Post by Spike-X on 2007-12-09
> **SonicSteve said:**
> What exactly are you saying? You can't paint everyone with the same color. In Canada our laws are different than yours. As far as being treated like a criminal at times, what exactly are you meaning?

Here's a hint: The post to which I was replying began with, ***"In the eyes of the recording industry..."***.

I'll leave you to take it from there.

---

### Post by SonicSteve on 2007-12-10
> **Spike-X said:**
> Here's a hint: The post to which I was replying began with, ***"In the eyes of the recording industry..."***.

I'll leave you to take it from there.

Thanks,
That bit of context was helpful. I understand what your point now.

I at least (I'm sure others as well) can say that own virtually all the music content on my systems. The ratio is beyond 99.9% owned. The remaining .01% takes into account music that I once downloaded -about 5 songs- and the occasional time someone emails something they shouldn't have. I don't believe in just downloading music, we'll only hurt ourselves.
If we download, musicians won't be able to make a living, they will stop recording, we will have less music available. There will also be some positive spin offs, entertainment industry fill with sleaze is weakened, meaning less sleaze. Less tabloids showing us the exploits of the Britany Spears of the world etc.

Now back to discussion. I think the only way to get the 1000 CD's ripped is to slowly peck away a few each day. Even at 6 a day it will be done in half a year!! Approx.

---

### Post by aaaantoine on 2007-12-10
Perhaps a CD-ROM disc changer would come in handy for this daunting task.

---

### Post by inversekinetix on 2007-12-10
download what you can and rip the rest save time and hassle

---

### Post by VCSkier on 2007-12-11
I'm facing a similar task, but would like a method that suits itself better to creating bit-perfect physical backups.  Is there a quality ripping frontend for linux that will create cue sheets so that I can easily burn the audio back to a cd, while keeping the track times and gaps accurate?  So far, K3b seems to be the only viable option, but it's so big and heavily dependent on KDE.  I'd prefer something more gnome friendly.  Thanks.

---

### Post by inversekinetix on 2007-12-12
Think yourselves lucky, whatever method you use it will be faster than it was for me ripping 600 LPs

---

### Post by MetalMusicAddict on 2007-12-12
> **svtfmook said:**
> i should have stayed on top of this, but i've decided to do it now...

so what's the easiest way?

Well I just did 650 or so using Grip and went to FLAC. I also have a Grip HOWTO [HERE]("http://ubuntuforums.org/showthread.php?t=183125").

It really depends oh what you're looking for. [abcde]("http://lly.org/~rcw/abcde/page/") is another way to go. You can set up multiple instances and have them rip/encode one right after another.

What format do you want to go to? Is space a issue?

Really just best to get in there and do it. :) Even if it takes a while.

> **svtfmook said:**
> because i have a brother who owns a record store and get my music through his store.  i don't believe in p2p or torrents.  they are putting independently owned businesses out of business.
Awesome. =D> I seek out every shop like this and have even thought about starting one myself.

---

### Post by julian67 on 2007-12-12
> **VCSkier said:**
> I'm facing a similar task, but would like a method that suits itself better to creating bit-perfect physical backups.  Is there a quality ripping frontend for linux that will create cue sheets so that I can easily burn the audio back to a cd, while keeping the track times and gaps accurate?  So far, K3b seems to be the only viable option, but it's so big and heavily dependent on KDE.  I'd prefer something more gnome friendly.  Thanks.

[Ripit]("http://www.suwald.com/ripit/ripit.html")

> 
The program will do the following without user intervention:

  # gets the Audio CD Album/Artist/Tracks information from CDDB
  # rips the Audio CD Tracks
  # encodes to flac, mp3 or ogg
  # id3 tags encoded songs
  # Creates an playlist (m3u) file
 ** # Can generate a toc (cue) sheet for nice DAO burning**
  # Can prepare and send a CDDB submission and save it locally
  # Can extract hidden songs and split ghost songs
  # May create md5sum files for all tracks
  # Run several encoder processes at the same time and same run


---

### Post by n3tfury on 2007-12-12
> **inversekinetix said:**
> download what you can and rip the rest save time and hassle

no.

---

### Post by VCSkier on 2007-12-15
> **n3tfury said:**
> no.
+1

Go w/ abcde.  Setup is a bit of work, but its quite nice thereafter.

---

### Post by dasunst3r on 2007-12-15
Like others said, *grip* is the best CD ripper I have used to date.

Understandably, ripping 1,000+ CDs is not an easy task.  If you really, really love open source, you should rip all your music in Ogg Vorbis format.  Otherwise, MP3 will be just fine, although I like my music in VBR.

If you have kids and more computers, I'd pay them to help you.

---

### Post by Lostincyberspace on 2007-12-15
For quality I would first rip to flac and then resave them to cds and easier retrieval later since you can index it a little more. And if it is to much space then you can re-encode to a smaller format.

---

### Post by Bungo Pony on 2007-12-15
Here's a suggestion if you have some drivespace to spare...

What I usually do is rip my CDs to .wav format first (I also use EAC in Windows). Ripping to .wav files is incredibly fast. Once I rip a whole pile of them, I'll set CDex to convert them all to MP3 format, and then I'll walk away from the PC.

It's the MP3 encoding that slows everything down which is why I do it afterward.

---

### Post by n3tfury on 2007-12-15
> **Bungo Pony said:**
> Here's a suggestion if you have some drivespace to spare...

What I usually do is rip my CDs to .wav format first (I also use EAC in Windows). Ripping to .wav files is incredibly fast. Once I rip a whole pile of them, I'll set CDex to convert them all to MP3 format, and then I'll walk away from the PC.

It's the MP3 encoding that slows everything down which is why I do it afterward.

if you're going to extract to .wav, why not extract to .flac and do the same thing while keeping all of the quality while using LESS space?

---

### Post by koleoptero on 2007-12-15
Grip :guitar: I've been using it since 2001 with no problems at all. And if you have enough free space use flac, you won't regret it.

---

### Post by Angus77 on 2007-12-17
Grip looks really nice.

Is there a way to set the drive offset?  I don't seem to be able to find the option.  It's something you can do in EAC and RubyRipper.

---

### Post by forrestcupp on 2007-12-17
The RIAA says that the average price of a CD is $12.75.  That means you have $12,750 in CD's!  I wish I had $12,750.  I wouldn't spend it on CD's.

---

### Post by Bungo Pony on 2007-12-17
> if you're going to extract to .wav, why not extract to .flac and do the same thing while keeping all of the quality while using LESS space?

What's the point of retaining quality when you're converting it to MP3? 

Recently as part of my slow switch from Windows, I've been trying to do audio work in Linux. Some of it is fantastic, like recording and editing in Audacity. But then there's the issue of extracting audio tracks...

I've tried Sound Juicer, Grip, and RipperX. All of them are crap. The best thing I did was run CDex in Wine. It works well, it extracts fairly fast, it's pretty straight-forward, it does exactly what I want, the results are great, and it's free.

But for large amounts of extraction, I'll probably continue to do it in Windows since EAC can do it at a phenominally high speed. (And yes, I tried using EAC in Wine, but it didn't work.)

IMO, Linux really needs work in this department.

---

### Post by lespaul_rentals on 2007-12-17
> **Dixon Bainbridge said:**
> Torrent the mp3's - might be quicker and less time consuming than manually sitting there and ripping them.  Queue them up and off you go. If you own the originals, there are no legal issues.

Wrong, wrong, wrong.  It might be quicker, but what is the bitrate?  It takes forever to hunt down a good 192+ kbps torrent.  How about the ID3 tags?  Most people are complete morons about tagging their music correctly.  It sucks to get an album with the artist name as the track number.  And even if you do own the originals, there **are** legal issues.  Have you never heard of the RIAA?  They scan popular trackers looking for people to warn/sue.  Even if you own a thousand copies of "The White Album" by The Beatles, torrenting it means you will share some upload.  Thus you are helping distribute illegal copies.

> **svtfmook said:**
> i don't believe in p2p or torrents.  they are putting independently owned businesses out of business.

No, they aren't.  I buy more music now that I p2p.  It's introduced me to bands I would have never otherwise heard of.

Either use a command-line batch job to make it quick, or use K3b to rip to .flac.  Not only is it faster ripping to a lossless codec, but K3b does its job very well.  (Yay for KDE apps.)

---

### Post by bruce89 on 2007-12-17
> **Bungo Pony said:**
> I've tried Sound Juicer, Grip, and RipperX. All of them are crap. The best thing I did was run CDex in Wine. It works well, it extracts fairly fast, it's pretty straight-forward, it does exactly what I want, the results are great, and it's free.

But for large amounts of extraction, I'll probably continue to do it in Windows since EAC can do it at a phenominally high speed. (And yes, I tried using EAC in Wine, but it didn't work.)

IMO, Linux really needs work in this department.

How the hammy can a FLAC ripped by Sound Juicer not be a perfect copy?

---

### Post by lespaul_rentals on 2007-12-17
> **Bungo Pony said:**
> What's the point of retaining quality when you're converting it to MP3? 

Recently as part of my slow switch from Windows, I've been trying to do audio work in Linux. Some of it is fantastic, like recording and editing in Audacity. But then there's the issue of extracting audio tracks...

I've tried Sound Juicer, Grip, and RipperX. All of them are crap. The best thing I did was run CDex in Wine. It works well, it extracts fairly fast, it's pretty straight-forward, it does exactly what I want, the results are great, and it's free.

But for large amounts of extraction, I'll probably continue to do it in Windows since EAC can do it at a phenominally high speed. (And yes, I tried using EAC in Wine, but it didn't work.)

IMO, Linux really needs work in this department.

Don't use Gnome applications for stuff like this, use K3b.

---

### Post by Bungo Pony on 2007-12-17
> How the hammy can a FLAC ripped by Sound Juicer not be a perfect copy?

The result was a digitally distorted rip :(
I was really pissed when I let it rip a whole CD like that, which took an incredibly long time.

> Don't use Gnome applications for stuff like this, use K3b.

I dumped K3b after it repeatedly crashed on me :(

---

### Post by bapoumba on 2007-12-17
I did a little cleanup and moved an off topic discussion starter post there :
[http://ubuntuforums.org/showthread.php?t=643311](http://ubuntuforums.org/showthread.php?t=643311)

Please keep this thread on topic, thanks.

---

### Post by kuja on 2007-12-19
I'd say the best one I've used is ripit. Beforehand I always used k3b, but if you need to do a lot screwing with the GUI can be tedious and slow you down, and besides that it won't let you do more than one CD at a time with more than one drive. 

With Ripit, just set up the config file, pull open a couple shells, type in the command once (ie: ripit -d /dev/hda), and then just press up;enter; every time you insert another cd ..... about as streamlined as things are going to get methinks. Another option if you only have one CD drive (it won't work with two, it'll mess up on you) is to use the --loop option. That way you don't even have to punch in the command again or hit up;enter;, soon as you pop in another it'll start ripping the next. Convenient no?

---

### Post by FuturePilot on 2007-12-19
I like Grip. Grip has paranoia. Sound Juicer made all my music all scratchy sounding. They came out perfect with Grip. It's also light weight, yet highly configurable.

---

### Post by tehhaxorr on 2007-12-19
Just rip the important ones, you can't seriously expect to listen to 1000cd's worth of music. just rip the ones you deem great cd's and leave the mediocre ones.

---

### Post by nutter78 on 2007-12-19
I'm going to look into Grip - thx 4 the heads up!

---

### Post by julian67 on 2007-12-19
> **kuja said:**
> I'd say the best one I've used is ripit. Beforehand I always used k3b, but if you need to do a lot screwing with the GUI can be tedious and slow you down, and besides that it won't let you do more than one CD at a time with more than one drive. 

With Ripit, just set up the config file, pull open a couple shells, type in the command once (ie: ripit -d /dev/hda), and then just press up;enter; every time you insert another cd ..... about as streamlined as things are going to get methinks. Another option if you only have one CD drive (it won't work with two, it'll mess up on you) is to use the --loop option. That way you don't even have to punch in the command again or hit up;enter;, soon as you pop in another it'll start ripping the next. Convenient no?

I've never needed to specify the device (unless I need to use a different one than is default), I just type ripit and hit return

---

### Post by kuja on 2007-12-19
> **julian67 said:**
> I've never needed to specify the device (unless I need to use a different one than is default), I just type ripit and hit return
You seem to be missing the larger picture. The OP has 1000 CDs to rip. Too many rippers can't even so much as handle ripping two CDs at once in two different drives. If you're going to do this (which will speed things up when you've got a lot to rip, drastically), you'll be wanting to specify the device ... seeing as you'll be using multiple drives to do it with.

---

### Post by julian67 on 2007-12-20
> **kuja said:**
> You seem to be missing the larger picture. The OP has 1000 CDs to rip. Too many rippers can't even so much as handle ripping two CDs at once in two different drives. If you're going to do this (which will speed things up when you've got a lot to rip, drastically), you'll be wanting to specify the device ... seeing as you'll be using multiple drives to do it with.

yes agreed, you're right it's good to use 2 drives if possible. But older processors will struggle running multiple encoders simultaneously so it isn't always practical. I can encode to ogg and flac simultaneously with my Athlon 2700 but it uses 100% CPU.... And older boards with not so good IDE controllers or poor optical drives might not be so great trying to rip 2 CDs at a time. But I agree it's the best way to work through a big collection by a long way. Ripit rules! :)

---

### Post by Dixon Bainbridge on 2007-12-20
> **lespaul_rentals said:**
> Wrong, wrong, wrong.  It might be quicker, but what is the bitrate?  It takes forever to hunt down a good 192+ kbps torrent.  How about the ID3 tags?  Most people are complete morons about tagging their music correctly.  It sucks to get an album with the artist name as the track number.  And even if you do own the originals, there **are** legal issues.  Have you never heard of the RIAA?  They scan popular trackers looking for people to warn/sue.  Even if you own a thousand copies of "The White Album" by The Beatles, torrenting it means you will share some upload.  Thus you are helping distribute illegal copies.


You're in the US, I'm in the EU. We have a more reasonable and sensible outlook on copyright issues atm. :)

---

### Post by amorangi on 2007-12-22
After a little experimentation and taking some hints from this thread I'm taking it "easy" and ripping with Ripit. Set up the config file and you're good to go. 
I'm ripping to Flac and mp3 VBR on highest quality, and a toc. I'm then archiving all this to an external drive which will be stored in my safe, and I'm putting the mp3s to my server for easy access. 
The VBR gives good enough quality but roughly 25% smaller than 320 CBR. The lowest quality I can stand is 192kb/s for mp3s, but prefer 256kb/s - but at this level you may as well just go for 320kb/s. The difference isn't noticeable on a portable player or in your car, but on a reasonable quality home stereo you can tell the difference. I guess it depends on where you're going to listen, but I'd rather have just one high quality file.  
Today I got through about 60 CDs, but took breaks to mow the lawns etc, so wasn't attentive to the whole time. I could have used multiple drives, but being a disk jockey gets tiresome, whereas swapping a CD every 5 - 10 minutes isn't too annoying.
The only thing I would have liked Ripit to be able to do which I don't think it can is to output the Flac and mp3 files to different directories.

---

### Post by julian67 on 2007-12-22
If you use the latest Ripit 3.7 beta version from [http://www.suwald.com/ripit/ripit.html]("http://www.suwald.com/ripit/ripit.html") you can have the different formats output to different folders

---

### Post by amorangi on 2007-12-22
Ahh, yes, I saw no new features for the Ripit beta, but I'd consider that a new feature. I'm using that now, though I have encountered a few bugs, none seem to be killer.

---

### Post by Ron F. on 2008-01-04
Ripping CDs is a task where it appears Linux has simply not caught up with Windows. I have used many rippers: grip, sound Juicer CD extractor, soundKonverter, EAC, dBpoweramp Music Converter (dMC,) and others whose names I now forget.

For running a native Linux solution, I think soundKonverter is best. For ripping it will use CD paranoia. I had to load a variety of codecs using the Synaptic Package Manager before it became useful to me, such as flac and vorbis-tools.

I have also run EAC under wine, and that works too.

But without question my choice is to run the reference version of dBpoweramp Music Converter under wine - it is a Windows program. I say this with about a thousand CDs from my collection ripped as prior experience. It has a problem ejecting CDs, but otherwise it works flawlessly under wine. It is as fast or faster than when running under Windows! It rips securely much faster than EAC, uses AccurateRip, and AMG for tagging including composer information, and album art, and can apply many DSP effects, some of which I have had to use in the past.

To eject a CD however, I have to hit the button on the tray - the software eject button provided by the application does not work under wine.

I find it quite useful, as AMG, (costs about $5/year for a subscription) provides better tag info than freedb.

I am using an all commercial solution, but it was not terribly expensive, and when ripping as many CDs as I have, the open-source paradigm was going to cost me much more (time is the most expensive resource there is) to get this all done.

Tagging goes pretty well for popular music, but fixing tags on classical music CDs, particularly older CDs is essentially a disaster. I use EasyTag for fixing tags. I am experimenting with MusicBrainz.

My entire CD collection has been ripped to FLAC. Life is good. I listen to it all using a Logitech Squeezebox device connected to my music system. My stockpile of CDs (and CD player) is now collecting dust!

-Ron

---

### Post by julian67 on 2008-01-05
> **Ron F. said:**
> Ripping CDs is a task where it appears Linux has simply not caught up with Windows. I have used many rippers: grip, sound Juicer CD extractor, soundKonverter, EAC, dBpoweramp Music Converter (dMC,) and others whose names I now forget.

For running a native Linux solution, I think soundKonverter is best. For ripping it will use CD paranoia. I had to load a variety of codecs using the Synaptic Package Manager before it became useful to me, such as flac and vorbis-tools.

I have also run EAC under wine, and that works too.

But without question my choice is to run the reference version of dBpoweramp Music Converter under wine - it is a Windows program. I say this with about a thousand CDs from my collection ripped as prior experience. It has a problem ejecting CDs, but otherwise it works flawlessly under wine. It is as fast or faster than when running under Windows! It rips securely much faster than EAC, uses AccurateRip, and AMG for tagging including composer information, and album art, and can apply many DSP effects, some of which I have had to use in the past.

To eject a CD however, I have to hit the button on the tray - the software eject button provided by the application does not work under wine.

I find it quite useful, as AMG, (costs about $5/year for a subscription) provides better tag info than freedb.

I am using an all commercial solution, but it was not terribly expensive, and when ripping as many CDs as I have, the open-source paradigm was going to cost me much more (time is the most expensive resource there is) to get this all done.

Tagging goes pretty well for popular music, but fixing tags on classical music CDs, particularly older CDs is essentially a disaster. I use EasyTag for fixing tags. I am experimenting with MusicBrainz.

My entire CD collection has been ripped to FLAC. Life is good. I listen to it all using a Logitech Squeezebox device connected to my music system. My stockpile of CDs (and CD player) is now collecting dust!

-Ron

The fact that you prefer a particular Win32 application only means something about your preferences, not about Win Vs Linux CD ripping in general.  I've used all the applications, both Win & Linux, that you mention and others too (i.e. Ripit, Asunder, Easy CD-DA Extractor, CDex) and my preference is for Ripit (cli)  or Asunder (GUI), both Linux apps.  On Windows I guess I'd use CDex as it is under a free license.  And of course you need codecs, this is the same situation with any OS. Some Win applications include the codecs, or download them as part of the install, but by default Windows doesn't support mp3, flac, Ogg or anything audio except WMA and WAV. The only difference with Linux is that in Linux the applications are usually licensed under GPL or similar and so you need to install the non-free codecs yourself, which is hardly difficult.  Distros support Wav, Ogg and Flac out of the box, some also support mp3 on install and the other codecs can easily be added in a few minutes. 

I was a big user of EAC when I used Windows but frankly I don't miss it.  If I acquire a cue+ape or cue+flac or cue+wav rip made by EAC I found I can easily deal with it using cuebreakpoint, shnsplit and Easytag so I no longer need Windows rippers running under Wine.  Most users don't really appreciate that EAC in secure mode can make bad rips too, and sometimes burst mode with test & copy is better.  In practice any of the cdparanoia based tools is going to work just as well and there is always Ruby Ripper for those who need a slower rip and an EAC style logfile of crc checks and soothing "OK" messages to reassure them :-) 

I have to say though that I was of the same mind for a while, I really thought Linux distros lacked good CD ripping and encoding tools...but it was more the case that I had to look a little harder and learn some new tools and generally become familiar with the Free environment in the same way that I had naturally become familiar with the Win32 environment over the years.  Switching from Windows to a distro is a lot like starting from zero or learning a new language....you miss a lot of things that later strike you as obvious, and things that seem like daunting obstacles or insoluble problems a few months later will look like the most trivial no brainer......usually :lolflag:

---

### Post by Ron F. on 2008-01-07
> **julian67 said:**
> The fact that you prefer a particular Win32 application only means something about your preferences, not about Win Vs Linux CD ripping in general.

Absolutely. I dislike Windows, and will always use an open-source solution under Linux, if it serves my needs.

> **julian67 said:**
> 
And of course you need codecs, this is the same situation with any OS. 


Very true. Regardless of the ripper used (except maybe iTunes) :)

> **julian67 said:**
> 
I was a big user of EAC when I used Windows but frankly I don't miss it.  If I acquire a cue+ape or cue+flac or cue+wav rip made by EAC I found I can easily deal with it using cuebreakpoint, shnsplit and Easytag so I no longer need Windows rippers running under Wine.


I like EAC, but I don't miss it either. If it was EAC versus native Linux rippers, it wouldn't be an issue. EAC is a great ripper, but does not offer anything that I had to have when ripping my thousand CDs.

> **julian67 said:**
> 
I have to say though that I was of the same mind for a while, I really thought Linux distros lacked good CD ripping and encoding tools...but it was more the case that I had to look a little harder and learn some new tools and generally become familiar with the Free environment in the same way that I had naturally become familiar with the Win32 environment over the years.  Switching from Windows to a distro is a lot like starting from zero or learning a new language....you miss a lot of things that later strike you as obvious, and things that seem like daunting obstacles or insoluble problems a few months later will look like the most trivial no brainer......usually :lolflag:

This is where I take a somewhat different opinion, and I have tried many rippers under Linux. The issue is not that native Linux tools are perfect for ripping a handful of CDs - they are. The issue is what is best for ripping a thousand, or even more CDs yourself, which could take a year or more before you are done. In that case - your computer, your OS, everything you have is less important - even money in some respects!!! Yes - think about it: all that matter is the time it is going to take to do it. It may be that the best solution is to pay someone else to do it.

Features like using online AccurateRip, being able to switch on the fly between online tagging databases, automatic download of album art, are very useful features when wading into a kiddie-pool full of CDs.

My recommendation for dBpoweramp was motivated by preferences I think are very useful when faced with a task of this magnitude.

-Ron

---

### Post by julian67 on 2008-01-07
> **Ron F. said:**
> Absolutely. I dislike Windows, and will always use an open-source solution under Linux, if it serves my needs.



Very true. Regardless of the ripper used (except maybe iTunes) :)



I like EAC, but I don't miss it either. If it was EAC versus native Linux rippers, it wouldn't be an issue. EAC is a great ripper, but does not offer anything that I had to have when ripping my thousand CDs.



This is where I take a somewhat different opinion, and I have tried many rippers under Linux. The issue is not that native Linux tools are perfect for ripping a handful of CDs - they are. The issue is what is best for ripping a thousand, or even more CDs yourself, which could take a year or more before you are done. In that case - your computer, your OS, everything you have is less important - even money in some respects!!! Yes - think about it: all that matter is the time it is going to take to do it. It may be that the best solution is to pay someone else to do it.

Features like using online AccurateRip, being able to switch on the fly between online tagging databases, automatic download of album art, are very useful features when wading into a kiddie-pool full of CDs.

My recommendation for dBpoweramp was motivated by preferences I think are very useful when faced with a task of this magnitude.

-Ron

yes, that's all about your preference and makes sense, whereas stating "Ripping CDs is a task where it appears Linux has simply not caught up with Windows" is all about presenting opinion as fact and doesn't make sense ;-)

---

### Post by Hallvor on 2008-01-07
> **svtfmook said:**
> well, i think sound juicer only rips at 128kbps.

what ripper does 192??

Try inserting this line in soundjuicer:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192
```

---

### Post by Ron F. on 2008-01-07
Julian67,

Ok - that's a fair statement and I have to admit that for normal CD ripping tasks, a Windows solution (or Mac for that matter) is not necessary today.

I think the issue of ripping huge quantities of CDs however is a different kind of problem.

-Ron

---

### Post by inversekinetix on 2008-01-07
> **lespaul_rentals said:**
> Wrong, wrong, wrong.  It might be quicker, but what is the bitrate?  It takes forever to hunt down a good 192+ kbps torrent.  How about the ID3 tags?  Most people are complete morons about tagging their music correctly.  It sucks to get an album with the artist name as the track number.  And even if you do own the originals, there **are** legal issues.  Have you never heard of the RIAA?  They scan popular trackers looking for people to warn/sue.  Even if you own a thousand copies of "The White Album" by The Beatles, torrenting it means you will share some upload.  Thus you are helping distribute illegal copies.




wrong,wrong,wrong.
The Recording Industry ***. of America and DMCA's jurisdiction ends at the US border, they might like to think it is global but each country has it's own laws (see the movies 'steal this movie' I and II).  Finding 192k+ files is as easy as adding a parameter to a search filter, tags are seldom a problem and can be easily fixed with automated tagging software.  To be absolutely certain of good bitrate, FULLY tagged media there are many servers which demand such criteria from their members.

---

### Post by allforcarrie on 2008-01-08
set a program to rip automaticly and eject when done. Turn on band of brothers and open a beer.....

---

