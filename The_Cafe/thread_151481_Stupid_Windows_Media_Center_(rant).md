---
title: "Stupid Windows Media Center (rant)"
date: 2006-03-28
forum: The Cafe
---

### Post by prizrak on 2006-03-28
So I decided to take the plunge into the media center world, since I don't really use my desktop anymore. So I went out and got me a Radeon 7000 with a TV out (well my GF had a TV Out but it was S-video and my TV is too old for that). I boot my favorite OS (Ubuntu) and the TV Out doesn't work. Well it actually works but the picture jumps. Now the card was listed as supported and said to use VESA drivers but it didn't work so w/e. I know that ATI support on Linux is horrible so I didn't take that as a strike against Ubuntu but I did decide to go with Windows.  
Oh and the PC is not being used as a PVR just for DVD/MP3/DIVX. 
Well first I didn't plan on using a remote and just going in through VNC so I installed regular XP. The TV Out was working fine except it would turn black and white if the tv was turned on to cable as opposed to input but turning the tv on and off solved that. Then I decided to get the remote so installed XP MCE on it (father has an MSDN subscription through his company for all OS's so it's all legit). 
One thing that annoyed me in the first place was the fact that MCE ain't nothing but an interface and there should be no reason to install a whole new OS but MS doesn't want it to be easy so a reinstall it was. Upon booting and turning the interface on it was all nice and pretty, except it wouldn't work with my Radeon, because aparently it checks for a DX9 compatible card. I found a work around for that through editing the all hated registry. I was happy for about a second when it turned out that a video card with 32MB or RAM (which ran movies just fine through WMP) was not enough for the wonder that is MCE to play ANY video. 
I dropped by my uncle's who had a spare Svideo to Composite cable and hooked up my primary card to the TV (the GF4). The MCE worked and video was played and all was good till I decided to trust MS and run through the optimization wizard. The wizard decided that a resolution different than what I, the actual owner of the TV, chose was better and changed it. That resulted in my videos being cut off on both sides, which since I watch anime was an issue because subtitles would get cut off in some instances as well, and my Japanese stops at "baka" (idiot). Of course even with the tweakmce power toy there is no option to revert back to the original resolution. 
Well then it was time to use the repair function of the installer, to make a long story short it broke my remote completely as well as my flash for online spotlight funcitonality (reinstalling flash did nothing) w/o solving the original problem. At which point I strongly considered Linux since the GF4 needed no drivers for TV Out at all (the picture was in full color and clear even through POST) but the guides out there made it seem pretty difficult plus I had to beat it at this point. So I backed up the 40 Gigs of stuff I had on there and did a clean install which of course did nothing cuz the wizard came up again and didn't actually show the changes it did (picture looked the same till MCE was restarted). 
That was time for some registry hacking, I located the key that was responsible for resolution and changed it to what I wanted it to be. As soon as MCE started up it changed the key right back. (I miss you Linux config files). Then I had an idea, if I create a new user the settings should be on default and if they are not, I can make it a limited user that is not allowed to do anything to the registry. So I create a limited user account and start MCE to see how it looks, whaddaya know the wizard doesn't come up and the interface is running at the resolution I specified (I didn't edit the registry at all). Now it's working great and I'm happy.
If I ever wonder why I switched to Linux, there is the reason - The mofing OS DOESN'T think it knows better how things should be done and lets me change the options I want if they don't work with my particular setup.
P.S. Next person to tell me Windows is easy to use and set up is gonna get stabbed in the face with my butterfly knife.

---

### Post by colsinc on 2006-03-28
I must say I had a similar experience with windows and multimedia.  not using MCE, though.  I bought a TV card (Twinhan DTV mini TER), which I installed on my windows machine, and installed the tv program that comes with it.  so, I set it to record my favourite show, minimised the program to the task bar and left it.  I didn't use the comp for a few days, but had left it on.  I checked in the day after *Lost* had been on, and guess what?  the comp had crashed and it hadn't recorded.  so i gave it the benefit of the doubt and reset it.  next week? same deal.  turned out the tv program would crash every couple of days and i would have to restart.  Now, I'm using linux.  it takes about five lines of CL commands to set the card up, kaffeine can scan DVB channels fine, and it runs perfectly.  I haven't rebooted in two weeks.:D

---

### Post by Lord Illidan on 2006-03-28
> If I ever wonder why I switched to Linux, there is the reason - The mofing OS DOESN'T think it knows better how things should be done and lets me change the options I want if they don't work with my particular setup.
P.S. Next person to tell me Windows is easy to use and set up is gonna get stabbed in the face with my butterfly knife.

Well, there are some people for whom the OS does know better how things should be done...

But I agree, the registry in Windows sucks. Config files in Linux rule!

