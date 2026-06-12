---
title: "BibleZ - new bible study application"
date: 2009-07-13
forum: Ubuntu Christian Edition
---

### Post by zefanja on 2009-07-13
Hello,

my name is Stephan and I'm from Germany. Last month I started to devolop a new bible software called BibleZ. I know that there ist Xiphos and BibleTime, but both use the sword modules. A university in Germany startet a new project for modules in XML. They called [Zefania XML modules]("http://sourceforge.net/projects/zefania-sharp/").

BibleZ is still unstable, but you can take a look at [biblez.zefanjas.de]("http://biblez.zefanjas.de/en") or visit the [Launchpad project page]("http://launchpad.net/biblez"). There you find also a PPA.

Regards, Stephan

---

### Post by david_kt on 2009-07-13
> **zefanja said:**
> Hello,

my name is Stephan and I'm from Germany. Last month I started to devolop a new bible software called BibleZ. I know that there ist Xiphos and BibleTime, but both use the sword modules. A university in Germany startet a new project for modules in XML. They called [Zefania XML modules]("http://sourceforge.net/projects/zefania-sharp/").

BibleZ is still unstable, but you can take a look at [biblez.zefanjas.de]("http://biblez.zefanjas.de/en") or visit the [Launchpad project page]("http://launchpad.net/biblez"). There you find also a PPA.

Regards, Stephan

Would you please explain how bibleZ would be different/better than Xiphos or bible time?

DK

---

### Post by zefanja on 2009-07-14
> Would you please explain how bibleZ would be different/better than Xiphos or bible time?

BibleZ is not better than Bibletime or Xiphos - at the moment. The only difference is, that BibleZ uses other modules than BibleTime/Xiphos. 

Stephan

---

### Post by Aronzak on 2009-07-24
> **david_kt said:**
> Would you please explain how bibleZ would be different/better than Xiphos or bible time?

DK

As far as I gather, Zefania XML is extremely simple. Because of this, it is very easy to write your own XML parser, making it easy to write basic software, for a lot of platforms. Unfortunately, at the moment, the Zefania format doesn't have support for things like complex poetry. This makes it less good for desktop study, but a good format for looking at the bible on the go on a phone etc...

There are a lot of tools to convert Zefania XML files to other formats, including basic HTML, allowing them to be comatible with other bible programs, and just a basic web browser (probably available on every platform, ever.)

Zefania could gather momentum and become more popular in the future. It's a good idea to have support for it.

---

### Post by jonathonblake on 2009-07-25
> **Aronzak said:**
> There are a lot of tools to convert Zefania XML files to other formats,

FWIW, there is a toolset that converts Zefania XML to the format used by _The Sword Project_. (Which means that BibleTime, JSword,  Xiphos, etc  can easily include  Z-XML formatted content.)

> Zefania could gather momentum and become more popular in the future.

Z-XML has some competition.
* OSIS: Bible Technologies Group;
* USFM: International Bible Society;
* GBF: eBible, but they are in the process of switching to USFM;
* USFX: Onyx Project/WordSend/eBible, and they use it only for conversion to USFM;
* ThML: Christian Classics Ethereal Library;
* LitML: Christian Classics Ethereal Library;
* XSEM: SIL, but they  no longer support/use it, preferring USFM and OSIS;

>  It's a good idea to have support for it.

I'll grant that this is a chicken and egg issue. However, currently, everything I'm aware of, that is available in Z-XML format is either currently available in other file formats, or has copyright related issues.

jonathon

---

### Post by zefanja on 2009-07-28
Hello jonathon,

maybe you're right and there is the one question: Why we need a new bible study app for Ubuntu?

My main motivation to start develop BibleZ was that I need a project to learn python :). And so it was easier to start a new app than contribution to an existing one.

You have the freedom of choice. That's the way of opensource.

Regards, Stephan

---

### Post by Ascenti0n on 2009-07-29
You should go for it. It's hypocritical for anyone to say, "why should we have another *? when we already have x?". With that attitude there would only be one of everything, no variety, no choice, no competition.

