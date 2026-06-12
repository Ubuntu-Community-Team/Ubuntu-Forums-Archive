---
title: "Going to sell custom Ubuntu PCs - Need ubuntu user input"
date: 2007-08-20
forum: The Cafe
---

### Post by samb0057 on 2007-08-20
I own an IT service company in the DC area. We are launching a program to sell ubuntu PCs online. We will have 5 base models, starting around $350, and fully customizable (multiple hds, optical drives, linux distros, etc.).

Our lineup will include 1 Intel and 1 AMD based value model, 1 Athlon 64 X2 based and 1 Core 2 duo based high performance model, and a Core 2 Duo/Quad based extreme gamer's model.

We are planning to offer the current Ubuntu/Kubuntu/Xubuntu/Edubuntu release as well as the most recent LTS release (so we would currently offer 7.04 and 6.06). We will also offer 64-bit versions of each of these OSes, as well as CentOS 4 and 5. A no-os option will also probably be available.

We need some input from you, Ubuntu users who may be looking to buy a computer. We want to serve the Ubuntu community, what compelled me to do this personally was that I've been looking for a 100% Ubuntu compatible PC for some time and it's very hard to find a good one. I don't like Dell's current options, System76 is quite expensive, etc. I wound up having basically no choice but to build my own, and spent countless hours trying to find compatible hardware.

What would you look for if purchasing an Ubuntu PC? Should we offer Linux Mint and/or other distributions?

I hope to get some advice here as I really want this idea to take off, both for my business and for the feeling I'll get knowing that I'm contributing to Ubuntu by providing 100% compatible machines as well as a user-friendly image for ubuntu.

Also, any ideas for how to make our site appealing to Windows users so we can bring them over to Ubuntu?

--------------

Mods: This is not meant to be spam, I'm not trying to sell anything (if i do launch this it wont be for at least a month or two anyway), I just need some advice from the Ubuntu community here. Thank you.

---

### Post by DeadSuperHero on 2007-08-20
Well, as for making an appealing site, be sure to make it slick, nice looking, and perhaps have some video demonstrations of what Ubuntu can do. Also include a video of some of the eyecandy if you are planning on including Compiz Fusion.
I think that it would be easier if you waited till October for Ubuntu/Kubuntu/Xubuntu/Edubuntu 7.10 to come out. Just a thought.
In any case, I'd buy one if there were actual stores selling them, rather than just online.

---

### Post by samb0057 on 2007-08-20
Yes we are going to offer the newest release of Ubuntu at all times, as well as the most recent LTS.

Very good idea about the ubuntu videos, this could definitely attract windows users. Hadn't even thought of that but I will definitely be doing that now.

---

### Post by samb0057 on 2007-08-20
Any idea where i can get a high quality video of beryl/compiz effects?

There are tons of them on youtube, but they are all pretty low quality, and most look unprofessional. Nice, but not suited for a business web site.

---

### Post by DeadSuperHero on 2007-08-20
Well, you could try recording your own. I've always had trouble with recording my desktop, because it takes a lot of resources on my machine.

---

