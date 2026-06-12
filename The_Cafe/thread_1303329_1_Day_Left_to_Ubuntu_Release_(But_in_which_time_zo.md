---
title: "1 Day Left to Ubuntu Release (But in which time zone ?)"
date: 2009-10-28
forum: The Cafe
---

### Post by medya on 2009-10-28
as we all see, the countdown says 1 day left to Karma Koala, 
I guess it would be nice to have Hours Left to release . (that would make it even more exciting)  , as it is diffrent to say next day in different time zones . it could mean 1 hour or 24 hours .

so does anyone know, how many hours left to official release ?

---

### Post by WalmartSniperLX on 2009-10-28
It's your timezone (mine says 2 days left).

But couldn't tell you the details on hours or minutes.

---

### Post by deancasino on 2009-10-28
> **medya said:**
> as we all see, the countdown says 1 day left to Karma Koala, 
I guess it would be nice to have Hours Left to release . (that would make it even more exciting)  , as it is diffrent to say next day in different time zones . it could mean 1 hour or 24 hours .

so does anyone know, how many hours left to official release ?

I was seriously going to begin the same thread just before I saw this lol

---

### Post by albandy on 2009-10-28
Canonical Headquarters are in London, so I think they are using GMT time, for example, I'm in Spain, GMT+1, and the counter says 1 day left.

---

### Post by medya on 2009-10-28
the javascript generates the same image for all users in all time zones .
whatever, we need a Count Down , I wanna schedule to download ubuntu at very first minutes .

---

### Post by x3roconf on 2009-10-28
> **medya said:**
> the javascript generates the same image for all users in all time zones .
whatever, we need a Count Down , I wanna schedule to download ubuntu at very first minutes .

me too :)

---

### Post by Bibek on 2009-10-28
var d = new Date();
    dom = d.getDate();
    month = d.getMonth();
    year = d.getYear();
    if (year < 2000) year = year - 100;
    else year = year - 2000;

    if (year == 9 && month == 9)
        days = 29 - dom;
    else 
        days = 0;
    if (days < 0) days = 0;
    if (days < 10) days = '0' + days.toString();


var base = 'http://www.ubuntu.com/files/countdown/910/countdown-9.10-1/';

document.write('<a href="http://www.ubuntu.com/"><img id="countdownimage" src="'+base+days+'.png" width="180" height="150" border="0" alt="Ubuntu 9.10 - Coming soon" style="padding-top:2px;background-color:transparent"></a>');

// document.write('<a href="http://www.ubuntu.com/"><img id="ubuntucountdownimage" src="'+base+'here.png" width="180" height="150" border="0" alt="Ubuntu 9.10 is here"></a>');
//

---

### Post by medya on 2009-10-28
now the countdown logo no longer says  1 day , it says Coming soon .
it is 1 Am here, do u think it will be released in minutes ? or I better go to sleep if it is not gonna be released soon .

---

### Post by koleoptero on 2009-10-28
Better go to sleep. I'm betting on Friday.

---

### Post by infestor on 2009-10-28
> **albandy said:**
> Canonical Headquarters are in London, so I think they are using GMT time, for example, I'm in Spain, GMT+1, and the counter says 1 day left.

that would be my guess too. i am also in GMT+1 so i will have to wait 1 hour more (not that impatient though :) )

---

### Post by t0p on 2009-10-28
> **medya said:**
>  I wanna schedule to download ubuntu at very first minutes 

I realise you're probably(?) kidding.  But I just want to point out: the servers will be inundated with requests because of this attitude.   With the result that downloads may be very slow, or even impossible.

It would be a good idea if everyone who can use a bittorrent client does so to get hold of 9.10.  If we all get the .iso via bittorrent, then seed it for a while afterwards, downloads will get *easier*, not harder.  And if we leave the direct download servers for those who need them (because their ISPs block or throttle bittorrent), their downloads will be easier too.

"Ubuntu" is all about being nice to each other.  So let's all do "Ubuntu"!

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-28
Yes please! I still remember that I was unable to update the karmic beta, when I needed to get some cruicial bugs fixed, because of a lot of users were downloading .iso files

