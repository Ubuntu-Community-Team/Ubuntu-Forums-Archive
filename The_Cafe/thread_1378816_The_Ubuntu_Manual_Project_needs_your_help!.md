---
title: "The Ubuntu Manual Project needs your help!"
date: 2010-01-11
forum: The Cafe
---

### Post by humphreybc on 2010-01-11
We are working on a new Ubuntu project that you may have heard about, [The Ubuntu Manual Project.]("https://wiki.ubuntu.com/ubuntu-manual") It is a complete beginners manual for Ubuntu, featuring comprehensive guides, How Tos and information on anything you need to know after first installing Ubuntu.

We need help from the community to give us some more information. We would prefer responses from beginner Ubuntu users, but if you are a seasoned Ubuntu user and can recall when you first started using Ubuntu, we would appreciate your input as well.

Feel free to answer each question in as much or as little detail as you like.

To view what content we have at the moment, visit the [Table of Contents.]("https://wiki.ubuntu.com/ubuntu-manual/TableOfContents")

**_Questions:_**

[B]1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?

2. Do you believe a manual like this should be included in Lucid Lynx by default?

3. If it was to be included by default, do you think it should be on the desktop?

4. Would you be interested in printing such a manual?

5. Do you think PDF is a good format, or would you prefer HTML or another format?

6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox
Evolution
Totem
Ubuntu One

7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Display
External devices
Webcams
Sound
Disk Drives
Wireless/Infrared[/B]


Thankyou for taking the time to respond. With your help, we hope to be able to create something that will make the transition to Ubuntu easier for newcomers.

For more information about the project, and to see how you can help, visit our wiki: [https://wiki.ubuntu.com/ubuntu-manual](https://wiki.ubuntu.com/ubuntu-manual)

Benjamin Humphrey
Ubuntu Manual Project Leader

---

### Post by f-teem on 2010-01-11
#2 yes,
#3 it doesnt have to be right on the desktop,but it should be eassily accessible by a new ubuntu user
#5 yes,I think the best format would be pdf

my 2 cents :)

---

### Post by cbabbage on 2010-01-11
1 - How to use Synaptic and the software repositories to the best advantage.
2 - yes
3 - yes 
4 - yes
5 - PDF
6 - Open Office and Firefox
7 - Printing, external devices and sound.

---

### Post by tom.swartz07 on 2010-01-11
Def talk about Grub and Partitioning.
Ive answered many questions about how to dual boot and set up ubuntu.

How WUBI should be implemented and maintained. Again, a number of my posts are helping those who have broken WUBI installs because they use them improperly.



Perhaps you could include a guide on how to set up an install after its installed. How to update, how to install packages, tour of software center and synaptic, how to install important compatibility- Java, DVDs, Flash, etc.

---

### Post by juancarlospaco on 2010-01-11
1)The ubuntu way of installing things, .deb and dependencies
2)Yes
3)Yes, but using a SymLink, not the file itself.
4)Yes
5)HTML is more reliable, it can include HTML5 ogg audio/video, javascript, and more
6)OpenOffice
7)Extenal Devices/Printing *(i mean a printer is an external device)*

Please use APT:/URL links on the Manual, 
then if you are talking about an application you can install it clicking the name.

:)

---

### Post by k3lt01 on 2010-01-11
Not being a smarty here but why are you trying to re-invent the wheel? 

[This]("http://www.ubuntupocketguide.com/") guide which is posted in [this thread]("http://ubuntuforums.org/showthread.php?t=1052065") is already freely available. Plus there is the also readily available [Official Ubuntu Documentation]("https://help.ubuntu.com/") which already covers most things.

---

### Post by humphreybc on 2010-01-11
> **k3lt01 said:**
> Not being a smarty here but why are you trying to re-invent the wheel? 

[This]("http://www.ubuntupocketguide.com/") guide which is posted in [this thread]("http://ubuntuforums.org/showthread.php?t=1052065") is already freely available. Plus there is the also readily available [Official Ubuntu Documentation]("https://help.ubuntu.com/") which already covers most things.

Perhaps you should see the wiki section on justification:
[https://wiki.ubuntu.com/ubuntu-manual#Justification](https://wiki.ubuntu.com/ubuntu-manual#Justification)

---

### Post by Mornedhel on 2010-01-11
Why not both PDF and HTML ?  If you write your manual in something like ReST, or Emacs' Muse publishing mode, or some of the other markup plain text formats, you should be able to generate a variety of outputs from a single source.  Plus it's easier to maintain version control on plain text files (in case you were planning to publish PDFs with OpenOffice or something with binary files), and the sources are more human-readable.

A GNU info manual would be a nice touch too.  Easier to navigate when you don't have an X server for whatever reason.

---

### Post by humphreybc on 2010-01-11
We are using LaTeX so yes, we will be able to output to multiple formats.

We just want to see what would be the most popular.

---

### Post by houseworkshy on 2010-01-11
Excellent Idea.  I'm not quite a noob nor yet seasoned.  One of the first things I did on-line in Ubuntu  was seek for such a thing and thanks to advice from this forum got this [http://www.ubuntupocketguide.com/index_main.htm](http://www.ubuntupocketguide.com/index_main.htm)  It was , and still is, invaluable.  However, it is not comprehensive and  there is certainly room for one which goes with the live CD.

1  I'll cheat on this one and choose installing in general.  As this guide would be the first thing people see on their new system I'd suggest the examples would be the first things people need to do anyway so they can work through as they set up.  So, easiest first, add/remove or whatever it is called in Lucid for a game perhaps.  Then remove it.  Then hardware drivers.  Then synaptic and software sources, explain that and have them enable, then install something and point out the properties tab ( when one is new &#8220;but where is is?&#8221; can be a puzzle.  If you choose something which does not add a link entry that would be an opportunity to show main menu.  Then explain that the GUI is only that and introduce the terminal and apt-get.  This would be after a basic tour of the GUI of course.

2  Yes.  It is important to remember that many people are not on-line.  With that in mind a basic into to .deb files and maybe aptoncd would also be useful.  When I first used Ubuntu I was off line and depended on what I could download on friends machines ( the library didn't allow the use of recordable media ).  Besides what use is an on-line guide when what's wrong is ones internet connection?  In fact, much later in the book, go big on connecting.  Whilst it does itself for most routers it can be a noob nightmare for dial up users..  If you only have one detailed section make it that one as once on-line there is plenty of help available for anything else.

3  Sort of.  You could have a &#8220;welcome read me&#8221; document on the desktop which points at places>documents>manuals.  This would encourage orderly habits and could also function as a disposable item to use when you explain renaming, deleting recovering etc.  I know &#8220;manuals&#8221; doesn't exist as a folder by default but you could show them how to make it.

4  I don't have the capability unfortunately.

5  No preference

6  The needs of users vary so I don't know, which ever has the least good built in help I suppose.. Mentioning built  in help at the start of the sections would be good.   .I wish I'd known about /user/share/doc earlier so point that out.  I found it so useful so often for some programs, some only put in the change log and copyright unfortunately, that I made it one of my bookmarks.

7  Display probably as if that is too wrong one can't do a thing.

This is a very good idea, the important things to do are to pitch at noobs but at a higher level than what is there already and do not assume they are on-line as so many application helps do.  When I wasn't, that assumption was a real barrier.

---

### Post by JoshuaRL on 2010-01-11
Might want to check out the [Ubuntu Community Learning Project.](https://wiki.ubuntu.com/Learning)  Not exactly the same, but your idea could easily fall under the umbrella of what they're trying to do.  And they have Canonical support too.  Better to consolidate and work together than to branch or start fresh and be yet another project in search of help.

But I may be wrong, there may be a lot of support for this idea and UCLP may not want a hand in it.  It would be a good idea to check first though.  I know every one of the board members except for Martin Owens, and I'm sure they would all be happy to discuss your idea.

---

### Post by chessnerd on 2010-01-11
1. How to use the Software Center to its fullest potential
2. It depends on what the final product is like when Lucid comes out. As long as it is a fully finished, professional-looking product, then it should. If it's unfinished, or rushed to meet the deadline, no. Then it should be mentioned with a link to a website containing the manual, but it shouldn't be included.
3. Yes, a link to the manual should appear on the desktop by default.
4. Probably not. If it was short and without too many pictures then I might spare the ink on it, but otherwise, I wouldn't bother with it.
5. PDF is good
6. Evolution
7. Printing/scanning - it's both important and more difficult than in Windows

Good luck, you guys. I'm sure the finished product will help a lot of people. Just make sure to point them here if they need more help. The guys on this forum are better than any manual.

---

### Post by brishu on 2010-01-12
Questions:

*1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?*
 **->** The software Center. 
****** not exactly a ubuntu specific thing, but setting up a network with your Windows so that you can share files easily should also imo be a topic that should be considered.

*2. Do you believe a manual like this should be included in Lucid Lynx by default?*
**->** while i DO think that having a tutorial included by Default is a good idea, i say we let it have a trial run. if it goes well/ looks like its maintainable then yes. 

*3. If it was to be included by default, do you think it should be on the desktop?*
**->** On the Applications Menu yes, on the Desktop no. Maybe on the LiveCD desktop

*4. Would you be interested in printing such a manual?*
**->** Dont have the resources to .... but i might print off a chapter or select pages to give to friends

*5. Do you think PDF is a good format, or would you prefer HTML or another format?*
**->** id say keep a .pdf option, and HTML version is also a good idea, although i would say a HTML version that is almost identical to the .pdf version and doesnt have fluff like Videos, vids are helpful at times, but a nice detailed page is easier to go back to.

*6. We are including a section on using the default applications. Which do you think should have the most detail?*
**->**
Open Office <- most of the things i needed do needed, word(OOo Writer in this case ), and working 7+ hours on a project and having it not format correctly when it was opened in Word, and then spending ANOTHER hr on fixing the formatting was not an experience i want to deal with ... 


*7. Out of the following hardware categories, which one should have the most detail?*
**->** I'm going with say Printers, but thats mainly cause most of my hardware was compatible and i have had absolutely no problems.

---

### Post by Nevon on 2010-01-12
**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**
Instructions on how to install software using the package manager, rather than downloading strange executables from random websites.

**2. Do you believe a manual like this should be included in Lucid Lynx by default?**
Sure. They do that with Linux Mint already.

**3. If it was to be included by default, do you think it should be on the desktop?**
Yes, and preferably opened by default on a newly installed system.

**4. Would you be interested in printing such a manual?**
Not for me, no.

**5. Do you think PDF is a good format, or would you prefer HTML or another format?**
PDF is great. Perhaps you could have an alternative version if you'd like, but for me, PDF is solid.

**6. We are including a section on using the default applications. Which do you think should have the most detail?**

Rhythmbox
F-Spot
Open Office
Tomboy
**Empathy** (I'm sure it can be confusing for new users)
Firefox
Evolution
Totem
Ubuntu One

**7. Out of the following hardware categories, which one should have the most detail?**

**Printing/Scanning** (This can sometimes be quite difficult even for more experienced users.)
Display
External devices
Webcams
Sound
Disk Drives

---

### Post by nilarimogard on 2010-01-12
1. Adding PPAs - the visual way, and how to find a PPA you might be interested in.
2. Yes
3. Yes
4. Yes
5. PDF is ok.
6. Rhythmbox -> people love music. Firefox would have been my main choice, but people already know most about it since it's you can use it in all operating systems.
7. Sound

---

### Post by Khakilang on 2010-01-12
5. I think PDF is a good format.

---

### Post by YosefKaro on 2010-01-12
1) Where to turn for help eg the forums or IRC ie to promote community awareness; I was totally at a loss until I discovered the community.
2) yes
3) yes
4) yes
5) pdf
6) firefox and empathy
7) printing/scanning

---

### Post by Mornedhel on 2010-01-12
To be honest, I fail to see the advantages of PDF in this case, while HTML clearly has some:

* video support
* copy pasting works better than from a PDF
* can read it even without X working in case of emergencies
* navigating hyperlinks is easier than in a PDF

---

### Post by irishbreakfast on 2010-01-12
1. I agree with houseworkshy
2. Yes
3. Yes. Good for newbies.
4. Never
5. Actually the first preference is for one where the user can enter their own notes. 
6.  don't care
7. Sound

---

### Post by tadcan on 2010-01-12
6. Pitvi (or whatever video editor is chosen) since the goal is to have the same functionality in ubuntu as is in win/osx. 

/rant/
The help files so far have been very lacking in this regard. Simply saving to install an editor and away you go, which passed the responsibility onto the app creator to provide the documentation. Mark said in a speech that he wanted those tasks to be done in ubuntu. I get the impression that no one at canonical knows about video editing.  
/rant/

---

### Post by ianto` on 2010-01-12
**_Questions:_**

**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**
A guide to effectively using apt-get and synaptic,  especially the predefined sections in the menu on the left-hand side which can be helpful when searching for an application/package which does a specific task. (Not a fan of the Software Centre!)

**2. Do you believe a manual like this should be included in Lucid Lynx by default?**
Certainly

**3. If it was to be included by default, do you think it should be on the desktop?**On the Desktop only when it is being used as a LiveCD however after installation it should be placed in the Examples folder or even better in the System drop-down menu in GNOME.

**4. Would you be interested in printing such a manual?**
I prefer not to print documents (economic on ink).

**5. Do you think PDF is a good format, or would you prefer HTML or another format?**For the main objective PDF is excellent however having a mirror site online is also useful for those who wish to use it as a quick reference.

**6. We are including a section on using the default applications. Which do you think should have the most detail?**
*Open Office*

**7. Out of the following hardware categories, which one should have the most detail?**
*Printing/Scanning*

---

### Post by fromthehill on 2010-01-12
**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**
restricted-extras, flash, jre, and other proprietary software everyone needs but isn't included

**2. Do you believe a manual like this should be included in Lucid Lynx by default?**
yes

**3. If it was to be included by default, do you think it should be on the desktop?**
yes, otherwise new users can't find it

**5. Do you think PDF is a good format, or would you prefer HTML or another format?**
every format is fine as long as it can be opened with a double-click

[B]6. We are including a section on using the default applications. Which do you think should have the most detail?
[/B]
those applications are pretty straightforward.
maybe a manual howto install software with software-center and a manual for synaptic-package manager.

another thing to include would be something about security. telling users ubuntu isn't invulnerable for malware and a list of commands that break your system [(something like this) ]("http://ubuntuforums.org/announcement.php?f=11")

