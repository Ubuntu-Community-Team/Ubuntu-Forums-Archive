---
title: "Ubuntu-ce Jaunty"
date: 2009-06-21
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-06-21
I want to continue Ubuntu CE developement, and I have contacted Jereme and he agreed to support it. In the mean time, please let me know what should be in ubuntu-ce.

So far what I have in mind is:

1. Dansguardian, firehol, tinyproxy, with dansguardian gui as configuration and management tools.
2. e-sword-installer.
3. opensong

Previously it has bibletime, gnomesword, bible memorizer, and gnucash.Please let me know which ones is important to you so that I could include it in the ubuntu-ce package.

DK

---

### Post by jimv on 2009-06-22
It might help to stop for a moment and ask, "Is it necessary to have a whole distro just to serve an incredible small niche?"

You might just consider putting together a repository with a meta-package that will install all of those things that you just mentioned, instead of creating a whole new distro.  You'll save a lot of time and bandwidth that way.

---

### Post by david_kt on 2009-06-22
> **jimv said:**
> It might help to stop for a moment and ask, "Is it necessary to have a whole distro just to serve an incredible small niche?"

You might just consider putting together a repository with a meta-package that will install all of those things that you just mentioned, instead of creating a whole new distro.  You'll save a lot of time and bandwidth that way.

Good question. So far I have been thinking that is the case, until I realize I could not find live cd with internet filtering by default, or at least difficult to find.

Country like Indonesia  (250 million population) and Vietnam ( 85 million population) requires porn filtering by law! So, if that law is enforced, that would be a lot of demand for Ubuntu CE distro :D .


Having said that, you could try to apt-get install ubuntu-ce, I have put up a trial repository. But this is just trial. What you have to do is:

1. Add below repository:

