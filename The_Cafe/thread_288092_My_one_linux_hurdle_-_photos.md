---
title: "My one linux hurdle - photos"
date: 2006-10-29
forum: The Cafe
---

### Post by m.musashi on 2006-10-29
Just one you ask? Well, in truth there have been several but with time I learn, adapt and overcome. However, as I slowly move more and more to full time linux user, I come to larger hurdles. At the moment it's photo management. Until recently I've been using windows to upload and organize photos. I used the wizard to upload photos to a folder and give all the pictures a similar name (usually a data) with a sequential file number. When viewing or working on photos I used Nero or Picasa.

I've been using Ubuntu for almost a year now slowly adding a new skill or app. I felt it was time to tackle photos so a couple weeks ago I moved all my windows docs and pictures to /home. I've tried gthumb, f-spot and Picasa for linux (thanks automatix). However, I am not entirely happy with any of these. Is there something else I might try? I don't do much with the pics. I just want a simple upload tool that allows me to name files as a group as they are uploaded, shuffle them around, resize them for emailing, create albums to upload to a web page (JAlbum in windows does this wonderfully) and creating CDs for archiving or ordering prints. So far, Picasa seems to be the best bet but it is really slow to upload. In windows (using the upload wizard) I could upload a 100 photos in a minute or two. In Ubuntu-picasa it was closer to 5 min. What I really miss is the ability to upload a bunch of photos and automatically name them 2006.10.29_001, ...002, etc. Unless I'm missing something Picasa won't do that. Gthumb did them sequentially but it didn't seem to follow the order in which they were taken. I haven't tried f-spot yet for this but I was frustrated by it's tool for importing from the HD and for organizing.

Please don't read this as a complaint. I love Ubuntu and am working my way to 100% user. I'm going to try and keep using Picasa and hopefully adapt. I was just wondering if I'm missing something that might be an even better option.

Thanks.

---

### Post by awakatanka on 2006-10-29
Digikam maybe something for you.