---

### Post by HappyFeet on 2009-10-28
> **medya said:**
> I wanna schedule to download ubuntu at very first minutes .

I'm sure your quality of life will improve drastically if you download the very second it is released. :rolleyes:

---

### Post by HappyFeet on 2009-10-28
> **t0p said:**
> But I just want to point out: the servers will be inundated with requests because of this attitude.   With the result that downloads may be very slow, or even impossible.

Just use aria to download it. Do, as an example:
```
aria2c http://cdimage.ubuntu.com/daily-live/current/karmic-desktop-amd64.iso 
```
It will download it from multiple locations at the same time, drastically speeding up the download. Or better yet, use bittorrent.

---

### Post by sdowney717 on 2009-10-28
install the beta now, most everything is already baked in.
I assume there will be a few final releases yet to come out.
this way you miss rush hour.

---

### Post by Cam42 on 2009-10-28
seconded on the bittorrent method of downloading.

---

### Post by OpenGuard on 2009-10-28
Thousands of people updating their systems at a time .. good luck with that ;)

---

### Post by bonfire89 on 2009-10-28
When Jaunty was coming out I waited until midnight here in Toronto (Eastern Timezone)

It did not come out at midnight, and was not out.


I waited for hours after midnight eastern timezone finally going to sleep without downloading it.


I suspect it is based on Hawaii time or w/e timezone is next to the international date line.



Edit: it would be sweet if I could set something up to automatically start downloading the torrent whenever it comes out so that I don't have to wait up for it, and so I can help seed it asap.

---

### Post by t0p on 2009-10-28
> **sdowney717 said:**
> install the beta now, most everything is already baked in.
I assume there will be a few final releases yet to come out.
this way you miss rush hour.

This is an interesting point.  Just how different is the beta from the final release?  I wouldn't have thought there are a great number of differences...

---

### Post by OpenGuard on 2009-10-28
> **bonfire89 said:**
> When Jaunty was coming out I waited until midnight here in Toronto (Eastern Timezone)

It did not come out at midnight, and was not out.


I waited for hours after midnight eastern timezone finally going to sleep without downloading it.


I suspect it is based on Hawaii time or w/e timezone is next to the international date line.

No, it's based on how fast Canonical guys can change the data on their website & upload final release images.

---

### Post by medya on 2009-10-28
> **t0p said:**
> I realise you're probably(?) kidding.  But I just want to point out: the servers will be inundated with requests because of this attitude.   With the result that downloads may be very slow, or even impossible.

It would be a good idea if everyone who can use a bittorrent client does so to get hold of 9.10.  If we all get the .iso via bittorrent, then seed it for a while afterwards, downloads will get *easier*, not harder.  And if we leave the direct download servers for those who need them (because their ISPs block or throttle bittorrent), their downloads will be easier too.

"Ubuntu" is all about being nice to each other.  So let's all do "Ubuntu"!

ofcourse I was gonna download using torrent , because it is even faster than server-downloading for me ;)

I just cant wait to have the torrent file .

---

### Post by 23meg on 2009-10-28
Due to the complex nature of the [release process]("https://wiki.ubuntu.com/ReleaseProcess"), in which multiple people working in different timezones take part, it's not possible to tell beforehand at what time exactly it will be out.

---

### Post by onclouds on 2009-10-28
ahh Hell!! Just release the damn .iso already!.. I'm anxious to try on liveCD for a couple of days and then.. 

**BOOM!!**
Karmic Koala + 30GB wasted on win7 for lans ;)
**BOOM!!**

---

### Post by kingofpain on 2009-10-28
Actually... if they say the release is on 29'th... then, it should be available at 0.01 GMT.
That's my point of view... of course, it's not going to be like that. I remember, last year i think, a guy from new zealand had to wait a day more than the actual release date announced.:D

---

### Post by Johnsie on 2009-10-28
Judging from previous alpha/beta testing experiences, if you already have the beta then you probably pretty much already have the release version. They don't tend to upgrade alot of packages on release day.

If you're looking for the full download then it will be whenever Cannonical decide... Midnight? Not sure why the staff would want to be in the office supporting a new release at midnight. If I were them I'd release it tomorrow morning when they are all in the office ;-) 