**7. Out of the following hardware categories, which one should have the most detail?**

Sound can be a real headache
internet access (especially wireless)

---

### Post by jlh68 on 2010-01-12
No. 7:  SOUND, next printers/scanners
No. 6:  Emphathy.   Note on OpenOffice, there is a lot of info about it in other places, to include much on OO.o is loading up the manual.
No. 5:  PDF is good.
No. 4:  Printing could be done by Lulu.com
No. 3:  Yes include it on desktop
No. 2:  Yes
No. 1:  JRE, Restricted Extras, Ubuntu Netbook Remix differences from the regular desktop and how to install it with out an optical drive.

---

### Post by ianto` on 2010-01-12
> **jlh68 said:**
> No. 4:  Printing could be done by Lulu.com

I really really highly recommend [SIZE="4"]**not using lulu.com**[/SIZE] because they are well known as a scam-site.  Just Google "lulu.com scam" without the punctuation marks and a whole list of bad things about the site will appear such as trying to sell people ISBNs which are already in use as well as a lot more.  Instead if you are serious about getting published use Lightning Source or a similar company.

---

### Post by enz1m3 on 2010-01-12
While I do believe PDF is a good format for support documentation (easier to print while maintaining formatting, etc.), I agree HTML has a better way to display information such as videos. But ultimately, I think PDF is easier to maintain, and maintaining two versions of the same manual would be very hard to accomplish.

As for the topics in the manual, one I find people having lots of trouble is video/audio codecs (installing medibuntu usually fixs most of them), so an explanation why these aren't included by default (I believe there's an explanation at medibuntu's website) and how to install them would be of much value, imo.

I'm already helping in translating it to Portuguese, and I don't believe I'll have any problems continuing that (at least until Lucid), but something more would be too much time-consuming for someone like me (who doesn't have free time at all)

---

### Post by humphreybc on 2010-01-12
I'd just like to thank everyone for their feedback so far, it's much appreciated. :)

---

### Post by llamaSniper on 2010-01-12
Questions:

3. If it was to be included by default, do you think it should be on the desktop?

Yes.

4. Would you be interested in printing such a manual?

Nothing more than 10 pages for printing (a quick-reference chart perhaps?)

5. Do you think PDF is a good format, or would you prefer HTML or another format?

PDF is good, Adobe provides Adobe Reader for Linux, but PDF isn't open-source. In the interest of allowing Windows users to read the manual, however, I would use PDF. Perhaps make multiple formats available? 

6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox/Totem plugins, Open Office transitioning from MS office, Evolution transitioning from MS outlook

7. Out of the following hardware categories, which one should have the most detail?

Sound/Printing/Scanning, these are essential to beginning users, and fixes must be readily available.

---

### Post by Dayofswords on 2010-01-12
**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**
installing from source code

**2. Do you believe a manual like this should be included in Lucid Lynx by default?**
sure

**3. If it was to be included by default, do you think it should be on the desktop?**
link to it, actually file in /home

**4. Would you be interested in printing such a manual?**
depends on the final length, i've got only so much ink and paper
[B]
5. Do you think PDF is a good format, or would you prefer HTML or another format?[/B]
pdf is nice, but if you end up with html, go html5


[B]
6. We are including a section on using the default applications. Which do you think should have the most detail?[/B]

the big 3!
Open Office
Firefox
Evolution(though Thunderbird is better =p)

[B]
7. Out of the following hardware categories, which one should have the most detail?[/B]

Printing/Scanning
External devices



i could help some, somehow

---

### Post by k3lt01 on 2010-01-12
Ok here are my thoughts.


**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**How to use Ubuntu Software Center, provided that is the devs get it working by Lucid because atm it is broken.

**2. Do you believe a manual like this should be included in Lucid Lynx by default?**Yes, but then again the LiveCD is can only be so big, what would you have them remove so it could be included?

**3. If it was to be included by default, do you think it should be on the desktop?**No, not on the desktop but within an Ubuntu specific folder in Documents.

**4. Would you be interested in printing such a manual?** Yes I would.

**5. Do you think PDF is a good format, or would you prefer HTML or another format?**HTML would be my preference with a link to a "printable" text version of th HTML page.

**6. We are including a section on using the default applications. Which do you think should have the most detail?**

Rhythmbox - No, Banshee is better
F-Spot - No
Open Office - Yes because most people use "office" applications but then again OOo has so much documentation already easily available.
Tomboy -  No because I never use it.
Empathy - Nooooooooo, Pidgin is better and Empathy has some serious security issues.
Firefox - No, seriously if someone cannot use FF they aren't going to be able to access a HTML version of this book are they.
Evolution - Maybe.
Totem - What's there to learn?
Ubuntu One - No, I think it's pretty much only serious "geeks" who use Ubuntu One anyway

**7. Out of the following hardware categories, which one should have the most detail?**

Printing/Scanning - Yes
Display - Yes especially how to select and configure the different hardware eg. ATI, Intel etc.
External devices - Such as?
Webcams - Yes
Sound - Maybe
Disk Drives - What type of Disk Drives? CDs, DVDs, Bluerays, HDDs, Flash?

---

### Post by bronxbomberz41 on 2010-01-12
1) Using Synaptic, Using apt-get, getting flash working (rarely works 'out of the box')
2)Yes
3)No
4)No
5)PDF is good and preferred to other formats
6)UbuntuOne because people probably still are a little unfamiliar with Cloud Computing and don't know how to backup their computers, and F-Spot because photo management has become such an integral part of a normal user's experience (picasa, facebook, etc)
7)External Devices- everybody has an ipod and there isn't great or consistent documentation on how to use it properly with ubuntu without dualbooting windows especially for the ipod touch or the iphone.

---

### Post by Nicolas.Perrault on 2010-01-12
1)A list of Windows and Mac programs, and their Linux equivalent.
2)Yes, quite definetly.
3)No, but in the documents folder.
4)If I ever need to. But not for the moment.
5)PDF is great. An online version could be awesome too.
6)(No particular opinion)

I know this is kind of stupid, but once we're done with Lucid Lynx, and all the other other versions up to W, I propose Wacky Wombat for the Ubuntu 20.0.;):D

---

### Post by k3lt01 on 2010-01-12
Having just had a look at the Wiki page Chapter 3 indicates there are different versions available yet it seems like Chapter 4 (4.1) will only discuss Gnome. While I myself dislike KDE, and have only limited knowledge of the others, I think because: 
1. There are variants of Ubuntu that have these desktop environments as standard.
2. These desktop environments are also available through the official repositories.
3. Many users DO prefer these Desktop Environments to Gnome.
they should be discussed in a great a detail as Gnome would be. This includes their default programs in preference to Ubuntu's (Gnome's) default programs.

---

### Post by humphreybc on 2010-01-13
> **k3lt01 said:**
> 3. Many users DO prefer these Desktop Environments to Gnome.
they should be discussed in a great a detail as Gnome would be. This includes their default programs in preference to Ubuntu's (Gnome's) default programs.

This release is just the Ubuntu Manual. If it is successful, then we may consider doing a Kubuntu Manual and a Xubuntu Manual etc...

I would also like to mention that we have a meeting coming up this Saturday for anyone who is interested, you're welcome to come along and lurk or join in - it's a public meeting in our own channel.

Meeting details:

[Saturday the 16th January 2010 at 1100 UTC/GMT]("http://www.timeanddate.com/worldclock/fixedtime.html?day=16&month=1&year=2010&hour=11&min=0&sec=0&p1=0") in #ubuntu-manual on irc.freenode.net

The Agenda can be found [here.]("https://wiki.ubuntu.com/ubuntu-manual/Meetings#Agenda")

---

### Post by running_rabbit07 on 2010-01-13
> **humphreybc said:**
> **_Questions:_**

**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**
Security. Cover AppArmor or at least UFW. At a minmum, mention them both and link them to bodhi.zazen's Security stickies for full detail.> **2. Do you believe a manual like this should be included in Lucid Lynx by default?**If it can be easily found or even pasted to the dekto and/or the home folder, then yes. It would have to be easily accessible and recognized for what it is by its title.> **3. If it was to be included by default, do you think it should be on the desktop?**Yes. Could it be listed in Ubuntu Software Center as a download also? (I have found docs in Synaptic, but there is no knowing where they go when installed.)> **4. Would you be interested in printing such a manual?** I would definitely read it. I am not into wasting paper on something I am not going to read every day. The most important thing is making it easily available to those who delete it from the desktop.[B]
5. Do you think PDF is a good format, or would you prefer HTML or another format?[/B][/QUOTE] I prefer PDF.
> **6. We are including a section on using the default applications. Which do you think should have the most detail? ** I have seen a lot of complaints about getting music, mostly, MP3s working, so I would say Rhythmbox needs to covered well. Firefox needs coverage for the sake of security and installing NoScript if at all possible. Empathy uses the key ring, so that will need to be covered. Many of the new people complain about entering their password over and over. They don't seem to care about how that secures their system, so covering how the keyring can be set to unlock multiple properties could be a good thing, though it wouldn't be wise as far as security is concerned. I don't use the other functions listed very often, but I'd recommend touching base on all of them. Put some emphasis on how Ubuntu One works, so that people will be more inclined to use it.
> [B]Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox
Evolution
Totem
Ubuntu One

[/B]**7. Out of the following hardware categories, which one should have the most detail?** I'd say the average user wants their webcams, printers, and external devices to work with minimal thought process, so they need to be covered. With all of the sound problems in Karmic, if they are not ironed out before the release of Lucid, then the work arounds may need to be covered.
> [B]Printing/Scanning
Display
External devices
Webcams
Sound
Disk Drives[/B]All in all, you have a large task ahead of you and hopefully a few people helping. I hope this helps you out and I look forward to reading the manual. Thank you and your crew for what you are doing.

---

### Post by running_rabbit07 on 2010-01-13
> **k3lt01 said:**
> Having just had a look at the Wiki page Chapter 3 indicates there are different versions available yet it seems like Chapter 4 (4.1) will only discuss Gnome. While I myself dislike KDE, and have only limited knowledge of the others, I think because: 
1. There are variants of Ubuntu that have these desktop environments as standard.
2. These desktop environments are also available through the official repositories.
3. Many users DO prefer these Desktop Environments to Gnome.
they should be discussed in a great a detail as Gnome would be. This includes their default programs in preference to Ubuntu's (Gnome's) default programs.

Maybe you could start a thread and get volunteers to help build a Kubuntu and/or Xubuntu manual going. It would be great to have all three DEs covered, but Ubuntu is Ubuntu's project and I doubt they have enough people on their team to write a good manual about all three DEs.

---

### Post by k3lt01 on 2010-01-13
> **running_rabbit07 said:**
> Maybe you could start a thread and get volunteers to help build a Kubuntu and/or Xubuntu manual going. It would be great to have all three DEs covered, but Ubuntu is Ubuntu's project and I doubt they have enough people on their team to write a good manual about all three DEs.Sorry but I myself have no interest in KDE, I dislike it actually, and I am not really into the other DEs either. I am interested in assisting with the Ubuntu variant because that is what I myself use.

My point reverts back to the fact that  Ubuntu is a Canonical product, as is Kubuntu, Xubuntu etc. To be fair to all users and variants the manuals should, IMHO, be written concurrently so current and potential users can make informed choices regarding what is best for them.

---

### Post by running_rabbit07 on 2010-01-13
> **k3lt01 said:**
> Sorry but I myself have no interest in KDE, I dislike it actually, and I am not really into the other DEs either. I am interested in assisting with the Ubuntu variant because that is what I myself use.

My point reverts back to the fact that  Ubuntu is a Canonical product, as is Kubuntu, Xubuntu etc. To be fair to all users and variants the manuals should, IMHO, be written concurrently so current and potential users can make informed choices regarding what is best for them.

Totally agree. I tried KDE myself and well.... I am back with the GNOME monster.

---

### Post by aimpau on 2010-01-13
1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?

*Hardware Setup: Making sure everything works*

2. Do you believe a manual like this should be included in Lucid Lynx by default?

*Of course.*

3. If it was to be included by default, do you think it should be on the desktop?

*Yes, but let's be different here. In windows, there is what we call "**Help and Support**"...I think for linux, the title of the help file or symlink is "**Don't know what to do next?**"...basically, the file is like "speaking humanely" to the new user.*

4. Would you be interested in printing such a manual?

*I wouldn't so I can save the trees...but what I want is that I can bluetooth a portion of the manual to my pocketPC and read it wherever I go*

5. Do you think PDF is a good format, or would you prefer HTML or another format?
[I]
Both. HTML can have video, sound, SVG/PNG, flash, etc...if you want, you can incorporate this to Prism.[/I]

6. We are including a section on using the default applications. Which do you think should have the most detail?

*Jokosher? Blender? Scribus? Inkscape? haha...kidding...:) No choice here...*


7. Out of the following hardware categories, which one should have the most detail?

*External devices: bluetooth, wifi, ipod, smartphone, ir remote, etc..*

---

### Post by blazemore on 2010-01-13
The best way to ask for help on the forums.
How to submit your ideas to Brainstorm.

---

### Post by slakkie on 2010-01-13
> **humphreybc said:**
> We are working on a new Ubuntu project that you may have heard about, [The Ubuntu Manual Project.]("https://wiki.ubuntu.com/ubuntu-manual") It is a complete beginners manual for Ubuntu, featuring comprehensive guides, How Tos and information on anything you need to know after first installing Ubuntu.

Feel free to answer each question in as much or as little detail as you like.

To view what content we have at the moment, visit the [Table of Contents.]("https://wiki.ubuntu.com/ubuntu-manual/TableOfContents")

**_Questions:_**

**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**


Package maintenance, upgrades. It is not a Ubuntu specific thing. But explaining which tools are available to maintain your installed packages would help. Eg. a discussion about apt-get vs aptitude (google for blogs, there are some really nice discussion on this). 

Discuss:
apt-get
apt-file
apt-cache
apt-*
aptitude
dpkg


> 
2. Do you believe a manual like this should be included in Lucid Lynx by default?


Yes and no. I personally do not need documents to be installed, put it in a package so people can install the documentation if they want to. For new users I would say, yes install it by default. What is your target audience?

> 
3. If it was to be included by default, do you think it should be on the desktop?


No.

> 
4. Would you be interested in printing such a manual?


Printing? No, but I do know people in the printing industry, I can always ask. But I doubt they will bite... 

