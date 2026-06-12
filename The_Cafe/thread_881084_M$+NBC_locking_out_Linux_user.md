---
title: "M$+NBC locking out Linux user"
date: 2008-08-05
forum: The Cafe
---

### Post by xebian on 2008-08-05
With the Olympics just around the corner, looks like Linux users has no recourse but use Windows to view the Olympics.

Even windows in vbox won't install the required silverlight plugins.

Does anyone knows alternative sites other than NBC? :(

---

### Post by Icehuck on 2008-08-05
> **xebian said:**
> With the Olympics just around the corner, looks like Linux users has no recourse but use Windows to view the Olympics.

Even windows in vbox won't install the required silverlight plugins.

Does anyone knows alternative sites other than NBC? :(

Or you can just get moonlight which is the linux version.

---

### Post by tom66 on 2008-08-05
Or you can get a cheap TV card with Free to air or Freeview capabilities (like in the UK) and tune into the BBC. Or get a free to air box. I'll probably record it if I can get a signal.

---

### Post by ooobuntooo on 2008-08-05
Use Firefox for Windows under WINE!

---

### Post by xebian on 2008-08-05
> **Icehuck said:**
> Or you can just get moonlight which is the linux version.
I might try this thanks. I hope I could get past NBC check for OS.

---

### Post by tom66 on 2008-08-05
Forge the user agent string with this Firefox plugin:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by xebian on 2008-08-05
> **tom66 said:**
> Or you can get a cheap TV card with Free to air or Freeview capabilities (like in the UK) and tune into the BBC. Or get a free to air box. I'll probably record it if I can get a signal.

But not for non-UK viewers.

---

### Post by xebian on 2008-08-05
> **tom66 said:**
> Forge the user agent string with this Firefox plugin:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

I tried (changing useragent) that already but no go.  Somehow NBC checks the OS

---

### Post by tom66 on 2008-08-05
Probably activex. You might have to try WINE with the switcher.

---

### Post by mrgnash on 2008-08-05
Couldn't care less.

---

### Post by amazingtaters on 2008-08-05
> **xebian said:**
> I tried (changing useragent) that already but no go.  Somehow NBC checks the OS

I got past the OS check fine, but couldn't get any video to load.

---

### Post by mips on 2008-08-05
> **mrgnash said:**
> Couldn't care less.

I'm not watching the olympics either.

---

### Post by ZarathustraDK on 2008-08-05
You could get one of these also ;)

[IMG]http://www.pinkgodzillagames.com/retro/old%20tv-thumb.JPG[/IMG]

---

### Post by StrawberryJam8 on 2008-08-05
I like watching Olympic bloopers, so i'll probably wait for those on Youtube.

---

### Post by amazingtaters on 2008-08-05
Really one of the few events that I actually want to watch is rowing. Oh and discus. Other than that though, I could pass on the rest of the Olympics.

---

### Post by mips on 2008-08-05
Depending on where you live you might be able to see it on Youtube. Youtube will be streaming to 77 teritories but NOT those that already have the digital rights.

Would like to see the list of countries.

---

### Post by benny bronx on 2008-08-05
> Really one of the few events that I actually want to watch is rowing. Oh and discus. Other than that though, I could pass on the rest of the Olympics.

I'd watch if they threw the discus at the boats.

---

### Post by bobbybobington on 2008-08-05
Avast me Harties! Tis a [good day fur plunderin']("http://newteevee.com/2008/08/05/pirate-olympics-5-alternative-ways-to-watch-the-olympic-games-online/")\\:D/

---

### Post by tamoneya on 2008-08-08
> **amazingtaters said:**
> Really one of the few events that I actually want to watch is rowing. Oh and discus. Other than that though, I could pass on the rest of the Olympics.

Yes i cant wait for rowing either.  Four years ago they would always show it at like 4 AM.

---

### Post by phrostbyte on 2008-08-08
If someone actually gets this working on Moonlight they are a hero.

---

### Post by kernelhaxor on 2008-08-08
> **xebian said:**
> 
Even windows in vbox won't install the required silverlight plugins.


Am using windows in vbox and I was able to install silverlight .. works fine

---

### Post by Dr. C on 2008-08-08
One can try [http://www.cbc.ca]("http://www.cbc.ca")
Works fine on Ubuntu 64bit

---

### Post by xdevnull on 2008-08-08
Try this out...
[http://www.nbcolympics.com/tv_and_online_listings/zone=PT/day=0/sport=FE/online.html](http://www.nbcolympics.com/tv_and_online_listings/zone=PT/day=0/sport=FE/online.html)

I installed user agent to lie about my OS, so the screen comes up.  It asks me about silverlight, which I decline, b/c it won't work...but no video seems to come up.

It's a great thing that NBC is transmitting some of the less popular sports via the internet...too bad they won't do it in a format everyone can see.

---

### Post by galamud on 2008-08-09
If it helps, here's some python code I hacked up to imitate the official Silverlight client.  Unfortunately piping its output into mplayer directly doesn't work (it bitches about "Cannot seek backward in linear streams!"), and that's all I've had time to try.

```
#!/usr/bin/python

import urllib2

url = "http://msolympics-ENC11-high.wm.llnwd.net/msftolympicslive-live/msolympics_ENC11_high?e=1218255518&amp;h=a0559a7d0fb468695e1b47c2fb81326f"

opener = urllib2.build_opener()
opener.addheaders = [
    ('User-Agent', 'NSPlayer/11.08.0005.0000'),
    ('Accept', '*/*'),
    ('Accept-Language','en-us, *;q=0.1'),
    ('Connection', 'Keep-Alive'),
    ('Pragma', 'client-id=3505472483, playlist-gen-id=252031, xClientGuid={00000000-0000-0000-0000-000000000000}, xPlayStrm=1, no-cache,stream-time=0,stream-offset=4294967295:4294967295,packet-num=4294967295,max-duration=0, LinkBW=2147483647,rate=1.000, AccelDuration=20000, AccelBW=2147483647, stream-switch-count=3, stream-switch-entry=ffff:1:0 ffff:2:0 ffff:3:0'),
    ('Supported', 'com.microsoft.wm.srvppair, com.microsoft.wm.sswitch, com.microsoft.wm.startupprofile, com.microsoft.wm.predstrm'),
    ]

f = opener.open(url)

for line in f:
    print line
```

---

### Post by Kingsley on 2008-08-09
I just found this website: [http://itsgametime.tv/OlympicsLive.html](http://itsgametime.tv/OlympicsLive.html)

I'm not yet sure if it works correctly though.

---

### Post by mocha on 2008-08-09
I'm running WinXP in virtualbox with IE 6, installed a "silverlight" executible when prompted and it's working fine, sound and all.  User agent switcher in Linux Firefox never showed video.

---

### Post by Saint Angeles on 2008-08-09
cant you just read about who wins in the paper or on the news?

whats the point of watching some weirdos play with eachother?

---

### Post by BigSilly on 2008-08-09
[Is this no good?]("http://news.bbc.co.uk/sport1/hi/olympics/default.stm")  Also, what about [this?]("http://www.bbc.co.uk/iplayer/categories/olympics") Should be working for viewers across the globe shouldn't it?

---

### Post by pt123 on 2008-08-09
> **Saint Angeles said:**
> cant you just read about who wins in the paper or on the news?

whats the point of watching some weirdos play with eachother?

huh?

---

### Post by skiani on 2008-08-09
Feedback to NBC:

[email]nbcolympicsfeedback@nbcuni.com[/email]

---

### Post by jeyaganesh on 2008-08-10
What about Zattoo TV. From Uk I could see some BBC,Four,Euro news and French channels using Zattoo.

---

### Post by AR_Kozz on 2008-08-10
Silverlight doesn't work with Wine, and the linux port of Silverlight, Moonlight, doesn't work yet (I tried both) so there's no way around this issue for those of us in the US. If I lived in the UK or Canada, it would be easy. But the broadcasting market in those countries isn't dominated by companies that are so brazen as to hold a blockbuster event hostage to launch a beta version of their crappy software.

I have contaced nbc about it, via email feedback on nbc.com. I urge everyone else to do the same and request flash format olympics video immediately. Tell them you won't watch nbc anywhere, otherwise.

Obviously a lot of people are really pissed off about this. If enough of us complain to nbc, they may get the message and put their broadcast in flash where it belongs. Or at least wmv.

---

### Post by BigSilly on 2008-08-10
> **AR_Kozz said:**
> Silverlight doesn't work with Wine, and the linux port of Silverlight, Moonlight, doesn't work yet (I tried both) so there's no way around this issue for those of us in the US. If I lived in the UK or Canada, it would be easy. But the broadcasting market in those countries isn't dominated by companies that are so brazen as to hold a blockbuster event hostage to launch a beta version of their crappy software.

I have contaced nbc about it, via email feedback on nbc.com. I urge everyone else to do the same and request flash format olympics video immediately. Tell them you won't watch nbc anywhere, otherwise.

Obviously a lot of people are really pissed off about this. If enough of us complain to nbc, they may get the message and put their broadcast in flash where it belongs. Or at least wmv.

It's not as hopeless a suggestion as it may first appear. If there was some way to get everyone who has been affected by this to email and badger NBC, you'd be sure of some kind of result. At the very least it has to be better than posting on forums about how crap it is.

I think it's an absolute disgrace. The BBC aren't perfect when it comes to other OS's, but I'm bloody glad I live in the UK in this instance. 

I simply cannot believe this was allowed to happen. Locking people *OUT* of such a massive event. It's insanity.

---

### Post by galamud on 2008-08-10
Does anyone want to actually work on the problem instead of just yelling at NBC/MS?  I doubt they invented their own video codec for this.  I posted some code up above for sending the same headers that the Silverlight client sends, and that actually got me the stream from the server.  I just need some help figuring out how to decode that stream.

We can totally get this to work with some team effort.  We could probably make a ******* awesome olympic sport viewer, too, with some menu systems and picture-in-picture.

---

### Post by TimboUK on 2008-08-10
As one of the previous posters said, Im sure if you went to [www.bbc.co.uk](www.bbc.co.uk) and accessed the BBCI player, you'd be able to watch the olympics coverage there.  They certainly have the opening ceremony on it, as I saw it the other day when watching a repeat of Dr Who.

Id be interested to know if its blocked to people outside the UK.

---

### Post by phrostbyte on 2008-08-10
[http://en.wikipedia.org/wiki/VC-1](http://en.wikipedia.org/wiki/VC-1)

^ That's probably the codec being used.

MPlayer seems to support it. I am not sure about VLC.

---

### Post by amazingtaters on 2008-08-10
> **TimboUK said:**
> As one of the previous posters said, Im sure if you went to [www.bbc.co.uk](www.bbc.co.uk) and accessed the BBCI player, you'd be able to watch the olympics coverage there.  They certainly have the opening ceremony on it, as I saw it the other day when watching a repeat of Dr Who.

Id be interested to know if its blocked to people outside the UK.

Those of us outside of the UK can get all the iPlayer radio broadcasts we want, but no video. I tried watching the mens coxless swept 4 (rowing) and couldn't.

---

### Post by Sunflower1970 on 2008-08-10
> **BigSilly said:**
> [Is this no good?]("http://news.bbc.co.uk/sport1/hi/olympics/default.stm")  Also, what about [this?]("http://www.bbc.co.uk/iplayer/categories/olympics") Should be working for viewers across the globe shouldn't it?
Doesn't work for anyone with a US IP (Not sure about the rest of the world, though). If one uses a proxy to mask the US IP then it can be used.

---

### Post by AR_Kozz on 2008-08-10
> **galamud said:**
> Does anyone want to actually work on the problem instead of just yelling at NBC/MS?  I doubt they invented their own video codec for this.  I posted some code up above for sending the same headers that the Silverlight client sends, and that actually got me the stream from the server.  I just need some help figuring out how to decode that stream.

We can totally get this to work with some team effort.  We could probably make a ******* awesome olympic sport viewer, too, with some menu systems and picture-in-picture.

I'm not too skilled about that, but I bet maybe you could figure out what it uses if you examine the documentation from the moonlight project. It's at, I think, 
[http://www.go-mono.com](http://www.go-mono.com) 

The binaries include no codecs, but the source apparently does, which suggests you are right that it's not a new proprietary thing, but even if it was I bet it's included in the source.

---

### Post by AR_Kozz on 2008-08-10
> **galamud said:**
> Does anyone want to actually work on the problem instead of just yelling at NBC/MS?  I doubt they invented their own video codec for this.  I posted some code up above for sending the same headers that the Silverlight client sends, and that actually got me the stream from the server.  I just need some help figuring out how to decode that stream.

We can totally get this to work with some team effort.  We could probably make a ******* awesome olympic sport viewer, too, with some menu systems and picture-in-picture.

I bet maybe you could figure out what it uses if you examine the documentation from the moonlight project. It's at
 
[http://www.go-mono.com](http://www.go-mono.com) 

the download links to the 0.7 binary and the source are in the lower right.

The binaries include no codecs, but the source apparently does, which suggests you are right that it's not a new proprietary thing, but even if it was I bet it's included in the source.

---

### Post by Diggs808 on 2008-08-11
I have an idea that may just work...but it will take some effort and a little money on our part.  Lets stage an old fashioned write in protest!  Notice how all of these shows that nearly get canceled are saved by write in campaigns?  In the case of Jericho...the show was saved (at least it was allowed to wrap up) by fans sending bags of nuts to the president of CBS.  So lets do the same...except...lets send them a copy of our favorite distro.  It won't cost much...just go online and download the ISO...burn it to a CD or two and then send it to the president of NBC along with a POLITE AND FRIENDLY letter.  

Personally I will commit to sending one of these per day until they change thier mind or the olympics end.  

Sample Letter

**Mr. Jeff Zucker **
President and Chief Executive Officer 
NBC Universal Television Group
30 Rockefeller Plaza
New York, NY 10112 
(212) 664-4444


Dear Mr Zucker,  

I have thourgholy enjoyed the Olympics so far, however we have recently discovered that the online content enjoyed by many in the United States is not available for computer users who run Linux Operating systems includling Ubuntu, Red Hat, and others.  This is very disappointing for those of us who choose to use Linux.  It means that we are not able to view the olympics and cheer on our team in our favorite sports.  

We are not asking for much, however what we are asking for is simple.  Allow us access to the online content that many others are already enjoying.  Websites outside of the US (cbc.ca and others) are broadcasting thier internet content in Flash.  We respectfully ask as a community of computer users and olympic fans that you make your content available to those consumers who do not use Microsoft products.  

If you do not have the technical resources available to make this happen we offer our services as a community to make this work.  

Thank you very much for your time.

Signed,

(YOUR NAME HERE)

---

### Post by k_i_k on 2008-08-11
Actually, while it is not completely trivial, it is possible to get the live stream URLs from the NBC website without going through its terrible user interface.

I wrote a short Python script to do just that. See attached. As is, it will scan the current Tennis schedule and print the matches that are being streamed live, together with and MMS stream URL. The stream can be downloaded with mimms (apt-get install mimms) or viewed with xine or mplayer (which can also save streams with the -dumpstream option). Look inside for examples of how to change Tennis to your favorite sport (like Badminton :-). If you want to view past matches, change 'Live ' to 'Rewind ' in the script. Although, I've so far had not had much success with that.

Alas, this script will only work if you're inside the US. Try the script, modify to your heart's desire and spread the word.

On a technical note, here are the Python XML packages I have installed (you may only need some, haven't checked):
```

python-libxml2
python-lxml
python-xml
```

---

### Post by grotto on 2008-08-11
"M$" :rolleyes: 

How about ¢anoni¢al? Yes, that's pretty dumb too.

---

### Post by globose on 2008-08-12
> **k_i_k said:**
> Actually, while it is not completely trivial, it is possible to get the live stream URLs from the NBC website without going through its terrible user interface.

I wrote a short Python script to do just that. See attached. 

Alas, this script will only work if you're inside the US. Try the script, modify to your heart's desire and spread the word.

On a technical note, here are the Python XML packages I have installed (you may only need some, haven't checked):
```

python-libxml2
python-lxml
python-xml
```

Thanks again for typing this script up, k_i_k.  For anyone wanting more information about this script, or for debugging problems, there is more information in this forum: [http://ubuntuforums.org/showthread.php?t=883142&page=4](http://ubuntuforums.org/showthread.php?t=883142&page=4)

Pages 4 and beyond have a lot of helpful posts, plus a newer version of the script by k_i_K (in post #36), and a modification of that from me (in post #54) for those who are getting an error code relating to "No module named ext.reader"

---

### Post by carltonh on 2009-11-03
I am reviving this thread because I had this NBC-Linux issue attempting to watch Heroes at [www.nbc.com/heroes](www.nbc.com/heroes).  Since this is the top ubuntuforums.org result on a Google search, I want to update to say how you can get around this without Windows.

First, I'm using Ubuntu 9.10 x86 and Wine 1.1.32 from the winehq.org repository.  I download and install Firefox (3.5 at the moment) for Windows, separately I downloaded silverlight.exe from silverlight.net, and then the 32 bit Windows version of Adobe Flash.  Then install the last two in Wine.

Note that Firefox did freeze and slow down at a couple points during installation of these, but then seemed to work well enough.  [www.nbc.com/heroes](www.nbc.com/heroes) let me watch a whole episode without any problems, though it is slightly choppy because my laptop has an old old ATI card, and can't use the proprietary ATI driver...and so I didn't bother trying full screen.

I didn't try using Moonlight (1.0.1) for Windows instead of Silverlight, but I did confirm that Moonlight in standard Linux Firefox will not work to watch episodes on NBC.com

---

### Post by jrusso2 on 2009-11-03
I run Netflix in virtualbox and that uses silverlight so I would think this would work also.

---

### Post by doorknob60 on 2009-11-04
> **carltonh said:**
> I am reviving this thread because I had this NBC-Linux issue attempting to watch Heroes at [www.nbc.com/heroes](www.nbc.com/heroes).  Since this is the top ubuntuforums.org result on a Google search, I want to update to say how you can get around this without Windows.

First, I'm using Ubuntu 9.10 x86 and Wine 1.1.32 from the winehq.org repository.  I download and install Firefox (3.5 at the moment) for Windows, separately I downloaded silverlight.exe from silverlight.net, and then the 32 bit Windows version of Adobe Flash.  Then install the last two in Wine.

Note that Firefox did freeze and slow down at a couple points during installation of these, but then seemed to work well enough.  [www.nbc.com/heroes](www.nbc.com/heroes) let me watch a whole episode without any problems, though it is slightly choppy because my laptop has an old old ATI card, and can't use the proprietary ATI driver...and so I didn't bother trying full screen.

I didn't try using Moonlight (1.0.1) for Windows instead of Silverlight, but I did confirm that Moonlight in standard Linux Firefox will not work to watch episodes on NBC.com

...Or just use Hulu (either their Linux-compatible Flash site or their native Linux desktop client) and don't worry about all this stuff :P

---