The only people who know are the webmasters.

---

### Post by sdowney717 on 2009-10-28
i usually start with alpha6 or first beta to upgrade. 
you never need to imstall the final, simply updating packages eventually gives you the final release.

---

### Post by Smudger on 2009-10-28
Where can I get a torrent of the beta version?

---

### Post by Pott on 2009-10-28
It went from 2 Days to 1 Day to ... "Coming Soon" here.

---

### Post by speedwell68 on 2009-10-28
I have been running the release candidate for a few days now, it's lovely and there have been a few large daily updates.  I have just completed an upadte so I assume I am now running the final.

---

### Post by dbyjazz on 2009-10-28
Isn't it the same thing if you just download the beta now? Then just update tomorrow..

---

### Post by Old_Grey_Wolf on 2009-10-28
In my opinion it will be available Thursday or Friday depending on timezone. 

I am not in a hurry to download and install it. These are the steps I will take:

1 ) I am going to start backing up my important files on Saturday morning. 
2 ) Read the release notes for known problems.
3 ) If there are no known problems for my hardware, then download a copy. 
4 ) If there are known problems, look for solutions, then download a copy if solutions exists. 
5 ) Create a Live USB to check for compatibility with my hardware.
6 ) If the Live USB works, then I will install it on a parallel partition with my current version. 
7 ) I will test the new partition after transferring all my setup, important data, and applications.
8 ) If the partition works after a few days of testing/use, I will resize the new partition to eliminate the old version.

---

### Post by Squonk07 on 2009-10-28
> **t0p said:**
> It would be a good idea if everyone who can use a bittorrent client does so to get hold of 9.10.  If we all get the .iso via bittorrent, then seed it for a while afterwards, downloads will get *easier*, not harder.

I make a point of being a good citizen and downloading a torrent version to seed even if I have a standard download--I just feel like it's the right thing to do.

---

### Post by keplerspeed on 2009-10-28
Torrent is generally faster, expecially when the servers are being hammered, like they will be in a few hrs. And seed, even if it is only for a few minutes.

---

### Post by LookTJ on 2009-10-29
I think they will release the release image as soon as all the timezones are into Thursday.

---

### Post by HappyFeet on 2009-10-29
> **Squonk07 said:**
> I make a point of being a good citizen and downloading a torrent version to seed even if I have a standard download--I just feel like it's the right thing to do.

You don't need to download a separate bittorrent version. Just put the one you downloaded into your torrent folder and click the  .torrent file, and it will verify you have it, and it will seed.

---

### Post by HappyFeet on 2009-10-29
> **LookTJ said:**
> I think they will release the release image as soon as all the timezones are into Thursday.

Last release it came out around 2-3pm london time.

---

### Post by LookTJ on 2009-10-29
> **HappyFeet said:**
> Last release it came out around 2-3pm london time.
15:30/3:30pm to be exact :).

I'll be waiting for the torrents around 9am London time. :), to seed.

---

### Post by bibekdai on 2009-10-29
waiting for 9.10 :D

---

### Post by VioletsPie on 2009-10-29
I remember Jaunty was released around noon EST.

---

### Post by vader897 on 2009-10-29
I am from Australia. I feel tortured, I have been checking constantly  since midnight last night. Its now 7pm on the 29th. Sigh.

---

### Post by medya on 2009-10-29
> **vader897 said:**
> I am from Australia. I feel tortured, I have been checking constantly  since midnight last night. Its now 7pm on the 29th. Sigh.

yeah me too . at least they could Tweet a message or something like "guys we wont release at least for next 5 hours"

---

### Post by vader897 on 2009-10-29
If only they said it was going to be released on the 30th... Then i could rest easy, get on with my assignment, and find a pleasant surprise when it came out a few hours early.

---

### Post by medya on 2009-10-29
> **vader897 said:**
> If only they said it was going to be released on the 30th... Then i could rest easy, get on with my assignment, and find a pleasant surprise when it came out a few hours early.

agreed .
perhaps they wanted to make the release day as Close as possible to windows 7's release day.