> 
5. Do you think PDF is a good format, or would you prefer HTML or another format?


I think you should provide the guide in multiple formats:
* HTML
* PDF
* Plain text
* Postscript
* etc.

I would love to use the text and PDF format.


> 
6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox
Evolution
Totem
Ubuntu One


None of the above. Perhaps Tombot and Open Office, however for the latter I think the OOo project should provide documentation itself. I would rather have a comparison between several applications which do the same, so a user can determine which one he prefers based on the book. Give them choice, don't choose for them.

> 
7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Display
External devices
Webcams
Sound
Disk Drives
Wireless/Infa-Red[/B]


All of the above, with equal importance. I take it the book is focussed on Desktop usage, and people will touch all (most) of these subjects when using a desktop. 

For printing I would also like to see remote administration of CUPS. You can teach users to setup a central printing server from which the rest of the network can print. Think it would help small/medium businesses.


I also would like to state that you can use the following guides in your book if you want to (but please give credit):

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)
[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)


From my own blog:
Please mention these as licensed under the FreeBSD documentation license, however I grant the Ubuntu documentation team a waiver to relicense them if needed. 

[http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/](http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/)
[http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)
[http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/](http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/)
[http://blog.opperschaap.net/2009/11/16/chroot-with-upstart/](http://blog.opperschaap.net/2009/11/16/chroot-with-upstart/)

Hope this helps.

---

### Post by del_diablo on 2010-01-13
> **running_rabbit07 said:**
> Maybe you could start a thread and get volunteers to help build a Kubuntu and/or Xubuntu manual going. It would be great to have all three DEs covered, but Ubuntu is Ubuntu's project and I doubt they have enough people on their team to write a good manual about all three DEs.

The Ubuntu and Xubuntu and Kubuntu manual would be identical regardless, why make several?

---

### Post by gsmanners on 2010-01-13
I'm not a beginner, but I'll give the answers I would have given about 5 years ago:

1. How to compile from source.
2. Yes.
3. Yes.
4. No.
5. HTML is preferred.
6. Firefox
7. Display

---

### Post by Cam42 on 2010-01-13
> 
1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?
Installing software.
> 
2. Do you believe a manual like this should be included in Lucid Lynx by default?
yes
> 
3. If it was to be included by default, do you think it should be on the desktop?
 yes
> 
4. Would you be interested in printing such a manual?
 maybe> 
5. Do you think PDF is a good format, or would you prefer HTML or another format?  PDF
> 
6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox
Evolution
Totem
Ubuntu One
Firefox and OpenOffice.org. They're arguably the most used programs for beginners. > 
7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Display
External devices
Webcams
Sound
Disk Drives
Wireless/Infa-Red
Disk drives, and webcams.

---

### Post by Anuovis on 2010-01-13
[LEFT]1. An easy-to-understand explanation on the system as a whole, it's components and how they interact. (kernell, packages, what manages the windows, how are the files organized, how are devices recognized and grouped, etc.)

2. Yes

3. Yes

4. It depends on the length and the content, but probably yes. At least some parts of it.

5. PDF is OK

6. Open Office, Firefox, F-Spot

7. Wireless, Printing/Scanning, Display




[/LEFT]

---

### Post by UberElvis on 2010-01-13
2. Yes, definitely.
3. Yes.
4. Personally, no, but I'm sure a lot of beginners would.
5. I personally think HTML would be best.
 
I'll come back to this thread if I can think of answers for #1, 6, and 7.

---

### Post by k3lt01 on 2010-01-13
> **del_diablo said:**
> The Ubuntu and Xubuntu and Kubuntu manual would be identical regardless, why make several?They wouldn't be identical because Gnome, KDE etc aren't identical. They use different programs to achieve the same end result.

---

### Post by sbrown1992 on 2010-01-13
[B]1. Installation of Software using the Software Center

2. Yes, Yes, double Yes (if it's ready by then)

3. A shortcut on the desktop would be good

4. No

5. PDF as default, with other formats available

6. Firefox. Once they have that worked out all other info can be found online

7. Wireless[/B]

---

### Post by Dark_Stang on 2010-01-13
> **humphreybc said:**
> 1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?
Basic use of the operating system, including installing and removing software. The absolute biggest problem most people have when switching from Windows or Mac to Linux is breaking themselves out of the "Oh I need to search for this piece of software online or buy it in a store" mentality. If we can break that quickly it makes most people start to realize that Linux **is not** Windows/Mac and that their old way of thinking doesn't carry over.

> **humphreybc said:**
> 2. Do you believe a manual like this should be included in Lucid Lynx by default?
On the default .iso, yes. But don't you dare stick this in my minimal install or as a suggestion for other packages.

> **humphreybc said:**
> 3. If it was to be included by default, do you think it should be on the desktop?
A sym link would be okay, or under System > Help.

> **humphreybc said:**
> 4. Would you be interested in printing such a manual?
The last comprehensive manual for an OS that I saw was larger than an encyclopedia, so no, not really. Also, what are you going to do when a program changes and the manual has to be updated? Paperless is the way to go these days.

> **humphreybc said:**
> 5. Do you think PDF is a good format, or would you prefer HTML or another format?
PDF is nice as long as it stays organized. But I would still prefer HTML or some sort of web interface so users could easily click on things to jump through sections. It doesn't have to be fancy by any means, most technical manuals aren't.

> **humphreybc said:**
> 6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox
Evolution
Totem
Ubuntu One
Most of those users should be able to figure out a web browser or a media player. Even evolution is very similar to outlook and thunderbird. I think OOo should have a detailed section on loading and saving MS files. I'm out of touch with what the average user does though so there may be more important things.

> **humphreybc said:**
> 7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Display
External devices
Webcams
Sound
Disk Drives
Wireless/Infa-Red[/B]
Again, I'm a little out of touch with what most home users do. I work on computers all day long removing infections. So I assume most people take their computers home and look at porn and download free games all day. But I would think that printing/scanning would be the most important. Again, this would break the user out of the usual Windows/Mac way of doing things.

The problem with setting up displays is that it depends on the video card inside the PC. Most home users have no idea what a video card even is. So even having simple things like "For nVidia cards click here, for ATI cards click here, etc." will confuse most people.

Most external devices are plug and play these days. I don't see too many things like webcams, external drives, printers, scanners, etc that Linux can't pick up on and use right away.

Wireless networking is always important. But, just like with the video cards, most users are clueless as to what's inside their computer.

---

### Post by Rodemire on 2010-01-14
**_Questions:_**

[B]```
2. Do you believe a manual like this should be included in Lucid Lynx by default?
```
[/B]Yes it should.[B]

```
3. If it was to be included by default, do you think it should be on the desktop?
```
[/B]Yes it should or maybe included as part of the examples with a launcher on the desktop. Newbies to Ubuntu would have access to it without a hassle.[B]

```
 4. Would you be interested in printing such a manual?
```
[/B]Yes i would be,even though i read Keir's Ubuntupocketguide almost a year ago, i still refer to it today. Ubuntu (and linux in general) requires a lot of unlearning[B]

```
5. Do you think PDF is a good format, or would you prefer HTML or another format?
```
[/B]I think pdf would be a better format, easy to navigate[B].

```
6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox
Evolution
Totem
Ubuntu One[/B]**
```**
In order of preference:
Open office, Evolution (people need to guided thoroughly from the changeover from MS Office so they can trust that Ubuntu can take care of their office needs, lets face it, office apps are a must in any OS)
Empathy 
Totem & Rhythmbox (the codecs issue needs to be resolved very early in a user's Ubuntu experience, it can be a BIG turnoff not to be able to play mp3s on a machine)[B]

```
7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Display
External devices
Webcams
Sound
Disk Drives
Wireless/Infa-Red
```

[/B]For me, wireless broadband, it is very sad the lack of adequate support that Ubuntu has on some 3g cards, and to be honest, Ubuntu is not "Ubuntu" without the internet.[B]
---------------------------

[/B]I really like the idea and i hope you manage to get it done by the time 10.04 comes out. Newbies who read it will be very fortunate to have such a resource at their reach.

Good idea guys.

---

### Post by abdulmajid on 2010-01-14
#1 How to use synaptic manager, installing and uninstalling packages.

#2 Yes

#3 No.

#4 Yes

#5 pdf or html both are good, but not chm.

#6 open office, ubuntu one and evolution.

#7 printing/scanning, webcams, sound and wireless/infrared.

---

### Post by haydoni on 2010-01-14
1. Emphasis on the new Software Centre, as well as the purpose of root permissions; this is in drastic contrast to what old Windows users may be familiar with (being able to download any-old-rubbish and execute it). Could this be located in a **Quick Start** section - many people will want to only read a couple of pages before getting "stuck in", and this might be less daunting.

2. Yes, definitely. 

3. A link to it should appear on the desktop (so if it is deleted the pdf is still on the system and can be used for reference).

4. No. But if there were a Quick Start section, then some new users may want to print just this.

5. Yes.

6. Many of these will have their own guides and you cannot expect to explain everything. A rough guide to the software and links to more detailed guides could be better IMO.

7. The majority of these should be plug-and-play, is this not one of the distinguishing features/philosophies of Linux? - no need to find drivers...

---

### Post by nerdy_kid on 2010-01-14
1. how to fix page tearing -- this took me ages on NVIDIA (have to put a script that starts nvidia-settings -l in /etc/X11/Xsession.d)
2. Absolutly.
3. Yes.
4. No
5. PDF is good...
6. OpenOffice, Evolution, and Fspot.
7.Webcams, Printing, Wireless, Sound, and Display.  That will cover most of the common issues that people run into.

---

### Post by hero1900 on 2010-01-14
[LIST=1]
[*]**If you could choose one 	Ubuntu-specific thing to be included in an Ubuntu Manual, what would 	it be?**
 	**Many users dont know what is open 	source and how to use the synaptic and the ubuntu software center if 	we clear it for them from beginning they will be able to understand 	the idea and then they can use it correctly with no fear ** 	
[*]**Do you believe a manual like 	this should be included in Lucid Lynx by default?**
 	**That will be great I would like to 	see it**
[*]**If it was to be included by 	default, do you think it should be on the desktop?**
 	**I think this is a good idea since 	many users will not search for it, so better to be infront of them 	and then if he done he can remove or put it any other place**
[*]**Would you be interested in 	printing such a manual?**
 	**Maybe some pages not all**
[*]**Do you think PDF is a good 	format, or would you prefer HTML or another format?**
 	**PDF the best**
[*]**We are including a section on 	using the default applications. Which do you think should have the 	most detail?**
 	**I will order it from the most to 	the least:**

[LIST=1]
[*]**Open Office**
[*]**totem**
[*]**Empathy**
[*]**F-Spot**
[*]**Rhythmbox**
[*]**Ubuntu One**
[*]**Firefox**
[*]**Evolution**
[*]**Tomboy**
[/LIST]
 	
[*]**Out of the following hardware 	categories, which one should have the most detail?**
 	**In hardware sound still got 	problems so it is the most important for me**
[/LIST]

---

### Post by gabo.cr on 2010-01-14
1- Ubuntu dual booting.
2- Yes.
3- No.
4- Yes.
5- PDF is better.
6- Open Office.
7- Printing/Scanning.

I would be more than glad to help translating.

---

### Post by Gizenshya on 2010-01-14
> **humphreybc said:**
> 
Feel free to answer each question in as much or as little detail as you like.

[B]1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?

2. Do you believe a manual like this should be included in Lucid Lynx by default?

3. If it was to be included by default, do you think it should be on the desktop?

4. Would you be interested in printing such a manual?

5. Do you think PDF is a good format, or would you prefer HTML or another format?

6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox
Evolution
Totem
Ubuntu One

7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Display
External devices
Webcams
Sound
Disk Drives
Wireless/Infa-Red[/B]


In addition to threads like these, it would be a good idea to gather data from the general help section about what issues come up.

Would a date-based version be possible?  (for the TOC as well...)


1.  My "one thing" is system backup and recovery.  I've been trying for weeks to do a full system backup, but it has proved to be difficult.  I think I'm close, but at every imaginable step I've had questions that have required knowledge of different programs and particulars.  Well, I've backed it up, but I haven't been able to restore it yet.  When I do finally get it working, I would have to start all over again from scratch  if I do it again, because I've tried and failed so many things I don't remember which things worked or not for each step.

Ok, and another thing... :p  File system overview.  I still know very, very little about how the file system is structured (where program folders, driver folders, etc. are, and what the other default folders do/are).  Leaving home is a very intimidating thought for a noob.  It also would add greatly to the basic understanding of the OS in general.

2.  Yes

3.  Yes and no.  I think there should be a link to a folder that contains not only the final manual, but also all the other "example" files that current distros have.  I'm very much a noob, but I've used Ubuntu off-and-on for years.  I only found out about these example files a couple months ago.  At any rate, a manual of this kind would be useless if it couldn't be found instinctually by a complete noobie.

4.  Probably.  Due to having boot information, I probably would since it is hard to google problems when the computer won't even boot.

5.  I prefer PDF.

6 and 7, I don't have enough experience with many of those to have any meaningful input.

---

### Post by Torrilin on 2010-01-14
> **humphreybc said:**
> [B]1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?

I think the most important thing is how to use Launchpad to solve problems that the manual doesn't address directly, and most documentation doesn't cover. You won't find a manual for "how to install Ubuntu Netbook Remix on your Asus EEEpc 1201N laptop". But if you understand how to find out what hardware is in your laptop, and how to use Launchpad it is much easier to find the particular tricky points.

> 2. Do you believe a manual like this should be included in Lucid Lynx by default?

Yes, absolutely. The current "manual" included with Ubuntu is a confused mish-mash, and if you're stuck offline with a problem it's very difficult to find what you need to solve it. That means for many users the first step to solving their problem is "boot into Windows". Since Windows boot sequences are pretty long, and many humans are bad at remembering error messages, the user might forget about what problem led them to reboot for weeks.

> 3. If it was to be included by default, do you think it should be on the desktop?

It should be on the desktop or in a Help category for Ubuntu Netbook Remix on the LiveCDs. For a regular install, it might be best to have it accessible via the regular help tools. The biggest concern is to make sure the user can find the manual when they're on a business trip and a software update causes their wireless drivers to trigger a kernel panic. You don't want to leave them stuck with no way to solve the problem, and the rescue disk is at home.

> 4. Would you be interested in printing such a manual?

Most of the time, I prefer that documentation or other non-fiction reference works be on a computer and searchable with the best available search engines. I am very used to indexes in print works having too few keywords, and I read quickly so just trying to flip through a book to find the right page can be distracting. Well written manuals and reference works are very absorbing reading for me, and I don't often have a day to devote to reading a manual for fun.

> 5. Do you think PDF is a good format, or would you prefer HTML or another format?

I really hate PDFs because they are difficult to search. They're too much like a real book in terms of how you interact with them. And unlike a real book, they're not pleasant to browse. They're often problematic on a small screen too.

> 6. We are including a section on using the default applications. Which do you think should have the most detail?

Ubuntu One

Because the biggest problem for home and small business users is getting into the habit of backing things up properly. People really remember awful experiences when their hard drive starts dying, or their power supply fries in a thunderstorm.

The other included software is important. But there's nothing quite like that sinking feeling when you realize that your family's three desktop computers are all fried after a thunderstorm... and it'll be at least $1500 to replace them.

> 7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Display
External devices
Webcams
Sound
Disk Drives
Wireless/Infa-Red[/B]

I think it's maybe better to look at what Canonical thinks of as "the Ubuntu user" and prioritize the hardware that way. (really, there are probably several target Ubuntu users) Printing and scanning shouldn't be grouped together... or if they are, that implies the typical Ubuntu user is a fairly heavy user of the Gimp, Inkscape and Scribus, and perhaps there should be special focus on cameras and color management appliances. (judging from the forums... this is not the typical Ubuntu user)

Wireless and infrared devices also shouldn't be grouped together. The software to use infrared to sync a Palm Pilot with a laptop is very robust and well supported. The software to get your wireless network card working is often flakey. The software to hook your Bluetooth enabled laptop and phone together is way past flakey. And while it may all be networking from the OS point of view, from the user's point of view it feels like 3 very tasks, and the user interfaces are very different. The user who wants to use their cellphone as a modem is also probably quite different from the person who is stuck screaming at a Broadcom wireless card.

I really admire the writing in the manual for my new Canon digital camera. It's "just" a point and shoot, with almost nothing in the way of manual controls. But the manual clearly has a target audience in mind (new photographers who are confused by f-stop and ISO), and it walks the new user through every bit of the camera's functions. By the end of reading the manual, a novice user should feel very comfortable taking the camera out of fully automatic mode. If you're a professional photographer, the manual will probably irritate you and bore you. My camera is very much aimed at the novice, and the manual matches it quite well. If the manual for a full frame digital SLR was written in the same way, it would be pretty useless to a professional photographer who just spend $2000 on a camera.

---

### Post by Cygnia on 2010-01-14
> 1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?

Multimedia Playback Issues especially codecs for music and video.

> 2. Do you believe a manual like this should be included in Lucid Lynx by default?

Yes.

> 3. If it was to be included by default, do you think it should be on the desktop?

Probably best to put into System >> Help & Support

> 4. Would you be interested in printing such a manual?

Probably not.

> 5. Do you think PDF is a good format, or would you prefer HTML or another format?

I think integrated into the Help section is best.

> 6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox
Tomboy
Totem
Ubuntu One

> 7. Out of the following hardware categories, which one should have the most detail?

Sound

---

### Post by Revolutionary101 on 2010-01-14
1. I would like a section on how to install programs from .tar.gz, .run, and .bin

2. Yes, no doubt about it. If someone has problems with internet setup they will need the manual on their computer installed by default.

3. Yes it should be on the Desktop as a "Welcome to Ubuntu Manual". This will be easy for first time users just to click and easily become familiar with Ubuntu.

4. No but I think people should have the option of printing it. Just because I don't need to doesn't mean other people won't.

5. I think PDF is a good format.

6. Evolution will need the most detail because I think if people are easily able to set up their e-mail that will make them want to stick with Ubuntu.

7. Disk Drives will need the most detail because if you are dual-booting Ubuntu with another OS you will need lots of advice.

---

### Post by SigmaSanti on 2010-01-14
I would suggest that before you have any user enter any command that could potentially damage, reformat or otherwise make there computer do something unusual. You print in big bold letters, **read these the directions carefully** with all sorts of radioactive symbols and caution tape. 
This should not be to discourage people, but to make sure they dont do some silly mistake and end up in the support forum asking for how to recover a formated hard drive.
Sounds like a great idea. 
#2 - yes
Hardware - sound, display, and printer support are the most important for helping people accomplish there goals.

---

### Post by humphreybc on 2010-01-14
... Thanks for everyones responses - these have been fantastic!

We've taken the preliminary data from this thread and turned it into some pretty graphs and charts on our [research page.]("https://wiki.ubuntu.com/ubuntu-manual/Research")

I'd also like to let you know that we are running [another survey]("http://questionpro.com/t/ADd2yZGu50") through QuestionPro that should give us some more detailed statistics.

Once again, thankyou for your feedback.

---

### Post by doublewitt on 2010-01-14
**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**
How to work with .tar files efficiently. This is a serious stumbling point for newbies... there are existing pages (online) but somehow they need to be redone so people can easily understand... sort of like easy as 1-2-3 language... you know what I mean, make it more simple. .tar files is a big problem...

After that, backup/restore would be vital to newcomers...
 
 **2. Do you believe a manual like this should be included in Lucid Lynx by default?**
Yes
 
 **3. If it was to be included by default, do you think it should be on the desktop?**
Yes - right there when you need it!
 
 **4. Would you be interested in printing such a manual?**
Yes
 
 **5. Do you think PDF is a good format, or would you prefer HTML or another format?**
You could offer both formats - preferably PDF
 
 **6. We are including a section on using the default applications. Which do you think should have the most detail?**

How about more details for Kontact + KOffice Workspace + Konqueror? What a great combination! It took me a while to get this going to my satisfaction... if it was presented more like a complete package with appropriate intructions... it would be a great help. All of that combined makes a powerful setup! How about a K Launcher? The whole K-Series needs a better presentation. People don't grasp the fact that all K-Applications joined together creates a wonderful work environment (K - Package)... I am thrilled to have these on my computer... but there is a weak spot there - a better presentation with details would be beneficial.
 
 Rhythmbox
 F-Spot
 Open Office
 Tomboy
 Empathy
 Firefox
 Evolution
 Totem
 Ubuntu One
 
 **7. Out of the following hardware categories, which one should have the most detail?**

I think they all need more detail...
 
 Printing/Scanning
 Display
 External devices
 Webcams
 Sound
 Disk Drives
 Wireless/Infa-Red

---

### Post by k3lt01 on 2010-01-14
> **doublewitt said:**
>  **6. We are including a section on using the default applications. Which do you think should have the most detail?**

How about more details for Kontact + KOffice Workspace + Konqueror? What a great combination! It took me a while to get this going to my satisfaction... if it was presented more like a complete package with appropriate intructions... it would be a great help. All of that combined makes a powerful setup! How about a K Launcher? The whole K-Series needs a better presentation. People don't grasp the fact that all K-Applications joined together creates a wonderful work environment (K - Package)... I am thrilled to have these on my computer... but there is a weak spot there - a better presentation with details would be beneficial.Problem is that by the current thinking these are Kubuntu (KDE) applications and are not going to be discussed in the Ubuntu (Gnome) book.

---

### Post by yester64 on 2010-01-14
> **humphreybc said:**
> 

**_Questions:_**

[B]1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?

2. Do you believe a manual like this should be included in Lucid Lynx by default?

3. If it was to be included by default, do you think it should be on the desktop?

4. Would you be interested in printing such a manual?

5. Do you think PDF is a good format, or would you prefer HTML or another format?

6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox
Evolution
Totem
Ubuntu One

7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Display[/B]


[B] External devices
Webcams
Sound
Disk Drives
Wireless/Infa-Red[/B]


Thankyou for taking the time to respond. With your help, we hope to be able to create something that will make the transition to Ubuntu easier for newcomers.

For more information about the project, and to see how you can help, visit our wiki: [https://wiki.ubuntu.com/ubuntu-manual](https://wiki.ubuntu.com/ubuntu-manual)

Benjamin Humphrey
Ubuntu Manual Project Leader

#1 Philosophy on Ubuntu
#2 in general i think it would be good to have a guide placed on the desktop
#3 yes
#4 yes
#5 both. Not everyone uses PDF and HTML is real standard, meaning everyone has a webbrowser installed at first start.
#6 any standard application. Whatever Ubuntu comes pre installed with should be in the manual.
#7 pretty much any hardware people connect such as webcam's, wifi, networking etc.
 
 I think as far as a manual it should be real written with the dummy in mind. A lot of books aimed to beginners talk to people who know a thing or two about computing.
 But i think a manual should address specifically the closed minds. Or to put it the other way, if anyone with no knowledge can understand and use it it is good.

---

### Post by Rick1971 on 2010-01-15
7. all, why not do all?

---

### Post by perspectoff on 2010-01-15
I have always liked Ubuntuguide.org (at [http://ubuntuguide.org](http://ubuntuguide.org)) and Kubuntuguide.org (at [http://kubuntuguide.org](http://kubuntuguide.org)).

Why re-invent the wheel over and over again?

Take a look at the existing guides and just copy them to your needs. They are covered by the FDL (Free documentation license) and are written in good English, unlike many of the guides circulating around the web (including the official Ubuntu documentation).

---

### Post by colaho on 2010-01-15
2) Just provide a link during the first login should be enough
4) No
5) HTML
6) Empathy
7) Display

---

### Post by proxess on 2010-01-15
1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?
A: How to use Synaptic

2. Do you believe a manual like this should be included in Lucid Lynx by default?
A: No

3. If it was to be included by default, do you think it should be on the desktop?
A: No

4. Would you be interested in printing such a manual?
A: Yes

5. Do you think PDF is a good format, or would you prefer HTML or another format?
A: No, ODT

6. We are including a section on using the default applications. Which do you think should have the most detail?
A: Open Office, Firefox, and Evolution

7. Out of the following hardware categories, which one should have the most detail?
A: Printing/Scanning

---

### Post by puzzler995 on 2010-01-15
[LIST=1]
[*]Difference between KDE and GNOME, (Still cant figure it out)
[*]Yeah!!!
[*]No, but it should definitely be in the help button.
[*]No I'd use it as an ebook
[*]PDF is great, unfortunately it hangs on adobe, but oh well
[*]They all should have great detail. But if I have to choose one, I would say Firefox, as you can get support for the others with it.
[*]They all need a lot of detail. But people seem to have the most trouble with wireless.
[/LIST]

---

### Post by stanca on 2010-01-15
1.How to add and install new apps through synaptic and software sources.
2.Yes!
3.No.Menu>System>About Ubuntu.
4.Yes.
5.PDF,somewhere in ~home/Documents.
6.Rhythmbox,Firefox,Totem,Ubuntu One.
7.Display,Sound,Disk Drives,External Devices.
Just my useless humble opinion.;):)

