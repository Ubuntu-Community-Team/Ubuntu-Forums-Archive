---
title: "Worship Software"
date: 2007-03-19
forum: Ubuntu Christian Edition
---

### Post by tractordriver88 on 2007-03-19
My church is looking into getting new worship software as it is finally time for a church of 900 members and good volunteers to get away from PowerPoint. 
We looked into Mac software, but it's all to expensive. Is their any software we could use with Ubuntu that is free or fairly low priced that would do the same thing as Media Shout or Easy Worship?
Thanks.

---

### Post by adam.tropics on 2007-03-19
I don't know about 'worship software' at all, but if you've been using Powerpoint, then OpenOffice.org.Impress might be worth a look. It would have the advantage for you that firstly it can be run in windows as well if that is an issue, and secondly, it can, for the most part run any existing Powerpoint presentations you might have.

---

### Post by urukrama on 2007-03-19
There is something, but I forget what it is called. It was designed for some evangelical church in England (London?), and is available for free.

I'll see if I can find it again...

EDIT: oh, and Opensong plans or hopes to release a Linux version at some point, at least according to the website. Perhaps someone would like to give them a hand?

EDIT2: apparently a Linux version of Opensong is already available. See below.

---

### Post by brandon moore on 2007-03-25
> **urukrama said:**
> There is something, but I forget what it is called. It was designed for some evangelical church in England (London?), and is available for free.

I'll see if I can find it again...

EDIT: oh, and Opensong plans or hopes to release a Linux version at some point, at least according to the website. Perhaps someone would like to give them a hand?


are you thinking of OpenLP.org's software? It's okay, but very basic. OO.org does a much better job IMO

---

### Post by robacarp on 2007-03-26
I think that the software that tractordriver88 is looking for is more like Songbase or similar.  The reason is that Powerpoint or alternatives such as Openoffice are not really optimized for the project of putting songs and bible verses on the overhead.

There is a lot of software out there to do this, some of it better than others, but I have not herd of a free package.  Then again I have not been looking for some time.

The basics of 'Worship Software' is:

[LIST]
[*]modifyable Database of songs
[*]dual screen compatibility....the projector displays the current verse, the user clicks on verses on the screen which then change what the projector displays.  This allows for the jumping around inside a song without cycling through all the slides.
[*]sometimes include integration with bible software or other software packages for an all-in-one church projector managment software solution.
[/LIST]

---

### Post by BoredOutOfMyMind on 2007-03-26
> **adam.tropics said:**
> I don't know about 'worship software' at all, but if you've been using Powerpoint, then OpenOffice.org.Impress might be worth a look. It would have the advantage for you that firstly it can be run in windows as well if that is an issue, and secondly, it can, for the most part run any existing Powerpoint presentations you might have.

Are you wanting this for the overhead/projection system?