Open Source and the like, promotes freedom of choice.

As we say sometimes here in the UK: go ahead and 'fill your boots'.

Keep us up to date with your progress.

---

### Post by Ascenti0n on 2009-07-29
One other thing regarding formats:

[COLOR="DarkRed"][SIZE="4"]PLEASE keep to FREE and OPEN standard[/SIZE][/COLOR]s

like Pyhthon and std XML perhaps even MySQL if a db is required.

---

### Post by jonathonblake on 2009-07-29
> **Ascenti0n said:**
> It's hypocritical for anyone to say, "why should we have another *? when we already have x?". 

Bob Pritchett (Logos Research Systems, Inc) can show you the data that demonstrates that, for most purchasers, Libronix is shelfware.

Both BibleWorks, LLC and Findex.com have instituted policies to minimize their software ending up as shelfware. Neither has publicly stated what percentage of their purchased software ends up as shelfware.

I've seen studies that indicate that most purchases of the software produced by those three firms ends up as shelfware.

My point was:
* Who is the target user?
* What is the Unique Selling Position?
* Why is this proposal not going to result in shelfware.

There are at least a dozen Bible Study Programs that claim to run as native applications on Linux. There are another dozen Bible Study programs for Windows, that can run under WINE with few, if any issues. There are at least two Bible Study programs for Mac OS X, whose creators claim can run on Linux, with the appropriate Mac emulation software.

What does BibleZ offer, that those programs don't offer?

Should it be just another Bible Study Program in somebody's collection of that software genre?

> With that attitude there would only be one of everything, no variety, no choice, no competition.

I fully aware of the different needs and requirements of different users. 

I am acutely aware of the problems with "one size fits all", whether it is in clothes, books, or software.

Competition in the Bible Study Software world can be extremely cut-throat.

> Open Source and the like, promotes freedom of choice.

Nobody is objecting to freedom of choice.

Writing Bible Study software is hard work. Very hard work. Getting permission to distribute "new" resources with your Bible Study software is decidedly non-trivial.

The question is "How likely is this proposal to accomplish its aims?"

> **Ascenti0n said:**
> PLEASE keep to FREE and OPEN standards

The OP has already stated that it will use Zefania XML. This file format  purports to be GPL, but I haven't found anything that specifies which version of the GNU GPL it uses --- if any. 

About half the software that I've found, that can read Z-XML  files, does not appear to be distributed under any FLOSS license.

jonathon

---

### Post by Ascenti0n on 2009-07-29
@jonathonblake:

Pls dont' get the impression my post was singling you out, I wasn't. The sole reason for my post was to provide some moral support to the OP. All he was doing was bringing an idea for a project to the attention of the community, highlighting the fact that he wanted to learn Python along the way.

All to often on these forums, people are hacked down instead finding applicable and objective replies and sometimes for reasons that defy logic.

---

### Post by zefanja on 2009-07-31
Hello,

In situations like these, I wished my english would be better...

Jonathon, you're right in many of your points, but Ascenti0n is also right. Like I wrote before, the main motivation was to learn python and so I looked for an usefull project. Ok, I would choose any another project, but there are more german modules in Z-XML than SWORD-modules. (Yes, I know that it is possible to convert them.)

> What does BibleZ offer, that those programs don't offer?

It's difficult to say, because I started BibleZ two months ago. But there are some features planned that I missed in Xiphos/BibleTime (such as Notes, Tags, Tabs(BibleTime), ...).

Regards, Stephan

---

### Post by zefanja on 2009-08-03
Hello,

BibleZ 0.3 is now availible. You can install it from the [BibleZ PPA]("https://launchpad.net/~biblez/+archive/ppa").

Here a short summary of improvments:

[LIST]
[*] Note support
[*] Strongs
[*] improved search
[*] bible links
[*] improved bible passage input
[*] many other changes
[*] …
[/LIST]

Regards, Stephan

---

### Post by zefanja on 2009-09-29
Hello,