deb [http://thuygiang.homelinux.com/Ubuntu_CE](http://thuygiang.homelinux.com/Ubuntu_CE) binary/

2. Run sudo apt-get update and then sudo apt-get install ubuntu-ce


DK
EDIT: I forgot to mention, China ( more than 1 billion population) also requires porn filtering by law as well.

---

### Post by jimv on 2009-06-22
But is the filtering required on the OS or by the ISP?  Seems like it would be ISP.

---

### Post by david_kt on 2009-06-22
> **jimv said:**
> But is the filtering required on the OS or by the ISP?  Seems like it would be ISP.

The law is targeted at individual, not companies. Offcourse the implementation/enforcement is difficult so far. There have been cases internet cafe owner (not the ISP) was found guilty for not putting porn filter.

DK

---

### Post by jonathonblake on 2009-06-24
> **jimv said:**
> It might help to stop for a moment and ask, "Is it necessary to have a whole distro

A Live CD/DVD will have to be constructed, so that it can be demonstrated on the systems that potential users currently utilize.

From a strictly marketing POV, a single CD/DVD image is essential for livery and  brand awareness. Along with that, I'd also suggest a name  change --- if Canonical hasn't yet ordered one. 

> just to serve an incredible small niche?"

I'm not convinced that it is "an incredible small niche". 

One **major** issue is that there has been virtually no marketing of Ubuntu Christian Edition.

>  putting together a repository with a meta-package

A repository for the individual packages, and a metapackage that installs everything works for people that allready have installed Ubuntu. 

Metapackages dos not work for product demonstrations. Nor do they work for organizations that encourage their members to migrate to Ubuntu Christian Edition.

jonathon

---

### Post by mhancoc7 on 2009-06-25
> **jonathonblake said:**
> A Live CD/DVD will have to be constructed, so that it can be demonstrated on the systems that potential users currently utilize.

From a strictly marketing POV, a single CD/DVD image is essential for livery and  brand awareness. Along with that, I'd also suggest a name  change --- if Canonical hasn't yet ordered one. 



I'm not convinced that it is "an incredible small niche". 

One **major** issue is that there has been virtually no marketing of Ubuntu Christian Edition.



A repository for the individual packages, and a metapackage that installs everything works for people that allready have installed Ubuntu. 

Metapackages dos not work for product demonstrations. Nor do they work for organizations that encourage their members to migrate to Ubuntu Christian Edition.

jonathon


I agree. That is why I always wanted the distro to be available for download so that users could have the entire distro ready to go. I also agree that this is not a small niche at all. It is still an untapped niche in my opinion.

Yes, there really has not been any marketing for Ubuntu CE since that costs money and this project has always been 100% free and will of course always be.

I am hoping that david_kt and anyone else who is interested can help to continue the development of Ubuntu CE no matter what it becomes a live cd or a meta package.

I am curious, why do you feel that there should be a name change? What name do you propose?

Jereme

---

### Post by adzik on 2009-06-25
Just as a side note, has there been any consideration to work with Ichtux? As it's based on Kubuntu, could this not be a joint effort?
I don't know the full spectrum of the differentiating factors.
Otherwise, I am glad to hear someone willing to take up UCE and continue.
Do you need help? I am not a developer, but maybe I can assist with something.

---

### Post by mhancoc7 on 2009-06-25
> **adzik said:**
> Just as a side note, has there been any consideration to work with Ichtux? As it's based on Kubuntu, could this not be a joint effort?
I don't know the full spectrum of the differentiating factors.
Otherwise, I am glad to hear someone willing to take up UCE and continue.
Do you need help? I am not a developer, but maybe I can assist with something.

Well, early on there was some issues between me and the developer of Ichthux. There was a major disagreement on what was included in Ubuntu CE. Since we included some closed-source items like e-Sword that was a major issue with the Ichthux folks.

I am not opposed to a collaboration, however, I do not want Ubuntu CE to lose its "identity".

The only reason that I am not continuing development as usual is do to time constraints. I plan to let david_kt and others continue the development of the distro and I will continue to host the files and website. If this does not work out then I will eventually have the time to restart the method of development that I have been imploying for several years now.

Thanks for you offer to help. You should probably contact david_kt since he is heading up the current development push.

Jereme

---

### Post by david_kt on 2009-06-25
> **mhancoc7 said:**
> Well, early on there was some issues between me and the developer of Ichthux. There was a major disagreement on what was included in Ubuntu CE. Since we included some closed-source items like e-Sword that was a major issue with the Ichthux folks.

I am not opposed to a collaboration, however, I do not want Ubuntu CE to lose its "identity".


I guess the Ichthux developer spoke on behalf of ubuntu developer, i.e. to avoid closed-source items. But if only installer packed as debian, I think he would not have any concern as the installer itself is opensource, but bearing LGPL license, not GPL. 

I have completed packaging daily bible verse and bible trivia. Combine with dansguardian gui should be enough for the core of ubuntu CE. And as this three packages is based on component already available in standard ubuntu (Perl dan Zenity), it should be easy to maintain if we upgrade to later release of ubuntu.

To make it ease to maintain, meta package with repository is very good as we could upgrade any package anytime and user would automatically. After that, we just need to create live cd and it is also very easy to build as well as we just need to remove unnecessary package, and then add ubuntu-ce meta package.

I am still struggling with postinst. Without this method, we would need to edit a little bit the configuration file of dansguardian, tinyproxy, and firehol, Not so much work, just to copy these 3 files. But if the postinst script works, the live cd could be made even easier. And user upgrading from ubuntu also would be able to sudo apt-get install ubuntu-ce without any further instruction. 

The main problem for me now is the theme and spash screed, I have not even study how to make the theme splash yet. I have made trial live CD though, using ubuntu CE 4 wallpaper and boot screen. But splash from ubuntu CE 4 did not work in Jaunty.

DK

---

### Post by david_kt on 2009-06-25
> **adzik said:**
> Just as a side note, has there been any consideration to work with Ichtux? As it's based on Kubuntu, could this not be a joint effort?
I don't know the full spectrum of the differentiating factors.
Otherwise, I am glad to hear someone willing to take up UCE and continue.
Do you need help? I am not a developer, but maybe I can assist with something.

May be we could borrow some artwork from ichtux. But to keep the size small, I would prefer to avoid anything KDE. And so far the three packages I made only work on gnome. Of course it could easily ported to KDE, it is only I have no time to do it yet.

What you could help is give your wish, what do you want to see in ubuntu CE. Users' need is the most important aspect for me. That should be the direction of the development.

DK

---

### Post by adzik on 2009-06-25
There are certainly things I have always considered - for myself/family - in a Christian OS environment. 
My perspectives may be a little business centric as that is my strength, so bear with me. 
I have had the privilege of dealing a little on a business (suggestive/feedback) level with a certain denomination's head office, and some things have become clearer as to what a christian user and organization would appreciate, possibly even use within a business environment.
So here are some of my thoughts, as well as some feedback I have received from many younger, practicing Christians, and people in the office. This may overlap some elements already existing or planned. 

- modern bible access / translations easily available (pay option OK)
- greek strong's concordance / applications - or easy access to one
- bible reader/speech (this was a big item)
- access to Bible on CD/MP3 etc - 90% of those I know don't know where to find, or look for this. 
- christian music / store integration within music manager software
- christian books / materials at hand / online (in this regard, the feedback seemed to be a series of methods to easily have ebook access and applications, if any, to import/purchase for reading or sampling books off of the desktop)
- secure/encryption (for average user) for private files where sensitive information exists, although Ubuntu does have facilities for these in a way.
- keeping in tandem (of course!) with an awesome desktop/workstation experience that Ubuntu is already.

There are many more items that would be great to see, but as of this writing, I know of no possible applications or methods to make them happen. 
Prayer is a big part of any practicing Christian's life, and to have easy access, methods, prayer lists, requests and correspondence on a p2p ad-hoc level seems rudimentary at best.  
Ultimately, an environment that is not catered exclusively to, but incorporates a proper, non-tacky, online and immediately accessible way of prayer/request/reply/acknowledgment/delivery and so forth would seem like a great tool, but maybe a lofty goal. Too bad I am no developer. Makes me very aware of the sacrifice and efforts of anyone that does create such applications and tools in their spare time.

If there is anything more I can contribute, I will gladly do it.
Also, anything from a business/discovery angle I would be willing to help out with too, if it were ever needed.
And if you ever need some translation into Polish, I'm in.

Thanks for taking up UCE.  I believe the Christian community needs this greatly, but doesn't fully realise it.

---

### Post by david_kt on 2009-06-25
Thank you for your feedback Adzik, below are my comment.

> - modern bible access / translations easily available (pay option OK)
- greek strong's concordance / applications - or easy access to one

I thought e-Sword could fulfill it? Otherwise, give us some link to those softwares.
 
> - bible reader/speech (this was a big item)

Not sure about this one. Is it mp3 bible?

> - access to Bible on CD/MP3 etc - 90% of those I know don't know where to find, or look for this. 
- christian books / materials at hand / online (in this regard, the feedback seemed to be a series of methods to easily have ebook access and applications, if any, to import/purchase for reading or sampling books off of the desktop)

We could create standard bookmark so that the new ubuntu ce would have necessary bookmark ready for user. May be below could be those links you want to add:
[http://kjvmp3.com/kjvmp3.html](http://kjvmp3.com/kjvmp3.html)
[http://www.audiotreasure.com/](http://www.audiotreasure.com/)
[http://www.mp3bible.org/kjv/index.cfm](http://www.mp3bible.org/kjv/index.cfm)
[http://sigm.net/home](http://sigm.net/home)

or let us know what links you have in mind.

> 
- christian music / store integration within music manager software

I would have to search for this feature.

> - secure/encryption (for average user) for private files where sensitive information exists, although Ubuntu does have facilities for these in a way.

I think it could be done by making a script so that user could encrypt, open and lock using right click. The manual method is below:
[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)
[http://www.ubuntugeek.com/how-to-create-a-private-encrypted-folder-on-ubuntu-810-intrepid.html](http://www.ubuntugeek.com/how-to-create-a-private-encrypted-folder-on-ubuntu-810-intrepid.html) 

> 
Prayer is a big part of any practicing Christian's life, and to have easy access, methods, prayer lists, requests and correspondence on a p2p ad-hoc level seems rudimentary at best.

Ultimately, an environment that is not catered exclusively to, but incorporates a proper, non-tacky, online and immediately accessible way of prayer/request/reply/acknowledgment/delivery and so forth would seem like a great tool, but maybe a lofty goal. Too bad I am no developer. Makes me very aware of the sacrifice and efforts of anyone that does create such applications and tools in their spare time.


May be a bookmark to setup free forum?

[http://www.freeforums.org/](http://www.freeforums.org/)

Or option to host forum? But to host a forum require a bit of work on user. Below there is free software to setup forum:

[http://www.simplemachines.org/](http://www.simplemachines.org/)

DK

---

### Post by adzik on 2009-06-26
> **david_kt said:**
> I thought e-Sword could fulfill it? Otherwise, give us some link to those softwares.
 
You're right, it does. This is certainly already included. 
Additional ones: 
[http://www.xiphos.org]("http://www.xiphos.org") > speech/reader component.
[http://www.thegoan.com/firebible]("http://www.thegoan.com/firebible") (more of a browser assistant to firefox)
Many more, but I suppose they aren't necessary, and some are QT/KDE apps.


> **david_kt said:**
> Not sure about this one. Is it mp3 bible?  No, just a reader, such as xiphos has integrated.
This is just my viewpoint, but I like to hear a chapter at one time read to me, and sometimes just prefer to hear a selection while I am working. 



> **david_kt said:**
> We could create standard bookmark so that the new ubuntu ce would have necessary bookmark ready for user. May be below could be those links you want to add:
[http://kjvmp3.com/kjvmp3.html](http://kjvmp3.com/kjvmp3.html)
[http://www.audiotreasure.com/](http://www.audiotreasure.com/)
[http://www.mp3bible.org/kjv/index.cfm](http://www.mp3bible.org/kjv/index.cfm)
[http://sigm.net/home](http://sigm.net/home)

or let us know what links you have in mind.

I think such links would be very helpful. Clear and concise, to point people in the right direction.
I'll have to check my pc at home for additional links. I have a bunch of them.


In regard to the media manager / store integration, here's why I bring this up. I would venture to say that 80% of people that are Christian, or at least the ones I have met and dealt with over the last few years, download, copy and generally do not buy the music they listen to. The general consensus I have gathered is that 
[LIST=1]
[*]any christian music/cd tends to be more expensive then the mainstream counterparts
[*]no unified place to get music online
[/LIST]
At least, this seems to be true in Canada.
I don't know what would need to be done for an integrated experience, such as magnatune, but I think long term, it would aid in simplifying and allowing Christians to find what they need right from the desktop, so to speak.


> **david_kt said:**
> I think it could be done by making a script so that user could encrypt, open and lock using right click. The manual method is below:
[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)
[http://www.ubuntugeek.com/how-to-create-a-private-encrypted-folder-on-ubuntu-810-intrepid.html](http://www.ubuntugeek.com/how-to-create-a-private-encrypted-folder-on-ubuntu-810-intrepid.html) 
I only bring this up because I would be one to use this. The easier (and clearer) it is to do this, the more confidence it may foster in using UCE in business, and personal use if there is a chance of circumvention/confiscation etc.



> **david_kt said:**
> May be a bookmark to setup free forum?

[http://www.freeforums.org/](http://www.freeforums.org/)

Or option to host forum? But to host a forum require a bit of work on user. Below there is free software to setup forum:

[http://www.simplemachines.org/](http://www.simplemachines.org/)

DK

Perhaps. If something existed, such as a notifier, widget, or feed for subscribed categories and urgency, to put in a request and so forth - and a way to acknowledge those requests from the desktop or similar, not having to scour, or lurk in forums.
Maybe someone knows of a method to do this, as I don't at the moment. Try to consider this more of a queued/chat option/ticket system for all to see. 
Maybe I am not informed enough about what's available, but this is wish, not an immediate expectation.

If nothing is possible on that level, I'll keep looking.
Maybe something will turn up.


Hopefully I didn't overrun you guys with too much. 
These are just some thoughts. Ultimately, your time should be used for those things which are most needed.

---

### Post by jonathonblake on 2009-06-27
> **mhancoc7 said:**
> why do you feel that there should be a name change?

Mainly for branding and support related reasons.


jonathon

---

### Post by shane2peru on 2009-06-27
I want to say first of all, I'm glad this project has not died!  I have watched it for a long time, and honestly had given up on it's come back.  Thank you david_tk for taking over the development.  If I can be of help please let me know.  I'm not a programmer, but I'm pretty decent with command line, etc.  Second I don't know what it takes to make a meta-package, but I would be all for getting a meta-package into the repos.  If most of everything is installable from the repos I would think this shouldn't be too difficult.  With that being said, I can't disagree with the philosophy of having and maintaining the LiveCD iso.  I don't want to overload you but both would be optimal.  I used UCE before, but left when releases became sluggish.  Now I'm running 64bit, so I wouldn't mind installing a meta-package, but probably will not download and install again.  But it is always nice to have a cd to hand out, and that I would do.

This is strictly my opinion here, but when a branch wanders too far from the source it becomes a tree and not a branch.  I like to stay close to the trunk. :)  That is where the support is.  So unless you plan on running your own complete distro, stick close to the trunk. :D  That is just my opinion so you can take it or leave it. 

**Bible application:**
I like e-Sword, but have been running The Word a little more [www.theword.gr](www.theword.gr) because it was faster with the sqlite db, however e-Sword switching to the sqlite db probably is about on equal terms as far as speed ect.  The Word has always run very nice with wine, and never given me problems, where e-Sword was a little more fickle in that reguard.  I put my vote in for Xiphos, it isn't as up to par as the other two, but it was made for running on Linux, and I like that.  And there is active development on it.  Those are positive factors.

I really liked the GUI for Dan's Guardian and if that can be maintained and kept up that would be great.  I would also highly recommend setting things up for opendns.com as for filtering.  It doesn't slow the machine down at all, and works very well.  With DG on occasion it would give me problems with uploading to my web site.  This very well could be my lack of understanding and running it, but worth mentioning at any rate.

I'm really glad to see this project once again heading on a forward path.  I will offer my support here on the forums for fixing problems too.

Shane

---

### Post by david_kt on 2009-06-29
> I don't know what it takes to make a meta-package, but I would be all for getting a meta-package into the repos.  If most of everything is installable from the repos I would think this shouldn't be too difficult. 

I have made a trial repository with metapackage and hosted at home. And today I got I free website to create another try, before I contact Jereme for official website as I do not want to mess up his website. Please try below steps:

1. Add wine repository
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

2. Add Xiphos repository
[https://edge.launchpad.net/~pkgcrosswire/+archive/ppa](https://edge.launchpad.net/~pkgcrosswire/+archive/ppa)

3. Add ubuntu ce trial repository on /etc/apt/sources.list:
deb [http://david_kt.freeno1.com/Ubuntu_CE](http://david_kt.freeno1.com/Ubuntu_CE) binary/

After that:
```
sudo apt-get update
sudo apt-get install ubuntu-ce
```

>  With that being said, I can't disagree with the philosophy of having and maintaining the LiveCD iso.  I don't want to overload you but both would be optimal.  I used UCE before, but left when releases became sluggish.  Now I'm running 64bit, so I wouldn't mind installing a meta-package, but probably will not download and install again.  But it is always nice to have a cd to hand out, and that I would do.

If everything is already enlcosed in metapackage, it is very easy to launch iso, I use reconstructor and it would only take minimum effort.

> This is strictly my opinion here, but when a branch wanders too far from the source it becomes a tree and not a branch.  I like to stay close to the trunk. :)  That is where the support is.  So unless you plan on running your own complete distro, stick close to the trunk. :D  That is just my opinion so you can take it or leave it. 

Agreed. I try to minimize adding unnecessary packages.

> I like e-Sword, but have been running The Word a little more [www.theword.gr](www.theword.gr) because it was faster with the sqlite db, however e-Sword switching to the sqlite db probably is about on equal terms as far as speed ect.  The Word has always run very nice with wine, and never given me problems, where e-Sword was a little more fickle in that reguard.  I put my vote in for Xiphos, it isn't as up to par as the other two, but it was made for running on Linux, and I like that.  And there is active development on it.  Those are positive factors.

I think Xiphos should be the default install, and I will include e-Sword isntaller. As for The Word, I could include installer as well but that might be not necessary as The Word is platinum application in wine. 

> I really liked the GUI for Dan's Guardian and if that can be maintained and kept up that would be great.  I would also highly recommend setting things up for opendns.com as for filtering.  It doesn't slow the machine down at all, and works very well.  With DG on occasion it would give me problems with uploading to my web site.  This very well could be my lack of understanding and running it, but worth mentioning at any rate.

I re-write the dansguardian GUI as the old version written by Jereme was based on gambas, and it is not installable anymore as Jaunty has moved to gambas2. It is could be installed by adding gambas. Now I write it using zenity, and also improve the code to cater for future release. Previously it was hardcoded to specific Firefox Version so as if there is firefox version update, it would break dansguardian GUI. The new one I write I hope could be use even for karmic Koala without any change in the code.

Please test the included package in the ubuntu-ce and let me know if you have any suggestions.

DK

---

### Post by shane2peru on 2009-06-29
> **david_kt said:**
> 
1. Add wine repository
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

2. Add Xiphos repository
[https://edge.launchpad.net/~pkgcrosswire/+archive/ppa](https://edge.launchpad.net/~pkgcrosswire/+archive/ppa)

3. Add ubuntu ce trial repository on /etc/apt/sources.list:
deb [http://david_kt.freeno1.com/Ubuntu_CE](http://david_kt.freeno1.com/Ubuntu_CE) binary/

After that:
```
sudo apt-get update
sudo apt-get install ubuntu-ce
```



DK

Ok, I already had the first two setup and the third I added and get this error:

```

Get:6 http://david_kt.freeno1.com binary/ Release [9370B]     
Ign http://david_kt.freeno1.com binary/ Release
Get:7 http://david_kt.freeno1.com binary/ Packages [9370B]
74% [Working]bzip2: (stdin) is not a bzip2 file.
Err http://david_kt.freeno1.com binary/ Packages
  Sub-process bzip2 returned an error code (2)
Fetched 43.6kB in 5s (7710B/s)
W: GPG error: http://david_kt.freeno1.com binary/ Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://david_kt.freeno1.com/Ubuntu_CE/binary/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
shane@shane-desktop:~$ sudo apt-get install ubuntu-ce
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-ce

```
I tried removing the last slash and it said the line was malformed, so I added that last slash back in and tried updating several times, it wouldn't work.  :(   Also I don't remember if I mentioned but I'm running amd64 version of Ubuntu.  I don't know if that would matter, but wanted to mention it non the less.

Shane

---

### Post by david_kt on 2009-06-29
> **shane2peru said:**
> 
W: GPG error: [http://david_kt.freeno1.com](http://david_kt.freeno1.com) binary/ Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://david_kt.freeno1.com/Ubuntu_CE/binary/Packages.bz2](http://david_kt.freeno1.com/Ubuntu_CE/binary/Packages.bz2)  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

I did not sign the package as such you must accept unsigned packages. If sudo apt-get update have error, please repeat it until success before you could do sudo apt-get install ubuntu-ce.

Alternatively, you could add below repository as well:

deb [http://thuygiang.homelinux.com/Ubuntu_CE](http://thuygiang.homelinux.com/Ubuntu_CE) binary/

and then try again sudo apt-get update, and sudo apt-get install ubuntu-ce.

DK

---

### Post by shane2peru on 2009-06-29
> **david_kt said:**
> I did not sign the package as such you must accept unsigned packages. If sudo apt-get update have error, please repeat it until success before you could do sudo apt-get install ubuntu-ce.

Alternatively, you could add below repository as well:

deb [http://thuygiang.homelinux.com/Ubuntu_CE](http://thuygiang.homelinux.com/Ubuntu_CE) binary/

and then try again sudo apt-get update, and sudo apt-get install ubuntu-ce.

DK
Hmm, I added that one too, and still not getting it.  This is the problem here:
```


W: Failed to fetch http://david_kt.freeno1.com/Ubuntu_CE/binary/Packages.bz2  Sub-process bzip2 returned an error code (2)

```
It seems that this file, Packages.bz2 is not there.  Or perhaps corrupted.  The gpg error, I understand as a key being signed, that I can understand.  I know nothing of making repos, other than I have made one on my local machine for local access.  I don't know what is in that file, I think it is just a text file of the packages in the repo, but none the less, it appears to not be there.

Shane

---

### Post by david_kt on 2009-06-29
> **shane2peru said:**
> Hmm, I added that one too, and still not getting it.  This is the problem here:
```


W: Failed to fetch http://david_kt.freeno1.com/Ubuntu_CE/binary/Packages.bz2  Sub-process bzip2 returned an error code (2)

```
It seems that this file, Packages.bz2 is not there.  Or perhaps corrupted.  The gpg error, I understand as a key being signed, that I can understand.  I know nothing of making repos, other than I have made one on my local machine for local access.  I don't know what is in that file, I think it is just a text file of the packages in the repo, but none the less, it appears to not be there.

Shane

Could you remove [http://david_kt.freeno1.com/Ubuntu_CE](http://david_kt.freeno1.com/Ubuntu_CE) from repository and try again?  
deb [http://david_kt.freeno1.com/Ubuntu_CE](http://david_kt.freeno1.com/Ubuntu_CE) binary/ is mirror of 
deb [http://thuygiang.homelinux.com/Ubuntu_CE](http://thuygiang.homelinux.com/Ubuntu_CE) binary/

DK

---

### Post by shane2peru on 2009-06-29
> **david_kt said:**
> Could you remove [http://david_kt.freeno1.com/Ubuntu_CE](http://david_kt.freeno1.com/Ubuntu_CE) from repository and try again?  
deb [http://david_kt.freeno1.com/Ubuntu_CE](http://david_kt.freeno1.com/Ubuntu_CE) binary/ is mirror of 
deb [http://thuygiang.homelinux.com/Ubuntu_CE](http://thuygiang.homelinux.com/Ubuntu_CE) binary/

DK

I tried that too, the update works fine, however the package ubuntu-ce is not found.  I think the mirror is working fine, because I did fine dansguardian-gui (You are the maintainer of this one).  I didn't install that though, I need to back up before doing that.  This is my production machine, and I don't want to mess it up. Splash themes and artwork is easy for me to fix, DG, isn't. :)  Do you have a list of the packages there?  Perhaps there are some others I would check out.

Shane

---

### Post by david_kt on 2009-06-29
> **shane2peru said:**
> I tried that too, the update works fine, however the package ubuntu-ce is not found.  I think the mirror is working fine, because I did fine dansguardian-gui (You are the maintainer of this one).  I didn't install that though, I need to back up before doing that.  This is my production machine, and I don't want to mess it up. Splash themes and artwork is easy for me to fix, DG, isn't. :)  Do you have a list of the packages there?  Perhaps there are some others I would check out.

Shane

I will try again to see why ubuntu-ce is not found. Did you try to see it in synaptic? Just in case it is wrong name. Another option is to run sudo apt-get update again just in case the downloaded file is corrupted.

For dansguardian-gui, it should not interfere with your setting UNLESS you launch "Autoconfigure/Reset Firehol, Dansguardian and Tinyproxy". But even if you launch it, it will back up your orininal configuration to program.conf.oroginal.

This gui would be very helpful if you find dansguardian difficult to configure and manage.

Edit:
For the list of packages, you could browse and download deb file here:

[http://thuygiang.homelinux.com/Ubuntu_CE/binary/](http://thuygiang.homelinux.com/Ubuntu_CE/binary/)

Xiphos is on xiphos repository, and others in ubuntu official repository.

DK

---

### Post by shane2peru on 2009-06-29
> **david_kt said:**
> I will try again to see why ubuntu-ce is not found. Did you try to see it in synaptic? Just in case it is wrong name. Another option is to run sudo apt-get update again just in case the downloaded file is corrupted.

For dansguardian-gui, it should not interfere with your setting UNLESS you launch "Autoconfigure/Reset Firehol, Dansguardian and Tinyproxy". But even if you launch it, it will back up your orininal configuration to program.conf.oroginal.

This gui would be very helpful if you find dansguardian difficult to configure and manage.

Edit:
For the list of packages, you could browse and download deb file here:

[http://thuygiang.homelinux.com/Ubuntu_CE/binary/](http://thuygiang.homelinux.com/Ubuntu_CE/binary/)

Xiphos is on xiphos repository, and others in ubuntu official repository.

DK

Ahh, that explains it!
[http://thuygiang.homelinux.com/Ubuntu_CE/binary/ubuntu-ce_1.1_i386.deb](http://thuygiang.homelinux.com/Ubuntu_CE/binary/ubuntu-ce_1.1_i386.deb)
wrong architecture that explains why it wouldn't show up when I do a search for it.  It seems as though the amd64 version automatically reads the name and rejects it because the architecture is not correct.  That is actually kind of a neat thing.  If you want to PM me and explain how to build that deb, I can throw a 64bit package together for you.  I have built things before, but I don't understand it, I just follow directions.  Let me know.

Shane

---

### Post by david_kt on 2009-06-29
> **shane2peru said:**
> Ahh, that explains it!
[http://thuygiang.homelinux.com/Ubuntu_CE/binary/ubuntu-ce_1.1_i386.deb](http://thuygiang.homelinux.com/Ubuntu_CE/binary/ubuntu-ce_1.1_i386.deb)
wrong architecture that explains why it wouldn't show up when I do a search for it.  It seems as though the amd64 version automatically reads the name and rejects it because the architecture is not correct.  That is actually kind of a neat thing.  If you want to PM me and explain how to build that deb, I can throw a 64bit package together for you.  I have built things before, but I don't understand it, I just follow directions.  Let me know.

Shane

I just got hold of the tar ball of opensong:

[http://opensong.svn.sourceforge.net/viewvc/opensong.tar.gz?view=tar](http://opensong.svn.sourceforge.net/viewvc/opensong.tar.gz?view=tar)

It is the only package with i386 architecture. But I make it as a dependency of ubuntu-ce, I have to mark ubuntu-ce as i386. What we could try is remove opensong and mark ubuntu-ce with all architecture. But I find opensong is very usefull application and should be included in ubuntu ce.

DK

---

### Post by jonathonblake on 2009-06-30
> **shane2peru said:**
>  It seems as though the amd64 version automatically reads the name and rejects it because the architecture is not correct.

I've run into  that issue several times.  Only by reading each line on suod apt-get update, did I realize that the issue is  architecture.

jonathon

---

### Post by david_kt on 2009-07-08
> **adzik said:**
> 
I only bring this up because I would be one to use this. The easier (and clearer) it is to do this, the more confidence it may foster in using UCE in business, and personal use if there is a chance of circumvention/confiscation etc.


I have made a GUI to create and manage encrypted directory in home folder.
Please check it out:

Add repository to your sources.list:

deb [http://david-kt.atbhost.net/Ubuntu_CE/](http://david-kt.atbhost.net/Ubuntu_CE/) binary/ 

sudo apt-get update
sudo apt-get install encfs-gui

After that you could find it in Application > System tools > encfs gui

Please let me know you opinion about this simple tool.

DK

---

### Post by mhancoc7 on 2009-07-08
> **david_kt said:**
> I have made a GUI to create and manage encrypted directory in home folder.
Please check it out:

Add repository to your sources.list:

deb [http://david-kt.atbhost.net/Ubuntu_CE/](http://david-kt.atbhost.net/Ubuntu_CE/) binary/ 

sudo apt-get update
sudo apt-get install encfs-gui

After that you could find it in Application > System tools > encfs gui

Please let me know you opinion about this simple tool.

DK

Hi DK,
Just wondering when you think a new release might be ready. I have been getting a ton of requests lately. Just wondering so I can update the site and what not.
Thanks, Jereme

---

### Post by david_kt on 2009-07-08
> **mhancoc7 said:**
> Hi DK,
Just wondering when you think a new release might be ready. I have been getting a ton of requests lately. Just wondering so I can update the site and what not.
Thanks, Jereme

With this last package, it should be ready for release.
Tomorrow I will try to create and upload the live cd (beta release?), just wondering where I will upload it. May be I will upload it using torrent.

The only thing that still lack is desktop background. I have made the live cd greeter, usplash and gdm login (I add "christian edition" to the default ubuntu).


DK

---

### Post by mhancoc7 on 2009-07-08
> **david_kt said:**
> With this last package, it should be ready for release.
Tomorrow I will try to create and upload the live cd (beta release?), just wondering where I will upload it. May be I will upload it using torrent.

The only thing that still lack is desktop background. I have made the live cd greeter, usplash and gdm login (I add "christian edition" to the default ubuntu).


DK

Cool. As for the upload, if you can upload it somewhere temporarily then I can have the main mirror that is provided by Oklahoma Christian University copy it to their server. They have enough bandwidth to handle the load and have been providing space for years now.

Did you want to host the repos on my server?

Thanks, Jereme

---

### Post by david_kt on 2009-07-08
> **mhancoc7 said:**
> Cool. As for the upload, if you can upload it somewhere temporarily then I can have the main mirror that is provided by Oklahoma Christian University copy it to their server. They have enough bandwidth to handle the load and have been providing space for years now.

Did you want to host the repos on my server?

Thanks, Jereme

Yes sure, the repos now is very bad as it is freehosting. Frequently the download fail. Just let me know how to upload it to your server, or you could mirror this site:

[http://david-kt.atbhost.net/Ubuntu_CE](http://david-kt.atbhost.net/Ubuntu_CE)

and that mirror would be the official repository.

DK

---

### Post by k_chupe on 2009-07-08
I've been hoping that someone would start the uce back up. I believe that having bible study tools pre-installed is a must. eSword is nice but gnome sword is just as good in my opinion. Having wine included is a must as well, being that some bible study software and other windows apps haven't a linux equivalent. Virtual box is exellent as you can run virtual machine in it, and it's free. I had better luck using it to run my windose software than wine. Some Christian based wallpaper is also a nice thought. As far as ichthux, it can be downloaded from the syntac package manager, being that it's available as a desktop environment rather than a complete os. some pre bookmarked sites in the browser such as blue letter bible study site as well as others that give you access to bible study material would be good. As far as unwanted apps, I believe if you could incorporate within the install process the option to "tick" the apps you want installed with uce and leave the ones you do'nt want "unticked" would probally be the best way to get around installing new apps or unistalling pre-installed ones. This option is used with osx and has proved to work well meeting the specific needs of individuals. I hope this helps and am excited of the promising future of uce thanks to someone that realized the great value in catering to the needs of God's people.

---

### Post by Tropcon on 2009-07-10
Oh cool! This excites me! I'm in a rush, so I've only read the first page of this thread, but it looks like this project could save me a lot of time setting up a computer for my brother (and tweaking my own.)

I was just wondering if any of you had heard of a program called "Accountability-Pal." It looks to be a very good accountability program, but I also know that it's a total pain to install from the source.
I know that I've had it running before (after a few days of hunting for dependencies) but I can't remember how I did it (it was several months ago.) I still have all the files to compile it (I think). Here's the home page, if you're interested: [http://www.accountabilitypal.org/](http://www.accountabilitypal.org/)

I'll let you know if I ever get a working binary.

Thanks loads! (I would be downloading the ISO right now to check it out, but I'm on a portable drive at the moment.)

---

### Post by k_chupe on 2009-07-12
I had another suggestion. Why not used u-lite(a stripped down version of hardy heron 8.04) and upgrade the kernel to the jaunty kernel and add whatever you want as far as apps goes, then you can make an iso and presto!

---