---

### Post by ementos on 2010-01-15
1. more about hardware install (drivers etc. for example once I didn't know, that for my tablet Pentagram I should only write something to xorg.conf)

2. Yes of course

3. I think yes, because some users don't look at small icons without label on gnome panel.

4. Yes, but electronic version good too.

5. PDF may be
6. Ubuntu One (it's something new)

7. Printing/Scanning

---

### Post by luckydeveloper on 2010-01-16
1 - A very good and detailed Command line Tutorial. I know it is there on the web. We cant expect every one to be online to check those every time they want to learn. Also Ubuntu is getting bigger and bigger in terms of user base.. so "intermediate-knowledge" people like me now want to learn more and more things in ubuntu. A very detailed "Bash" section is a a must in that case .

---

### Post by Jekshadow on 2010-01-16
> **humphreybc said:**
> 
**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**
It would not be as useful to me, but for new users, a list of applications included with Ubuntu correlating to what they might have used on Windows or Mac may help.

Example:
Word -> OpenOffice.org Writer
Internet Explorer -> Firefox
Notepad -> Gedit
etc.

> **humphreybc said:**
> 
**2. Do you believe a manual like this should be included in Lucid Lynx by default?**
Yes, defiantly. I would like the feature of allowing the user to read/browse it while installing the OS, so they don't just have to wait.

> **humphreybc said:**
> 
**3. If it was to be included by default, do you think it should be on the desktop?**
I think it should be kept with the rest of the Ubuntu help pages, and a symlink or .desktop file should be placed on the desktop.

> **humphreybc said:**
> 
**4. Would you be interested in printing such a manual?**

I do not really see much use in printing it, as it would come with Ubuntu by default and be online. We also want to keep Linux distros as environment friendly as possible.

> **humphreybc said:**
> 
**5. Do you think PDF is a good format, or would you prefer HTML or another format?**

A PDF would be good because it is only one file and can be read by nearly every OS. It would also be helpful if copies in other formats were provided online (LaTeX, HTML, ODT, etc.).

> **humphreybc said:**
> 
**6. We are including a section on using the default applications. Which do you think should have the most detail?**

Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox
Evolution
Totem
Ubuntu One

Cover the ones that the users will use most and are not as familiar with. I would cover OpenOffice.org and Evolution first, and then Firefox, Totem and F-Spot next.

> **humphreybc said:**
> 
**7. Out of the following hardware categories, which one should have the most detail?**

Printing/Scanning
Display
External devices
Webcams
Sound
Disk Drives
Wireless/Infa-Red
Choose the ones that the user will interact with the most. I would choose WiFi (who doesn't use WiFi) and Printing.

---

### Post by rahilm on 2010-01-16
1. How to use synaptic and install ubuntu-restricted-extras
2.Yes. only if it is not too large. 
3. a .desktop link will do.
4. of course not
5. Yes
6. OPen office and then F spot
7. Display

---

### Post by jpkotta on 2010-01-16
> 1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?
I would put in a section on third-party apt repos, including ISVs and PPAs.

> 2. Do you believe a manual like this should be included in Lucid Lynx by default?
As long as it stays current, accurate, useful, etc., there is no reason why it shouldn't be included by default.

> 3. If it was to be included by default, do you think it should be on the desktop?
A symlink on the desktop would be OK, but must be in the menu as well.  The benefit of having it on the desktop is that it is ridiculously obvious for a completely new user.  But once the user knows of the existence of the manual, it's just clutter.  They need to be able to remove it from the desktop and still have easy access.

I should add: DO NOT PUT THIS IN /home.  That is not where it belongs.  /home is for things *I* (or other users) make.  A symlink is OK.  It should probably go in /usr/share/doc.

> 4. Would you be interested in printing such a manual?
No, because then you lose internal and external hyperlinks.  You're going to have lots of cross references, right?

> 5. Do you think PDF is a good format, or would you prefer HTML or another format?
Both.  Write it in a format that can generate both kinds of output.  There are many tools that will do this (reStructured Text, LaTeX, OO.o (I think)).  Assuming this is going to be a community project, I would recommend something like LaTeX or reStructured Text where you edit plain text and run it through a document processor to generate the final form.  The advantage of plain text is that it is relatively easy to merge work from several people and keep track of changes.  LaTeX has the advantage of producing beautiful output, but requires some effort to learn.

> 6. We are including a section on using the default applications. Which do you think should have the most detail?

Totem, because that leads to all sorts of weirdness as far as multimedia goes.  This stuff can be infuriating for a new user because of all the different codecs, and the restrictions surrounding some of them.  It has gotten much better, but still needs some explanation.  If a part is included to explain the various legal problems, make it so that section is completely self-contained and can easily be skipped (a general rule for any extra explanatory sections in a how-to type document).

```
7. Out of the following hardware categories, which one should have the most detail?

```
Not sure, but it's infrared, not infa-red.

---

### Post by Dixi1801 on 2010-01-16
[B]1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be? Not too sure, maybe the desktop experience?

2. Do you believe a manual like this should be included in Lucid Lynx by default? yes, a manual like this should be included with all distro's i think personally!

3. If it was to be included by default, do you think it should be on the desktop?
yes

4. Would you be interested in printing such a manual?
pass

5. Do you think PDF is a good format, or would you prefer HTML or another format?
i think PDF would be good, maybe with a few pics in there, like step by step for things.

6. We are including a section on using the default applications. Which do you think should have the most detail?

*_Open Office << _*

7. Out of the following hardware categories, which one should have the most detail?

pass again :P

so there's my attempt at helping :)
[/B]

---

### Post by Shpongle on 2010-01-16
i think it should definitely show new users how to use synaptic , some command line , even a few basics , show them how to set up the restricted extras and dvd playback. how to trouble shoot wireless etc!. assume everything wont work! because if something doesn't they'll look to the manual. include a link to the forums too just in case. 

the psychocats site has some really good stuff on there maybe see what you can add , with users permission of course 

 as for the format i think it should be in html , who wants to scroll for ages to a certain chapter when you can click a link in the menu! , makes sense to do that! ,

Id make it visible on the desktop!. maybe a section explaining linux and how its different from mac or windows would help , stuff like file systems , the directory structure , file types etc. 

 just stuff i see with new people who are using linux (ubuntu in particular) for the first time,  around me

---

### Post by AmrH on 2010-01-16
1. A quick tutorial on how to create a new theme for Ubuntu.
2. Yes it should.
3. In the documents, with a shortcut on the desktop.
4. Yes I'd.
5. PDF is a universal format, so it should work on any device. Keep in mind that somebody may store the manual on his PDA.
6. Open Office.
7. Printing/Scanning.

---

### Post by perspectoff on 2010-01-16
> **humphreybc said:**
> Perhaps you should see the wiki section on justification:
[https://wiki.ubuntu.com/ubuntu-manual#Justification](https://wiki.ubuntu.com/ubuntu-manual#Justification)

Read it. It's not very compelling.

Here's the official Ubuntu documentation rationale for not doing what you're trying to do (from [https://wiki.ubuntu.com/DocumentationTeam/IndependentDocEfforts](https://wiki.ubuntu.com/DocumentationTeam/IndependentDocEfforts) ):

========================================================================
One of the strengths of free software is its openness, the diversity of its users, and the freedom to contribute in a variety of ways.

However, it is also valuable to have a community structure that is able to ensure that contributions are used in a co-ordinated, efficient manner. Ubuntu, a project founded on community involvement, is oriented toward this goal. This is true for documentation, as well.

A number of independent documentation initiatives exist, such as wikis, documentation-centric blogs, and forums with howto sections. Independent documentation sites are a valuable contribution to Ubuntu, but there are several inefficiencies caused by such multi-centric documentation:

* Lack of teamwork - expertise and efficiency is lost, on both sides. Without direct participation in Ubuntu documentation by outside experts, the Ubuntu documentation team loses valuable input. Furthermore, independent documentation loses the centralized structure of Ubuntu and the standardization of the Ubuntu documentation (for better or worse).

* Reinventing the wheel - time is consumed by different people doing the same things. This is sometimes a common problem with free software communities, in general.

* Difficulty for users to find information - when information is located over various different websites, it is time consuming for users to find it. A single authoritative website is easier for users to consult.
 
* Work not included in Ubuntu - the Ubuntu documentation team selects articles from the community wiki for incorporation into the official system documentation (which is shipped with Ubuntu as the Ubuntu Help System). Material that is found only on independent sites cannot be incorporated into the official documentation by this system. 

The documentation team therefore encourages independent sites to submit their material to the Ubuntu wiki:

"Hi [name],

I've just read your guide [guide name] at [URL]. You clearly have an enthusiasm about Ubuntu and a desire to help others get up and running with the best possible experience.

There is a lot of information similar to yours in the Ubuntu Documentation Website at http://help.ubuntu.com/.  This information is written and maintained through the effort of both the Ubuntu Documentation Team and a large volunteer Ubuntu community. This collective approach allows a coordinated pooling of resources, constructive feedback, and peer review.

Please consider becoming a direct participant in this community and bringing your expertise to the Ubuntu Documentation project! Please visit https://wiki.ubuntu.com/DocumentationTeam/ for more information.

You can also immediately start participating by joining the Ubuntu Documentation Team mailing list at

 https://lists.ubuntu.com/mailman/listinfo/ubuntu-doc

or, on IRC, in the #ubuntu-doc channel on the irc.freenode.net server.

Join the growing Ubuntu documentation team!

Best Regards,"

---

### Post by lorsen on 2010-01-16
1) How to get the first packages installed, e.g. ubuntu-restricted-extras, in order to get media things working (mp3, youtube, ...)

2 & 3) Yes, maybe there can be question during install if manual desired or not

4) Depends on the size ;-); should also be available online

5) I guess pdf is the one to choose

6) Open office or firefox; some apps I don't know ;-) 