---

### Post by bibekdai on 2009-10-29
Its a long wait :D

---

### Post by vader897 on 2009-10-29
Hmm maybe, Except lots of people in the IT loop has had Windows 7 for a while. We all got it for free through msdn about a month or two ago.

---

### Post by koleoptero on 2009-10-29
This topic has made me visiting the ubuntu homepage every ten minutes or so. Stop it you people, relax. :p

---

### Post by mrmememe on 2009-10-29
I've set the 'Reload Every...' option on [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent) and I'm still waiting... At least I don't have to refresh the main ubuntu website all the time :)

---

### Post by vader897 on 2009-10-29
I am pretty sure people like us are making their job harder :P

---

### Post by mashcaster on 2009-10-29
I will check on the weekend as I am still using 8.04, but have 9.04 in VirtualBox.  So hopefully, I will upgrade the VirtualBox installation on the weekend. :D

---

### Post by beast2k on 2009-10-29
Okay, it's 7 AM the "day of" and still no link, disappointing.

---

### Post by kthaker on 2009-10-29
I've been checking [http://releases.ubuntu.com/](http://releases.ubuntu.com/) every couple of hours to see if the karmic release images are up yet... sadly their not.

im in a GMT+2 zone..and the time is already 12:56pm... so im sure in the next few hours.. it should become available. 

Ubuntu release days always make me nervous!! 
kind of like what christmas mornings used to be  

:lol:

---

### Post by Absorbed on 2009-10-29
In the past it has been released at about 12 noon GMT, which would mean it will be available in about an hour.

---

### Post by n00ne on 2009-10-29
> **mrmememe said:**
> I've set the 'Reload Every...' option on [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent) and I'm still waiting... At least I don't have to refresh the main ubuntu website all the time :)

Great idea.
now when I'll get back from work hopefully I will have the image on my hardrive already :-)

---

### Post by 23meg on 2009-10-29
> **kthaker said:**
> I've been checking [http://releases.ubuntu.com/](http://releases.ubuntu.com/) every couple of hours to see if the karmic release images are up yet... sadly their not.


Don't download the images as soon as they seem to be available. You may end up downloading incomplete images, and that slows down the syncing of the mirrors and thus may delay the release.

Various news websites, blogs and forum posts will soon be screaming "It's released!!!11" as soon as they see some new files around releases.ubuntu.com (maybe even earlier); don't believe them. Wait for the official release announcement.

---

### Post by mashcaster on 2009-10-29
Guaranteed to be released before 12:59:59PM GMT-12

---

### Post by vader897 on 2009-10-29
Just a little website I put up for occasions such as this one...
[Its the Final Countdown]("http://dl.getdropbox.com/u/1032158/its_the_final_countdown/index.html")

That's counting down to 12 midnight in Australia of the 29th. Surely it has to be released before the end of my day. After all the release name is Karmic **Koala**. :P

---

### Post by kthaker on 2009-10-29
> **23meg said:**
> Don't download the images as soon as they seem to be available. You may end up downloading incomplete images, and that slows down the syncing of the mirrors and thus delay the release.

i definitely agree with that! i think the trick with the torrent file a few posts back is the best download strategy for me.... in any case... will all have to be queued overnight. 

im sure the download mirrors will be on fire the minute the word gets out..

exciting stuff! ;)

---

### Post by mrmememe on 2009-10-29
> **n00ne said:**
> Great idea.
now when I'll get back from work hopefully I will have the image on my hardrive already :-)

Thx. You only need to set your web browser so it would open torrents automatically (without asking) in your bittorent client (Transmission, in my case) and then uncheck the 'Display option dialogue' option in Transmission preferences... Then it will download automatically.

---

### Post by ramesh_thiru on 2009-10-29
another 30 min to go ?

---

### Post by fatality_uk on 2009-10-29
> **mashcaster said:**
> Guaranteed to be released before 12:59:59PM GMT-12

There are no "real" guarantees. As 23meg said, Please just wait until the "official" announcement is made. From past experience, it's usually best to wait until about 3pm GMT.

---