[http://www.digikam.org/](http://www.digikam.org/)
Plugins : [http://www.digikam.org/plugins.html](http://www.digikam.org/plugins.html)
And some on kde-apps : [http://www.kde-apps.org/content/show.php?content=16082](http://www.kde-apps.org/content/show.php?content=16082)

---

### Post by mips on 2006-10-29
Have you looked at digiKam ?

Looks like it supports batch renaming in the tools menu.

Edit: To late, awakatanka beat me to it.

---

### Post by m.musashi on 2006-10-29
I haven't heard of digikam. Thanks for the sugestion. I was going to install it but it's not in the repos. I have all the standard repos uncommented but synaptic doesn't show it. Will it be a manual install? I've never mastered that and I didn't find a how to in the forums yet. Is it a kde app? Do I need to install the kubuntu-desktop option first?

---

### Post by z_diver on 2006-10-29
Quoting from their website, "JAlbum runs on Windows, Mac OS X, Linux and others".   Have you tried it yet?

---

### Post by m.musashi on 2006-10-29
> **z_diver said:**
> Quoting from their website, "JAlbum runs on Windows, Mac OS X, Linux and others".   Have you tried it yet?

No, not on Linux. It isn't in the repos and I've never figured out how to install or compile apps not available through apt (unless I find a nice how to:)). I don't use jalbum much so it's not a big deal. Mainly I just want a nice tool for uploading and organizing. Picasa is close, I will give digikam a try as soon as I figure out how to install it.

---

### Post by mostwanted on 2006-10-29
> **m.musashi said:**
> No, not on Linux. It isn't in the repos and I've never figured out how to install or compile apps not available through apt (unless I find a nice how to:)). I don't use jalbum much so it's not a big deal. Mainly I just want a nice tool for uploading and organizing. Picasa is close, I will give digikam a try as soon as I figure out how to install it.

That ought to set you up: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

BTW, Digikam is indeed in the official repositories, you probably haven't enabled them all. The link explains how to do that as well.

---

### Post by mips on 2006-10-29
> **m.musashi said:**
> I haven't heard of digikam. Thanks for the sugestion. I was going to install it but it's not in the repos. I have all the standard repos uncommented but synaptic doesn't show it. Will it be a manual install? I've never mastered that and I didn't find a how to in the forums yet. Is it a kde app? Do I need to install the kubuntu-desktop option first?

Really weird as i can see it in the repos, main pool. Yes, it's a kde app. It's part of kubuntu-desktop so it must be there.

I don't think you need the kubuntu-desktop. If it has any dependancies it should list them.

have you tried [B]sudo aptitude digikam
[/B] ?

---

### Post by chaosgeisterchen on 2006-10-29
Edgy offers them in the main repository?

```
chaosgeisterchen@sequentia:~$ sudo apt-cache policy digikam
Password:
digikam:
  Installiert:1:0.8.2-2ubuntu1
  Mögliche Pakete:1:0.8.2-2ubuntu1
  Versions-Tabelle:
 *** 1:0.8.2-2ubuntu1 0
        500 http://de.archive.ubuntu.com edgy/main Packages
        100 /var/lib/dpkg/status
chaosgeisterchen@sequentia:~$
```

I hope you can read the essentials out of it, my system is German.

---

### Post by mostwanted on 2006-10-29
> **mips said:**
> have you tried [B]sudo aptitude digikam
[/B] ?

You mean **sudo aptitude *install* digikam**.

---

### Post by m.musashi on 2006-10-29
> **mips said:**
> Really weird as i can see it in the repos, main pool. Yes, it's a kde app. It's part of kubuntu-desktop so it must be there.

I don't think you need the kubuntu-desktop. If it has any dependancies it should list them.

have you tried [B]sudo aptitude digikam
[/B] ?

I used synaptic and searched. It did not list it.

I also just noticed that picasa (linux version) does not have the option to upload pictures to my picasa account on the web - unless I'm just not seeing it.

---

### Post by m.musashi on 2006-10-29
Here is my sources.list
```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://www.beerorkid.com/compiz edgy main-edgy
deb http://amaranth.selfip.com edgy lrm

deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://dl.google.com/linux/deb/ stable non-free

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END
```
As far as I know, that should give me access to all the supported repos. I don't know why digikam isn't showing up in synaptic. I haven't tried via apt or aptitude but I just installed the kubuntu-desktop so I guess it's now a moot point.

Thanks for feedback.

---

### Post by nalmeth on 2006-10-29
I'm pretty sure theres no linux Picasa version, you're running the windows version in wine. I may be out of touch on picasa news though, I don't use it.

**F-spot** is perfect for my photo-management needs. Can you elaborate at all on why you don't like it? I can pick out a couple faults, but overall I love the app.

I didn't really like **digikam**'s interface, but it may give you the features you need. 

I liked **showimg** until I messed with the windows and the interface was uncomfortable. It's quite good, but be careful what you do with the windows.

Others you may want to look into:
[B] gthumb
gqview
gwenview[/B]

---

### Post by m.musashi on 2006-10-29
> **nalmeth said:**
> I'm pretty sure theres no linux Picasa version, you're running the windows version in wine. I may be out of touch on picasa news though, I don't use it.

**F-spot** is perfect for my photo-management needs. Can you elaborate at all on why you don't like it? I can pick out a couple faults, but overall I love the app.

I didn't really like **digikam**'s interface, but it may give you the features you need. 

I liked **showimg** until I messed with the windows and the interface was uncomfortable. It's quite good, but be careful what you do with the windows.

Others you may want to look into:
[B] gthumb
gqview
gwenview[/B]
You're right. I believe that picasa is using wine in some way and there is no linux port. However, it must not be the most recent version since I have the option to upload to picasa on the web in windows but not linux.

As for f-spot, I admit I didn't give it a real long look. When it wouldn't import photos in a way I was used to I kind of gave up there and tried picasa. I've only used digikam for about 5 minutes but so far I like it. Personally, I'd like to see a very nice and updated port of picasa but so far, digikam may fill most or all the holes I'm seeing in the other apps. Once I figure out which one like the best I'll add all my photos and see how things go. I'll give f-spot another look too.

---

### Post by m.musashi on 2006-10-29
> **mostwanted said:**
> That ought to set you up: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

BTW, Digikam is indeed in the official repositories, you probably haven't enabled them all. The link explains how to do that as well.

Thanks for the link. Nice how-to.

---

### Post by mips on 2006-10-29
> **mostwanted said:**
> You mean **sudo aptitude *install* digikam**.

](*,) Duh, yes that's what I ment. Thanks for pointing that out.