7) Printing/Scanning

---

### Post by samh785 on 2010-01-16
[B]1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?
[/B]
I would want to see a section devoted to acquiring the restricted extras. This was very confusing to me when I was a new user. I think that a new user who installs ubuntu is likely to be confused by the fact that you can't play mp3 files or flash videos by default. We need to clarify the reasoning behind this and direct them to the proper channels to acquire the codecs if they desire.

[B] 2. Do you believe a manual like this should be included in Lucid Lynx by default?

[/B]Absolutely. New users that don't have experience with linux will want an easy to find instruction manual so they can have their questions answered easily and without needing an internet connection.

** 3. If it was to be included by default, do you think it should be on the desktop?**

As stated above: absolutely.

[B] 4. Would you be interested in printing such a manual?

[/B]Personally, I wouldn't be interested because of how much it costs me to print things. However I am sure that there would be people that would like to print a manual out. From my experience older unexperienced users like to hold things in their hands when they read it.

** 5. Do you think PDF is a good format, or would you prefer HTML or another format?**

PDF is a great format. Many e-readers can use PDF files, so I think that this would be a good way for people to read the manual on-the-go if they can't print the manual (and happen to have an e-reader)

** 6. We are including a section on using the default applications. Which do you think should have the most detail?**

I think that **Ubuntu One** should have the most detail. While being a simple concept for the technically savvy, it might confuse new users. A section should written about it that explains what it is and why it would be useful. 

** 7. Out of the following hardware categories, which one should have the most detail?**

For me this is a toss-up between **external devices** and **sound**. I think that these are the two things that gave me the most trouble when I was beginning to use ubuntu.

---

### Post by Jackp90 on 2010-01-16
1. Explaining how to use the software center and install software importantly how to install applications from tar balls.  Obviously we don't want that on the first page but I believe that it would be important to have that information in there.  When I first started playing around with Ubuntu I remember how hard it was for me to find out how to install software via tar ball. 

2. Most defiantly

3. Absolutely not the desktop has always been a clean slate and that is how it should be kept.  There are some users that wont use the manual and by keeping the desktop clean it shows that the desktop wont be cluttered by things that the user doesn't want.

4. Probably not but who knows 

5. HTML for two reasons: items can be linked to make navigation easier and if the manual will be on the cd space can be saved by using a common html style sheet for the whole manual.

6. Open Office


7. External devices



**Good luck and remember we are counting on you.**

---

### Post by Dr. C on 2010-01-16
**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**

Hardware installation with an emphasis on all networking hardware

**2. Do you believe a manual like this should be included in Lucid Lynx by default?**

Yes
[B]
3. If it was to be included by default, do you think it should be on the desktop?[/B]

No It should be accessible from Help and Support

**4. Would you be interested in printing such a manual?**

No 

**5. Do you think PDF is a good format, or would you prefer HTML or another format?**

PDF is fine
[B]
6. We are including a section on using the default applications. Which do you think should have the most detail?[/B]

Firefox
Evolution 

**7. Out of the following hardware categories, which one should have the most detail?**

Actually one the is not listed namely Networking and this is very critical
This includes all forms of networking not just Wireless/Infrared in particular

Wired
Wireless a/b/g/n
DSL modems, PPPoE etc
Dial-up modems
Cellular (2.xG, 3.xG, cellphone tethering, etc.)
and any other form of networking the community can come up with. 

Networking is so critical for an off-line manual because it allows the user to get help on-line on other subjects that may be lacking in the manual. If a user needs information on OpenOffice.org and it is not in the manual they can get this information on-line ***provided they can get on-line***, but if the user needs networking information, ***in order to get on-line***, they can only rely on the manual which is why networking in the manual is so critical

---

### Post by syklops on 2010-01-16
> **Mornedhel said:**
> To be honest, I fail to see the advantages of PDF in this case, while HTML clearly has some:

* video support
* copy pasting works better than from a PDF
* can read it even without X working in case of emergencies
* navigating hyperlinks is easier than in a PDF

Have to agree here. I don't understand why so many people are choosing PDF. PDFs were created as a way of having documents which could be shared but not edited. Hardly in line with the Open Source community's ideals is it?

Also, the ability to copy and paste from the document will be important, as and when shell commands are needed to be typed by the end user.

As for the other questions:

1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?

If I were you, I would go through the top5 most asked questions on Ubuntu forums and include them. I would imagine getting flash to work would be one, getting the wireless card would be another, and troubleshooting sound to be in there also.

2. Do you believe a manual like this should be included in Lucid Lynx by default?

Absolutely. 

3. If it was to be included by default, do you think it should be on the desktop?

Yep

4. Would you be interested in printing such a manual?

No. Also I don't know why it would be necessary.

5. Do you think PDF is a good format, or would you prefer HTML or another format?

See above.

6. We are including a section on using the default applications. Which do you think should have the most detail?

Aptitude / dpkg and their GUI related apps.


7. Out of the following hardware categories, which one should have the most detail?

Wireless cards/Other Network devices. For many people they do not work out of the box(though things are alot better than when I started with linux). Once you have internet, you can search the web on setting up every other device, but with no internet, there is not much use in instructions on setting up a webcam.

> Networking is so critical for an off-line manual because it allows the user to get help on-line on other subjects that may be lacking in the manual. If a user needs information on OpenOffice.org and it is not in the manual they can get this information on-line provided they can get on-line, but if the user needs networking information, in order to get on-line, they can only rely on the manual which is why networking in the manual is so critical

Couldn't say it better myself.

---

### Post by phillw on 2010-01-16
[B]1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?

[/B]Linux is not windows- that article that explains the differing mind-sets, it is an important thing to learn[B]

2. Do you believe a manual like this should be included in Lucid Lynx by default?

[/B]Yes[B]

3. If it was to be included by default, do you think it should be on the desktop?

[/B]Not the File, That should be under System --> Help and Support, but a link would be useful on the desktop for N00bies[B]

4. Would you be interested in printing such a manual?

[/B]I wish I had the facilities to do so - Q5 answers better..[B]

5. Do you think PDF is a good format, or would you prefer HTML or another format?

[/B]PDF is something most everyone is used to, HTML would be best if the manual could be done like the wiki pages are, with chapter and headings all internally bookmarked.[B]

6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox  - [/B]We're in danger of the fight of the music players here, if that is going to be 'the one', then sure[B]
F-Spot - [/B]Tried it - better an intro to GIMP[B]
Open Office -[/B] Just say it is like a certain well known package and a quick How To as to setting it up to 'talk' (ie load & save) in that package format.[B]
Tomboy -[/B] I use gedit[B]
Empathy - [/B]I still use pidgin, so no comment[B]
Firefox - [/B]How to import bookmarks from IE for dual booters / Wubi would be nice[B]
Evolution - [/B]I use Gmail - Web system, as administer some groups[B]
Totem - [/B]No idea of[B]
Ubuntu One - [/B]I get 10GB free with humyo.com - well, you did ask !![B]

7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning - [/B]Scanners possibly, a lot of printers are PnP with Ubuntu[B]
Display - [/B]If they get a display, then the stickies on the subject are the best place to go for problems**, **A shortened version of the stickie on the subject[B]
External devices - [/B]Use the forums[B]
Webcams - [/B]They're either PnP or a pain[B]
Sound - [/B]A shortened version of Audio Gotchas stickie[B]
Disk Drives - [/B]A how to introducing the differences between C:, D: and the likes of hda0,1 and sda0,1 etc would be good[B]
Wireless/Infa-Red[/B] - IR possibly not, BlueTooth may be a better one - A list of WiFi that works nice & those that don't (already available) would be handy along with the work-rounds.

Just my thoughts - mainly on what seems to me that crops up most often in questions.

Phill.

---

### Post by ssulaco on 2010-01-17
> **humphreybc said:**
> 1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?
**Easy to read and understand,dualbooting procedure**

2. Do you believe a manual like this should be included in Lucid Lynx by default?
**Yes**

3. If it was to be included by default, do you think it should be on the desktop?
**System Tools**
4. Would you be interested in printing such a manual?
**No**

5. Do you think PDF is a good format, or would you prefer HTML or another format?
**PDF**

6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox ---**Yes**
Evolution
Totem
Ubuntu One

