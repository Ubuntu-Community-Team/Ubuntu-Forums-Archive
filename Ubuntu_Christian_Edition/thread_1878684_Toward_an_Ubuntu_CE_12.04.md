---
title: "Toward an Ubuntu CE 12.04"
date: 2011-11-10
forum: Ubuntu Christian Edition
---

### Post by Archangelos on 2011-11-10
Just a little side thing I'm working on in a partition on me hard drive right now. After several days of tweaking and reconfiguring, I think I have a functioning and updated version of Ubuntu CE based on Ubuntu 11.10 desktop amd64. Had to drop a few things including Wine Christian Repo and The Dansguardian GUI. Sorry, just had too many dependencies that need to be updated. So I've gone with Web Content Control and Dansguardian 2.9.whatever... and it is finally configured properly and functioning correctly.  This isn't an announcement of anything major right now, just a pep talk to get people thinking in terms of a long term upgraded CE when Ubuntu 12.04 comes out next spring. I'm impressed with Ubuntu 11.10, but want to keep my CE as well.   Most everything is still maintained -- Xiphos, BibleTime, Bibledit, Hdate, OpenSong, Dansguardian are applications I use everyday. All of the Wine applications will easily migrate onto new versions of Wine and there needs to be an upgraded Wine CE repository for 12.04.  So this is simply as an FYI and hopefully it will spark conversation and get volunteers and developers moving toward reawakening what Ubuntu CE could be and should be.  Blessings.       [IMG]http://i947.photobucket.com/albums/ad313/Archangelos2010/Screenshotat2011-11-10153617.png[/IMG]

---

### Post by BillyBoa on 2011-11-10
And of course you discarded Unity. I like your work, it's nice.

---

### Post by Archangelos on 2011-11-10
> **BillyBoa said:**
> And of course you discarded Unity. I like your work, it's nice.

What can I say? Unity was cramping my style. I need expansion and space. I'm a mystic for crying out loud. :popcorn:

---

### Post by jonathonblake on 2011-11-10
> **Archangelos said:**
> Had to drop a few things including Wine Christian Repo

*Wine Christian Repo* can be replaced by a shell script that installs the following:
[LIST]
[*]    In the beginning was THE WORD;
[*]    The Unbound Bible;
[*]    The Interlinear Scripture Analyzer;
[*]    Theophilos Bible Software;
[*]    Easy Sunday school planner;
[*]    Virtual Rosary;
[*]    BibleMapper;
[/LIST]

Are there any other programs that require WINE that should be on that list?

Are there any programs on that list that can be removed?

One of the complaints about *Wine Christian Repo* was that it installed "old" versions of those programs. With fewer programs in the list, it might be easier for the script-maintainer to update it, when new versions of the program are released.

jonathon

---

### Post by Archangelos on 2011-11-10
> **jonathonblake said:**
> *Wine Christian Repo* can be replaced by a shell script that installs the following:
[LIST]
[*]    In the beginning was THE WORD;
[*]    The Unbound Bible;
[*]    The Interlinear Scripture Analyzer;
[*]    Theophilos Bible Software;
[*]    Easy Sunday school planner;
[*]    Virtual Rosary;
[*]    BibleMapper;
[/LIST]

Are there any other programs that require WINE that should be on that list?

Are there any programs on that list that can be removed?

One of the complaints about *Wine Christian Repo* was that it installed "old" versions of those programs. With fewer programs in the list, it might be easier for the script-maintainer to update it, when new versions of the program are released.

jonathon

Cool. Thanks. I'll look it up. :)

By the way, since we're taking a break during Ubuntu 11.10 to have a good, decent and healthy rant about bigger issues of Ubuntu in general, I have one myself. Being as positive and calm as possible, I really am having some serious ideological issues with Unity and Gnome 3 right now. I'm seriously disappointed. Almost to the point of looking for other options. More than half the reason for switching to Gnome from KDE was the look and custom-ability of the desktop environment. That was the whole appeal. I have come to rely on many panel apps and indicators that simply are no longer functional and have been depreciated.

So here's the crossroads I'm at--am I going to let Canonical dictate to me what is 'depreciated' and what isn't? Is that what Linux is about? More control? More hedgeonomy? More stiffing? This is beginning to look and feel very """Microsoftish""" if you know what I mean. 

Pretty DEs with no customization by the user just don't cut it. I feel a little bit betrayed by Gnome right now as well. They could have been done in the spirit of customization. I'm seriously contemplating scrapping Gnome and Unity altogether right now and re-exploring KDE.

I just somehow know I should have never left SUSE KDE. I come to depend on Gnome now and the carpet is pulled out from under my feet. 

This is a big crossroads right now for Ubuntu. They're going to have to decide what they're about. And if it keeps up this way, I'm looking elsewhere, I can tell you. And what that means is that it's a crossroads for CE development. It may be time to re-imagine the whole thing.

Just thinking out loud. Blessings. ;-)

---