---

### Post by frodon on 2006-03-28
For the media center concept, my god is GeekBox : [http://www.geexbox.org/en/start.html](http://www.geexbox.org/en/start.html)

---

### Post by A-star on 2006-03-28
I use Meedio for my Media Center, it runs on windows but nothing beats it imho.

---

### Post by prizrak on 2006-03-28
[QUOTE=frodon]For the media center concept, my god is GeekBox : [http://www.geexbox.org/en/start.html](http://www.geexbox.org/en/start.html)[/QUOTE]
That thing looks pretty cool, I love the Tux interface :)

---

### Post by joflow on 2006-03-28
they don't sell mce in stores because it has very specific hardware requirements.   if you run it on unsupported hardware, that's not mce's fault. I run mce without issues.  its the easiest way to get a pvr that's more feature rich then a tivo.  power users will prefer meedio or mythtv.

---

### Post by Gijith on 2006-03-28
I've also had problems with MCE. But I've read reviews that said it's been updated nicely for Vista.

---

### Post by jason.b.c on 2006-03-28
Check out,

[www.team-mediaportal.com](www.team-mediaportal.com)

it looks preaty cool too..:)

---

### Post by prizrak on 2006-03-28
[QUOTE=joflow]they don't sell mce in stores because it has very specific hardware requirements.   if you run it on unsupported hardware, that's not mce's fault. I run mce without issues.  its the easiest way to get a pvr that's more feature rich then a tivo.  power users will prefer meedio or mythtv.[/QUOTE]
Yeah that's what MS tells you, which is complete and utter BS. MCE is WinXP Pro (2K5 comes on two CD's and when it asks you to put the first CD back in, it calls it "WinXP Pro SP2" CD), with remote drivers and a remote driven interface that is based heavily on the WMP. The hardware is just fine for it (got a few friends with comps that came with MCE) the issue is that there is very little control over what the OS does. I'm sure if I had a newer TV with an S-Video/DVI/HDTV inputs it would work just fine. The point here really is that MS thinks it's users are complete and utter idiots. It's fine to have wizards and things done for the user when the user is a person who just wants an appliance as opposed to a computer but power users should be given the option to take control. Not to mention that it is completely and utterly idiotic to not have an interface that lets you adjust aspect ratio and resize the picture on the monitor if you want your product to be used with TV's. Majority of TV's do not have the same controls that computer monitors do. Not to mention many people keep TV's till they die since they tend to be fairly expensive.

Oh and to add to the woes. The wonder that is MCE is supposed to monitor the My* folders for changes. Well it did add all my songs except that for some reason when I looked at albums I ended up with three albums called "The Trinity" by Sean Paul each of which contained some of the songs from the album, two albums were "Initial D" one having all but one song and the other one having the last song, etc... I figured the reason was because I was transfering the music over the network after the reinstall so I copied everything in a different directory and deleted it all from MCE. Moved the files back and told MCE to add my music. Now I got 119 songs as opposed to about 640 and it downloaded some album info with cover art off the internet so now I got 38 albums with about 34 of them having 1 or 2 songs and the rest of my songs nowhere in sight (cept the HDD). Also don't get me started on support for container formats such as ogm or matroska, there is no option to choose subtitles or language and global codec settings are ignored by MCE cuz it knows better aparently. 
If I wasn't tired of reinstalling my OS (and the Online Spotlight thing) I would be doing a custom Gentoo based Media Center with MythTV

---

### Post by l.capriotti on 2006-03-29
I wish there would be a Linux port of XBMC (with TV support!):

[http://www.xboxmediacenter.de/](http://www.xboxmediacenter.de/)

That would be the killer ....
Luigi

---

### Post by thefamousnomo on 2006-03-29
get the live GeexBox cd. boot. evaluate. enjoy!

---

### Post by l.capriotti on 2006-03-29
my respect for GeekBox, but XBMC is on another planet compared to it.
Luigi

---

### Post by joflow on 2006-03-29
[QUOTE=prizrak]Yeah that's what MS tells you, which is complete and utter BS. MCE is WinXP Pro (2K5 comes on two CD's and when it asks you to put the first CD back in, it calls it "WinXP Pro SP2" CD), with remote drivers and a remote driven interface that is based heavily on the WMP. The hardware is just fine for it (got a few friends with comps that came with MCE) the issue is that there is very little control over what the OS does. I'm sure if I had a newer TV with an S-Video/DVI/HDTV inputs it would work just fine. The point here really is that MS thinks it's users are complete and utter idiots. It's fine to have wizards and things done for the user when the user is a person who just wants an appliance as opposed to a computer but power users should be given the option to take control. Not to mention that it is completely and utterly idiotic to not have an interface that lets you adjust aspect ratio and resize the picture on the monitor if you want your product to be used with TV's. Majority of TV's do not have the same controls that computer monitors do. Not to mention many people keep TV's till they die since they tend to be fairly expensive.