7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Display
External devices
Webcams
Sound
Disk Drives---**Yes**
Wireless/Infa-Red[/B]

Thanks

---

### Post by humphreybc on 2010-01-17
> 
Have to agree here. I don't understand why so many people are choosing PDF. PDFs were created as a way of having documents which could be shared but not edited. Hardly in line with the Open Source community's ideals is it?


We do not want the end product to be edited, it's a manual - not the source code.

If users want to help with the project, then the team is open to anyone and the bzr branch is also open to anyone, but the end product shouldn't be able to be edited.

---

### Post by dmaxel on 2010-01-17
[LIST=1]
[*]Not sure.
[*]Most definitely.
[*]Along with the help button.
[*]Printing? Probably not.
[*]PDF would be fine if it's not part of the Help button.
[*]Firefox, Evolution, OpenOffice
[*]SOUND SOUND SOUND. Then Printing/Scanning, then Display.
[/LIST]

---

### Post by k3lt01 on 2010-01-17
> **humphreybc said:**
> We do not want the end product to be edited, it's a manual - not the source code.

If users want to help with the project, then the team is open to anyone and the bzr branch is also open to anyone, but the end product shouldn't be able to be edited.Forgive me if I am wrong here, but, I think you have really missed syklops point. The intent of the PDF format is against Open Source ideologies, whereas Linux (Ubuntu) is supposed to support Open Source ideologies. Therefore regardless if you want the Manual to be editable in its final format or not shouldn't the Manual support something that supports it parent product? 

I'll go further and say that a HTML wiki style manual could allow users to add comments to their own manual in addition to the information already there. This is a realistic option because you will never be able to write all conceivable information and what suits some may not be enough for others.

---

### Post by Mornedhel on 2010-01-17
> **k3lt01 said:**
> Forgive me if I am wrong here, but, I think you have really missed syklops point. The intent of the PDF format is against Open Source ideologies, whereas Linux (Ubuntu) is supposed to support Open Source ideologies. Therefore regardless if you want the Manual to be editable in its final format or not shouldn't the Manual support something that supports it parent product? 

I'll go further and say that a HTML wiki style manual could allow users to add comments to their own manual in addition to the information already there. This is a realistic option because you will never be able to write all conceivable information and what suits some may not be enough for others.

I'm the guy syklops quoted about PDF and HTML being a better idea, but no, those points aren't entirely valid.