I want to announce, that there is a RC for BibleZ 0.4. Many new features and improvements. You can install Biblez via [PPA]("https://launchpad.net/~biblez/+archive/ppa"). There is also a [Windows Installer]("http://launchpad.net/biblez/0.4/0.4/+download/Setup.exe"). 

Links:
[LIST]
[*][About BibleZ]("http://biblez.zefanjas.de/?q=node/6")
[*][Wiki]("http://wiki.zefanjas.de/doku.php?id=en:willkommen")
[/LIST]

Regards, Stephan

---

### Post by zefanja on 2009-10-01
Hello.

The new BibleZ strings are imported to Launchpad today, so the only thing to do before releasing BibleZ 0.4 is: Translations.

You can contribute your translations at [Launchpad]("https://launchpad.net/biblez/+translations").

I also updated the settings for the RSS Feeds:
[LIST]
[*][http://biblez.zefanjas.de/en/rss.xml]("http://biblez.zefanjas.de/en/rss.xml") for english content
[*][http://biblez.zefanjas.de/de/rss.xml]("http://biblez.zefanjas.de/de/rss.xml") for german content
[/LIST]

Regards, Stephan

---

### Post by RevJack on 2009-10-02
It's looking pretty good!

---

### Post by tomasterisk on 2009-10-04
I'm willing to give this a try. 

But I am still new to this type of installing. When I tried to download it, having pasted in those two lines from your page I was told that something or other was out of date? What else was I supposed to do?

---

### Post by zefanja on 2009-10-05
Hello,

you have to update your your system's software sources with ```
sudo apt-get update
``` in a Terminal or Refresh in Synaptic. After this you can install BibleZ with ```
sudo apt-get install biblez
``` or search this package in synaptic.

Regards, Stephan

---

### Post by refdoc on 2009-10-07
Hi Stephan, 

Just a quick reply - I am one of the Xiphos/CrossWire lot, so take this with  the pinch of salt.

BibleZ looks like a really nice application - I particularly like that it supporrts from start RtoL scripts (my favourite bugbear with many applications, including some of ours)

Wrt Xephania XML - you complain that it does not offer paragraphing and other "advanced" features. The reason I guess is simple and will be unlikely to change - Wolfgang Schultz did create Xefania as a simple format, not wanting to make it complicated. 

Essentially the options with creating Bible XML formats are to keep it "simple and stupid" or to go the whole hog and then you end up either in a mess (many have done so) or you have to think very, very hard and need lots of advice (from programmers just as much as from theologians, translators etc etc.)

We at CrossWire use OSIS XML (albeit translated via our engine, instead of pure XML) because it offers the full range of encoding facilities we want to present to our users. The format is mature and internationally recognised. SIL and many Bible Societies use it internally, together with USFM (a bible translator format) which can be pretty much seamlessly translated forward and backward. It is designed by some leading XML lights (Patrick Durusau from ODF/OpenOffice fame was part of it). So, using it means that a lot of work is done already at the design level + is delivered to the application in predigested format.

CrossWire's SWORD library offers python bindings which are in good shape, so you could, if you wanted have a look at those and maybe make use of them.

Wrt offers of modules - CrossWire has pretty much every public domain bible available and many more copyrighted ones where we were able to get permissions (look also into our beta repository and the Xiphos repository. If some programmes offer more then you need to be careful to ensure that these are actually truly public domain - case in point are a Portuguese Bible floating about and also a Turkish one. Both are distributed widely but former is a corrupted version of a copyright text, latter is under copyright and copied illegally. Once we noticed this we withdrew them and notified anyone else who got them from us, but a lot of people still distribute them. Same may apply to other things you find available. Otherwise we would be interested to learn about such texts and probably rapidly incorporate them too. We have a pretty large module maker community. 

Regards

---

### Post by tomasterisk on 2009-10-12
I have been using BibleZ for a while. While I noticed some pretty good features I have also come across some that do not seem to work. I am not able to easily go from one translation to the next. The same for navigating the Bible itself.

My impression is that this is not quite ready for prime time, though I am sure, with some further work, that it will be an excellent tool.

Now - the reason why I write - how do I uninstall? The add/remove does not seem to recognize it (3rd party, I assume). I seem to have to have some outdated repositories, giving me that caution triangle on the top  right bar. I do not seem to be able to resolve it because I cannot get rid of the software.

Any help on this? Thisis not a major problem, but one that I do want to take care of.

---

### Post by zefanja on 2009-11-03
Sorry for the big delay...

@tomasterisk: Thank you for my feedback. I will set your propsals for the BibleZ 0.5 Milestone. 

You can uninstall Biblez like every other app via Synaptic or sudo apt-get remove biblez.

@refdoc: Thank you also for your thoughts. I thought and think about your words and maybe I will switch to OSIS XML in BibleZ 0.5. But for now Zefania XML is ok.

Best Regards...Stephan

---

### Post by longtom on 2009-11-15
Hi Stephan,

I was on your PPA page.  I noticed that you have not a user friendly PPA for adding your repo to Hardy.

I am aware that it is quite simple to do so myself.  What I would like to know is if your program is supported by Hardy, considering it is still the present LTS and is supported until 2011.

Thank you for your efforts and God bless you!

---

### Post by zefanja on 2009-11-21
@longtom: I know, but BibleZ need at least Qt4.4. Hardy has only Qt4.3.

---

### Post by Flavian on 2010-01-06
> **refdoc said:**
> 

We at CrossWire use OSIS XML (albeit translated via our engine, instead of pure XML) because it offers the full range of encoding facilities we want to present to our users. The format is mature and internationally recognised. SIL and many Bible Societies use it internally, together with USFM (a bible translator format) which can be pretty much seamlessly translated forward and backward. It is designed by some leading XML lights (Patrick Durusau from ODF/OpenOffice fame was part of it). So, using it means that a lot of work is done already at the design level + is delivered to the application in predigested format.

CrossWire's SWORD library offers python bindings which are in good shape, so you could, if you wanted have a look at those and maybe make use of them.

Wrt offers of modules - CrossWire has pretty much every public domain bible available and many more copyrighted ones where we were able to get permissions (look also into our beta repository and the Xiphos repository. If some programmes offer more then you need to be careful to ensure that these are actually truly public domain - case in point are a Portuguese Bible floating about and also a Turkish one. Both are distributed widely but former is a corrupted version of a copyright text, latter is under copyright and copied illegally. Once we noticed this we withdrew them and notified anyone else who got them from us, but a lot of people still distribute them. Same may apply to other things you find available. Otherwise we would be interested to learn about such texts and probably rapidly incorporate them too. We have a pretty large module maker community. 

Regards

Hi there :)
I'll take this as an opportunity to talk to someone from Crosswire directly.
Hope my feedback can help :)
In your post you mentioned why you are using OSIS instead of XML and such, and also state that you have "a lot of modules" also copyrighted ones where you can get the permissions.

Let me tell you my little story.
I've been using e-sword, mybible, macsword and gnomesword for quiet a lot of time.
The only program that really satisfied me was MYBIBLE.
Why?
Because, it really really frustrated me, as a German speaking person that there were few modules available in German.
And the ones that ARE available are really old. Who wants to read a Luther bible from 1912 today in 2010?! Or an Elberfelder from 1882 (if I am correct) I don't.
And that's why I used mybible.
If what you say is true, then I would be very very pleased to see translations like the "Schlachter 2000", Elberfelder 2003, Jantzen NT, NEÜ, NGÜ and what have you on osis!
I feel kinda sad that I have to wait and wait for years and not see any changes in modules in German.
Afaik the "Schlachter 2000" bible is already available on: [www.bibleserver.com](www.bibleserver.com) as for now, which it also had not been for a long long time.
The reason why I use Zefanja XML via Mybible for windows or BibleZ for linux is simple.
I can use and compare / cross-read a variety of translations that, by all respect, every other format has FOR YEARS failed to bring to my desktop.

This may be because of legal issues. If not, I do not quiet understand why not more newer German translations are added.

Here's a list of modules I am using right now: (maybe some of them conflict with copyright issues, I don't know, and to be quiet honest, I really don't care. I have most of them in Book format, so I don't see a reason of why not using them digitally)

* Schlachter 2000
* Jantzen NT
* Luther 1912, 1984
* Elberfelder 1985, 2003
* Einheitsübersetzung
* Neue evangelistische Übersetzung
* Hoffnung für Alle
* Gute Nachricht
* Konkordantes NT
* Interlinear

* Volxbibel
* DaBhar
* Neue Welt Übersetzung

I have not found any format that can give me such a broad variety of translations, therefore I will stick to Zefanja.

---

### Post by refdoc on 2010-01-06
> **Flavian said:**
> 
Here's a list of modules I am using right now: (maybe some of them conflict with copyright issues, I don't know, and to be quiet honest, I really don't care. I have most of them in Book format, so I don't see a reason of why not using them digitally)

That is your prerogative. 

As a (German) user I am as frustrated as you are. As a module maker and distributer I am bound by the law. 

If Xefania or anyone else distributes stuff they have no right to distribute they will have a problem sooner or later. 

Wrt Schlachter 2000 and NGU I do hope to be able to advise of some good news soon. The HfA is in our repo.

---

### Post by Flavian on 2010-01-06
Thanks, refdoc for your fast answer :)

I totally understand what you are saying, and do not want to blame anyone for reasons he can not influence (such as copyright issues) :)
Question: Are the German translations really all that strictly copyrighted, in comparison to their English pendents?

You said that the HFA is in your repos. But isn't it locked? Afaik when I tried it way back in 2006(?) one had to purchase a key from "Brunnen Verlag" to unlock it before being able to use it.

Great news about SLT 2000 and NGÜ! (I've been waiting sooo long for the SLT 2000 to be released in any other format, it's my favorite translation and I use it most of the time). That was the main reason why I sticked to Zefanja for such a long time.

I think new translations in a newer and more up-to-date German would also blow new wind in the sails of projects like Crosswire. So I am looking forward to it.

Thanks again.
May other publishers realize that copyrighting the Word of God may hinder its advancement :)
Why not GPL it? (I am sure it's called different for literature, but you get the idea ) ;)

Regards
Flo

---

### Post by refdoc on 2010-01-06
> **Flavian said:**
> Thanks, refdoc for your fast answer :)

I totally understand what you are saying, and do not want to blame anyone for reasons he can not influence (such as copyright issues) :)
Question: Are the German translations really all that strictly copyrighted, in comparison to their English pendents?

There are a whole lot less of  them for starters. In English there is an abundance of late 19th century translations which are reasonable enough today still. German has probably changed more than English. We have just as a poor response from most major English publishers, but it is easier to step sideways. And there is the NET and the ESV, where the publishers have openly embraced FLOSS and free distribution.

>  Great news about SLT 2000 and NGÜ!  I am working on the former right now and hope to finalise it as a module sometime in January. It will then go back to the publisher, who need to check it and set up their infrastructure. It will be a for sale module. Then I will, assuming everyone is as happy as they are now move on to work on the NGUE. Or whatever else. 

> I think new translations in a newer and more up-to-date German would also blow new wind in the sails of projects like Crosswire. So I am looking forward to it.

Glad to make you happy. I am happy too. I do think indeed focussing on English major translations is not the best way forward. If we get big German, French Italian new translations we will gain ultimately as much or more traction.

---

### Post by Flavian on 2010-01-06
Thanks for your quick reply again :)

I wish you God's blessings on your work.
Keep it up! :)

Yours Flo
Ps: Any ideas on how much the SLT will cost then?

---

### Post by refdoc on 2010-01-06
> **Flavian said:**
> 
Ps: Any ideas on how much the SLT will cost then?

Not sure. Not my call. The publisher will sell directly.

---

### Post by zefanja on 2010-03-23
> **sleepbarn said:**
> this is downloadable for free right?

Yes, you're right

---