Oh and to add to the woes. The wonder that is MCE is supposed to monitor the My* folders for changes. Well it did add all my songs except that for some reason when I looked at albums I ended up with three albums called "The Trinity" by Sean Paul each of which contained some of the songs from the album, two albums were "Initial D" one having all but one song and the other one having the last song, etc... I figured the reason was because I was transfering the music over the network after the reinstall so I copied everything in a different directory and deleted it all from MCE. Moved the files back and told MCE to add my music. Now I got 119 songs as opposed to about 640 and it downloaded some album info with cover art off the internet so now I got 38 albums with about 34 of them having 1 or 2 songs and the rest of my songs nowhere in sight (cept the HDD). Also don't get me started on support for container formats such as ogm or matroska, there is no option to choose subtitles or language and global codec settings are ignored by MCE cuz it knows better aparently. 
If I wasn't tired of reinstalling my OS (and the Online Spotlight thing) I would be doing a custom Gentoo based Media Center with MythTV[/QUOTE]


MCE is for those who want it to just work right out of the box.  Thats why they take the "idiot" approach.  If you were looking for something thats more customizable and you dont want to reinstall OSs then have a look at Meedio...you can tweak it to your liking.

As for as the My Music problem.  I think its because MCE groups albums based on ID3 tags.  Make sure the tags for "album" are identical for all songs.  I have that same problem, I just didn't care enough to try to fix it.

---

### Post by joflow on 2006-03-29
[QUOTE=l.capriotti]I wish there would be a Linux port of XBMC (with TV support!):

[http://www.xboxmediacenter.de/](http://www.xboxmediacenter.de/)

That would be the killer ....
Luigi[/QUOTE]


Why not MythTV?  Is it not better then XBMC?

---

### Post by prizrak on 2006-03-29
[QUOTE=joflow]MCE is for those who want it to just work right out of the box.  Thats why they take the "idiot" approach.  If you were looking for something thats more customizable and you dont want to reinstall OSs then have a look at Meedio...you can tweak it to your liking.

As for as the My Music problem.  I think its because MCE groups albums based on ID3 tags.  Make sure the tags for "album" are identical for all songs.  I have that same problem, I just didn't care enough to try to fix it.[/QUOTE]
Actually people who want stuff OOTB get TiVo ;)
Yeah I made sure the tags were correct, I think the issue was more along the lines of MCE adding music incrementally as it was being loaded over the network. Now it doesn't seem to load more than 50 songs out of my folder even though there are like 640 songs or something. At this point it's a matter of principle to make it work :)

---

### Post by joflow on 2006-03-29
tivo is a digital vcr..its not a media center.  it can't play music or movies or access online content other then tv listings.  so people who want a media center that works out of the box use mce.  those who only want pvr functionality get tivo.

i've read that pretty much every media center software has issues with large music collections including mythtv and meedio.

---

### Post by prizrak on 2006-03-29
[QUOTE=joflow]tivo is a digital vcr..its not a media center.  it can't play music or movies or access online content other then tv listings.  so people who want a media center that works out of the box use mce.  those who only want pvr functionality get tivo.

i've read that pretty much every media center software has issues with large music collections including mythtv and meedio.[/QUOTE]
Actually TiVo can be used as a media center (according to a friend who has one) it has the online spotlight type thing that MCE comes with and you can actually put your music/video on it's HDD. I'm not sure what formats it can handle tho. I believe a media center PC would be vastly superior tho in any case. Hmm I never heard that about the music collections, maybe I should lurk some MS forums and see what's up. 
I would like to say that it's a nice product, it's just that lack of some pretty basic IMO functionality is annoying.

Edit: Found a neat little trick with MCE. Apparently MCE relies on the WMP's (Windows Media Playa) media library for the music it displays. So using that you can have a better control of the library that MCE recognizes. 
Now to figure out how to force Language/Subtitle settings from my matroska files.

---

### Post by l.capriotti on 2006-03-30
MythTV is great, but if you want a plain set top box for all your multimedia need is a huge package that needs a full distro - much like MCE. 
XBMC is a all-in-one application that, if ported to Linux, would only need a compact system, launching in seconds and not minutes...
Anyway, from the moment I'm enjoying it on my XBOX, but I'm missing the TV funcionalities that will never be implemented because of the XBOX "OS" limitations.
Luigi

---