The open source part of the manual comes from the *source*, not from the compiled result. Just as you use binaries compiled from open sourced code, you read a manual compiled from open sourced code. That is what humphreybc proposes (he says earlier in the thread they are going to write it in LaTeX -- which in my humble opinion may be another mistake, but that's beside the point). The process of editing the manual is the same as contributing to an open source project: get the current material from bzr, edit it, commit your changes. Also, since one of the goals is to produce a professional-quality manual, I don't think anyone can contribute, you probably need to join the team before you can commit.

Wiki-style edition is achieved with a wiki CMS. You can't expect the end user to install and configure something like that just to be able to take notes in the manual. Most wikis even require the CMS just to display the content in a human-readable format -- the database is binary, except for dokuwiki and other plain text wikis, in which the nice formatting is still provided by the CMS. Overall, wiki-style is a terrible choice for offline reading and note taking.

I still vote for plain text markup like ReST or Muse (not LaTeX). It makes generating PDF *and* HTML *and* possibly other formats barely more costly than generating just PDF or just HTML.

---

### Post by Frak on 2010-01-17
> **llamaSniper said:**
> but PDF isn't open-source.

[Portable Document Format is released as ISO/IEC 32000-1:2008, recognized by the International Standards Organization and International Electrotechnical Commission.]("http://www.iso.org/iso/catalogue_detail.htm?csnumber=51502")

PDF is free to be used by anybody.

---

### Post by k3lt01 on 2010-01-17
> **Mornedhel said:**
> The open source part of the manual comes from the *source*, not from the compiled result.I do understand this point. What I am saying is shouldn't this Manual be Open from "Go to Whoa"? Doing that would support the Open Source philosophy.

> **Mornedhel said:**
> Also, since one of the goals is to produce a professional-quality manual, I don't think anyone can contribute, you probably need to join the team before you can commit.That is beside the point atm. This is after all just a thread about ideas, which seemed to be set in stone even before the thread was initiated in the first place. Regardless of this, it is possible to have a "notes" section, thus the presentation of this thought.

> **Mornedhel said:**
> Wiki-style edition is achieved with a wiki CMS. You can't expect the end user to install and configure something like that just to be able to take notes in the manual. Most wikis even require the CMS just to display the content in a human-readable format -- the database is binary, except for dokuwiki and other plain text wikis, in which the nice formatting is still provided by the CMS. Overall, wiki-style is a terrible choice for offline reading and note taking. Ok I over simplified my point, promoting a Wiki style was just an idea.

Some will say this is beside the point but I will say it anyway. I'm a High School Teacher by profession and a Motor Mechanic by trade. In both lines of work I have used applications/programs, similar to this idea, that are Web browser based. They were all built for Windows XP and Vista with IE, yet using WINE I can run them on my Ubuntu machines and FireFox. A few of them have a "Notes" section at the end of each chapter (for the want of a better word). These "notes" are user input, now NO database or CMS is installed on my Ubuntu machines YET I can still use this facility without having to set anything up myself. So I cannot see why this facility cannot be implemented without having to make things any harder for the end user with regards to setting up a database or CMS.

---

### Post by k3lt01 on 2010-01-17
> **Frak said:**
> [Portable Document Format is released as ISO/IEC 32000-1:2008, recognized by the International Standards Organization and International Electrotechnical Commission.]("http://www.iso.org/iso/catalogue_detail.htm?csnumber=51502")

PDF is free to be used by anybody.A question for you? Are you personally charged anything to use Google? Just like your signature suggests just because it is free to use doesn't mean it is Open Source.

---

### Post by nskhanolkar on 2010-01-17
1.making people who switch over to Ubuntu from Microsoft comfortable in the new programs 
2.whats lucid lynx?
6.Tomboy
7.External devices

---

### Post by dv3500ea on 2010-01-17
1.Installing software (how to use Ubuntu software center / synaptic / .debs) as opposed to the 'Windows' way of doing things. It would be good if this included advice on how to install things without an internet connection (keryx, aptoncd etc).
2.Yes.
3.Yes.
5.It should open and be read in Yelp. (but have available a pdf download online).
6.I actually think most of these are well documented in Yelp.
7.Definately sound (in my experience this doesn't work out of the box and even as an advanced user I have not been able to get recording working).

---

### Post by Ferux on 2010-01-17
1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?
Definetely the way of installing programs, but things like wireless settings, bluetooth etc cannot be forgotten.

2. Do you believe a manual like this should be included in Lucid Lynx by default?
Yes

3. If it was to be included by default, do you think it should be on the desktop?
Yes

4. Would you be interested in printing such a manual?
No

5. Do you think PDF is a good format, or would you prefer HTML or another format?
PDF is ok, but something more interactive would be more helpful, also for newbies.

6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox --> too straight forward, just explain how users should add their music
F-Spot --> not needed
Open Office --> this can be interesting to explain
Tomboy --> not needed
Empathy --> interesting to explain
Firefox --> everybody who has ever seen internet, knows how to work with this, not needed
Evolution --> explain this, people need to access their mail
Totem --> Explain how to install the codec's and how to make DVD's work. Other things not needed. People will use Nautilus to find a movie and double-click it there.
Ubuntu One --> I have no experience with this

7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning --> explain scanning, printing is too automatic to explain
Display --> this needs to be explained
External devices --> explain how to use bluetooth devices like mice
Webcams --> no experience with this
Sound --> too easy
Disk Drives --> not for newbies
Wireless/Infa-Red --> wireless needs to be explained

---

### Post by Frak on 2010-01-17
> **k3lt01 said:**
> A question for you? Are you personally charged anything to use Google? Just like your signature suggests just because it is free to use doesn't mean it is Open Source.
Some of their services, yes, but normal search, no.

---

### Post by Ordhaj on 2010-01-17
Questions:

1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?

Initial configuration including trouble-shooting internet connection (wireless or otherwise)

2. Do you believe a manual like this should be included in Lucid Lynx by default?

No, but put a link to it on the download site (which would work better because then they'd have it before they downloaded.

3. If it was to be included by default, do you think it should be on the desktop?

Yes.

4. Would you be interested in printing such a manual?

Yes, depending on size.

5. Do you think PDF is a good format, or would you prefer HTML or another format?

PDF would be the best format, with embedded fonts. That way everyone sees the same manual. No misunderstandings due to changes in display.

6. We are including a section on using the default applications. Which do you think should have the most detail?

Totem: it's the one that trips the user up the most due to codex to be downloaded and legal reasons.

7. Out of the following hardware categories, which one should have the most detail?

Wireless/Infa-Red

---

### Post by jzacsh on 2010-01-17
[B]
3. If it was to be included by default, do you think it should be on the desktop?
[/B]a symlink -- nothing is worse than a cluttered desktop[B]

5. Do you think PDF is a good format, or would you prefer HTML or another format?
[/B]
I really think it would be fairly disappointing to see more use of the clunky/nasty-ness that is PDF (IMO). I really think as linux users and welcomers we should be the _first_  people to show, by example, that a guide is just as use-able in HTML or another format.

-- As far as the issue, "maintenance of many formats" -- I thought this wasn't even an issue now-a-days.. aren't there formats that are super clean and easy to automate into other formats? eg. DocBook (*idk I've never even looked into it*) -- formats that you (as a user, even) just click "print pdf" or .. "show plain text", etc.??

-- also, as an advocate of command-line usability I think PDF would be the last thing I'd show a fellow user. I'd maybe show them an html doc (*in which I can display via `html2text` right to my own console, or the easy-to-use w3m, etc*). Anyway, without any more ranting -- I just think we, as a foss community, should be using the most extensible and open formats!
[B]

[/B]

---

### Post by Frak on 2010-01-17
> **jzacsh said:**
> -- also, as an advocate of command-line usability I think PDF would be the last thing I'd show a fellow user. I'd maybe show them an html doc (*in which I can display via `html2text` right to my own console, or the easy-to-use w3m, etc*). Anyway, without any more ranting -- I just think we, as a foss community, should be using the most extensible and open formats!

Well, if a person is in CLI, and is a newbie, they won't be looking at any docs through the CLI. They will boot into Windows or find another computer to search documentation on, which PDF is perfect because it can be viewed without the clutter of many files.

As for HTML vs. PDF for a format, PDF isn't open to interpretation as HTML is. PDF is always rendered one way. HTML is messy and open to interpretation based on the engine being used.

For the open format comment, and I don't want to say this again...

**[SIZE="5"]PDF is an open format[/SIZE]**.

---

### Post by wavery on 2010-01-17
#1 Printing through a Windows based network
#2 Yes
#3 Yes
#4 No
#5 PDF is fine
#6 Ubuntu One
#7 Disk drives

---

### Post by jzacsh on 2010-01-17
> **Frak said:**
> 
As for HTML vs. PDF for a format, PDF isn't open to interpretation as HTML is. PDF is always rendered one way. HTML is messy and open to interpretation based on the engine being used.

For the open format comment, and I don't want to say this again...

**[SIZE="5"]PDF is an open format[/SIZE]**.

How much interpretation? I really don't care that PDF is an open format, I'm honestly more concerned with: I create a document (especially one of this nature) with the purpose of conveying a message. My message is, at its lowest level, conveyed best with text. The fact that I can't read a PDF via command line because its mixed in with all kinds of other garbage is what dissapoints me.

_At least answer this_: Do you really feel that the interpretation difference between rendering engines is something that makes the manual less usable?

---

### Post by mariano_rcia on 2010-01-17
1#Guidelines about migrating stuff from MS Windows or Mac to Ubuntu-Linux.

---

### Post by Mornedhel on 2010-01-17
> **Frak said:**
> As for HTML vs. PDF for a format, PDF isn't open to interpretation as HTML is. PDF is always rendered one way. HTML is messy and open to interpretation based on the engine being used.

For the open format comment, and I don't want to say this again...

PDF is an open format.

PDF is, technically, an open format, that much is true. In fact, it's an ISO spec. It's been so for a year and a half, while it was proprietary for around 15 years before that, but let's gloss over this.

PDF is *not* "always rendered one way". PDF has many extensions that are not part of the ISO spec and that only Adobe fully implements. Even PDFs without extensions are not necessarily rendered like the author intended. Some PDF printers do not embed all fonts in the file to make it lighter and assume they're common enough that they'll be available everywhere. (They're generally reasonably common, but to get an exact render of what the thing should look like, you should *not* make such assumptions.)

Rendering the thing exactly is probably not the main focus anyway, since it's meant to be an online manual, not a printed book. Looking decent and professional is enough (and professional does not mean "fancy").

I dislike PDF for multiple other reasons, none of which are relevant to the discussion. I've made my point earlier on why I would prefer HTML.

---

### Post by freechelmi on 2010-01-17
Hi Just in case you don't know. A 300 pages book has been done in french by Didier roche & others , I guess there would be some work to share : 

[http://framabook.org/ubuntu.html](http://framabook.org/ubuntu.html)

---

### Post by Frak on 2010-01-17
> **jzacsh said:**
> _At least answer this_: Do you really feel that the interpretation difference between rendering engines is something that makes the manual less usable?

Yes.

---

### Post by Mornedhel on 2010-01-17
> **Frak said:**
> Yes.

Seriously ? You believe that because some versions of Internet Explorer interpret the padding attribute differently, the manual would be less usable ?

I've seen you around quite a bit, otherwise I'd just dismiss you as a troll at this point. Would you mind explaining your answer ?

---

### Post by Frak on 2010-01-17
> **Mornedhel said:**
> Seriously ? You believe that because some versions of Internet Explorer interpret the padding attribute differently, the manual would be less usable ?

I've seen you around quite a bit, otherwise I'd just dismiss you as a troll at this point. Would you mind explaining your answer ?
Port-a-bility. Not everyone has access to the internet everywhere they go, but it's pretty difficult to not have a PDF reader with you. Many applications on Windows install it as a part of the application, there are many PDF readers, and Ubuntu has one by default. Keeping one file is much better than keeping a slew of files.

Also, being a manual, it should be presented in book form that can be transported in a portable manner. There's nothing wrong with shipping updated revisions from time to time, but it should be something along the lines of a travelers guide that one can use without being strongly coupled to an access point.

---

### Post by humphreybc on 2010-01-17
> **k3lt01 said:**
> Forgive me if I am wrong here, but, I think you have really missed syklops point. The intent of the PDF format is against Open Source ideologies, whereas Linux (Ubuntu) is supposed to support Open Source ideologies. Therefore regardless if you want the Manual to be editable in its final format or not shouldn't the Manual support something that supports it parent product? 

I'll go further and say that a HTML wiki style manual could allow users to add comments to their own manual in addition to the information already there. This is a realistic option because you will never be able to write all conceivable information and what suits some may not be enough for others.

We realize that, but just as the Ubuntu Forums use a proprietary forum system, Ubuntu One is closed source and Jono Bacon runs a Mac to record his music, we must choose the appropriate format that will get the job done the best. Often at times open source just doesn't cut it.

We also would like the Manual to be cross-platform capable, so it can be read by people on Windows and Mac before they try Ubuntu.

"Well that sounds like HTML!" is what I hear you say. Yes, it does. The benefit of LaTeX is that we can export our manual into **many different formats** and we will be doing just that. We will probably create an HTML version, a docbook version, a plain text version etc etc.

For now the priority is getting the PDF output working as best as possible as this is what people want. It's flexible, it's familiar, it's printable and it works on practically every operating system - even mobile devices. It also provides support for hyperlinking and local bookmarking.

Also, please bear in mind that we have to have a version for every single language - so that would be a lot of outputting on our part. And remember that for printing, we would need to change the page size for each locale - for example, Americans use US Letter, most other countries use A4. 

These questions are just to get a rough idea of what the community would prefer.

Regards,
Benjamin

---

### Post by k3lt01 on 2010-01-17
> **Frak said:**
> As for HTML vs. PDF for a format, PDF isn't open to interpretation as HTML is. PDF is always rendered one way. HTML is messy and open to interpretation based on the engine being used.Not entirely correct, There are different versions of Acrobat Reader as the standard changed. Older versions of Acrobat Reader will not render documents produced in newer versions as they are intended. Try it out for yourself, you will get a notification saying it. Likewise HTML has changed BUT most of the problems with rendering webpages comes from the program(s) used to build the pages. MS Word is a shocker for it, it adds MS specific coding that is NOT part of any HTML standard. IE will read it while browsers such as FireFox wont.

> **Frak said:**
> For the open format comment, and I don't want to say this again...

**[SIZE="5"]PDF is an open format[/SIZE]**.Don't get angry just because someone doesn't agree with you, that's just non-productive.

> **humphreybc said:**
> "Well that sounds like HTML!" is what I hear you say.Please don't put words in my mouth.

> **humphreybc said:**
> For now the priority is getting the PDF output working as best as possible as this is what people want. It's flexible, it's familiar, it's printable and it works on practically every operating system - even mobile devices. It also provides support for hyperlinking and local bookmarking.So it seems I was correct, the choices were made before this thread was started.

> **humphreybc said:**
> Also, please bear in mind that we have to have a version for every single language - so that would be a lot of outputting on our part.That is impractical at this time don't you think?

I respect what you and your group are doing. I do question, and I am not alone in this, the wisdom of it though. Much of this information is already easily and freely available so it brings me back to the question of why are you trying to re-invent the wheel? I have read your wiki page, thank you for suggesting it, and from what I see there is no way you will be able to contain all of what people are saying within a 50 page book. The last Chapter of the Getting Started Guide for OOo is 17 pages and you are considering a swathe of programs not just 1.

---

### Post by Frak on 2010-01-17
> **k3lt01 said:**
> Don't get angry just because someone doesn't agree with you, that's just non-productive.

kelt01, take a deep breath, and let it out. I proved you wrong, let it go.

---

### Post by k3lt01 on 2010-01-17
> **Frak said:**
> kelt01, take a deep breath, and let it out. I proved you wrong, let it go.Whatever you say sir, I'll let you go on your merry way believing what you want.

---

### Post by Frak on 2010-01-17
> **k3lt01 said:**
> Whatever you say sir, I'll let you go on your merry way believing what you want.
We can keep going on all day, but you must accept it sometime.

---

### Post by k3lt01 on 2010-01-17
> **Frak said:**
> We can keep going on all day, but you must accept it sometime.I accept that since July 2008 (only 18 months) PDF as a format has been so called Open Source. Prior to that it was Closed Source, owned and modified solely by Adobe systems.

[http://en.wikipedia.org/wiki/Portable_Document_Format](http://en.wikipedia.org/wiki/Portable_Document_Format)

Like I said don't get angry just because some people disagree with you. Now if you don't mind do me a favour and settle yourself down before you tell others to.

---

### Post by Mornedhel on 2010-01-18
> **Frak said:**
> Port-a-bility. Not everyone has access to the internet everywhere they go, but it's pretty difficult to not have a PDF reader with you. Many applications on Windows install it as a part of the application, there are many PDF readers, and Ubuntu has one by default. Keeping one file is much better than keeping a slew of files.

Also, being a manual, it should be presented in book form that can be transported in a portable manner. There's nothing wrong with shipping updated revisions from time to time, but it should be something along the lines of a travelers guide that one can use without being strongly coupled to an access point.

I don't think keeping "a slew of files" is that prohibitive. All you need to do is store the manual in /usr/doc/somewhere, and add a link to the index wherever you want (desktop, examples, Places menu, whatever). The user never need see the actual folder with the dozen HTML files in it. And there are more systems with a web browser installed out of the box than there are with a PDF reader, although I will agree that the PDF reader is usually one of the first things a user will install.

I never imagined that it should be stored on the Internet, and I don't think any proponent of HTML did either.

We've had plenty of manuals that were not presented in book form, by the way. Take a look at all the Info manuals and the various online HTML documentations. Works fine.

Anyway, as another poster said, this discussion is pretty much moot since there the primary version *will* be PDF anyway.

---

### Post by Scunnered on 2010-01-18
2. yes   I would also suggest that a link to it be available on the Ubuntu home page so new adopters can see what they are getting into.  This might better prepare individuals. 
3. yes
4. yes
5. yes

6. Open Office &#8211; far too much involved to offer within documentation &#8211; guide to OOo documentation / forum.
Empathy
Evolution
Ubuntu One

7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning &#8211; start with the advice of checking that printer will work with Linux. A lot of printing problems revolve around this.

Wireless/Infrared &#8211; Have this very clearly set out.  Firstly ensure that it can be immediately found within the documentation.  This was my first problem with Ubuntu and I would expect that others have this experience despite the improvements on connectivity since 8.04.  Highlight need to clearly know what wireless card is in use as a lot of problems seem to revolve around this.  

**Just to stress the point on Wireless I could not see any reference to it in the table of contents**

---

### Post by humphreybc on 2010-01-18
I'd just like to remind everyone to keep this thread on topic, please.

---

### Post by bvanaerde on 2010-01-18
> **perspectoff said:**
> I have always liked Ubuntuguide.org (at [http://ubuntuguide.org](http://ubuntuguide.org))...
Why re-invent the wheel over and over again?

This is what I was thinking too.
Having one central place for all the manuals/howto's makes it a bit easier for beginners to search for solutions. Maybe working together with those guys from ubuntuguide will give a better and faster result?

My answers:
1. Partitioning guide when installing Ubuntu
2. Yes. Maybe a bookmark to the online manual will suffice
3. No
4. No
5. HTML
6. Empathy
7. External devices

---

### Post by kamokow on 2010-01-18
1) I cant think of anything in particular. Possibly a very basic driver guide so people can make Ubuntu, well, work.
2) Maybe, I wouldnt really want it. A good idea would be to put an option in the installer, for if you would like the guide. (just my opinion). Or you could make a browser bookmark for it like the above poster suggested.
3) No opinion.
4) Not personally.
5) PDF or HTML is fine in my opinion.
6) OpenOffice.org, because most new users were probably previously using MS Office.
7) Display and sound seem to be the problems most new users experience first. So probably those.

Just my thoughts.

---

### Post by alegallo on 2010-01-18
1. Post-install configuration (drivers, codecs)

2. Yes, at least a basic one (well, there IS a basic one already!)

3. In the menu it would be OK, under resources.

4. Not really, if I can read it on my desktop. Parts of it may be interesting on paper.

5. Both have pros and cons: HTML, links are useful, but you get lost quite easily. PDF is book-like, easy to be read start-to-end, much more difficult to browse.

6. Open Office, Firefox

7. Display, Disk Drives


Thank you for using your time in finding out what we (may) need ;)

---

### Post by d80zoom on 2010-01-18
1. Specific Hardware Guides: Wireless, Video, Disk Partitioning.

2. Yes, it should be.

3. Yes, in the “Examples” folder, with all the other documents.

4. I would print the pages that I need to help during installation. Partition and information on Wireless set up, and Video card configuration.

5. I would prefer a PDF format.

6. Ubuntu One is the newest application which has the least amount of information available.

7. Out of the following hardware categories, which one should have the most detail?

I would like to see separate chapters in detail about these items:
Printing/Scanning: Use USB Cable vs. Parallel cable.
Display: how to use ndis wrapper in detail.
Disk Drives: partition options.
Wireless/Infrared detailed settings for internet access.

---

### Post by k3lt01 on 2010-01-19
It seems people are totally misunderstanding simple things like

**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?** 

Tell me what is Ubuntu specific about installing from tar? or partitioning? or the myriad of other suggestions that have been made? Ubuntu is a Debian system, Debian is a Linux OS. There is very little until Karmic was released that can be called Ubuntu specific that a noob would need explaining to differentiate Ubuntu from Debian or other Linux systems.

---

### Post by ianp5a on 2010-01-19
1. Ubuntu-specific thing? **The GUI solution** to each problem. This is for **beginners**!
2. **Yes**. included in Lucid Lynx by default.
3. 0n the desktop? **No**. The **Help button** is the right place. It could get deleted or lost among other junk on the desktop.
4. Printing? **No. A waste.**.
5. **HTML** is preferred. 
-  Quicker to load an HTML page than waiting for an entire PDF to load
-  Bookmarking, gestures and more, in my familiar browser environment.
-  Identical version on-line.
-  Printing is *possible* with either
  
> **humphreybc said:**
> The Ubuntu Manual Project. It is a **complete beginners manual** for Ubuntu

**Excellent initiative! **This is what Linux/Ubuntu really needs to broaden the acceptance. I find Ubuntu good. The only problem is getting help on the forums. It's all too techy!

Please make sure the ***easy GUI way*** to do something is included and prominent.  All too often the enthusiasts on the forums only know command line ways to do things that can be easily done with a GUI. This puts a lot of people off Linux.

---

### Post by chuina on 2010-01-19
Each time i log in this forum I see more than one unsloved 
wired or wireless internet connection problem.

So there should be more info about "How to connect to the 
Internet using wired+wireless method"

Thanks.

---

### Post by echoforever on 2010-01-19
[SIZE="1"]1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?

[COLOR="Blue"]Comparison of Ubuntu flavours available or a pointer to an existing comparison table. 
Things to do after an install/upgrade.
As a newbie, after my first install, I didn't know about restricted extras until I went through websites describing 'Top N things to do after an installation.'
This is not Ubuntu specific, but it is among first few things I would do after installing Ubuntu. A guide for connecting other machines (ex: a windows laptop) in a LAN; sharing internet connection with Ubuntu machine acting as a router to other machines.
How to rebuild a live CD out of my installation.[/COLOR]

2. Do you believe a manual like this should be included in Lucid Lynx by default?
[COLOR="blue"]Yes.[/COLOR]

3. If it was to be included by default, do you think it should be on the desktop?
[COLOR="blue"]Yes.[/COLOR]

4. Would you be interested in printing such a manual?
[COLOR="blue"]No[/COLOR]

5. Do you think PDF is a good format, or would you prefer HTML or another format?
[COLOR="blue"]PDF for offline reading. HTML for online version.[/COLOR]

6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox
Evolution
Totem
Ubuntu One

[COLOR="blue"]No preference[/COLOR]

7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Display
External devices
Webcams
Sound
Disk Drives
Wireless/Infrared

[COLOR="blue"]Wired/wireless networking. I am looking for tools and controls available. Also options available other than those that come with default installation. I had problems setting up PPPOE connection after my first installation. I was fiddling with Network Manager instead of using pppoeconf, which was helpful in my case.[/COLOR][/SIZE]

---

### Post by BrandonBan6 on 2010-01-19
[B]1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be? 
[COLOR="Navy"]Introduction to the community, no matter how amazing documentation you create, people are always going to want to talk to other people for instant help. So much so, that they will pay for support with Dell, Microsoft, etc. Introduce them to the community and the support options available.[/COLOR] 

2. Do you believe a manual like this should be included in Lucid Lynx by default? 
[COLOR="Navy"]I think it should be bundled with the Help features, i don't want my distro of choice becoming too much more cluttered. [/COLOR]

3. If it was to be included by default, do you think it should be on the desktop?[COLOR="Navy"] No[/COLOR]

4. Would you be interested in printing such a manual?[COLOR="Navy"] No[/COLOR]

5. Do you think PDF is a good format, or would you prefer HTML or another format? [COLOR="Navy"]I think HTML, web based as things seem to be going anyway. Maybe a default tab in Firefox? [/COLOR]

6. We are including a section on using the default applications. Which do you think should have the most detail? [COLOR="Navy"]- None really, I like linux/ubuntu because i can customize for instance I've listed replacements for the below apps I automatically install: 
[/COLOR]
Rhythmbox - [COLOR="Navy"]VLC or Banshee[/COLOR]
F-Spot - [COLOR="Navy"]Gimp and Picasa[/COLOR]
Open Office 
Tomboy
Empathy - [COLOR="Navy"]Pidgin and Skype[/COLOR]
Firefox
Evolution - [COLOR="Navy"]Thunderbird[/COLOR]
Totem - [COLOR="Navy"]VLC[/COLOR]
Ubuntu One - [COLOR="Navy"]Dropbox (unless ubuntu one gets multi-platform support)[/COLOR]

7. Out of the following hardware categories, which one should have the most detail? -[COLOR="Navy"] DISPLAY!!! Why is it still a nightmare to get ATI drivers working the way they are supposed (i know, different post). [/COLOR]

Printing/Scanning
Display 
External devices
Webcams
Sound
Disk Drives
Wireless/Infrared[/B]

---

### Post by lukjad on 2010-01-19
**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**

I'm not to clear what Ubuntu=specific means, but I would like to see something like shortcuts for Nautilus/GNOME.

**2. Do you believe a manual like this should be included in Lucid Lynx by default?**

Yes. I think that it would be very helpful to have this kind of a guide there at least on the off chance that something goes wrong causing you not to be able to connect to the Internet. 

**3. If it was to be included by default, do you think it should be on the desktop?**

That's a hard question. My feeling is that it should be on the taskbar on a clean install possibly labeled "Help". I would put it right next to the System drop down menu, perhaps breaking it up into major sections with a "Search" feature.

**4. Would you be interested in printing such a manual?**

I don't think my printer could handle it, so no. :)

**5. Do you think PDF is a good format, or would you prefer HTML or another format?**

PDF is not a good format, in fact I think PDF is a fairly lousy format. It's nice for presentations and good if you want to just send someone something in such a fashion that they can't edit it. This is only good when you have complex formatting. Hopefully the guide won't need this. Another thing I have against PDFs is that they are a pain to convert, edit, or to enlarge. I would say at least HTML and possibly a PDF version of it to make it "portable". 

**6. We are including a section on using the default applications. Which do you think should have the most detail?**

I would say a a guide on Synaptic and how to use it, A quick Tutorial on Rhythmbox, and where they can find the terminal. Also perhaps something showing them the structure of where everything is. 

From the list:

Rhythmbox
F-Spot

**7. Out of the following hardware categories, which one should have the most detail?**

Definitely these two in this order: 

Sound
Printing/Scanning

---

### Post by skarychinezeguie on 2010-01-19
the very first thing i would want included is what i do every time i install ubuntu. after all the updates, drivers and third party hardware drivers are installed i immediately install compiz, and cairo dock (excluding the clock) and set it as a startup item. also i tweak the crap out of compiz and get everything looking all pretty. There should be a distro that includes this stuff by default with a wizard because the average windows switcher is NOT gonna know how to set all that up.

once you unlock the full potential for ubuntu to look and feel more like a mix of windows and OS X ubuntu will gain more recognition. Ease of use. I work at an Apple call center. for every awesome caller i get 10 retards who can't figure out how to drag an icon to their dashboard after hearing "click your mouse on the icon, but don't let go. keep that click held down and move your mouse around and the icon will stay attached to it. then once you move it to the dashboard and let go, the icon will then be attached to the dashboard."

it doesn't get much clearer, but i'll be darned if they don't keep telling me nothing's happening. get off my phone sir.

---

### Post by knurledflanges on 2010-01-20
1. A clear explanation of GRUB, wubi, how to set up dual-booting, and what to do if things go wrong. Especially an explanation of what wubi does and how it's more or less out of a newbie's depth to make their wubi installation the only OS on their computer if that's what they decide they want to do.

2. If it suceeeds at being at least reasonably comprehensive about the kind of stuff that newbies need to know, then yes. If it's kind of cobbled together, turns something of a blind eye to the kind of actual difficulties newbies face, and can't get away from assuming knowledge when trying to explain the more complex stuff, then no.

3. If it was really good, sure.

4. No

5. Anything that's small, easily searchable, and doesn't put potentially unfamiliar interface controls in your face, so probably not PDF.

6. Since this a list of apps that are there to be accessible and useful to the stereotypical beginner/casual user, and they're mostly all pretty intuitive apps and/or have decent documentation of their own that's fully applicable to the Ubuntu version, I would say the answer is Totem if it meant giving beginners some assistance with getting the codecs needed to make their stuff play in it.

7. Wireless. If you have an internet connection then at least the information you need for the other stuff is available to you. No connectivity is when you're really stranded and need the help of a locally-stored manual the most.

---

### Post by longtom on 2010-01-20
To the OP.  I have e-mailed you in connection with your request some days ago.  As you didn't react can we assume your team is complete?

Good luck!

---

### Post by delphiexile on 2010-01-20
**1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?**
Showing people how to solve their problems , what should they do and what they shouldn't do in order to keep their system safe and clean optimized.

Most of people suffers from apt problems , the manual should better take in charge this kind of problems very well , as instance you can include how to solve major problems.

How to install drivers when jockey-gtk doesn't recognize some hardware , and how they can find a suitable drive.

Sound and video problems esspecialy with skype and cheese and some media players are frequent problems.

**2. Do you believe a manual like this should be included in Lucid Lynx by default?**

Yes of course , it would be great.

**3. If it was to be included by default, do you think it should be on the desktop?**
No , it should not appear on desktop , but in the top panel , you must include a notice in the first boot about the manual.

**4. Would you be interested in printing such a manual?**
Me I'm not intrested , the manual should be used on the work session , but I believe that some pages should printed when it concerns how to solve problem related to GRUB and some problems of boot , the manual should make a notice on the page which should be printed in case of these problems , the help must be provided when the user can't access to system , printing these pages is a good solution .

**5. Do you think PDF is a good format, or would you prefer HTML or another format?**
No , I do not think that PDF is a suitable format for theis manual , I believe it should be provided as a part of Ubuntu like the help center , but I believe to provide a PDF version so as to be able to read where working outside Ubuntu.

**6. We are including a section on using the default applications. Which do you think should have the most detail?**
Rhythmbox
F-Spot
Open Office
Tomboy
Empathy
Firefox
Evolution
Totem
Ubuntu One
+
Hardware testing: This utility is good , I hope you can add a function to test webcams.

**7. Out of the following hardware categories, which one should have the most detail?**
1- Display: The most important.
2- External devices: Like satelite cards .
3- Webcams
4- Sound
5- Printing/Scanning (more support to canon and hp printers)
6- Wireless/Infrared
7- Disk Drives


=====================================

As you see I mentioned some improvements for some parts of the system , these should be treated as essential adds to the system.

I hope we can translate this manual very soon to other languages.

---

### Post by Mornedhel on 2010-01-20
What format does Yelp use, by the way ?

---

### Post by teward on 2010-01-20
[U]**NOTE: Bold font indicates my answers/choices.  Note that I didn't answer a few questions :P**

Questions:[/U]

2. Do you believe a manual like this should be included in Lucid Lynx by default?
**Indeed**

3. If it was to be included by default, do you think it should be on the desktop?
**No, probably linked somewhere on the system, as a system file that anyone can read and then a sym-link be put to it in the user's home folder.**

5. Do you think PDF is a good format, or would you prefer HTML or another format?
**PDF isn't a bad format, although sometimes its a pain.  I'd rather see HTML, as I do most stuff through internet stuff.**

6. We are including a section on using the default applications. Which do you think should have the most detail?
**(Bold indicates my choices)**
Rhythmbox
** F-Spot**
** Open Office**
Tomboy
Empathy
** Firefox**
Evolution
Totem
Ubuntu One

7. Out of the following hardware categories, which one should have the most detail?
**(Bold indicates my answers)**
Printing/Scanning
Display
External devices
**Webcams**
Sound
**Disk Drives**
**Wireless/Infrared**

---

### Post by clydehunter on 2010-01-20
I used Ubuntu 9.04 some but I liked Ubuntu 9.10 better.
But with  9.04 I could change the time to select XP Pro or 9.04. I did not see that option in 9.10 so I eventually stopped using it.

I would probably use Ubuntu as my only OS if I could use some of my XP downloads and if I could use Google Chrome instead of Firefox as my browser. I do not like Firefox.

---

### Post by suzenon on 2010-01-20
1. setting up and configuring personal firewall
2. 3. sorry , don't know what it is
4. don't think so
5. both pdf and html are good, don't really care as long as it's easy to find/navigate
6. OO, Totem...
7. sound and external devices

---

### Post by lightningfox on 2010-01-20
Here are my answers.

I didn't answer question 1 because I couldn't think of anything.


2. yes

3. yes

4. yes

5. PDF

6. Open Office

7. Wireless/Infrared

---

### Post by jARLAXL on 2010-01-20
> **humphreybc said:**
> [B]1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?Sound configuration (pulseaudio, dev chooser,control, tips). 2nd to that tips about installing/removing software and generally things that are very different than a M$ system

> **humphreybc said:**
> 2. Do you believe a manual like this should be included in Lucid Lynx by default?YES> **humphreybc said:**
> 3. If it was to be included by default, do you think it should be on the desktop?YES

> **humphreybc said:**
> 4. Would you be interested in printing such a manual?Not really

> **humphreybc said:**
> 5. Do you think PDF is a good format, or would you prefer HTML or another format?YES, openoffice would be equally good

> **humphreybc said:**
> 6. We are including a section on using the default applications. Which do you think should have the most detail?
1.Empathy
2.F-Spot
3.Open Office


> **humphreybc said:**
> 7. Out of the following hardware categories, which one should have the most detail?
1.Sound
2.External devices
3.Wireless/Infrared
4.Display[/B]

---

### Post by darolu on 2010-01-21
1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?
I would focus on easy-to-follow instructions to install applications, and a "tutorial" to teach new comers where to look at when not finding what they need in the manual; I would include a GRUB section to help new users to fix it when they install the other -pervasive- OS.

2. Do you believe a manual like this should be included in Lucid Lynx by default?
Depends on how big this manual is going to be; if it is considerably large, it shouldn't be included but linked either to a web based version (say html) or to the software centre.

3. If it was to be included by default, do you think it should be on the desktop?
Absolutely NOT, one of the things that made me switch to Ubuntu (I used to use Slackware and openSuSE) was the clean desktop look, no icons on the desktop is characteristic of Ubuntu and should not change.

4. Would you be interested in printing such a manual?
Not at all.

5. Do you think PDF is a good format, or would you prefer HTML or another format?
Yes, PDF is a good format.
HTML is more universal though, so I would use HTML.

6. We are including a section on using the default applications. Which do you think should have the most detail?

F-Spot
Tomboy
Empathy

This applications are, in my opinion, the ones that probably are unknown to new users; they are quite different from their privative analogs, applications like Mozilla Firefox or Openoffice.org are the exact same applications on all platforms so there is no need for detailed guides since chances the new comers are familiarized with them are large, applications like Evolution or Rhythmbox are very much alike than their privative analogs and/or other free/open source options and new users shouldn't experience difficulties when using them.

7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Wireless/Infrared

When I first started using Linux based systems, printers were quite difficult to configure and information about specific printers was hard to find (specially since I didn't know where to look and back then there was no google yet), not long ago I had problems configuring a PCI Parallel card, so a detailed guide about printers and scanners would be nice.
I haven't had problems with my wireless devices but I've read a lot of people with issues in this matter, since connectivity is extremely important; detailed wireless section (and networks in general) is a priority in my opinion.

---

### Post by TariBuntu on 2010-01-21
1. If you could choose one Ubuntu-specific thing to be included in an Ubuntu Manual, what would it be?

- A hardware troubleshooting guide (perhaps based on the most frequent forum searches), e.g. sound/video issues.

2. Do you believe a manual like this should be included in Lucid Lynx by default?

- Definitely.

3. If it was to be included by default, do you think it should be on the desktop?

- On the Live CD, perhaps. The installed version should have it in the Menus.

4. Would you be interested in printing such a manual?

- No, too lengthy (hopefully). Browsing the HTML would suffice.

5. Do you think PDF is a good format, or would you prefer HTML or another format?

- HTML is preferred if you want to keep it cross-platform.

6. We are including a section on using the default applications. Which do you think should have the most detail?

Rhythmbox (using Banshee)
F-Spot (using Gimp)
Open Office +
Tomboy 
Empathy
Firefox
Evolution
Totem (using smplayer)
Ubuntu One

7. Out of the following hardware categories, which one should have the most detail?

Printing/Scanning
Display
External devices
Webcams
Sound +
Disk Drives
Wireless/Infrared

---

### Post by blazemore on 2010-01-21
> **clydehunter said:**
> I used Ubuntu 9.04 some but I liked Ubuntu 9.10 better.
But with  9.04 I could change the time to select XP Pro or 9.04. I did not see that option in 9.10 so I eventually stopped using it.

I would probably use Ubuntu as my only OS if I could use some of my XP downloads and if I could use Google Chrome instead of Firefox as my browser. I do not like Firefox.

I'm PMing you as well, because it's unlikely you'll read this thread again.

You can downgrade Grub to the version used in Jaunty and below, without running into any problems.
There's a guide here: [http://brettshaffer.com/blog/linux/downgrade-grub-2/](http://brettshaffer.com/blog/linux/downgrade-grub-2/)

Google Chrome runs on Linux ([http://chrome.google.com](http://chrome.google.com)) and they provide a deb package for Ubuntu

---

### Post by flygin on 2010-01-21
1. (how to get rid of windows thinking.)

2. n/a

3. YES, help should be easy available from anywhere.

4. Just in exceptional cases, if you can not check it on-screen. (installation help with command line options)

5. html preferred. Bookmarks are important and click-able links essential.

6. An overview of different apps for each sector.

7. Introduction to the command line. 
If you can get an introduction about how to use the command line, an entire universe will open. This introduction will stay almost forever, the command line will not change over the next decades, especially the most basic concepts.
This tutorial is not the center of the manual, for sure, but it would be an extremely helpful extension!
The console does not have to be complicated. My app in progress
[http://thi-scripts.sourceforge.net](http://thi-scripts.sourceforge.net)
can make the console drastically easier and prevents the usual switching between website and console to copy/paste the commands. 

I definitely do not believe that we need a GUI for every little problem out there. With little guidance (see thi-scripts) the command line becomes easy. However, you need some very basic concepts to understand (like do not use 'sudo rm -rf /*')

---

### Post by sbjaved on 2010-01-21
1. The various ways to get help in case of a problem (forums, irc, google, locos) and information that Ubuntu is NOT Windows and it will not run windows programs but has good substitutes for commonly used apps

2. YES!

3. No, an entry in the 'System' menu would seem better

4. It would depend on the size of the manual

5. PDF would be okay since Ubuntu has native support

6. Firefox and Empathy, then OpenOffice

7. Display, Sound and Disk Drives (since these are the major hurdles users face)

---

### Post by humphreybc on 2010-01-22
Thankyou to everyone for answering the questions. They've been a great help :)

If you are interested in the progress of the manual, then you can join our [Facebook page]("http://www.facebook.com/pages/The-Ubuntu-Manual/266794861575?ref=nf") or [follow us on Twitter.]("http://twitter.com/TheUbuntuManual")

---

### Post by ubuntu-geek on 2010-01-22
Closed per request of thread starter.

---