### Post by dca on 2007-08-20
Make sure you can get a bunch of those Ubuntu stickers, I usually stick them (if you're looking at the side panel of PC) on the top right of the case w/ flat part facing the front.  Looks snazzy...

---

### Post by samb0057 on 2007-08-20
I would record my own, but I don't think my hardware is capable of the incredible effects you see in video son youtube, and definitely not recording them. I'll probably have to find someone I know who can make me a video, as anything hosted online is probably going to have to be compressed and low-quality.

---

### Post by cambrasa on 2007-08-20
"What would you look for if purchasing an Ubuntu PC?"

When I installed ubuntu on my PC, I still had to do three things "by hand" to get it running smoothly, requiring a lot of time, effort and expertise:

*editing the xorg.conf file to support higher screen resolutions.
*editing the ext/fstab file to turn off filesystem check on startup, which causes booting to take forever.
*installing libpam-keyring and editing some configuration file (can't remember which) so that the computer signs on to my wireless access point automatically on start up, without having to enter a password.

It would be nice if ubuntu did all those things by default. After all windows does them too. Or at least you should be able to set them in the System/Administration menu.

---

### Post by samb0057 on 2007-08-20
thanks cambrasa, that's exactly the type of advice I'm looking for. I should probably write some type of script, or manually go through every computer and set up basic stuff like screen resolutions, codecs, etc.

Keep the ideas coming!

---

### Post by NilsE on 2007-08-20
> **samb0057 said:**
> thanks cambrasa, that's exactly the type of advice I'm looking for. I should probably write some type of script, or manually go through every computer and set up basic stuff like screen resolutions, codecs, etc.

Keep the ideas coming!
I think this is the key to success.  Every user would more than likely want to system to perform to it's highest capability such as the graphics (resolution and eye candy), suspend/hibernation, networking, etc.. In other words everything that is on the system should work when delivered. 

I would suggest the script option for each system and include the script on a recovery CD with the original version of the OS, and any addon drivers to re-install in the event of a disaster. Instruction on the sleeve would also help.  IE. run Live CD, select this that and the other option, run this script and so on.

---

### Post by BDNiner on 2007-08-20
I guess you could also install some themes and backgrounds so there is a wider selection than the default offered. I would also install some applications by default. You could setup a menu system where they can choose what software they want by default. Things like having opera instead of firefox. Or amarok instead of rhythmbox. linux is all about choice so presenting these choices to your customers in a way that is not too confusing would be a great help.

---

### Post by ssam on 2007-08-20
> **samb0057 said:**
> I would record my own, but I don't think my hardware is capable of the incredible effects you see in video son youtube, and definitely not recording them. I'll probably have to find someone I know who can make me a video, as anything hosted online is probably going to have to be compressed and low-quality.

you should record compiz on the machines you are selling.

if you show a video of some effect that needs a $1000 graphics card, unstable/git versions of compiz, and hours of configuring, people will expect it out of the box when they buy a computer from you.

the only reason that you might record on a higher spec computer would be if the overhead of the recording software made the effects too slow.

you might want to look up the ubuntu OEM installer.

if you make a load of scripts or do customisation, you need to be sure that you don't break normal updates.

maybe you could add a custom repository, so that if you need to fix any of your customisation at a later date you can.

---

### Post by Bungo Pony on 2007-08-20
Change the default wallpaper. A lot of people are turned off by the orangy brown. Make a nice background with your company logo on it.

---

### Post by samb0057 on 2007-08-20
Yes, I was also thinking about writing a small manual and getting it professionally printed. I'll probably do that and include some small script or app for easy setup

---

### Post by katasuka on 2007-08-20
i think its a good idea to be making ubuntu compatible computers starting at $350. ive been looking for me a 100% ubuntu compatible desktop to replace this one and i dont have a lot of cash but all i ever see is well over $500 which sucks cuz i could go to wal-mart and get a windows comp for about $300 and remove wincrap and install ubuntu... but doing this might not work. i would be more than willing to spend the extra $50 or so and know its gonna work.

anyway, what i look for in a linux computer....
* has to be fast (duh) which means the base models need a lot of ram to run ubuntu well
* decent storage. at least 150+GB standard if possible
* at least a 15in monitor
* nvidia or ati graphics card with official drivers installed and working
* fully working soundcard (mic has to work also)
* and for those who *still* use dialup, a working dialup modem
* compatible wifi option with ethernet built in
* and of course... everything HAS to work. period. if something doesnt work, people will complain

as for suggestions for the site, i agree a vid on what ubuntu can do is a good idea
there should also be some how to vids on various things like how to use ubuntu if youre new and such

overall great idea, be sure to let me know when u lauch so i can check it out

---

### Post by dca on 2007-08-20
Doesn't Fedora 7 have a vers of X that reconfigs on the fly when PC connected to different types of monitors?

---

### Post by Omnios on 2007-08-20
Kewl a Ubuntu pc sounds kewl.

 I was thinking of something similar yes a bit different.

 Following the old e-machine idea I thought it might be interesting to make something more like a g-machine as in game. Im in the process of doing a bare bones type upgrade and using my old hard drive etc. This might also be an interesting development as a customer might be happy to save a couple hundred. 

 Anyways as I was saying it might be interesting to have some low price g-machine packages that consist of budget level motherboards be it the Asus mb with a entry level nvidia chip on board or a Gigabyte. I stated these two as they have a good reputation. I also looked into MSI which ahs a pretty good rep but also have laptop packages.

 Now the hole point here is to have a nice package of g-machines either as a PC or even a entry level laptop with a nvidia graphics card. The main point being low cost entry level as other stores etc have not caught onto this. 

Cheers

---

### Post by Mach1US on 2007-08-20
Looking more on the marketing points:
Especially important thing would be a ability to have the perspective user being able to run the software they are use to run on windows.
Highlite the options like Wine Vmserver which is now free and will allow for smooth introduction into Linux world.
Also make known a fact that almost all linux software is free and has free substitutes to expensive aplications like MS Office.
It is a key feature to put emphasis on Linux system stability and virtual immunity to conventional windows user nightmares caused by virus and spyware especially with todays sophisticated  website traps.
And as it allways is with a average pc consumer the first impression and overall look will make a difference ( definitely get rid of that brown look ) . 
Hope this helps.

---

### Post by Vadi on 2007-08-20
Excellent marketing ideas by Mach1US.

You -definitely- need to get Compiz Fusion onto them (well, Ubuntu does come with Compiz, but it's old, there's an easy guide on how to upgrade & install the settings manager that I could find if it's needed), because that's what converted me personally.

Accent on how easy it is to install software (via Add/Remove...), how much money you save (always a winner), and how linux is faster than windows (or some other fact in speed. Windows starts to degrade after a while due to all the registry changes, etc., and a normal user doesn't really know how to fix it and gets annoyed. Annoyed user with slow windows = excellent convert to the fast linux that doesn't degrade).

I would recommend that you also have an Edubuntu line - offer it to your local schools! I'm pretty sure a schools, like everywhere are on a tight budget and a special pre-configured "for learning" comp will sound enticing.

---

### Post by Paul133 on 2007-08-20
I'd recommend you make a separate /home partition on the computers. That way, if people decide to upgrade, they won't lose all their settings. 

Additionally, I'd reccomend you sell Ubuntu laptops, if possible. SInce many people can build desktops, but very few can find the necessary parts and build a laptop, they're stuck with either System76, the Dell Ubuntu, or a non-Ubuntu laptop. The first two options are pretty expensive, and the third gives no guarantee that the computer will run Ubuntu. A $499 or $599 Ubuntu laptop would be great.

Regarding Compiz Fusion, as long as the graphic cards are less than 3 years old, they should be able to run CF. I'm running CF right now on an Inspiron 1501 (AMD dual core processor, 1 gig of RAM with up to 256 MB of ATI shared video RAM) so your desktops should have no problem running CF.

Finally, I'd recommend you include common restricted codecs (eg MP3, etc.), but IANAL.

---

### Post by Vadi on 2007-08-20
I'm running CF on 512 ram with 32 mg video card...

Anyway, some more thoughts:

Like someone mentioned, the physical aspect is -very- imporant. So not only an internet-shop, but a normal walk-in shop. Why? Mostly to educate the public. People don't really go looking for new OS' when they're browsing on the internet, but when they're shopping in a mall, a computer store is a place they'll wander into.

And, if you can afford it, advertise! Everywhere! Newspapers, etc.

---

### Post by Dimitriid on 2007-08-20
Its just me but I was in the market for a Laptop and I found dell to be way too limiting in the choices and expensive too. They were also inconsistent with their offers ( I configured a system to my liking, then a week later when I was ready to make a purchasing decision they no longer had the same options available for the laptops which really turned me away from them ) I know they cannot commit to offers but it was a bit unexpected since it was not really advertised as a few days only kind of deal and the configuration just got a lot worst ( from nvidia graphics to intel, slower default processor, etc ) for basically the same price. I ended up choosing Acer which has been surprisingly compatible ( a few annoyances here and there but nothing huge ).

But to be honest things like videocards might be out of your control, lets hope not but driver support for em could take a turn for the worst. If you can make it a point never to sell ATI video solutions for example, not only cause of their support but because its just asking for trouble if you consider their linux record.

---

### Post by reacocard on 2007-08-20
My advice: Don't get fancy. Don't make drastic changes to the default Ubuntu, or huge version updates, just small things, like enabling binary drivers by default.

I would also love to see laptops in your lineup, although I understand that would be a bit harder to do. As for OSs, while limiting yourself to 6 or so pre-installed ones is good, why not also give the option of including CDs for other distros?

---

### Post by luckyd on 2007-08-21
Heres a video I made, pretty good quality you can put it on your site. It isn't completely finished but it shows most of major apps in ubuntu. Quite proud of it myself

btw I bought an ubuntu dell and I wasn't totally happy with the resolution auto configuration. I had put ubuntu on my ibook previously so I knew how to deal with it, but you should check every computer with the consumers chosen monitor (assuming you arent a big company) to make sure the resolution works correctly  

I hope you can open .rar's I just discovered them. It took a 178 meg .avi down to 10 megs. I'm never using .tar.gz's again :)

[http://www.mediafire.com/?0jxxbrakt5b](http://www.mediafire.com/?0jxxbrakt5b)

---

### Post by samb0057 on 2007-08-21
> **Vadi said:**
> Excellent marketing ideas by Mach1US.
I would recommend that you also have an Edubuntu line - offer it to your local schools! I'm pretty sure a schools, like everywhere are on a tight budget and a special pre-configured "for learning" comp will sound enticing.

Yes, we will also be offering Edubuntu.

I have decided on offering Ubuntu, CentOS, and Linux Mint. Still thinking about PCLinuxOS, but not sure yet.

---

### Post by samb0057 on 2007-08-21
Everyone

I have opened up the site for testing. It is not open for purchases of any kind, most of the functionality is still not implemented, but you can see the basic layout and functionality of the site.

It is at [www.athertek.com/store/](www.athertek.com/store/)

Take a look and let me know your suggestions. Thanks!

---

### Post by hiway on 2007-08-21
I am giving my ideas here... but hey- I have received help from this community so why not throw it out there?

I too am in the extended DC area. I work with a local e-cycler who has hundreds of used lappys and desktops coming in everyday... I am rebuilding them and selling them to end users with Ubuntu on them- at a great discount.

My suggestion would be to offer the Edubuntu package deal for prospective computer lab/school type settings with a "server" lappy for the teacher, and "workstations" for the students. Offer the whole deal with loaded machines and all of the educational software in place- it would be easy to add machines to this and the teachers of smaller children will love the programs and ease of use.

Want to team up? LOL!
I'll take west of the beltway and you can have east?   ROTF (I know, not fair huh?)

---

### Post by samb0057 on 2007-08-21
That sounds like a very good idea. I was thinking about offering an "Edu-PC" with Edubuntu preloaded, but I never though about offering a full solution such as this.

I'm sure we can definitely team up somehow though, I can link to you and vice-versa, I was also thinking about selling used Ubuntu PCs, so maybe I can come to you for supply of them.

Also, do you ever get new laptops?

---

### Post by reacocard on 2007-08-21
I like the site, clean, fast and professional-looking. My one suggestion would be to maybe add a little JavaScript to the computer-building pages so that they don't have to refresh every time you change something (it could default to the current behavior in the absence of JavaScript), but aside from that, it's excellent.

---

### Post by samb0057 on 2007-08-21
> **reacocard said:**
> I like the site, clean, fast and professional-looking. My one suggestion would be to maybe add a little JavaScript to the computer-building pages so that they don't have to refresh every time you change something (it could default to the current behavior in the absence of JavaScript), but aside from that, it's excellent.


Hey, thanks alot! Are you sure it's not too boring though? I find it to be kind of empty, but I don't know what to put in as i don't want to clutter it up with useless stuff.

I just added some new functionality, so that customizable add-ons will have descriptions with pictures and everything. so if you choose linux mint as your os, a link will appear to a page with a description along with screenshots of linux mint. this change along with a few others will be up pretty soon.

---

### Post by reacocard on 2007-08-21
> **samb0057 said:**
> Hey, thanks alot! Are you sure it's not too boring though? I find it to be kind of empty, but I don't know what to put in as i don't want to clutter it up with useless stuff.

I just added some new functionality, so that customizable add-ons will have descriptions with pictures and everything. so if you choose linux mint as your os, a link will appear to a page with a description along with screenshots of linux mint. this change along with a few others will be up pretty soon.

It is a tad empty, but wait until you have a frontpage, etc. before you judge it. It's better to have it a little empty than to have it too cluttered.

That new feature sounds great! Keep 'em coming! :D

---

### Post by bobbocanfly on 2007-08-21
If you are still getting the little introduction manual printed you should include some information about replacemnet for big Windows apps ie.

Gimp = Photoshop
OO.o = Microsoft Office
 
etc.

---

### Post by bigdidz on 2007-08-21
Unfortunately, I'm living in a underdeveloped country just north of the USA (please note that I am talking about Canada and not Québec that is the most beautiful country).  Could it be possible for you to sell in Canada too??  I know we have a free trade agreement between each other. Here, everything is windows:(

---

### Post by jc87 on 2007-08-21
Look up [reconstructor](http://sourceforge.net/projects/reconstructor) just in case you want to make Ubuntu custom ISO´s with your own configurations for your machines.

---

### Post by samb0057 on 2007-08-21
> **bigdidz said:**
> Unfortunately, I'm living in a underdeveloped country just north of the USA (please note that I am talking about Canada and not Québec that is the most beautiful country).  Could it be possible for you to sell in Canada too??  I know we have a free trade agreement between each other. Here, everything is windows:(

I don't see why not. I'll have to get my partner (he handles the legal/financial aspect of the business) to find out some more information, but if it's feasible I'll be sure to try and sell in as many countries as possible.

Thanks for the suggestions everyone!

---

### Post by Vadi on 2007-08-21
> **luckyd said:**
> Heres a video I made, pretty good quality you can put it on your site. It isn't completely finished but it shows most of major apps in ubuntu. Quite proud of it myself

btw I bought an ubuntu dell and I wasn't totally happy with the resolution auto configuration. I had put ubuntu on my ibook previously so I knew how to deal with it, but you should check every computer with the consumers chosen monitor (assuming you arent a big company) to make sure the resolution works correctly  

I hope you can open .rar's I just discovered them. It took a 178 meg .avi down to 10 megs. I'm never using .tar.gz's again :)

[http://www.mediafire.com/?0jxxbrakt5b](http://www.mediafire.com/?0jxxbrakt5b)

Wow, that's an excellent movie! Please finish it :)

---

### Post by samb0057 on 2007-08-21
Added some new features!
Now if you select ubuntu, xubuntu, centos, linux mint, etc. rather than just saying the name of the os, the name of the os is a link to a popup with a short description of the os as well as some screenshots.

athertek.com/store

also looking for more suggestions how to make it more visually appealing, and welcoming to windows users. Thanks!

---

### Post by Empath on 2007-08-21
Assess your competition, see what they have. See what you don't have, focus primarily on ease of use. Put yourself into the "what was I like when I first moved from Windows to Linux" and maybe include things such as a "Getting started with your new Linux PC" type of video which shows them how to do the basics. I mean let's face it, how many new people are gonna have the patience to read through a huge book on how to use it. Most people respond better with visual I've found. Other things you can do is have a list of "good sites for help" along with things like that.

---

### Post by Vadi on 2007-08-21
Some slogans you could use...

"Can't afford fancy Vista effects? Give Ubuntu a try - featuring (something about the, well, fancy effects)"

"Tired of your slow Windows freezing? Give Ubuntu a try - (something about it's continued stability...)

My imagination doesn't seem to be able to finish :/

---

### Post by samb0057 on 2007-08-21
I'll probably do that in my ads, but on the site itself i want to portray a feeling of Ubuntu not being like a quick-fix to windows problems, but a regular OS just like windows. I want to be able to say that all of our computers use Ubuntu casually, like it's really not a big deal at all.

Kind of hard to put what I'm trying to say into words. Good idea though I will definitely use those lines in my ads. Someone on google searching for solutions to their problems with Windows is an ideal potential customer.

---

### Post by Vadi on 2007-08-21
Right, that would be really good.

See if you can hit up System 76 for some of their [free stickers]("http://system76.com/article_info.php?articles_id=9") too ;)

---

### Post by samb0057 on 2007-08-21
Doubt they'll help me, I'm competition!
Stickers would be great though, I think I will try to have some made if it's not too expensive, or find someone who will sell them in bulk. I think i remember reading something by a guy here on the forums selling them, not sure though.

Everyone check out the new site - new color theme and new product descriptions added! Now I'm going to start working on the informational section about Linux and Ubuntu in general.

---

### Post by luckyd on 2007-08-21
its nice, but i would change the backround color from white to at least cream or something...  Being white make the logo not stand out enough. Stripes are always good too if you want to look cool. [http://www.stripegenerator.com/](http://www.stripegenerator.com/)

---

### Post by luckyd on 2007-08-21
heres the final version of my ad [http://www.mediafire.com/?5sltzylcnrk](http://www.mediafire.com/?5sltzylcnrk)

---

### Post by DougieFresh4U on 2007-08-21
A couple of days ago there was a link here in the forum to download the book of stickers and all you had to do was go get the sticker paper and print, darn, don't recall what thread I saw that in:(
I actually downloaded it (8.9MB) and it's saved in Documents, lots of pages of stickers

---

### Post by firedancer on 2007-08-21
ship outside the US  with  options on  shipment etc, etc.. 



cuz they kill plp with prices                        here  !:mad:

---

### Post by Altarbo on 2007-08-22
Hello,

I like your site and I like cheap computers.  There is something that I noticed, that while not a problem for me (or many of the other people here who will visit and comment on your site) may become a problem for you.  On your site you say that you will give free unlimited technical support by email.  You also offer many different distributions of Linux.  

Most of the distributions are very similar.  There is Ubuntu and several modified version of Ubuntu and Red Hat Enterprise (RHEL).  Having things like Linux Mint and multiple versions of the same OS is going to make it more confusing for customers, and having CentOS will make technical support more difficult (because the underlying system is so different, not necessarily because of some flaw with CentOS or RHEL).

I would recommend that you pick a base (one specific version of either Ubuntu or CentOS) and then add drop down menus for software as well as hardware.   For example, you could have a "Desktop Environment" list with XFCE, KDE, and GNOME.  You could then have a series of check boxes for "What Types of Software Would You Like Pre-Installed" (word it better, but you get the idea) with options like educational (the Edu* packages), multimedia (the Mint codecs and maybe some editing apps), and whatever else you think of.

Good luck,
Robert

---

### Post by samb0057 on 2007-08-22
> **Altarbo said:**
> Hello,

I like your site and I like cheap computers.  There is something that I noticed, that while not a problem for me (or many of the other people here who will visit and comment on your site) may become a problem for you.  On your site you say that you will give free unlimited technical support by email.  You also offer many different distributions of Linux.  

Most of the distributions are very similar.  There is Ubuntu and several modified version of Ubuntu and Red Hat Enterprise (RHEL).  Having things like Linux Mint and multiple versions of the same OS is going to make it more confusing for customers, and having CentOS will make technical support more difficult (because the underlying system is so different, not necessarily because of some flaw with CentOS or RHEL).

I would recommend that you pick a base (one specific version of either Ubuntu or CentOS) and then add drop down menus for software as well as hardware.   For example, you could have a "Desktop Environment" list with XFCE, KDE, and GNOME.  You could then have a series of check boxes for "What Types of Software Would You Like Pre-Installed" (word it better, but you get the idea) with options like educational (the Edu* packages), multimedia (the Mint codecs and maybe some editing apps), and whatever else you think of.

Good luck,
Robert


Yes, the tech support thing is not decided on but i don't think we'll be going that way. at first we were going to charge more and stuff, but now we're going for lower prices, so we can't afford to give free support.

Very good idea about the software dropdown, I may do something like that however the edu* choice is covered by edubuntu, desktop environments are covered by ubuntu/kubuntu/xubuntu, etc.

Preinstalled apps sound good though. Maybe an office package, multimedia package, etc.

The way i see it we will offer some kind of limited tech support for ubuntu, maybe or maybe not for centos. centos is more intended for advanced users anyway who are running a server, so they may not need much help. however for simplicity i may choose to use ubuntu only.

Thanks alot for your suggestions though everyone, this i really helping out!

---

### Post by samb0057 on 2007-08-22
> **luckyd said:**
> its nice, but i would change the backround color from white to at least cream or something...  Being white make the logo not stand out enough. Stripes are always good too if you want to look cool. [http://www.stripegenerator.com/](http://www.stripegenerator.com/)

Hey, thanks alot! I used that website and got a nice stripe image.

Everyone check out the new layout! It's not done, i didn't change the navbar to match the new layout, but it's getting there. Let me know what i can do to improve! athertek.com/store

---

### Post by Altarbo on 2007-08-22
> **samb0057 said:**
> Yes, the tech support thing is not decided on but i don't think we'll be going that way. at first we were going to charge more and stuff, but now we're going for lower prices, so we can't afford to give free support.That's understandable.  You might want to send an email to Canonical and see if they'll let you sell their support through you website.  You could have it optional like it is for normal Ubuntu users.

> Very good idea about the software dropdown, I may do something like that however the edu* choice is covered by edubuntu, desktop environments are covered by ubuntu/kubuntu/xubuntu, etc.Ubuntu, Edubuntu, Xubuntu, and Kubuntu are identical under the hood though.  You could do a minimal server install of Ubuntu and then install any of the four on top.  I was saying that it might confusing to list different variants of Ubuntu that are the same underneath next to something like CentOS which is significantly different.  It sounds like you have a more technical target audience in mind though, so the confusion factor probably won't be as big a deal.

> Preinstalled apps sound good though. Maybe an office package, multimedia package, etc.

The way i see it we will offer some kind of limited tech support for ubuntu, maybe or maybe not for centos. centos is more intended for advanced users anyway who are running a server, so they may not need much help. however for simplicity i may choose to use ubuntu only.

Thanks alot for your suggestions though everyone, this i really helping out!Welcome and the best of luck.

---

### Post by samb0057 on 2007-08-22
I see what you mean about the variants of ubuntu, with 64 bit and lts releases, i have 16 variants of ubuntu available. I'm trying to think of a practical solution but its hard to find this middle ground between freedom of choice and straightforwardness. I am aiming for a technical audience, but one of my main goals doing this is to try to convert new users to ubuntu by giving them good deals, so i have to make my site understandable and easy to use for Linux novices.

---

### Post by katasuka on 2007-08-22
> Heres a video I made, pretty good quality you can put it on your site. It isn't completely finished but it shows most of major apps in ubuntu. Quite proud of it myself

btw I bought an ubuntu dell and I wasn't totally happy with the resolution auto configuration. I had put ubuntu on my ibook previously so I knew how to deal with it, but you should check every computer with the consumers chosen monitor (assuming you arent a big company) to make sure the resolution works correctly

I hope you can open .rar's I just discovered them. It took a 178 meg .avi down to 10 megs. I'm never using .tar.gz's again

[http://www.mediafire.com/?0jxxbrakt5b](http://www.mediafire.com/?0jxxbrakt5b)

had to say also 7-zip compresses it to 9.4MB :D

the best way to compress a vid, convert it to theora but till theora becomes a standard, people on windows will need the codecs (would have to install it themselves) and google vid and youtube doesnt seem to support theora (yet).

---

### Post by bigdidz on 2007-08-23
Personally, I think that the strength of Linux is versatility.  Unfortunately, not a lot of people (like me) know how to use it and only see a easy way to crash there computer.

If I were you, I would try to make it possible to customers to customize there software the same way the they would expect to customize my hardware.  I imagine a web-questionnaire that ask what they would expect that there computer will do for them and recommend them witch packages they would need to get install.

Don't forget that Linux have just to much too much softwares and that the "normal Linux user" is faraway to know them all. In addition, if you have 10% of your customers that are real newbies they will know about nothing.

Nevertheless, some of you customers will probably know much more than you about Linux.  Let them use there knowledge to customize there computer as far as they want.

good lock,

Didier Amyot

---

### Post by Omnios on 2007-08-23
K here is a way to sell lots of computers and have happy customers. I learned this when a old friend of mine bought a putter with an amazing tower box however there was nothing special in that box.

 Anyways This is the deal on this. Now I am not saying go buy super expensive boxes but rather find a decent and kewl looking box that is around the same price of a regular box and you customers will be a lot happier. Go black or some other color. Have a few kewl leg lights. A nice from preferably without a door panel. Maybe some plexi.

 Explain the costs of the box and possible alternatives. Such as a cooling package of extra fans etc. Now they can get the no fan or fan choice but It becomes there choice. 
 
 Another consideration may be decal stickers to spruce up there box a bit. Personally the BSD mascot logo is ubber.

 Anyways do some research and see what you can come up with.

May the force be with you.
 Trust in the power of a cheap ubber box

---