### Post by bibekdai on 2009-10-29
> **vader897 said:**
> Just a little website I put up for occasions such as this one...
[Its the Final Countdown]("http://dl.getdropbox.com/u/1032158/its_the_final_countdown/index.html")

That's counting down to 12 midnight in Australia of the 29th. Surely it has to be released before the end of my day. After all the release name is Karmic **Koala**. :P
Good Job, Great ! :D

---

### Post by SuperSonic4 on 2009-10-29
Nothing at 12 noon GMT

---

### Post by vader897 on 2009-10-29
While I am hanging around I may as well ask.. What is with the coffee beans? what do they mean?

---

### Post by Teber on 2009-10-29
it would a members rank system. dependent on how many posts

---

### Post by spongypants23 on 2009-10-29
> **vader897 said:**
> While I am hanging around I may as well ask.. What is with the coffee beans? what do they mean?

Get your own thread.

---

### Post by mashcaster on 2009-10-29
> **fatality_uk said:**
> There are no "real" guarantees. As 23meg said, Please just wait until the "official" announcement is made. From past experience, it's usually best to wait until about 3pm GMT.

My guarantee is a real guarantee, as long as they release the OS on the 29th of this month.  Then it will definitely be released on or before the time I specified. :D

---

### Post by stuart.reinke on 2009-10-29
It's about like a kid in the car on a long trip.  Is it here yet?...Is it here yet?...Is it here yet?...Is it here yet?..............................
:lol:

---

### Post by Teber on 2009-10-29
> **stuart.reinke said:**
> It's about like a kid in the car on a long trip.  Is it here yet?...Is it here yet?...Is it here yet?...Is it here yet?..............................
:lol:

thanks for reminding me.

*starts singing the usual songs for that kind of trip*

---

### Post by mashcaster on 2009-10-29
Here you go:

[http://wwp.greenwichmeantime.com/time-zone/gmt-12/](http://wwp.greenwichmeantime.com/time-zone/gmt-12/)

So before this day is over, it will be released. ;)

---

### Post by vader897 on 2009-10-29
the problem with GMT -12 is that no countries are in that time zone.. which would mean it would be the 30th for pretty much everybody in the world if it were released at 11:50pm GMT -12.

---

### Post by Sean Moran on 2009-10-29
From here at GMT+8, I just hope it's gonna be downloaded before I wake up on Halloween, because that would be a bad omen.  I stay up late to start the download tonight on the 29th, or else I will happily wait until November, but I will not cut CDs on Halloween even if it was God's own o/s.

----o0o---

PS: I can tell by the traffic already that November looks like a better option.  Thank you from the heart to the developers of Karmic Koala, and I will download my release version on Sunday. Please understand that the work you have done is SO good that the whole world wants to have it, and NOW!

I shall wait my turn in the line.  Goodnight.

---

### Post by stuart.reinke on 2009-10-29
Just checked ubuntu Releases. It's here!!!!!!!!!!

---

### Post by matze_ on 2009-10-29
I think its up on some mirrors already, the 'rc' is gone form the filenames.