---

### Post by awakatanka on 2006-10-29
Should be in it but here is my sources.list
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb http://packages.freecontrib.org/plf edgy free non-free
#deb-src http://packages.freecontrib.org/plf edgy free non-free                                               
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
#deb http://archive.canonical.com/ubuntu dapper-commercial main

## Beryl 
deb http://www.beerorkid.com/compiz edgy main-edgy

## Koffice 1.6
deb http://kubuntu.org/packages/koffice-16 edgy main
```

---

### Post by maniacmusician on 2006-10-29
@m.musashi: if you can spare the time, shoot google an email about picasa. I think they have the resources to succesfully port it to linux (instead of just porting an uglier version under wine). maybe if they get enough emails about it, it'll at least get them thinking.

---

### Post by Zimmer on 2006-10-29
Albums for a web page? Try Albumshaper. creates albums which when saved are almost ready made to upload to a web site....

there is an example at
 [www.edenyer.nildram.co.uk](www.edenyer.nildram.co.uk)

---

### Post by Choad on 2006-10-29
the naming of masses of files can be done with the xfce tool "bulk renamer"

its a great little app in my opinion.

---

### Post by maniacmusician on 2006-10-29
it is a great app, but integrated functionality with a photo app would be even greater. always striving for the best :)

---

### Post by m.musashi on 2006-10-29
> **maniacmusician said:**
> @m.musashi: if you can spare the time, shoot google an email about picasa. I think they have the resources to succesfully port it to linux (instead of just porting an uglier version under wine). maybe if they get enough emails about it, it'll at least get them thinking.

Good idea...and done. I also suggested they allow you to use your unused gmail space for picasa. They only give you 250MB in Picasa (unless you pay) but I have 2.5GB going unused in gmail.

---

### Post by m.musashi on 2006-10-29
> **Choad said:**
> the naming of masses of files can be done with the xfce tool "bulk renamer"

its a great little app in my opinion.

> **maniacmusician said:**
> it is a great app, but integrated functionality with a photo app would be even greater. always striving for the best :)

Digikam does do this. As far as I can tell, Picasa does not. XnView for windows also does this but I don't know off hand if they have a Linux version. Ideally, one app to rule them all would be great. Personally, I'd like that to be Picasa because I like the google philosophy and I like that it easily uploads to Picasa on the web. It makes it really easy to share full resolution files with family since Picasa doesn't limit the file size of the up or download (just the amount of space you can have :)).

---

### Post by Old Pink on 2006-10-29
> **m.musashi said:**
> (JAlbum in windows does this wonderfully)

What's the difference between JAlbum for Linux and JAlbum for Windows? :confused:

Don't be complaining about a lack of applications if you haven't even explored outside the repositories... :rolleyes:

---

### Post by maniacmusician on 2006-10-29
> **m.musashi said:**
> Good idea...and done. I also suggested they allow you to use your unused gmail space for picasa. They only give you 250MB in Picasa (unless you pay) but I have 2.5GB going unused in gmail.
yes, a friend of mine suggested this as well, and I agree. If google is giving us this much free space, then it would be awesome to have that space be central storage for all google web-apps. that would be awesome

---