[http://www.opensong.org](http://www.opensong.org)

Welcome to OpenSong.org!
OpenSong is a free, open-source software application created to manage lyrics, chords, lead sheets, overheads, computer projection, and more. Download the full application for free and give it a try!

---

### Post by xilix on 2007-03-27
Our church uses [SongBeamer]("http://www.songbeamer.com/"), which is commercial and only available for Windows. But it is very productive!

Free worship software is:
[LIST]
[*][OpenSong]("http://www.opensong.org/") [Windows AND Linux!!!]
[*][Lyricue]("http://lds.sourceforge.net/screenshot.shtml") [Linux]
[*][openlp]("http://www.openlp.org/") [Windows, Linux-version planned]
[*][Easislides]("http://www.easislides.com/") [Windows]
[*][DreamBeam]("http://www.dreambeam.de/") [Windows]
[*][BeamIt]("http://www.beamit2.com/") [Windows, don't know if it is still under development...]
[*][Zionworx]("http://www.zionworx.org.uk/") [Windows]
[*][PowerWorship]("http://www.powerworship.com/") [Windows]
[*][The Beamer Project]("http://beamer.sourceforge.net/") [Windows]
[/LIST]

---

### Post by tractordriver88 on 2007-03-29
Hey folks, thanks for the replies. Open song looks like a good option, and I will give some of the others a try and show them to the rest of the Media Crew. 
As of now, we are using PowerPoint in the main worship area and Media Shout in our youth areas, but it's time to get away from PowerPoint to something a little more customizable on the fly and the people in the Youth area don't like Media Shout because it's really buggy and does not want to behave on any of our computers.
Thanks so much!

---

### Post by benste on 2008-04-05
I'm looking for such a software two, Iam also interested in using OpenOffice, but I need a Linux Software which can adreess 2 Screen AND can give videos as a background of a text, 
as far as I consider Openoffice can only trigger videos in the foreground.

Or can someone give me a tutorial how to bring the videos of Openoffice behind a text area??

---

### Post by alamarre on 2008-05-16
Try out Easy Media Presenter, it's still in early development and requires Java SE 5 or higher, but performs most of the usual presenter program functions.It's open source and hosted on sourceforge. If you have any questions feel free to contact me.

---

### Post by benste on 2008-05-17
How can I start it?

```
benste@vaiofe31m:~/Desktop/EMP_Beta_2$ ls
Backgrounds   lib           load.sh        Songs
Bibles        load.bat      MediaData.txt  TextInformation.txt
fobs4jmf.dll  load.command  Presenter.jar  Videos
benste@vaiofe31m:~/Desktop/EMP_Beta_2$ ./load.sh
bash: ./load.sh: Permission denied

```

---

### Post by alamarre on 2008-05-23
You should just run the load.sh included along with it. If that doesn't work e-mail me at [email]alamarre@gmail.com[/email] telling me what problems you've been having loading it and I'm sure we can resolve the problem quickly.

---

### Post by alamarre on 2008-05-23
Sorry I didn't look at your code before I replied. It would seem you didn't change the ownership of the file. Look up the chown command. If it still doesn't load after that make sure it's set to be executable. E-mail me either way I haven't got too much feedback and would like to know common problems and what people like and don't like about it.

---

### Post by benste on 2008-05-23
As far I can feedback you:

first: error shown while starting:
```
benste@vaiofe31m:~/Gemeinde/EMP_Beta_2$ sh ./load.sh 
: not found2: 
: not found4: 
23.05.2008 17:44:42 com.sun.corba.se.impl.ior.IORImpl getProfile
WARNUNG: "IOP00511201: (INV_OBJREF) IOR must have at least one IIOP profile"
org.omg.CORBA.INV_OBJREF:   vmcid: SUN  minor code: 1201  completed: No
	at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:473)

```

the programm looks nice it selfs but seems to be unstable for videos - I wasn't able to load the test video.

as user there are some missing things for me: first I want to define a font size (Arial 20pt bold) but there is only a font-style option for all and not every custom text.
Normally we use English text with german subtitles in our youthgroup and in our main service, but there we need german texts. How can we create or better import our .rtf files into the program ?

All in all this is a good start for me when video will work, but it isn't enough customizeable yet. I want to be able to do pre sets for every shown up verse. but maybe I'm only searching for openoffice with videobackgroundability and a maybe (not necesarry) a media manager

---

### Post by alamarre on 2008-05-23
I looked up the error you were having and the only clue I can get to the problem is that you don't have permissions to use a file you need to access. I'm assuming that's preventing it from loading the video library which is why you can't play the video. 

Try running it with sudo once and if that works chown or chmod the directory recursively. or just do the second part first. 

As for the font, I imagine you found the way to change the font type. Fonts are automatically bold. The font size is currently calculated by the verse to maximize use of the screen, but it will be able to be static in the final version. 

I would appreciate if you send any further comments or questions to me at [email]alamarre@gmail.com[/email] since it's easier for me to check there.

---

### Post by benste on 2008-05-23
Only for all others: -> we're in contact via IM - feel free to test this great work !

---

### Post by Matthew Wiebelhaus on 2008-05-29
> **benste said:**
> How can I start it?

```
benste@vaiofe31m:~/Desktop/EMP_Beta_2$ ls
Backgrounds   lib           load.sh        Songs
Bibles        load.bat      MediaData.txt  TextInformation.txt
fobs4jmf.dll  load.command  Presenter.jar  Videos
benste@vaiofe31m:~/Desktop/EMP_Beta_2$ ./load.sh
bash: ./load.sh: Permission denied

```

Instead of doing that you can CD that directory then use 

> sudo sh load.sh

You must be in that directory to excute that command. You can also cd the directory and try 

> sudo java presenter.java

But i got errors using that one so you probally need to recompile it using your jre version.

---

### Post by benste on 2008-05-30
I'm sorry that I didn't post it, alamare has already contacted me via IM.
We talked a lot about EMP and I think EMP is a solution for fast searching and presenting lyrics,
for my own use it is not well enough - in java videos don't start automaticly but I search asolution like OPenoffice with Video Background.

If someone knows a programm which can do it please let me know.
+ HOw can I insert videos in Openoffice 3.0 there is always an error - file type not supported or so

---

### Post by Matthew Wiebelhaus on 2008-05-30
> **benste said:**
> If someone knows a programm which can do it please let me know.
+ HOw can I insert videos in Openoffice 3.0 there is always an error - file type not supported or so

You will probally have to convert the file to a different format. There is a free and great conversion software for Windows with a nice interface, it could probally be sold for money, but I haven't found any great Linux conversion software. For now you can use their website to convert your video files. 

[http://www.mediaconverter.org/](http://www.mediaconverter.org/)

if you have windows i suggest you download the application. you can also try using it in wine but since it requires Dot.Net framework 2.0 i don't think it will work.

---

### Post by benste on 2008-05-30
What kind of forum is it here? is it windows?
- there are cuoples of linux applications for converting video files- I think the famous one is VLC which is free and also aviable for Windows.

- I think there is no problem with codes or so there is only a problem in Openoffice which doesn't allow me to insert any kind of video or audio

---

### Post by Matthew Wiebelhaus on 2008-05-30
> **BoredOutOfMyMind said:**
> Are you wanting this for the overhead/projection system?

[http://www.opensong.org](http://www.opensong.org)

Welcome to OpenSong.org!
OpenSong is a free, open-source software application created to manage lyrics, chords, lead sheets, overheads, computer projection, and more. Download the full application for free and give it a try!

This will be your best choice if you want free open-source software for Linux that is good.

---

### Post by benste on 2008-05-30
looks much easier than EMP - nice interface, but there is no video background avibable - so openoffice would be better
+ I can't even find how to make a background
+ We don't have a CCLI only something else

---

### Post by Matthew Wiebelhaus on 2008-05-30
Open office can do the videos but I dont know if you can layer the text above the video, but I haven't used openoffice presentation software yet but tell me how it goes. I tried EMP but I cant even fiure the software out, it looks good but it needs an easier to used interface with more options. I was going to contact the developer but I could find any email address or an source of contact.

---

### Post by benste on 2008-05-30
write him a PM he did post some posts ago.

- OpenOffice can't layer the videos in the background - and that the reason why I'm searching another software - MS office 2007 can have text infront of videos!!
BUt I want to use linux

---

### Post by Matthew Wiebelhaus on 2008-05-30
> **benste said:**
> write him a PM he did post some posts ago.

- OpenOffice can't layer the videos in the background - and that the reason why I'm searching another software - MS office 2007 can have text infront of videos!!
BUt I want to use linux

I have Office 2007 but the guide to get it on Linux is REALLY hard and it only works if your lucky.

---

### Post by benste on 2008-05-30
mh I think I'm abel to wait for a better releasea - So far I wasn't able to test videos in OO 3.0 because of no file type supported

---

### Post by Matthew Wiebelhaus on 2008-05-30
> **benste said:**
> mh I think I'm abel to wait for a better releasea - So far I wasn't able to test videos in OO 3.0 because of no file type supported

I dont think they will make any more file types supported you will just have to convert I think. Im going to test EMP again and see if I can explain how to use it.

EDIT: This software is very buggy if there is a video background feature it dosen't work.

---

### Post by benste on 2008-05-31
lol that's what I thought too, but contact alamare for more details on EMP.

- OPen Office supports various of file types including m4a mpg divx and so on and I think the default was ogg - I tried all these file type but none did ork.
I remeber there was the same bug for me in the 2.4 Version but I solved it with the help of someone here. But for now I don't remember how to solve it. I think it was something with the connecting between oo and ffmpeg for example

---

### Post by samuelmello on 2008-08-29
Hi,
 
There is also Datasoul.
It is also written in Java, open source and hosted in sourceforge.
The address is [www.datasoul.net](www.datasoul.net)

God bless,

 - Samuel

---

### Post by cjm5229 on 2008-08-31
Lyricue Is supposed to be a very versatile app that should be just what your looking for. I have never been able to try it out because our Church doesn't have a projector. From what I have read about it though it will handle song lyrics and Bible verses with an ability to change on the fly. It is also in the Ubuntu repos.

---

### Post by benste on 2008-09-01
look nice, but doesn't allow a video background,
I may try this one in next time for normal use.

---

### Post by wildman4god on 2008-10-02
Datasoul looks good, I am going to give it a try.

---

### Post by f03el on 2009-02-28
I have run Lyricue for a while and it works well for me. Alas, you can't configure keyboard shortcuts and I'd like to see some kind of database management tool.

Today I tested DataSoul, and it looks very impressing with many features. One thing I can't understand is why it was using 20-80 % CPU all the time, even when idling.

---

### Post by benste on 2009-03-02
Hi guys,

just wanted to let you know that
Allamare contacted me last month and told me that he would gonna redisgn his EMP which is written in Java, if you have ideas on what he should implement you may help him.

may god bless you.

---

### Post by josiahbryan on 2010-02-26
I confess, this may be a bit self-promoting, but I've decided to code my own software for use at our church. It's up on google code at:

[http://code.google.com/p/dviz/](http://code.google.com/p/dviz/)

Runs on Linux (so far, tested on CentOS and Fedora) and Windows. Sorry, haven't tested on Ubuntu yet.

Code contributors/hackers/coders welcome, by the way. Cheers!

---

### Post by blackhawkover on 2010-03-12
> **josiahbryan said:**
> I confess, this may be a bit self-promoting, but I've decided to code my own software for use at our church. It's up on google code at:

[http://code.google.com/p/dviz/](http://code.google.com/p/dviz/)

Runs on Linux (so far, tested on CentOS and Fedora) and Windows. Sorry, haven't tested on Ubuntu yet.

Code contributors/hackers/coders welcome, by the way. Cheers!


Love the look and feel of what you've done, but is there any ubuntu plans in the future? I'd love to see some of that?

---

### Post by josiahbryan on 2010-03-12
There's nothing specifically that excludes ubuntu in the source. Feel free to check out the source, grab a copy of Qt 4.6.2 and compile it - it should run without problems. There aren't any hard-coded paths in DViz that make it specific to any one OS, so it *should* run under ubuntu. Let me know if it doesn't and I'll gladly adjust it to make it work!

Feel free to post back here with any problems or questions or email me at [EMAIL="josiahbryan@gmail.com"]josiahbryan@gmail.com[/EMAIL]. Cheers!

---

### Post by who_da_fly on 2010-07-07
I'm the lead developer of OpenLP - though I'd just post a quick update to where OpenLP is with the port to Linux.

We've just recently released our second Alpha version, which is mostly functional. You can do almost everything that version 1.x could do, and more. Ubuntu folk are fortunate in that we have a release PPA where you can install Alpha 2 from.

In addition to the release PPA, there's a development PPA which contains the very latest revision, if you're feeling brave ;-)

Details to both PPA's can be found on our [download]("http://openlp.org/en/download.html") page. Have fun!

---

### Post by JonEK90 on 2011-02-09
Thanks to all who have added their experience on this thread. 
We are starting a new type of service in my church and I have been looking for some Worship Software (and I have no budget!). I am looking for operator controlled projected presentation features.

It has been a while since anyone added to this thread so I would be interested to hear from others what experiences and recommendations they have now.

I did some brief research and these are my conclusions:

[**Opensong**]("http://www.opensong.org/"): this appears to be an "official" open source but I have not installed or tried it because it has some problems running multiple displays on Ubuntu. Install looks tricky and it uses RealBasic (and I wonder if that will make it difficult to easily support various platforms.)

[**Lyricue**]("http://www.lyricue.org"): has a lot of features. The install adds a lot of libs to the system so I have not installed it. It seems very good but more complicated than I need so I am passing for now.

[**OpenLP**]("http://openlp.org"): seems to be very popular, runs on Windows and Ubuntu. Has good documentation although it is a little *Windows-centric* but lacks video back grounds and OO integration. I have installed it, possibly this will be our choice as it is *mainstream* and will allow Windows/Ubuntu collaboration.

[**datasoul**]("http://code.google.com/p/datasoul/"): this one has a tiny install base (it seems) but also has all the features including integration with OO & Powerpoint, videos, alerts etc. The documentation is limited but it was very easy to install. It uses Java6 (perhaps that it why the media support is good?) and runs on Windows, Ubuntu, & Mac. Right now I like it for it's simplicity. I wonder why it is so overlooked?

Hope this is useful.

---

### Post by oldsam on 2011-05-21
**ExpoSong** ([http://exposong.org](http://exposong.org)) is also a very nice piece of software.
It works on both Linux and Windows and is very easy to use.

It can import from OpenSong and SongSelect and uses the OpenLyrics data format which is also supported by some other applications.

It lacks bible integration and some other advanced features, but it's still a good choice for many situations.

---