[http://ftp.heanet.ie/mirrors/ubuntu-releases/releases/karmic/](http://ftp.heanet.ie/mirrors/ubuntu-releases/releases/karmic/)
[http://mirror.as29550.net/releases.ubuntu.com/9.10/](http://mirror.as29550.net/releases.ubuntu.com/9.10/)

---

### Post by yuli_capone on 2009-10-29
In what country are you?

---

### Post by Teber on 2009-10-29
could this be it?

[http://de.archive.ubuntu.com/ubuntu-releases/9.10/]("http://de.archive.ubuntu.com/ubuntu-releases/9.10/")

---

### Post by mrmememe on 2009-10-29
The torrent is up! Hooray!!! Downloading....

---

### Post by stuart.reinke on 2009-10-29
> **yuli_capone said:**
> In what country are you?

U.S.A. central time zone

---

### Post by Teber on 2009-10-29
same here. downloading and seeding both 32 and 64 bits versions.

:guitar:

---

### Post by onclouds on 2009-10-29
> **stuart.reinke said:**
> Just checked ubuntu Releases. It's here!!!!!!!!!!

can't see it yet! =(

---

### Post by matze_ on 2009-10-29
look here, [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) if it says up to date, try it. 
i think it goes on the fastest mirrors first.

here is one in the US.
[http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/](http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/)

---

### Post by Kantis on 2009-10-29
Torrenting Karmic as I write! Woohooooo!

---

### Post by stbear on 2009-10-29
hey ppl, Karmic was released about 12 hrs ago, and i'm using it for 6 hrs already
(yeah, my Internet is slow)

---

### Post by stuart.reinke on 2009-10-29
> **onclouds said:**
> err... flamer?

it still says "Coming Soon"

check here:    [http://noncdn.releases.ubuntu.com//]("http://noncdn.releases.ubuntu.com//")

---

### Post by OpenGuard on 2009-10-29
[**DOWNLOAD ( BitTorrent )**]("http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent")

---

### Post by yuli_capone on 2009-10-29
I'm in Romania and nothing yet...but i down from the Teber link:D!!

I'm going to buy a cd:)))

---

### Post by onclouds on 2009-10-29
> **stuart.reinke said:**
> check here:    [http://noncdn.releases.ubuntu.com//]("http://noncdn.releases.ubuntu.com//")

went there after I realized you weren't saying you saw it on Ubuntu's main site =)

bittorrent away!!! =D

---

### Post by yuli_capone on 2009-10-29
690 mb size?Even in my country it's not available,i'm downloading from you guys.
I mean that It's ok?(the right image)

---

### Post by mamamia88 on 2009-10-29
hope it comes out while still on campus they have like t1 or something i just have basic dsl

---

### Post by Teber on 2009-10-29
> **yuli_capone said:**
> 690 mb size?Even in my country it's not available,i'm downloading from you guys.
I mean that It's ok?(the right image)

i'm seeding now. help yourself mate :D

and yes: 690 mb it is

---

### Post by OpenGuard on 2009-10-29
Actually, Canonical have already published the final release on their main server - [http://releases.ubuntu.com/karmic/ubuntu-9.10-desktop-i386.iso](http://releases.ubuntu.com/karmic/ubuntu-9.10-desktop-i386.iso) :)

---

### Post by baronne on 2009-10-29
My 9.10 download is coming down ... I expect the Ubuntu home page will change very soon.:popcorn:

---

### Post by stuart.reinke on 2009-10-29
> **Teber said:**
> i'm seeding now. help yourself mate :D

and yes: 690 mb it is

For the next few days I'll be removing the seeding restriction while I'm away or asleep.

Yee Haw! Ain't this fun?:p

---

### Post by Teber on 2009-10-29
a friend of mine says today is an international feast day. i sure feel jubilant. downloading went fast enough, i'm happily sharing now :D

---

### Post by ridowan007 on 2009-10-29
[http://torrent.ubuntu.com/kubuntu/simple/karmic/alternate/]("http://torrent.ubuntu.com/kubuntu/simple/karmic/alternate/")
Its updated today. Please download and seed. :)

---

### Post by TalioGladius on 2009-10-29
I'm considering moving to x64 for the first time with this release.  Will I regret that decision?

---

### Post by papangul on 2009-10-29
Ubuntu.com is not loading, it appears that karmic has been released!

Edit: According to this softpedia article published 28mins ago, karmic has officially been released already:
[http://news.softpedia.com/news/Ubuntu-9-10-Officially-Released-125578.shtml](http://news.softpedia.com/news/Ubuntu-9-10-Officially-Released-125578.shtml)

---

### Post by Marcel-X on 2009-10-29
> **TalioGladius said:**
> I'm considering moving to x64 for the first time with this release.  Will I regret that decision?

I don't think so. The few incompatibility problems that occurred a couple off releases ago should be solved by now. It's just another logical step in progress.

Downloading ubuntu-9.10-desktop-amd64.iso from [http://noncdn.releases.ubuntu.com](http://noncdn.releases.ubuntu.com) with 1.2 MB/sec. I can't wait!

---

### Post by RichJacot on 2009-10-29
Does anyone know if these are the finals for UbuntuStudio 9.10?

[http://cdimage.ubuntu.com/ubuntustudio/daily/current/]("http://cdimage.ubuntu.com/ubuntustudio/daily/current/")

---

### Post by bibekdai on 2009-10-29
Ok, its out. 
[http://noncdn.releases.ubuntu.com//releases/9.10/](http://noncdn.releases.ubuntu.com//releases/9.10/)
Cheers!

---

### Post by xtremo on 2009-10-29
> **bibekdai said:**
> Ok, its out. 
[http://noncdn.releases.ubuntu.com//releases/9.10/](http://noncdn.releases.ubuntu.com//releases/9.10/)
Cheers!

Nice one!

---

### Post by 23meg on 2009-10-29
It's **not** out, since there's been no release announcement.

Wait for it to be posted to the [ubuntu-announce mailing list]("https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/date.html").

---

### Post by BigSilly on 2009-10-29
> **23meg said:**
> It's **not** out, since there's been no release announcement.

Wait for it to be posted to the [ubuntu-announce mailing list]("https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/date.html").

Right. Thanks for that. What have we been downloading then? The RC?

:D

---

### Post by TalioGladius on 2009-10-29
Wow.  For the first time in probably 3 years I haven't looked at the beta before an ubuntu release.  Just installed it in a VM, and I'm thoroughly impressed with this release so far.

The x64 iso needs to finish downloading and then it's time to reimage this beast.

---

### Post by OpenGuard on 2009-10-29
> **23meg said:**
> It's **not** out, since there's been no release announcement.

Wait for it to be posted to the [ubuntu-announce mailing list]("https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/date.html").

I'm writing this from the final releases ISO image ( downloaded from Canonical official server ) - system is 100% up to date, which means, it's not an RC. Announcement is just a formality ..

---

### Post by bibekdai on 2009-10-29
The official download page also has changed. 
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by 23meg on 2009-10-29
> **OpenGuard said:**
>  system is 100% up to date, which means, it's not an RC. 

That doesn't necessarily mean it's the final image.

> **OpenGuard said:**
> Announcement is just a formality ..

[Not really]("https://wiki.ubuntu.com/ReleaseProcess").

---

### Post by bibekdai on 2009-10-29
> **23meg said:**
> That doesn't necessarily mean it's the final image.



[Not really]("https://wiki.ubuntu.com/ReleaseProcess").

What about this page then ? Is this the RC ? [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by 23meg on 2009-10-29
> **bibekdai said:**
> What about this page then ? Is this the RC ? [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

As far as I can see, it's Ubuntu 9.04.

---

### Post by OpenGuard on 2009-10-29
> **23meg said:**
> That doesn't necessarily mean it's the final image.

Video driver issues have been fixed, everything else seems to run just fine .. for me, it's a final release ( probably for others as well .. depending on what they need ).

> **23meg said:**
> 
[Not really]("https://wiki.ubuntu.com/ReleaseProcess").

> Release minus 1 day: 

[LIST=1]
[*]**Pre-publish the CD images. **
[*]copy .manifest to .manifest.full, and prune all images from previous releases from the .manifest file to allow timely mirror probing 
[*]Begin running the mirror prober hourly on staging.ubuntu.com to monitor the propagation of the images to mirrors 
[*]Prepare a static front-page and a list of mirrors "just in case." (Matthew Nuzum) 
[*]Publish release announcement, release notes and feature walk through on the website (Matthew Nuzum)
[/LIST]


It's pretty close to Release minus 3 hours, so yeah, the final release should be already uploaded to all servers.

---

### Post by m4tic on 2009-10-29
Its 9.10 when i click on it. Means they've finished uploading it. Yes!

---

### Post by bvanaerde on 2009-10-29
The ubuntu website is suffering from the big amount of visitors atm :o

---

### Post by 23meg on 2009-10-29
[QUOTE=OpenGuard]Video driver issues have been fixed, everything else seems to run just fine .. for me, it's a final release ( probably for others as well .. depending on what they need ).[/QUOTE]

Fine. Please don't request support, file bug reports or complain about broken features on that installation.

[QUOTE=OpenGuard]It's pretty close to Release minus 3 hours, so yeah, the final release should be already uploaded to all servers.[/QUOTE]

Read what you've quoted:

> Release minus **1 day**: 

And even if the uploaded images *are* final, that doesn't mean they're meant to be downloaded at any point until the release announcement, since mirrors all over the world are syncing, and keeping the servers busy before the release will just delay the syncing, and effectively, the release.

---

### Post by m4tic on 2009-10-29
The home page has been down for a while

---

### Post by Icehuck on 2009-10-29
> **m4tic said:**
> The home page has been down for a while

No

---

### Post by TalioGladius on 2009-10-29
> **bvanaerde said:**
> The ubuntu website is suffering from the big amount of visitors atm :oyeah my x64 download has slowed to 28kb/sec.

---

### Post by sisco311 on 2009-10-29
> **23meg said:**
> 
And even if the uploaded images *are* final, that doesn't mean they're meant to be downloaded at any point until the release announcement, since mirrors all over the world are syncing, and keeping the servers busy before the release will just delay the syncing, and effectively, the release.

Is it okay to download it via torrents?

---

### Post by 23meg on 2009-10-29
> **sisco311 said:**
> Is it okay to download it via torrents?

Please refrain from downloading via any method until the announcement.

---

### Post by OpenGuard on 2009-10-29
> **23meg said:**
> Fine. Please don't request support, file bug reports or complain about broken features on that installation.

Don't worry, I will not ask for help - I've spent 2 weeks on testing Arch .. if Ubuntu fails, *Welcome, Arch!* :mrgreen:

---

### Post by sisco311 on 2009-10-29
> **23meg said:**
> Please refrain from downloading via any method until the announcement.

ok, thanks!

---

### Post by koleoptero on 2009-10-29
It's here :D

---

### Post by lelamal on 2009-10-29
> **23meg said:**
> Please refrain from downloading via any method until the announcement.

Hi, is this a proper announcement, now?

---

### Post by xuCGC002 on 2009-10-29
> **koleoptero said:**
> It's here :D

It's funny how I was waiting for it all morning, and then I find that it's released 30min after I leave for school.

:(

Dang, now I'll really want to go home.

---

### Post by samh785 on 2009-10-29
> **xuCGC002 said:**
> It's funny how I was waiting for it all morning, and then I find that it's released 30min after I leave for school.

:(

Dang, now I'll really want to go home.
Should have just installed the release candidate :P

---

### Post by immrlizard on 2009-10-29
I have always disliked the way that the way that they have done the initial day's initial release of the software.   I always try to spread the word on the torrent locations so that folks that need to get it through the regular download methods can get it.   Sometimes it isn't easy to get the locations of those.

I have a decent machine with a lot of bandwidth looking to seed and get it out.

Lets hope it (distribution methods) continues to get better.

This is my first time on the announce list, that may solve that.

---

### Post by sisco311 on 2009-10-29
> **lelamal said:**
> Hi, is this a proper announcement, now?

I think this is the official announcement: [https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000127.html]("https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000127.html")

---

### Post by 23meg on 2009-10-29
> **sisco311 said:**
> I think this is the official announcement: [https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000127.html]("https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000127.html")

That's right, it's out now.

---

### Post by lelamal on 2009-10-29
> **sisco311 said:**
> I think this is the official announcement: [https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000127.html]("https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000127.html")

Thanks sisco311! However, I believe people interested in Ubuntu don't know anything about such lists, nor do they care at all. Clearly, if the main Website announces that it's out, well it IS out for everyone out there...

---

### Post by bibekdai on 2009-10-29
> **23meg said:**
> That's right, it's out now.
Great! Cheers :D

---

### Post by mybunche on 2009-10-29
I just couldn't keep awake...

The home page looks great!

---

### Post by the fix it man on 2009-10-29
Best release ever!

---

### Post by Megrimn on 2009-10-29
Can't wait to get home... :biggrin:

---

### Post by Catarina on 2009-10-29
Downloading now :popcorn:

I hope 9.10 final really gives me a reason to upgrade, from what I tested on the Beta and RC1, I see no real purpose in a upgrade, imo. :-#

---