### Post by Archangelos on 2011-11-10
I'm just going to say one more thing right now about the continual development of CE and then I'm going to be developing and randomly checking this forum.  For the past 2 1/2 I have tried to contribute and hint toward expanding Ubuntu CE. My efforts have been largely met with a blank. Truth is, this project is 2 years behind where it should and I personally am starting from square one on my own CE. Since I'm in ministry I have a good idea what we need out of a platform. However, like others have said, nothing sustainable is going to come unless it's a team effort.  I think I have some things to offer, and I know for sure there are some of you who are far beyond me in your development talents. I'm not making any demands, I'm simply asking you to start stepping up to the plate, start the dialogue, start sharing, start brainstorming, and mostly--start developing.   By the spring I want to have a proto-type Ubuntu v8 based on 12.04 for a long term release (yes, we're up to CE v 8), if you didn't know that, it's because you've been ignoring efforts and some of us are tired of being ignored.   So Jereme and David, you can do what you want. Just know, I'm not waiting anymore. The project needs to survive regardless. It's not about any one person, it's about serving the needs of people and especially the church.  So, if I sound a little bit snarky and annoyed at all this bureaucratic foot dragging, maybe it's because I am a little bit annoyed at all of it.  CE was great -- 3 YEARS AGO! To Jerome and David, if you're not going to be able to maintain this project, the ethical thing to do is open it up, get a team of volunteers (and they are out there, I assure you!), and pass the baton. Otherwise, this is becoming an ownership groupy, and that's not what I'm about.  We need development and we need it now. So that's what I'm going to do --warts and all.   Blessings.

---

### Post by jonathonblake on 2011-11-11
> **Archangelos said:**
> am I going to let Canonical dictate to me what is 'depreciated' and what isn't? 

That is part of the reason why I think a Christian distro should be autonomous, in the way that *Sabily* (FKA *Ubuntu Muslim Edition*) is.

> Gnome and Unity altogether right now and re-exploring KDE.
Take a look at xfce. 

One issue with switching to KDE is Ichthux:
[LIST]
[*]Incorporate it into the new distro;
[*]Ignore it;
[*]Something else;
[/LIST]

> They're going to have to decide what they're about.

Not just Canonical, but the entire ecological framework that uses/has used Ubuntu, and other distros supported by Canonical as their upstream/side-stream support.

Over the last two or three years, Canonical has been leading Ubuntu down a path that increasingly looks to be locked down, proprietary, and fraught with licensing issues, with potential lawsuits from de facto patent trolls.

> it's a crossroads for CE development. It may be time to re-imagine the whole thing.

It's been five years since the Ubuntu Christian Edition was first released.

Going back to what I wrote earlier.  Who/what is the distro targeted to:
[LIST]
[*]Individuals;
[*]Families;
[*]Children;
[*]Clergy;
[*]Church/Parachurch employees/support people;
[*]Laity;
[*]Christian SOHO;
[*]Christian non-profits;
[*]Small Churches;
[*]Medium size churches;
[*]None of the above;
[/LIST]

Once that target audience has been decided upon,  the specific applications to be included can be discussed.

###

Personally, I'd like to see two different editions of the distro:
[LIST]
[*]Individual/Family;
[*]Church/SOHO;
[/LIST]

*Individual Family* would be similar to the current setup. This is not to deny discussion about the included software.  On the contrary, I think that this should be discussed.  Specific guidelines on what type software of will be considered should be laid out. (I realize that this is gets into bureaucratic paper shuffling. The idea here is to forestall, what I'd consider to be needless discussion, about whether a program that emulates Tfillin, Misbaha, Tasbeeh, Prayer Wheels, etc should be included.) At the same time, the guidelines should enable software from the most, if not the entire spectrum of Christianity to be included. 

*Church/SOHO* would deploy cloud based applications:
[LIST]
[*]LAMP;
[*]Drupal;
[*]WikiMedia;
[*]LedgerSMB;
[/LIST]

LAMP: This should be obvious, since this is a cloud server, but in case it isn't, I'll start there.

*Drupal* & *WikiMedia*: These two content management systems complement each other:
[LIST]
[*]*Wikimedia* for content this is random and disorganized prior to be added to the site;
[*]*Drupal* for content that is organized, prior to being added to the site;
[/LIST]

*LedgerSMB*: This is accounting software.  If this included, then an accountant, preferable a CPA would need to create a good set of default books for the following:
[LIST]
[*]501(c)(3) organization;
[*]Unincorporated Non-Profit organization;
[*]Unincorporated church;
[*]Incorporated non-profit church;
[*]Incorporated for-profit church;
[*]Limited Liability Partnership;
[*]Limited Liability Corporation;
[*]Sole Proprietorship;
[*]For-profit corporation;
[/LIST]

I am not an accountant. I do not know what would be required for each of those setups. :(

[COLOR="SeaGreen"]Worship software[/COLOR]:  I'm a high church pipe organ snob. (The *[COLOR="Navy"]1928 Book of Common Prayer[/COLOR]*, *[COLOR="Red"]Worship Service 1[/COLOR]* is too low church for my liking. Somebody that prefers the contemporary worship mode can, and should be involved in selecting this software.

[COLOR="SeaGreen"]Enterprise Resource Project Management Software[/COLOR]: This should include several different setups. Something along the lines of the following:
[LIST]
[*]501(c)(3) organization;
[*]Unincorporated Non-Profit organization;
[*]Unincorporated church;
[*]Incorporated non-profit church;
[*]Incorporated for-profit church;
[*]Limited Liability Partnership;
[*]Limited Liability Corporation;
[*]Sole Proprietorship;
[*]For-profit corporation;
[/LIST]

This is something I could play around with.  

That is a very incomplete list of what software would be included. What else would be included depends upon the "gaps" in ERP functionality.

As a side note, using the Church/SOHO edition to run the project would be a useful exercise in determining shortcomings of that specific edition.

jonathon

---

### Post by Archangelos on 2011-11-13
And what you mentioned above are all the sorts of things that bog down a one person operation. There needs to be someone on the development team of CE who deals with just such licensing issues that you mentioned Jonathan.

There are other issues as well. There needs to be an 'art' department if you will for themes. 

Also, we need to seriously begin thinking in terms of actual hardware options. Is this usable on tablets and other specialities? Will Gnome 3 and Unity fit the bill? What are other options?

I would actually like to incorporate a Kubuntu CE as well because I'm just not satisfied with the direction Gnome 3 and Unity are going. And yes, XFCE looks interesting. I think they Gnome 3 and Unity are headed in precisely the wrong direction, a direction that did not describe Ubuntu 4 years ago. I think it's off base, misdirected, and I'm not following.

And someone needs to rescript this whole Ubuntu Christian repository thing and get it up to date.

Furthermore, if Parental Controls GUI is not going to be updated to where it is actually functional (which it isn't), then it needs to be scrapped. It either needs to be at least up to Webcontentcontrol levels, or left behind. That's the short list so far.

That all being said, I've spent the last 3 days toying about with how a KDE CE could look and feel. I see no necessary reason to throw out the bakby with the bath water and think a morphing of the best elements of CE and Ichthux might be one option. Not a reissue of the past, but not a total break from it either.

I'm going to spent the next three days playing with XFCE and see how how I feel about things by midweek.

Blessings. :-)

---

### Post by jonathonblake on 2011-11-13
> **Archangelos said:**
> There needs to be someone on the development team of CE who deals with just such licensing issues that you mentioned 

I'll volunteer for looking after the licensing issues:
[LIST]
[*]Audio;
[*]Image;
[*]Video;
[*]Software;
[*]Documentation;
[*]Software;
[/LIST]

Later this weekend I'll draft an "Acceptable License Guideline", that covers acceptable licenses, required clearances, patents, and other illusions.

> There are other issues as well. There needs to be an 'art' department if you will for themes. 

+1  

[LIST]
[*]Images;
[*]Audio;
[*]Splash screens;
[*]Video;
[*]Software Templates;
[/LIST]

I have "My God is a Mighty Fortress" as a startup sound on my desktop.
Something like that good be used as a "theme" for the distro. I think I can get PD hymns in both "traditional worship" and "contemporary worship" formats for use as a sound theme.  

> Also, we need to seriously begin thinking in terms of actual hardware options. Is this usable on tablets and other specialties? Will Gnome 3 and Unity fit the bill? What are other options?

Unity might work for a non-techie desktop user that browses the internet and pushes paper. It doesn't work for cloud deployment, serious audio-video production, or research.

I think that Android, rather than Linux, will be the big player in the tablet market. I see far more potential in a meta-apt, that installs Christian software on an Android tablet, than a Christian distro tailored for tablets. Once the people power is there, there can be four teams:
[LIST=1]
[*]The desktop/single user team;
[*]The server/cloud team;
[*]The tablet market team;
[*]The *Android for Christians* team;
[/LIST]

I've listed them in order of priority. 

The fourth one, *Android for Christians* might be best served as a separate, independent project. Perhaps an *iOS for Christians* team could be created, to work in parallel with, and in conjunction with the *Android for Christians* and *The desktop/single user* teams.  
Either select existing apps in the respective marketplace (Apple, Android), or port them from the Debian/Ubuntu/Ubuntu Christian Edition repository to those platforms.

[For either Android, or iOS, I don't want to search through 100,000 apps, to find those that are helpful in the Christian life, and don't shove inappropriate adds at me. (The add for a local swingers club seemed somewhat inappropriate to me, when it popped up at the bottom of the display of Deuteronomy 5. I've since removed that Biblical software program from my Android device.)]

The distro also need to pay attention to accessibility issues.  Not only in installation of it, but also in how well the included software works with screen readers, voice input software, pointing devices, and other accessibility aids.

> And someone needs to rescript this whole Ubuntu Christian repository thing and get it up to date.

Abandon the existing names (Ubuntu Christian Edition, Ichthux.)
Create a new brand, with a new name.

As far as what programs it should include, use what Ichthux & UCE include as a starting point. (I am assuming that somebody can obtain a list of what Ichthux includes. I've forgotten the error message I receive, but I haven't been able to install for the last two or so years. The problem has been dependency issues. IIRC, it is something is required that neither Kubuntu nor Ubuntu include.)

> if Parental Controls GUI is not going to be updated to where it is actually functional (which it isn't), then it needs to be scrapped.

This gets into who the target audience is. It has been more than a year since I used dansguardian.

> I see no necessary reason to throw out the baby with the bath water and think a morphing of the best elements of CE and Ichthux might be one option. Not a reissue of the past, but not a total break from it either.

Apply "lessons learned" from the Ichthux project, and Ubuntu CE project to the 12.04 release.  

Is four months long enough to get a viable release ready?  Or will that simply be termed a pre-release, with v 1.0 being released in October 2012?

jonathon

---

### Post by Archangelos on 2011-11-13
Ok, jonathan. I'm game on all of this. So give me a few weeks to put together a basic prototype of what we're working toward and then I'll post up a torrent link. When you get the torrent iso, play around with it and hack it up the best you can. If you'll give a lot of attention to possible licensing issues and application possiblities, I'll be happy. There are a few things I think a CE needs to have, but I have no time for rescripting a repo. 

Yes, we need an art dept. I'm not a themer or an artist. And even if I were, I have no time right now between teaching and church. I have just enough time to get together the framework and then I need to pass the ball to other players to retune it and fine tune it. It also needs to be an organic effort. We can all take a look at what others are doing on it, but I do not want to get caught up in  beaurocracy. That's not what this is about. This is supposed to simply be an update of CE for Christians by Christians.

Right now, to be honest with you, I've scrapped the Gnome desktop. I have K and Unity running on the K desktop. Unity seems to not only be comfortable on K, but it actually seems to run faster and is far less buggy. I like it and it integrated fairly painlessly. Webcontentcontrol is up and running flawlessly on K and Unity, so that's what I'm going with.

But we need someone or someone's to pass this around to to get it tweaked and themed out. The only thing I ask is that it be tasteful, high quality, and not cheesed out like so many things done in the name of 'Christian'. 

Yeah, I see no reason if we put our heads together this fall and winter why we couldn't have something fairly nice in the way of a Kubuntu and Unity CE update by the spring. If you want XFCE in the mix, that's fine. But I don't have time to work out the XFCE end of it. I'm focussing on K because I think K actually gets it this time. Maybe they always did. We can keep our Unity and still maintain the customability of K, and that's what we're aiming for. I honestly feel that Gnome 3 is a buggy, hopeless, stiffling mess at this time. Here's a few screenshots and I keep working on it through this week and try to have something up fairly soon.

This is open for volunteers by the way. This absolutely cannot be a one man show this time. It's either going to be a collaboration and group sharing or it's going to be nothing. Each has a part to play and something to bring to the table. Right now I'm not sweating the small stuff. The only goal is that it serve the needs of the greater church worldwide. If it does that, is updated, and brings interest to Christian exploration and study, then I'm happy. So I guess right now, I'm looking at a Kubuntu CE in the works. Furthermore, if it goes with K4, this is going to migrate very well on tablets.

[IMG]http://i947.photobucket.com/albums/ad313/Archangelos2010/snapshot4.png[/IMG]

[IMG]http://i947.photobucket.com/albums/ad313/Archangelos2010/snapshot1.png[/IMG]

[IMG]http://i947.photobucket.com/albums/ad313/Archangelos2010/snapshot5.png[/IMG]

---

### Post by rushikesh988 on 2011-11-14
beautiful!!

---

### Post by Archangelos on 2011-11-14
> **rushikesh988 said:**
> [COLOR="Black"]**[COLOR="Black"][COLOR="Cyan"]beautiful!![/COLOR][/COLOR]**[/COLOR]

Thanks, rushikesh988. I decided to go ahead and keep Unity because I think it will be good for non-tech users. Seems to work perfectly with the K desktop too. So I think this might be a plan. The reason I'm pushing for smooth integration with tablets, which K does quite well, is because of the possibilities this creates for inter-church and intra-church connectivity. With tablets becoming more and more common, we might see a day when people start bringing their 'Bible tablet' to church. If we can make a Kubuntu CE that has this sort of integration and connectivity, this will be good for our sick and shut in members, along with expatriots and mission field workers who will still be able to connect to worship through voip services and chat services on their portable tablets. They will also have a complete Bible study platform to work from as well, along with user friendly and functional parental and net content filtering services included.

---

### Post by Archangelos on 2011-11-15
Ok. Update. At this time I've scrapped the K desktop as well and just left a Unity installation to work with. It's simple, and if I start choosing sides between Gnome and K, this might turn some away, and that's not what Ubuntu CE is about. People can add Gnome or K as they choose, but for right now, I'm thinking that a distro with just basic Unity CE will suffice and save some install disk space. Keep it simple, but expandable.

It should include at least the following

* Wine Christian Repository (which needs to be rescripted and updated. Volunteers are welcome. Preferably volunteers a lot like david_kt.)
* E-sword Installer (which needs to be rescripted and updated.)
* Xiphos
*BibleTime
*Bibledit (yes, it needs to be on here for Bible translators working in the field, domestically, and abroad.
* Hdate (needs to be included for Hebrew research and historical Bible date studies. Needs a hack to put on the Unity panel, which shouldn't be too hard, just time consuming.)
OpenSong (because it's useful.)
Lyricview (or something else like it for worship leaders)
* Webcontentcontrol GUI for Dansguardian (preferably with some slick hacks to lock it down.)
* New Themes, backgrounds, and icons. (a Christian artist and volunteer needs to take this by the horns and come up with some nice stuff).
* Licensing issues and what not to add on the install iso.

Needing feedback and further ideas. These are some of the basic requisites right now though in this project.

[IMG]http://i947.photobucket.com/albums/ad313/Archangelos2010/Screenshotat2011-11-16115602.png[/IMG]

---

### Post by Archangelos on 2011-11-16
Well, it's 11:15, and I've been thinking about it for about 2 and 1/2 hours now. I have to be honest with myself. I am really, really not happy with the Unity desktop, nor Gnome 3. I'm just not. It's about a whole lot more than just an upgrade from Gnome 2. Gnome 3 is not even the same sort of desktop experience anymore. It should not even be called 'Gnome'. Gnome is something that millions of people became accustomed to as being customizable, this this just is isn't anymore. In fact, I'm not even sure I want to put in the effort for an update of Ubuntu CE. To be honest with you, I'm feeling really let down and disillusioned with Ubuntu right now. I'm disappointed and upset with Unity to the point of seriously considering leaving Ubuntu altogether right now. And I just can't get over that feeling. That's how I've felt since Natty.

And man, that is really something for me to say. Because I was 1000% behind everything Ubuntu did 3 years ago and thought it was my answer. But it isn't anymore. The dynamic and feel has changed, and this just isn't what it used to be. Ubuntu isn't fun anymore. It's limiting and constrictive at every turn. It has become a constant annoyance.

I want a Christian Linux, but I don't want this. I'm just not playing this time. It's too ridiculous. They have really dropped the ball on this one.

---

### Post by jonathonblake on 2011-11-16
> **Archangelos said:**
> 
* Wine Christian Repository (which needs to be rescripted and updated. Volunteers are welcome. Preferably volunteers a lot like david_kt.)
* E-sword Installer (which needs to be rescripted and updated.)
* Xiphos
*BibleTime
*Bibledit (yes, it needs to be on here for Bible translators working in the field, domestically, and abroad.
* Hdate (needs to be included for Hebrew research and historical Bible date studies. Needs a hack to put on the Unity panel, which shouldn't be too hard, just time consuming.)
OpenSong (because it's useful.)
Lyricview (or something else like it for worship leaders)
* Webcontentcontrol GUI for Dansguardian (preferably with some slick hacks to lock it down.)
* New Themes, backgrounds, and icons. (a Christian artist and volunteer needs to take this by the horns and come up with some nice stuff).
* Licensing issues and what not to add on the install iso.


Open for discussion:
[LIST]
[*]Luach: Hebrew calender and Zmanim program;
[*]Orayta: Jewish books;
[*]Diatheke: web based front end from The Sword Project;
[*]BibleMemorizer: Scripture memorization program from The Sword Project;
[*]Lyricue: GNU Lyric Display System.  (Is this what was meant by LyricView?);
[*]Verse/gVerse:  Displays a verse on the desktop window;
[/LIST]

I think that covers the basic software for Bible study in a home or church setting.

jonathon

---

### Post by Anastasis on 2011-11-16
> **jonathonblake said:**
> Open for discussion:
[LIST]
[*]Luach: Hebrew calender and Zmanim program;
[*]Orayta: Jewish books;
[*]Diatheke: web based front end from The Sword Project;
[*]BibleMemorizer: Scripture memorization program from The Sword Project;
[*]Lyricue: GNU Lyric Display System.  (Is this what was meant by LyricView?);
[*]Verse/gVerse:  Displays a verse on the desktop window;
[/LIST]

I think that covers the basic software for Bible study in a home or church setting.

jonathon

 These are good, jonathon, and I'll see if I can get them on. I'm still in flux, but it's the morning and I've had coffee, so I'm feeling better about everything in general. I'm just going to have to work out my feelings about all of this. I need therapy.  However, I am determined to be positive and continue with some developments for the CE community in any way I can help. Just look how positive I'm being right now.  All systems go. ;-)

---

### Post by Archangelos on 2011-11-17
It is now 10:45 PM, on Nov. 17, 2011. I have been in thought all day concerning what the next step for me is on Ubuntu. And I've reached a decision and will not go back. I am, as of tonight, officially breaking off my relationship with Ubuntu proper. I will install and support Linux Mint for the foreseeable future. It with some grief and mixed emotions that I come to this point. There is not and never will be a more loyal and dedicated user of Ubuntu Linux than I. I was a hard won convert from SUSE in 2005-07 and have been glad to see the triumphs and milestones of Ubuntu. But it simply has changed it's entire dynamic as of last year. And it is no longer even a semblance of what it used to be.

I take it as a personal affront and insult to contemplate what Ubuntu has done to its user base in the last year. It has broken the entire social contract that was understood. It has broken continuity of use and user trust at this point. I no longer trust a distro whose development team would sink to such asinine and irresponsible depths as they have done in the last year. And as for the Gnome development team, it has shot itself in the foot completely. And there is no going back. And now there is currently developing  a NEW desktop environment called Mate that is being taken up and actively developed by the Linux Mint team. 

I guarantee you that 3 years from now, when Mate is miles beyond what it is now, and everyone sees what Gnome could have been and should have been, they will mourn the day they jumped the boat for a cheap and flaky hack called Gnome 3. It is an infuriating insult and slap to every dedicated Ubuntu user for the last several years. And they have lost me. I will not come back to Ubuntu. Even if they incorporated Mate, they have lost my trust and are no longer worthy of user trust in my opinion. The single best distro in Linux when from number 1 to number none in the course of a single year. And I'm content to let them go out on this goose chase they are on, but I'm sure not following. Ubuntu is a dead end road, and 12.04 will be the death nail.

It is almost unbelievable to me to realize that Ubuntu Linux is about to get straight up BEAT by Linux Mint, hands down. And when Mate is further and fully developed in its potential, it's going to rule the roost once again. I guarantee it. It is simply a superior DE to anything out there today. And it is only the tunnel vision and hegemony of the current bandwagon that blinds people to what Mate both is right now and will be in the future. They are kidding themselves about Gnome 3. And when it becomes more stiffing than Windows, they are going to kick themselves for not seeing reality.

So then, I will be working on a Christian Edition based off of a Mint variation. I'm happy for this change, and I agree and enjoy the ethos and philosophy of Linux Mint. I think it's probably the only viable option at this point and the only distro I can think of that has not completely lost its mind and its understanding of its user base.

So that's it. It's ends tonight. I will be glad to keep corresponding by email with any of you who are working on Christian Linux editions and updates. But personally, Ubuntu has lost my respect, my favor, and my trust. I give it a vote of no confidence.

So be it. I'm done.

---

### Post by Megaptera on 2011-11-17
I'm delighted to see this huge updating and modernising of CE. I'm really sorry but I've no developer skills or art skills to offer but I'll follow this project and I look forward to trying out the alphas and betas as they come out.

What's showing as screenshots here looks great!!

---

### Post by jonathonblake on 2011-11-17
> **Archangelos said:**
> 
So then, I will be working on a Christian Edition based off of a Mint variation. I'm happy for this change, and I agree and enjoy the ethos and philosophy of Linux Mint. I think it's probably the only viable option at this point and the only distro I can think of that has not completely lost its mind and its understanding of its user base.

a) The name of the distro/metapackage/whatever needs to be changed.

Linux Mint is based off of Debian, not Ubuntu.

Calling a Christian distro based off of Mint "Ubuntu Christian Edition" would be, at best, misleading.

In one of the messages ([http://ubuntuforums.org/showthread.php?t=1881718&highlight=ichthux](http://ubuntuforums.org/showthread.php?t=1881718&highlight=ichthux) Message # 11) Raphael was asking if we wanted to continue Ichthux.   

I've no intrinsic objection to calling it Ichthux.  If the current/former project managers of Ichthux are willing for this group to take it over, then do so.

b)  In the past, I did read some objections to using Linux Mint, on the basis of perceived antisemitism on the part of those developers.  Regardless of the accuracy of the claim, can those objections be overcome?;

c) The last time I installed Linux Mint, it was a rolling distro. This is not acceptable for SOHO/corporate usage. Nor am I convinced that non-techies should be using rolling distros. I won't have any objections to using a non-rolling branch of Linux Mint, as the foundation of the distro;


jonathon

---

### Post by Megaptera on 2011-11-17
> **jonathonblake said:**
>   
c) The last time I installed Linux Mint, it was a rolling distro. This is not acceptable for SOHO/corporate usage. Nor am I convinced that non-techies should be using rolling distros. I won't have any objections to using a non-rolling branch of Linux Mint, as the foundation of the distro;
jonathon

Linux Mint Debian Edition is a rolling release, but the other flavours, 10, 11 and current one "12 Lisa" follow a few weeks behind the Ubuntu releases so 11.10 has just been followed by Mint 12 'Lisa'.

---

### Post by stlsaint on 2011-11-17
> **Archangelos said:**
> It is now 10:45 PM, on Nov. 17, 2011. I have been in thought all day concerning what the next step for me is on Ubuntu. And I've reached a decision and will not go back. I am, as of tonight, officially breaking off my relationship with Ubuntu proper. I will install and support Linux Mint for the foreseeable future. It with some grief and mixed emotions that I come to this point. There is not and never will be a more loyal and dedicated user of Ubuntu Linux than I. I was a hard won convert from SUSE in 2005-07 and have been glad to see the triumphs and milestones of Ubuntu. But it simply has changed it's entire dynamic as of last year. And it is no longer even a semblance of what it used to be.

I take it as a personal affront and insult to contemplate what Ubuntu has done to its user base in the last year. It has broken the entire social contract that was understood. It has broken continuity of use and user trust at this point. I no longer trust a distro whose development team would sink to such asinine and irresponsible depths as they have done in the last year. And as for the Gnome development team, it has shot itself in the foot completely. And there is no going back. And now there is currently developing  a NEW desktop environment called Mate that is being taken up and actively developed by the Linux Mint team. 

I guarantee you that 3 years from now, when Mate is miles beyond what it is now, and everyone sees what Gnome could have been and should have been, they will mourn the day they jumped the boat for a cheap and flaky hack called Gnome 3. It is an infuriating insult and slap to every dedicated Ubuntu user for the last several years. And they have lost me. I will not come back to Ubuntu. Even if they incorporated Mate, they have lost my trust and are no longer worthy of user trust in my opinion. The single best distro in Linux when from number 1 to number none in the course of a single year. And I'm content to let them go out on this goose chase they are on, but I'm sure not following. Ubuntu is a dead end road, and 12.04 will be the death nail.

It is almost unbelievable to me to realize that Ubuntu Linux is about to get straight up BEAT by Linux Mint, hands down. And when Mate is further and fully developed in its potential, it's going to rule the roost once again. I guarantee it. It is simply a superior DE to anything out there today. And it is only the tunnel vision and hegemony of the current bandwagon that blinds people to what Mate both is right now and will be in the future. They are kidding themselves about Gnome 3. And when it becomes more stiffing than Windows, they are going to kick themselves for not seeing reality.

So then, I will be working on a Christian Edition based off of a Mint variation. I'm happy for this change, and I agree and enjoy the ethos and philosophy of Linux Mint. I think it's probably the only viable option at this point and the only distro I can think of that has not completely lost its mind and its understanding of its user base.

So that's it. It's ends tonight. I will be glad to keep corresponding by email with any of you who are working on Christian Linux editions and updates. But personally, Ubuntu has lost my respect, my favor, and my trust. I give it a vote of no confidence.

So be it. I'm done.

I would be a hypocrite of the worst kind if i did said that i didn't have some issues with ubuntu as of lately myself even as i continue my work as a ubuntu member. I know that there were previous works for a christian edition mint in the past but most fell through. Do check with some key mint devs to ensure you can use their trademark of "Mint" as we do with "Ubuntu". UCE was pretty much "grandfathered" in on that front which is why we are the only other project using Ubuntu in the title and on the forums. Of course we would still appreciate any effort's you put into UCE.

---

### Post by Anastasis on 2011-11-19
Just to let you know, I'm also going to be seriously considering basing it off the latest stable release of Debian 6. 

It might be time to just go back to square one.

---

### Post by Anastasis on 2011-11-19
Yeah. I think that's what I'm going to do. I'm going to start with the first building block of Debian 6.0.3. From there, I'm going to start hand crafting a new distro of Christian Linux.

I have grown weary of all these Debian spinoffs which become more and more closed off by the year.

I want it to be customized as a productivity center for real Christian workers. There are certain things that I as a Bible student and ministry worker need out of a platform. And therefore, all the bloatware and cutesy little nick-nacks can fall by the wayside.

* Productivity is key. 
* Continuity of use is key. 
* Long range church/individual support is key. 
* Desktop environment options are key. 
* Architecture options are key.

This time, I want it built right from the start. I want the very foundation to be solid and stable and not subject to the whims of the latest corporatist marketing trend. And I know that there are some that want such projects to be 'continuations' of this, that, or the other, but that's not really what I'm talking about. I'm talking about rethinking the entire concept. The computer world is really changing. This needs to be taken into account for the sake of stability on the user end.
 
I think a straight Debian base is the place to start. And then I can cut out about 50% of the licensing and theming issues that will give me headaches down the road. I don't have any answers yet. And I'm not making any promises. All I'm saying is I know what I need as a Bible worker, and everything heretofore just isn't going to cut it. If I will hand craft a distro around what I need and the way I actually use a computer to do my work, then maybe it will help other Christian workers in their respective fields as well.

I'm not making this for the masses. I'm making it for a specific target user who is about productivity along certain lines. It's not going to be for everybody. Mostly it needs to be designed for church settings worldwide, internationalized, multilingual, application oriented, and multitasking oriented.

I would like it to have various desktop environment options as well. And I want it all on one lean and customized multi-architecture DVD image. For starters, I want it to have the meat and potatoes. And there is something in me that insists that it be done in the spirit of Open Source, because I don't want some church marketing team to start monopolizing or tyranizing this enterprise.

And I SWEAR, if I don't guard it against that, they WILL! There's always some jackass in the crowd who wants to the Big Chief, and then the focus is not on the function or the kingdom or the church, but about their monetary bottom line.

I said it already, and I'll say it again. It's either going to be organic, or nothing. I will have nothing to do with a project that gets bureaucratic.

---

### Post by jimrew111 on 2011-11-19
1. don't use unity or gnome3-shell (make fall-back default or something)

2. give it a better background for the desktop(like this) [http://fond-ecran.imagup.com/w2-112-informatique-linux.html](http://fond-ecran.imagup.com/w2-112-informatique-linux.html)

3. put aptoncd in it so we can backup stuff.

4. it needs virtual box in it (AND GIMP).

5. good job:D.

---

### Post by Anastasis on 2011-11-21
> **jimrew111 said:**
> 1. don't use unity or gnome3-shell (make fall-back default or something)

2. give it a better background for the desktop(like this) [http://fond-ecran.imagup.com/w2-112-informatique-linux.html](http://fond-ecran.imagup.com/w2-112-informatique-linux.html)

3. put aptoncd in it so we can backup stuff.

4. it needs virtual box in it (AND GIMP).

5. good job:D.

Well, jimrew111, people may not understand the ethical ground I'm coming from. Gnome 3 actually does break the understood hacker ethic of freedom and responsibility. I am also convinced that it breaks the Debian social contract that has been understood for years. And most importantly, it breaks continuity of use. It was not without cause that Linux Torvalds recently stated, "Gnome 3 is an unholy mess." I couldn't agree more. And I know it is a legitimate feeling because I've literally felt that way long before I even knew Linus' feelings on the matter.

The situation is this as far as the future of a Christian Linux. It has to be 'sever' and 'IT' friendly as well, as I envision this as being usable by large churches. Therefore, there is a real need for MATE. It's not just about ideology, it's about the functionality of an application (as opposed to task [i.e., 'activity' woe be the term!]) oriented desktop environment. What's great about Linux Mint right now, is that the team is actively hacking away on Gnome 3 to make it usable. I'll also be doing a bit of hacking of my own.

I'm closely watching the developments. And yes, I've gone back to my former view on the matter. I think that Linux Mint might be a workable springboard to develop a Christian Linux. It's a new plan, and changes have to be made. Much thought needs to be given about which distro is going to stand the test of time and define what 'Linux' means in this decade. This effects long term support options for the user.

Watching.. Thinking.. Planning..

---

### Post by jimrew111 on 2011-11-21
haha that's funny that you mention MATE-desktop I was going to say use that but I thought
you would trash that idea, I was wrong. I am a christian btw.
when you get MATE into it sometime let me know. you can install MATE from the mint repo.
[http://www.n00bsonubuntu.net/content/how-to-install-mate-desktop-on-ubuntu-11-10/](http://www.n00bsonubuntu.net/content/how-to-install-mate-desktop-on-ubuntu-11-10/)
I'm thinking about trying it for the heck of it.:rolleyes:

---

### Post by Archangelos on 2011-11-21
> **jimrew111 said:**
> haha that's funny that you mention MATE-desktop I was going to say use that but I thought
you would trash that idea, I was wrong. I am a christian btw.
when you get MATE into it sometime let me know. you can install MATE from the mint repo.
[http://www.n00bsonubuntu.net/content/how-to-install-mate-desktop-on-ubuntu-11-10/](http://www.n00bsonubuntu.net/content/how-to-install-mate-desktop-on-ubuntu-11-10/)
I'm thinking about trying it for the heck of it.:rolleyes:

Actually, I'm running MATE right now on Mint. I'm also following perberos on his MATE repo Git social page. I'm currently working to get out all the bugs in this setup so that I can eventually begin working along with the Mint ports to GTK3 and make sure all of this can be migrated properly.

---

### Post by jimrew111 on 2011-11-21
when it gets ported to gtk3 it will still look like g2 right?
not g3 panel with g2 panel?

---

### Post by Anastasis on 2011-11-22
> **jimrew111 said:**
> when it gets ported to gtk3 it will still look like g2 right?
not g3 panel with g2 panel?

  Don't know yet. Just dreaming. Perberos sent me an email earlier stating that it might be interesting to see how it would migrate.  But there is another issue I'm more concerned with. Shouldn't E-Sword installer and Wine Christian Repos be merged, updated, and then put on a ppa? Brothers and sisters, you're just going to have to excuse my ranting and raving last week. But I needed to get that out of my system.  Truth is, I'm not even really decided yet. I'll work toward a UCE, I like Mint, but I'm leaning toward building it on top of Debian 6.0.3. At this point, I can see no point not to just have a pure Debian based Christian Linux. Maybe Debian at one point was not as 'user friendly' as Ubuntu and Mint. Those days are quickly disappearing, however.  I don't know. I just keep wanting to go back to Debian for some reason. Because I don't want to have to go through all this again in 2 years when update time comes.

---

### Post by mhancoc7 on 2011-11-23
I have been absent for a few years now from the development of Ubuntu CE. I am shocked at some of the things that I am reading. I never imagined that the project would garner so much attention.

I will admit that I have held this project close to my vest. However, that was something that I was upfront about from the very beginning. I have always wanted to open it up to more developers, but over the years many have come and gone with very little actually help. The last release was the first time that a dev stepped up to actually put some work into it. David has since had to step aside due to time constraints.

I also see that there are some that want to branch off and create their own Ubuntu CE. I applaud that and love the idea. However, I do plan to shift the approach that Ubuntu CE is being maintained.

When this project first began I worked very hard to get the approval to even have a place on this forum. I have fought many battles and have taken a lot of abuse. I do not view this as my project but I do want it protected.

I plan to start up an attempt to gather a development group from this forum to start fresh. I want to stay involved but don't have the time to fully develop Ubuntu CE anymore. I guess that is obvious though. :)

I don't want things to just get so de-centralized that there is no value in the work though. 

So keep you eyes on the forum for what is coming.

God Bless, Jereme

---

### Post by mhancoc7 on 2011-11-23
Starting fresh...
[http://ubuntuforums.org/showthread.php?t=1885790](http://ubuntuforums.org/showthread.php?t=1885790)

God Bless, Jereme

---

### Post by Archangelos on 2011-11-24
> **mhancoc7 said:**
> Starting fresh...
[http://ubuntuforums.org/showthread.php?t=1885790](http://ubuntuforums.org/showthread.php?t=1885790)

God Bless, Jereme

Oh bless you lad! I didn't want to have to go through all this. You're a good man, Jerome. Many blessings on the projects. I'll pipe up every now and then to give my two cents worth.

All is well again. I didn't have time to do this anyway with teaching and all. ;-)

Will be watching the progress. Peace and joy.

---

### Post by jonathonblake on 2011-11-24
> **Anastasis said:**
> Shouldn't E-Sword installer and Wine Christian Repos be merged, updated, and then put on a ppa?

*The e-Sword Installer Script* includes most of the gratis resources on e-Sword.net. Merging it with *The Wine Christian Repository Script* would make for a large script, that confuses more than it helps.  

There has been at least one proposal that the *In the Begining Ws The Word*, and perhaps *Bible Analyzer* be split out of *The Wine Christian Repository Script*, and into their own installation script, which includes resources and other tools for the appropriate program.

Having all the scripts in a PPA is a good idea.

jonathon

---

### Post by Megaptera on 2012-06-06
Thought I'd try to revive this old thread with this link to [http://ubuntuforums.org/showthread.php?p=12002585#post12002585](http://ubuntuforums.org/showthread.php?p=12002585#post12002585)
called The start of "new" Ubuntu CE   in case people want to share ideas.

---

### Post by stlsaint on 2012-06-06
> **Megaptera said:**
> Thought I'd try to revive this old thread with this link to [http://ubuntuforums.org/showthread.php?p=12002585#post12002585](http://ubuntuforums.org/showthread.php?p=12002585#post12002585)
called The start of "new" Ubuntu CE   in case people want to share ideas.

See here: [http://ubuntuforums.org/showthread.php?t=1998417](http://ubuntuforums.org/showthread.php?t=1998417)

---

### Post by sffvba[e0rt on 2012-06-06
> **stlsaint said:**
> See here: [http://ubuntuforums.org/showthread.php?t=1998417](http://ubuntuforums.org/showthread.php?t=1998417)

As requested, please see [http://ubuntuforums.org/showthread.php?t=1998417](http://ubuntuforums.org/showthread.php?t=1998417)

*Thread **closed**.*


404

---