### Post by joflow on 2006-03-30
[QUOTE=l.capriotti]MythTV is great, but if you want a plain set top box for all your multimedia need is a huge package that needs a full distro - much like MCE. 
XBMC is a all-in-one application that, if ported to Linux, would only need a compact system, launching in seconds and not minutes...
Anyway, from the moment I'm enjoying it on my XBOX, but I'm missing the TV funcionalities that will never be implemented because of the XBOX "OS" limitations.
Luigi[/QUOTE]

Wouldn't that be more of a hardware limitation since it only has tv-out.  No way of getting the cable connection.

---

### Post by joflow on 2006-03-30
[QUOTE=prizrak]Actually TiVo can be used as a media center (according to a friend who has one) it has the online spotlight type thing that MCE comes with and you can actually put your music/video on it's HDD. I'm not sure what formats it can handle tho. I believe a media center PC would be vastly superior tho in any case. Hmm I never heard that about the music collections, maybe I should lurk some MS forums and see what's up. 
I would like to say that it's a nice product, it's just that lack of some pretty basic IMO functionality is annoying.

Edit: Found a neat little trick with MCE. Apparently MCE relies on the WMP's (Windows Media Playa) media library for the music it displays. So using that you can have a better control of the library that MCE recognizes. 
Now to figure out how to force Language/Subtitle settings from my matroska files.[/QUOTE]

I guess it can play mp3s, I'm not seeing where it can play video files and an online spotlight feature on the website but maybe I'm not looking in the right place.

Still no HDTV support yet (MCE Vista will feature QAM for recording HDTV over cable and it already have OTA support).  Biggest missing feature is no multi-tuner support, so people have to stack tivos on top of each other to record two shows at the same time or watch live tv whihle its recording something.

---

### Post by prizrak on 2006-03-30
[QUOTE=joflow]I guess it can play mp3s, I'm not seeing where it can play video files and an online spotlight feature on the website but maybe I'm not looking in the right place.

Still no HDTV support yet (MCE Vista will feature QAM for recording HDTV over cable and it already have OTA support).  Biggest missing feature is no multi-tuner support, so people have to stack tivos on top of each other to record two shows at the same time or watch live tv whihle its recording something.[/QUOTE]
I'm going by what my friend says, since he's the one who owns it. I was never really interested in it because it's an appliance not a computer - ergo cannot be upgraded. There is no question as to MCE being superior to TiVo. That is not the point however, those who want the simplest possible media center will use TiVo anyone who will use a computer as one is already closer to the power user than a n00b. "Regular" users will not be running multiple tuners since those also require multiple set tops. 
And this is my real issue with MS, they make EVERYTHING idiotic even their IDE's are idiot proof. I don't see why it would be impossible to make an easy to use application that would require little effort to set up but also include some advanced functionality. Even the TweakMCE powertoy doesn't include what I view as basic functionality such as choosing MY resolution and screen size/position. I'm sure it would be perfect with a new TV that has an S-Video/DVI in but lets face alot of people still have older models since those things last forever. Though like I said I give it props it's a well thought out interface for using a remote and I like the Online Spotlight thing, I just wish it would be a little bit better.

---

### Post by benplaut on 2006-03-30
a member of my LUG decided to 'make' a mythtv box.

He bought a silent little Via box, installed Ubuntu Server w/ openbox, then set to work configuring mythtv.

He said it took him about an hour, but it runs like a charm, with planety of storage on an external 300gig ;)

---

### Post by joflow on 2006-03-31
[QUOTE=prizrak]I'm going by what my friend says, since he's the one who owns it. I was never really interested in it because it's an appliance not a computer - ergo cannot be upgraded. There is no question as to MCE being superior to TiVo. That is not the point however, those who want the simplest possible media center will use TiVo anyone who will use a computer as one is already closer to the power user than a n00b. "Regular" users will not be running multiple tuners since those also require multiple set tops. 
And this is my real issue with MS, they make EVERYTHING idiotic even their IDE's are idiot proof. I don't see why it would be impossible to make an easy to use application that would require little effort to set up but also include some advanced functionality. Even the TweakMCE powertoy doesn't include what I view as basic functionality such as choosing MY resolution and screen size/position. I'm sure it would be perfect with a new TV that has an S-Video/DVI in but lets face alot of people still have older models since those things last forever. Though like I said I give it props it's a well thought out interface for using a remote and I like the Online Spotlight thing, I just wish it would be a little bit better.[/QUOTE]


MCE is really an out of the box solution since most people buy it with new mce computers.  Its simply a matter of taking it out of the box, hooking it up to a tv/monitor and turning it on.

---

### Post by prizrak on 2006-03-31
[QUOTE=joflow]MCE is really an out of the box solution since most people buy it with new mce computers.  Its simply a matter of taking it out of the box, hooking it up to a tv/monitor and turning it on.[/QUOTE]
Unless your TV happens to be old :)

---

