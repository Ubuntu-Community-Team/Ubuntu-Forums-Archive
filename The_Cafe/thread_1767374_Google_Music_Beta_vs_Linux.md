---
title: "Google Music Beta vs Linux"
date: 2011-05-25
forum: The Cafe
---

### Post by Madspyman on 2011-05-25
Got an invite to this but it's still way in beta. First off currently there's no Linux support (not even for Chrome OS) for the Music Manager app that's required to upload your music with. Second Music Manager doesn't support ogg even though both Chrome browser/OS and Android both do.

Now the service is pretty useless if you can't upload music to it, but I was eventually able to get Music Manager working in Linux using Wine. Unfortunately the installer wouldn't work so I had to copy the MusicManager folder from       

Users/Yourname/AppData/Local/Programs/Google/MusicManager (do the windows slashes go the other way?) of a windows vm.

It runs (buggy like) in Wine right out of the folder but only seems to upload DRM free mp3 files. 

Streaming music is actually pretty nice i really like the interface it's very easy to navigate. It also syncs well with my Droid X. The Music Beta Android app could use some work though.

As a music locker, once they work out all the compatibility issues, this will be top notch. However, Amazon has them beat due to the fact you can buy music from them and you don't need to download an app to upload music so it's currently even more compatible with Google's OS than Google's service is.

Edit: The version of wine in the Ubuntu repo's won't work for this you need 1.3 from the Wine PPA, also it seems to only work on folders filled with drm free mp3 files it hangs forever on any other file type. Also it's a bit buggy sometimes it takes a sec to start uploading.

Here's a link to a Music Manager folder without the installer.

[Google Music Manager Without Installer]("http://www.mediafire.com/?n4k334kki094d51") - Kilbasar's link.

Update: Their is now a Native Linux version of Music Manager, the Wine process above is no longer necessary.

[http://www.google.com/support/music/bin/answer.py?hl=en&answer=1229972&topic=1100183]("http://www.google.com/support/music/bin/answer.py?hl=en&answer=1229972&topic=1100183")

---

### Post by zach4618 on 2011-05-25
I just got an invite for Music Beta and am now having the same problem - no Linux version of the Music Manager. Its also a shame that they dont support .ogg files. Come on Google! ChromeOS and Android are both based on Linux. Can't your services play nice with Ubuntu?

---

### Post by galacticaboy on 2011-05-25
Glad everyone is getting invites... I signed up for an invite the day it came out and never got one.

---

### Post by Madspyman on 2011-05-25
> **zach4618 said:**
> I just got an invite for Music Beta and am now having the same problem - no Linux version of the Music Manager. Its also a shame that they dont support .ogg files. Come on Google! ChromeOS and Android are both based on Linux. Can't your services play nice with Ubuntu?

Seems Wine is the only way right now and the MusicManager.exe installer doesn't work which is weird. I imagine if I tar'd up the Music Manager program folder it would work for anyone willing to install Wine. Google should at least offer a Wine solution until they get their native Linux app out.

---

### Post by smellyman on 2011-05-25
google taking over the world is not a good thing.

---

### Post by zach4618 on 2011-05-25
> **Madspyman said:**
> Seems Wine is the only way right now and the MusicManager.exe installer doesn't work which is weird. I imagine if I tar'd up the Music Manager program folder it would work for anyone willing to install Wine. Google should at least offer a Wine solution until they get their native Linux app out.

Can I take you up on your offer?

---

### Post by milhouse07 on 2011-05-25
i used virtual box to upload stupid music, took forever too. didnt think of using wine, will try it tonight!

---

### Post by Madspyman on 2011-05-25
Needs wine 1.3 the version in the ubuntu repo wont work.

---

### Post by Kilbasar on 2011-05-26
Hi All,

I can confirm that although the installer does not work in Wine, the actual Music Manager works fine (Wine 1.3). I just pulled the files from a VM, and ran them straight from the extracted directory.

So that others don't have to first install it in a VM just to extract the files, here they are.

[Google Music Manager Without Installer]("http://www.mediafire.com/?n4k334kki094d51")
md5: dd76c2d72997aeb6cad682621c9c320e

Enjoy!

---

### Post by forrestcupp on 2011-05-26
I hope Google isn't trying to come up with their own version of iTunes. All we need is a crappy alternative to another crappy concept for software.

And I *really* hope they're not working this toward forcing us to sync with Android. One of the main things I like about Android is not being tied to something like iTunes.

---

### Post by Kilbasar on 2011-05-26
I wouldn't get too worried. Although I'm annoyed there's no Linux client (or just a basic Java client) for uploading, you basically DO need a local piece of software when you want to upload thousands of files, and possibly then keep them in sync locally/remotely. The Music Manager ONLY does uploading, it's not in the slightest way iTunes-y. The actual Music Beta player is web-based, and the android app for it plays local files just file.

---

### Post by Sunflower1970 on 2011-05-26
Kilbasar: Thanks for the files. Music Manager now works :-) Unfortunately, I'm unable to upload any music. I keep getting an error saying the servers are down. Oh, well. 

Between Amazon Cloud, Google Music Beta and MP3Tunes, I can have a significant amount of my collection somewhere in the 'cloud' 

I also use Subsonic, but since my connection is kind of slow, that works best on my home network.

---

### Post by Kilbasar on 2011-05-26
> **Sunflower1970 said:**
> Unfortunately, I'm unable to upload any music. I keep getting an error saying the servers are down.

What version of wine are you using? Run "wine --version" if you're unsure. AFAIK it only works with 1.3x, not 1.2x. You can upgrade to 1.3x with:

```
sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo aptitude update
sudo aptitude install wine1.3
```

Yeah, subsonic is great, but like you, my terrible home DSL is not fast enough to make it feasible, and my ultra-cheap shared hosting does not support tomcat. I ended up going with Ampache, which is entirely PHP based (with a MySQL backend), so I was able to install it on my shared hosting. It is not as featureful as subsonic, but has all the basics (including android/iPhone/webOS apps), and is very easy to set up. I definitely recommend it to anyone with the same kind of unlimited-but-limited shared hosting that I have, as all you need is PHP and MySQL.

---

### Post by mdshann on 2011-05-26
Does no one use Ubuntu one? Seems like after getting an O/S for free the least we can do is help support them by using their music cloud service. It even streams to Android and iPhone!

---

### Post by Kilbasar on 2011-05-26
I hear you, but for how little I use streaming music (I'm mostly underground on the subway with no cloud access), $4/month isn't worthwhile, especially when I'm already paying for web hosting elsewhere. Once Google Music decides to charge, I'll probably stop using that as well, right now it's mostly in the "Ooh shiny free toy" category.

---

### Post by mdshann on 2011-05-26
I can understand that! Free is good that's why I have an amazon aws account even though all I use it for is minecraft lol.

---

### Post by jhonan on 2011-05-26
> **Kilbasar said:**
> Once Google Music decides to charge, I'll probably stop using that as well, right now it's mostly in the "Ooh shiny free toy" category.
They won't charge directly. It's all about advertising revenue.

---

### Post by hfw on 2011-05-26
Does anyone know if Google's music manager will follow sym links?

---

### Post by Madspyman on 2011-05-26
> **Kilbasar said:**
> Hi All,

I can confirm that although the installer does not work in Wine, the actual Music Manager works fine (Wine 1.3). I just pulled the files from a VM, and ran them straight from the extracted directory.

So that others don't have to first install it in a VM just to extract the files, here they are.

[Google Music Manager Without Installer]("http://www.mediafire.com/?n4k334kki094d51")
md5: dd76c2d72997aeb6cad682621c9c320e

Enjoy!

Added your link to my op.

---

### Post by Madspyman on 2011-05-26
There was a wine-less cloud based solution to this.

[https://chrome.google.com/webstore/detail/obojocfchdgdpgcigcdhdnlakfcbbgfn?hl=en-US]("https://chrome.google.com/webstore/detail/obojocfchdgdpgcigcdhdnlakfcbbgfn?hl=en-US")

It worked great until recently.

[http://groups.google.com/group/chrome-notebook-pilot/msg/a61c76431d88cba9]("http://groups.google.com/group/chrome-notebook-pilot/msg/a61c76431d88cba9")

The only reasoning behind it was that Google changed something. Wonder what's up with Google lately.

---

### Post by LowSky on 2011-05-27
I just use Amazon's cloud player. Since Banshee connects to the Amazon Store and I can set Amazon to keep all new purchased on their Cloud drive and/or download them directly, I don't need extra services like Google's.

---

### Post by Madspyman on 2011-05-27
> **LowSky said:**
> I just use Amazon's cloud player. Since Banshee connects to the Amazon Store and I can set Amazon to keep all new purchased on their Cloud drive and/or download them directly, I don't need extra services like Google's.

Amazon cloud player is where it's at right now, best support for all OS's, however the look of it's user interface leaves something to be desired. I love how Google's looks, it feels less cluttered, not to mention the 20,000 song limit, way more free space than Amazon. Other than that Google dropped the ball big time on OS support and doesn't offer a music store, but hey it's still only beta.

---

### Post by Sunflower1970 on 2011-05-27
> **Kilbasar said:**
> What version of wine are you using? Run "wine --version" if you're unsure. AFAIK it only works with 1.3x, not 1.2x. You can upgrade to 1.3x with:

```
sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo aptitude update
sudo aptitude install wine1.3
```


I'm running wine 1.3. Tried uploading some stuff today and it's still not taking it...

I'll have to play around with this this weekend to get it to work...

ah, well.

---

### Post by Madspyman on 2011-05-27
> **Sunflower1970 said:**
> I'm running wine 1.3. Tried uploading some stuff today and it's still not taking it...

I'll have to play around with this this weekend to get it to work...

ah, well.

What file types are you trying? .mp3 files are the only thing I've been able to get uploaded any other file type seems to hang indefinitely.

---

### Post by beew on 2011-05-27
I don't use this kind of stuffs but I think it will come to Linux, just have to wait. Remember it took a while for googletalk to support Linux. I think the abuse of WINE may have the effect that vendors are actually less likely to support Linux, if you can use some crippled version in WINE and that is good enough why bother making a native Linux version?

---

### Post by hfw on 2011-05-27
I can confirm that it hangs on .wma files.  (I know, embarrassing, but I've got them from before I converted to Ubuntu.)  .mp3 files are uploading fine for me.

---

### Post by Sunflower1970 on 2011-05-27
I'm uploading mp3's. 

I have had a minor success so far. I see one song has uploaded (out of 19), so maybe it just takes a very. long. time..?

I also have some .wma files that were given to me...I haven't tried to upload any of those, yet.

Too bad ogg isn't supported. That's what the bulk of my collection is. Oh, well. I'll just dream that support will happen, some day. (I'll dream that Amazon will also support that file type, some day too.)

---

### Post by hfw on 2011-05-27
It keeps freezing on me.  I have to stop it and restart it, but it is working.  About 40 songs uploaded so far.

---

### Post by Madspyman on 2011-05-27
> **Sunflower1970 said:**
> I'm uploading mp3's. 

I have had a minor success so far. I see one song has uploaded (out of 19), so maybe it just takes a very. long. time..?

I also have some .wma files that were given to me...I haven't tried to upload any of those, yet.

Too bad ogg isn't supported. That's what the bulk of my collection is. Oh, well. I'll just dream that support will happen, some day. (I'll dream that Amazon will also support that file type, some day too.)

Yeah nearly my entire collection of music is in ogg format. I've uploaded all my .mp3 files already and really would rather not have to convert my music collection to mp3 just to stream it from Amazon or Google. 

Google sent me this email, upon my support requests. 

> Thank you for your note.

We don’t currently offer a Linux version of the Music Manager, nor ogg vorbis format support.

We're constantly working to improve Music Beta, and I'll make sure to pass your request on to the rest of the team.

We appreciate your feedback.

Regards,

Bryce
The Music Beta Team

However Chrome/ium browser has ogg support. I'm starting to wonder if the Google Music Beta team is made up of the same guys on the Google Sketchup team.

---

### Post by sebmaynard on 2011-05-28
Alternatively, you could use:

[https://chrome.google.com/webstore/detail/obojocfchdgdpgcigcdhdnlakfcbbgfn](https://chrome.google.com/webstore/detail/obojocfchdgdpgcigcdhdnlakfcbbgfn)

Looks good so far! No where near as fully featured as the proper app, but runs in Chrome without installing anything else :)

---

### Post by trendit on 2011-05-28
Thanks for sharing the link.

---

### Post by Hooya on 2011-05-28
Really glad for this thread. First thing I did was request a Linux native app, or to make the app Wine friendly. For four days I uploaded using VirtualBox, but now I'm trying the Wine workaround posted in the OP.

If that starts to fail I've installed the Chrome app/extension from the previous page (thanks!)

Glad to see the Ubuntu community working on this. I'm sure Google is working on OGG and Linux support, but they know their main userbase is Windows/Mac with MP3 files.

Almost 3000 songs uploaded so far, out of 12k. Neat service, for sure.

---

### Post by zachthejones on 2011-05-28
I've been using the Wine workaround posted earlier. At first it gave me the error about not being able to access the servers, but I just left it to run last night and it uploaded a few songs. I've got it running now and it seems to be working, albeit very, VERY slowly.

I tried the Chrome Webstore App posted above last night, but it just froze and did nothing. Have they gotten it working? I'd almost prefer to upload stuff that way.... (not a control freak at all... ;-)

I do have faith that eventually there will at least be a way to upload via the browser...but I'm praying that comes sooner than later.

---

### Post by Madspyman on 2011-05-28
> **zachthejones said:**
> I've been using the Wine workaround posted earlier. At first it gave me the error about not being able to access the servers, but I just left it to run last night and it uploaded a few songs. I've got it running now and it seems to be working, albeit very, VERY slowly.

I tried the Chrome Webstore App posted above last night, but it just froze and did nothing. Have they gotten it working? I'd almost prefer to upload stuff that way.... (not a control freak at all... ;-)

I do have faith that eventually there will at least be a way to upload via the browser...but I'm praying that comes sooner than later.

I posted about that link earlier,

> **Madspyman said:**
> There was a wine-less cloud based solution to this.

[https://chrome.google.com/webstore/detail/obojocfchdgdpgcigcdhdnlakfcbbgfn?hl=en-US]("https://chrome.google.com/webstore/detail/obojocfchdgdpgcigcdhdnlakfcbbgfn?hl=en-US")

It worked great until recently.

[http://groups.google.com/group/chrome-notebook-pilot/msg/a61c76431d88cba9]("http://groups.google.com/group/chrome-notebook-pilot/msg/a61c76431d88cba9")

The only reasoning behind it was that Google changed something. Wonder what's up with Google lately.

The creator of MusicAlpha declared it dead.

> I looked into it and I really just don't understand why it doesn't work. I 
guess MusicAlpha is now officially dead. 

They still haven't fixed it and unfortunately the wine method is the only method that works. Google's own OS is currently the only one without any kind of fix for uploading to Music Beta.

---

### Post by geocode on 2011-05-29
Any tips on getting this working under wine?

So far I have:

download the MusicManager (already installed zip version from page 1).
Unzip
wine MusicManager.exe

And this starts out okay enter email pick type of music to use (itunes, windows media player, etc.)

First thing I noticed is that if I select pick folders it is missing the add and remove buttons and so the Next button is disabled.

Second no matter what I pick it goes to 95% and just hangs.

And subsequent starts it doesn't even start or it goes back to the beginning.

I am using wine 1.3.19.

What versions are working?

---

### Post by zachthejones on 2011-05-29
geocode, check and see what version of Windows Wine is set to run under. I think the default is XP. I had gotten an error message when first starting the program through Wine, so I switched it to run them in Windows 7 mode. It's uploading, just incredibly, incredibly slow. Over the last three days I've run it somewhere around 15 hours, and it's working on my eighth song right now. Ridiculously slow.

Does anyone know if the uploading program runs this slow in regular windows, or if there's some sort of interference thing going on when we use Wine. Or am I the only one uploading this stinking slow in Wine?

---

### Post by geocode on 2011-05-29
Okay so, I had to switch to i686 version of wine and then it started working.

I had rebooted into Windows (bluck!) and was able to upload about 800 songs in < 24 hours -- although windows stopped my internet connection twice so I really think it would have been around 14-16 hours.

So far I think I have only gotten the wine version to upload two songs...  I think I was uploading about 128k / second on windows and ... maybe close to immeasurable on wine....

---

### Post by neuralpathway on 2011-05-29
Not that this will much help other than verifying what you are experiencing, but I'm exact same thing slow upload happening over here.

At first run after starting my system it seems to upload a few MP3's but then starts slowing down to a crawl.

---

### Post by geocode on 2011-05-30
It seems to me that this is a problem in the wine network stack. I see several messages on the console about address and changes and not handled. I saw in the change logs about fixes in the network stack in 1.3.20.  I only have version 1.3.19.  Has anybody tried with a more recent version. Maybe we can file some bugs?

---

### Post by frankcm3 on 2011-05-30
Using wine 1.3.21 on Natty with limited success. Individual uploads are relatively quick(1-2 min per song) but it stops and must be quit and restarted often. 170 out of 1500 songs uploaded so far. Setting wine to win7 instead of XP seems to improve performance. No luck at all with the chrome extension.

---

### Post by zachthejones on 2011-05-30
I just did a VirtualBox installation of Windows Vista (yeh, sucks - was the only 32 bit version of Windows I had handy). Shared my music folder and ran the upload from there. It's running pretty snappy now. I threw up a [guide]("http://linux.zachjones.net/2011/05/30/google-music-uploading-in-ubuntu-11-04-using-virtualbox-and-windows/") so I could remember what I did to get it running. 

Not the greatest solution, but it works better than the Wine solution at the moment.

---

### Post by geocode on 2011-05-30
Yeah that's what I had to resort to also...

Hate having to boot any kind of windows anything...

But 336 songs since late this morning when I got it started... (10 hours maybe?).  Still seems slow but not like under wine.

---

### Post by hfw on 2011-05-31
This morning wine update from the ppa seems to have made a difference.  I just uploaded about 40 songs at almost 700k up before it froze and I had to restart it.  A big improvement from yesterday.

---

### Post by Rotarychainsaw on 2011-05-31
> **hfw said:**
> This morning wine update from the ppa seems to have made a difference.  I just uploaded about 40 songs at almost 700k up before it froze and I had to restart it.  A big improvement from yesterday.

Wanted to report the same thing. Wine update and things are much faster. I hope it keeps going.

---

### Post by Rotarychainsaw on 2011-06-03
Any updates? The uploader stopped working but I didn't change anything in WINE or whatever. Is there a new uploader version out? Maybe I need to reinstall wine.

---

### Post by bluescreenkid on 2011-06-03
I've written an installation script to get Google Music Manager running on Ubuntu.

I used a version of GMM that I downloaded yesterday, so I don't know if that will help anyone out.

Please let me know if it works OK, as I have only tried it on 2 PCs so far.

[http://goo.gl/5W7eX](http://goo.gl/5W7eX)


Thanks

BSK :D

---

### Post by aysiu on 2011-06-03
> **bluescreenkid said:**
> I've written an installation script to get Google Music Manager running on Ubuntu.

I used a version of GMM that I downloaded yesterday, so I don't know if that will help anyone out.

Please let me know if it works OK, as I have only tried it on 2 PCs so far.

[http://goo.gl/5W7eX](http://goo.gl/5W7eX)


Thanks

BSK :D
I'm not saying this is necessarily malicious (haven't tested it out myself), but I would caution new users against downloading your script.

You're a new user who joined today with 0 other posts. And the first post is a link to something you've created that you want others to install. It looks a little fishy, if not phishy.

---

### Post by bluescreenkid on 2011-06-03
> **aysiu said:**
> I'm not saying this is necessarily malicious (haven't tested it out myself), but I would caution new users against downloading your script.

You're a new user who joined today with 0 other posts. And the first post is a link to something you've created that you want others to install. It looks a little fishy, if not phishy.

i absolutely agree with you & you are quite correct. i only joined this forum, as i created the script this afternoon and saw people on here were having problems, so thought i would help out.

i don't know how i can prove it is not a phising application but all i did was to copy the files google music manager installed in windows, across to my ubuntu PC and wrote a script to copy the files into their correct place within the wine directory. then tied it all together to create the menu entry.

as i said before, i joined here to help people out but perfectly understand the hesitancy.

BSK :D

---

### Post by bwitt on 2011-06-03
I gave your installer a try, BSK. It installed fine, but I can't get beyond the login screen. It freezes up before I can finish entering my email. I had the same result when I tried this one, too - [http://code.google.com/p/google-music-manager-linux-wine/](http://code.google.com/p/google-music-manager-linux-wine/) . 

Any ideas? I'm really looking forward to getting this working!

Cheers!

---

### Post by Madspyman on 2011-06-03
> **bwitt said:**
> I gave your installer a try, BSK. It installed fine, but I can't get beyond the login screen. It freezes up before I can finish entering my email. I had the same result when I tried this one, too - [http://code.google.com/p/google-music-manager-linux-wine/](http://code.google.com/p/google-music-manager-linux-wine/) . 

Any ideas? I'm really looking forward to getting this working!

Cheers!

Are you using wine 1.3?

---

### Post by bwitt on 2011-06-03
> **Madspyman said:**
> Are you using wine 1.3?

No, I wasn't. But I am now and everything is good. 

Thanks!

---

### Post by bluescreenkid on 2011-06-04
> **bwitt said:**
> No, I wasn't. But I am now and everything is good. 

Thanks!

glad you got it working. the feedback i have got from other people is that it works OK with WINE 1.3. follow the instructions below to install it from the PPA

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```


BSK :D

---

### Post by gnomeuser on 2011-06-04
What I like about the Google Music approach from what I have seen so far is that rather than worry about how much space I use, it counts items. In theory I hope this means I can upload my FLACs without transcoding.

I got U1 Music streaming but having to separately transcode everything into Ogg Vorbis and then having to pay per every 20GB. I would use my FLACs there but seeing as my combined collection reached 1TB a while ago that would bankrupt me. Also U1 lack a web frontend for playing music and it overall feels poorly tagged on to an already annoyingly useless syncing service.

Since I don't run either service myself, I would worry about people such as the RIAA. They'll sue grandmas and dead people using the flimsiest of evidence, generally with disturbing success. While I generally have a good audit trail for my stuff I am sure they wouldn't stop them nor protect me and I am near certain that most of these services would bend me over, hand over my data and personal information to any sufficiently well paid group of lawyers.

At any rate while Google Music is desirable technology, it is not available in Brazil.

---

### Post by bluescreenkid on 2011-06-05
just had some feedback from my Google Music Manager on Ubuntu script, that might help out users of it and hopefully all people who are running GMM on ubuntu.

the tip comes from @dewguzzler on twitter.

if you set GMM to run in Windows 7 mode it works better when uploading.

for those that don't know how to do this, please follow the instructions below.

Applications > Wine > Configure Wine

Make sure you are on the Applications tab and click on the Add Application button. Goto where the MusicManager.exe is located.

*for users of my script it is located in users/<username>/Local Settings/Application Data/Programs/Google/Music Manager*

Highlight MusicManager in the Application Settings Window & user the Windows version drop down menu to select Windows 7. Click OK and you're finished.

Hope this helps out and thanks to @dewguzzler for the tip.


BSK :D

---

### Post by bluescreenkid on 2011-06-06
Just thought you might like to know I have released Google Music Manager install for Ubuntu version 2.

It's totally different and might work on other versions of Linux asides from Ubuntu but this hasn't been tested yet.

Unlike my previous script, it mimics the Windows MusicManagerSetup executable to retrieve the URL for downloading MusicManagerSetup.exe. Hopefully, if Google do decide to change the location, my script should have it covered.

Script Download URL : goo.gl/O4yFR
README is also available to read at [http://pastebin.com/CYpEY300](http://pastebin.com/CYpEY300).

Feedback is always welcome.

BSK :D

---

### Post by zachthejones on 2011-06-06
Okay, I have been uploading my collection (5,900+ files) with a virtualbox installation of Vista. I'm nearing the 4,000 mark in my uploads, but would love to switch off Vista. I am running the most updated version of Wine, and I even snagged an updated Music Manager installation script/package from [here]("http://ge.tt/9gTtUn4/v"). The uploads seem to be running at the same speed or faster than what I'm getting from my Vista VM. The only thing is, when I run the Music Manager in Wine (on Ubuntu), it is only showing that I have 27 songs uploaded. Should I just let it run for awhile and see if it realizes it already has over half my collection as it scans?

I just don't want to have to re-upload most of my collection or spend a bunch of time deleting doubles on Google Music.

Anyone else having this issue switching back from using a virtual machine to a Wine-assisted version of the Music Manager?

---

### Post by ARS on 2011-06-06
Works with latest wine (as mentioned above).
I have it working with wine 1.3 (emulation windows 7), Ubuntu 11.04.
**How I set it up:**
INSTALL WINE
```
sudo add-apt-repository ppa://ubuntu-wine/ppa
sudo apt-update
sudo apt-get install wine1.3
```

GET MUSICMANAGER
[http://code.google.com/p/google-music-manager-linux-wine/](http://code.google.com/p/google-music-manager-linux-wine/)

either use wine MusicManager.exe
or just double click the MusicManager.exe

Uploading at my max rate so seems to be good, songs also appear correctly online so far.

---

### Post by cyb3rkn19ht on 2011-06-07
Thank you!

Working great in Wine 1.3. I thought Google was above the no Linux support :(

---

### Post by Madspyman on 2011-06-08
> **cyb3rkn19ht said:**
> Thank you!

Working great in Wine 1.3. I thought Google was above the no Linux support :(

Yeah it's kind of embarrassing, currently the only way to upload music to Music Beta in Linux is through Wine, however Google's own Chrome OS is Linux, but you can't install Wine to it, making it currently the only OS not supported, maybe not the only one, but you get my point.

---

### Post by altheablue on 2011-06-10
[SIZE=2]Thanks for the help, various people in this thread. :cheers: <--this needs to be a smilie!

But... has anyone else had the downloading (uploading?) hang up completely? It was going fine the first day I set it up, and every time I've logged in since, it's stuck at 65 songs. I've restarted ~3,456 times, re-added the folder, tweaked the settings..so I just wondered if I'm the only one. :?

Edit: hmm, nevermind. It did actually download all my songs; it just didn't tell me that. Ok, carry on. :D
[/SIZE]

---

### Post by one.finefellow on 2011-06-14
> **Kilbasar said:**
> Hi All,

I can confirm that although the installer does not work in Wine, the actual Music Manager works fine (Wine 1.3). I just pulled the files from a VM, and ran them straight from the extracted directory.

So that others don't have to first install it in a VM just to extract the files, here they are.

[Google Music Manager Without Installer]("http://www.mediafire.com/?n4k334kki094d51")
md5: dd76c2d72997aeb6cad682621c9c320e

Enjoy!

This worked incredibly well.

Thank you.

---

### Post by oldarney on 2011-06-15
Worked perfectly, thank you.

Just wish I didn't have to do this... uber fail from google. Adobe and Google, your on notice.

---

### Post by pt123 on 2011-06-15
> **Madspyman said:**
> Yeah it's kind of embarrassing, currently the only way to upload music to Music Beta in Linux is through Wine, however Google's own Chrome OS is Linux, but you can't install Wine to it, making it currently the only OS not supported, maybe not the only one, but you get my point.

When will people realise Google doesn't care about the Linux desktop. Ubuntu should be cautious, this talk of switching to Google Chrome by Canonical is dangerous. Firefox and Mozilla are the true champions of the Linux desktop, always offering native linux versions of their applications.

---

### Post by joelzehring on 2011-06-16
bluescreenkid:

Thanks for wrapping up the GMM solution into a super-simple script. It's got about 40 of my 2000 songs up and still chugging.

---

### Post by zaphodbblx on 2011-06-17
> **kilbasar said:**
> hi all,

i can confirm that although the installer does not work in wine, the actual music manager works fine (wine 1.3). I just pulled the files from a vm, and ran them straight from the extracted directory.

So that others don't have to first install it in a vm just to extract the files, here they are.

[google music manager without installer]("http://www.mediafire.com/?n4k334kki094d51")
md5: Dd76c2d72997aeb6cad682621c9c320e

enjoy!

thanks dude!

---

### Post by hazelnut on 2011-06-17
You people should stop congratulating each other for figuring out how to use a windows solution (wine/vbox) and send google a note requesting support!  I did today.

---

### Post by tgm4883 on 2011-06-17
> **hazelnut said:**
> You people should stop congratulating each other for figuring out how to use a windows solution (wine/vbox) and send google a note requesting support!  I did today.

I did as well, but I don't see any harm in workarounds. Relax maybe?

---

### Post by zaphodbblx on 2011-06-18
> **hazelnut said:**
> You people should stop congratulating each other for figuring out how to use a windows solution (wine/vbox) and send google a note requesting support!  I did today.

I don't believe I was congratulating myself on anything..I was thanking another community member for providing a solution that "just works" . Google is a company that heavily relies on Linux but seems lacking in support of it.
PS. are you really monitoring this thread to excoriate people for being forced to use a windows work around...how sad

---

### Post by Foxcow on 2011-06-18
I too sent in a request for a native client for Linux.  Who would have anticipated Google not including Linux on account of the Chromebooks hitting the market.

---

### Post by Madspyman on 2011-06-18
> **hazelnut said:**
> You people should stop congratulating each other for figuring out how to use a windows solution (wine/vbox) and send google a note requesting support!  I did today.

Did that even posted the response they sent me in this thread. 

> **Sunflower1970 said:**
>  

Google sent me this email, upon my support requests. 

> Thank you for your note.

We don’t currently offer a Linux version of the Music Manager, nor ogg vorbis format support.

We're constantly working to improve Music Beta, and I'll make sure to pass your request on to the rest of the team.

We appreciate your feedback.

Regards,

Bryce
The Music Beta Team


Wine may not be the most desirable solution but it's still open source even if some of the programs you need to run using it aren't. In most cases the programs you can run in Windows but not Linux aren't open source anyway. 

The way I see it is that Linux port or not you're still gonna end up with a closed program using open source software to run it. To me Wine is nothing more than system files, and I have no problem installing some extra system files to make any program (open source or not) run.

---

### Post by maddog39 on 2011-06-21
I just got my invite today and have been long awaiting it to be quit honest. I'm uploading my Music on a windows partition right now and accessing my linux partition via ext2fsd. As far as native Linux support is concerned, I imagine that google will put music beta into their google API and that will allow us to create our own open source native client or so we hope.

[Edit]
I just discovered this little gem incase anyone is interested in trying to write their own client for linux. I did NOT look at this tarball yet, it may or may not contain the kind of stuff we are looking for.

[http://dl.google.com/dl/androidjumper/src/current/music-manager-source.tar.bz2](http://dl.google.com/dl/androidjumper/src/current/music-manager-source.tar.bz2)

---

### Post by gabylastar on 2011-06-22
I think I found the best solution so far. My music is on my Debian box. I shared it with Samba. I installed Music Manager on my wife netbook running Windows XP and let it do the job via the Samba share while I enjoy listening music under my Debian main computer.

Of course for this solution to work, you need a wife and her netbook :)

---

### Post by jack24 on 2011-06-22
Thank you for the download, it's a big help.

---

### Post by jack24 on 2011-06-22
Try requesting another invite.  I requested one and didn't get it, but when I requested another one it logged me in right away.

---

### Post by alexan on 2011-06-23
> We're sorry. Music Beta is currently only available in the United States

So, some may find useful avoid waste of time in even checking their website <_<"

---

### Post by BrokenKingpin on 2011-06-23
> **Madspyman said:**
> First off currently there's no Linux

Fail... won't even take a second look at this until they do.

---

### Post by walterbyrd on 2011-06-24
Can music from be downloaded from Google music manager? I was hoping to use this as a free backup for my music.

BTW: for those griping about google, or paranoid about google taking over the world: the way I see it, google is helping to prevent MS and/or Apple from monopolizing the market. Google, although maybe not perfect, is far less evil than MS or Apple (no BS lawsuits and/or patents from google, that I know of). 

Google haters, please feel free to not use this free service. Also feel free to enjoy your Apple/MS vendor lock-in, and monopolized market. And feel free to help support the MS/Apple ongoing war against freedom, by use BS patents, and BS lawsuits.

---

### Post by hfw on 2011-06-24
I do not know if it is possible to download our music back from Google, but I am pretty sure that Google does re-encode the music once they get it, so the quality of the file you download will not be quite the same as what you upload.

---

### Post by tgm4883 on 2011-06-24
> **hfw said:**
> I do not know if it is possible to download our music back from Google, but **I am pretty sure that Google does re-encode the music once they get it**, so the quality of the file you download will not be quite the same as what you upload.

*Citation needed

---

### Post by antimatter15 on 2011-06-24
> **hfw said:**
> I do not know if it is possible to download our music back from Google, but I am pretty sure that Google does re-encode the music once they get it, so the quality of the file you download will not be quite the same as what you upload.

I'm fairly certain they don't re-encode your music. When I was working on MusicAlpha (which was the first and probably only music beta uploading app, and stopped working a week after its release), the songs appeared in the library far too fast for Google to have done re-encoding. Also, the resulting songs were more or less bit-for-bit equivalent to the ones uploaded.

If anyone wants to help get MusicAlpha working again, any help is appreciated. I've found that MusicManager sends a protobuf encoded POST to [https://android.clients.google.com/upsj/](https://android.clients.google.com/upsj/)[something] where [something] is either metadata, playlists, playlistentries, sample, getjobs, upauth, though I assume it's metadata. 

All I need is to find out what exactly it's POSTing to that server, and then hopefully I can reverse engineer the schema for the protobufs. The main problem with that, is that I have no idea how to sniff a https encoded packet. I'm fairly certain it's possible some way or another.

---

### Post by hfw on 2011-06-24
Sorry, bad memeory.  It appears to only be flacs that are transcoded.  Knew I had seen it somewhere.

[http://www.google.com/support/music/bin/answer.py?hl=en&answer=1100462&ctx=cb&src=cb&cbid=-oxtjdhs69lke&cbrank=2](http://www.google.com/support/music/bin/answer.py?hl=en&answer=1100462&ctx=cb&src=cb&cbid=-oxtjdhs69lke&cbrank=2)

---

### Post by aysiu on 2011-06-24
If music can't be redownloaded, I'm not sure why I just uploaded my entire music collection to Google's servers. It's great to have an online back-up, but if the back-up can't be restored, it's useless.

Anyone know if the ability to download your music back again is in the works? I'll try out the Android app to see if making a song available offline really downloads the song to the SD card in a usable fashion. Of course, downloading them to a phone's MicroSD isn't the most efficient way of restoring a back-up.

---

### Post by tgm4883 on 2011-06-24
> **aysiu said:**
> If music can't be redownloaded, I'm not sure why I just uploaded my entire music collection to Google's servers. It's great to have an online back-up, but if the back-up can't be restored, it's useless.

Anyone know if the ability to download your music back again is in the works? I'll try out the Android app to see if making a song available offline really downloads the song to the SD card in a usable fashion. Of course, downloading them to a phone's MicroSD isn't the most efficient way of restoring a back-up.

It's not a backup, that isn't the use case. Use case would be having your music collection everywhere you have a network connection. AFAIK, Google doesn't have the licensing in place to redownload to your system.

---

### Post by aysiu on 2011-06-24
> **tgm4883 said:**
> It's not a backup, that isn't the use case. Use case would be having your music collection everywhere you have a network connection. AFAIK, Google doesn't have the licensing in place to redownload to your system.
You don't need licensing to redownload music from online storage. I can redownload from Amazon's Cloud Music. I can also redownload from Dropbox. No license involved.

In fact, it's quite the opposite of what you said--the record labels are trying to argue that it's not just a storage service and that Google and Amazon owe them licensing fees for the streaming capability.

---

### Post by tgm4883 on 2011-06-24
> **aysiu said:**
> You don't need licensing to redownload music from online storage. I can redownload from Amazon's Cloud Music. I can also redownload from Dropbox. No license involved.

In fact, it's quite the opposite of what you said--the record labels are trying to argue that it's not just a storage service and that Google and Amazon owe them licensing fees for the streaming capability.

I'm just going from this

[http://wallstcheatsheet.com/breaking-news/google-music-your-cheat-sheet-to-the-beta-launch.html/](http://wallstcheatsheet.com/breaking-news/google-music-your-cheat-sheet-to-the-beta-launch.html/)

---

### Post by aysiu on 2011-06-24
> **tgm4883 said:**
> I'm just going from this

[http://wallstcheatsheet.com/breaking-news/google-music-your-cheat-sheet-to-the-beta-launch.html/](http://wallstcheatsheet.com/breaking-news/google-music-your-cheat-sheet-to-the-beta-launch.html/)
I am, too.

From that very article: > Google &#8212; like Amazon (NASDAQ:AMZN) with its cloud service - maintains that Google Music is a backup service for users&#8217; own music collections &#8212; no different than using a backup hard drive.

But over the years, some labels and publishers have maintained that any time a user streams a song over the Internet, royalty payments apply. It's the streaming that the record labels have an issue with. Uploading and downloading to storage is a non-issue.

---

### Post by aysiu on 2011-06-24
Hm. Just tested the "available offline" feature in Google Music Beta for Android, and the file is nowhere to be found on the SD card, so I'm not sure how exactly that works.

I'm definitely no longer a fan of Google Music. I want a cloud backup solution. The ability to stream the music from anywhere has only limited appeal for me. Good thing Amazon actually lets you do both (stream and download).

---

### Post by tgm4883 on 2011-06-24
> **aysiu said:**
> Hm. Just tested the "available offline" feature in Google Music Beta for Android, and the file is nowhere to be found on the SD card, so I'm not sure how exactly that works.


Probably encrypted someone on there.

> **aysiu said:**
> 
I'm definitely no longer a fan of Google Music. I want a cloud backup solution. The ability to stream the music from anywhere has only limited appeal for me. Good thing Amazon actually lets you do both (stream and download).

If you are using it for Backup then yea, Google Music isn't for you. I have a NAS that I store mine on and use Google Music to stream my music. Amazon cloud storage seems to be 4 times more expensive than Google if you need more storage.

---

### Post by mrnatas20 on 2011-06-24
thanks for the info. upgraded wine to 1.3, installed and songs are being uploaded at a much higher rate than via virtualbox..

quick question though, has anyone figured out how to get it two work with two-step verification? I never got a prompt to enter data in the program after I added "Music Manager" to my application-specific authorized things.

I had to turn off two-step verification to get it to work..

---

### Post by arpia49 on 2011-06-26
The music is not encrypted... take a look into the Android folder in your MicroSD card.

---

### Post by aysiu on 2011-06-26
> **arpia49 said:**
> The music is not encrypted... take a look into the Android folder in your MicroSD card.
I did. It's not there.

---

### Post by tgm4883 on 2011-06-26
> **aysiu said:**
> I did. It's not there.

It most definitly is there, just tested it. It's renamed to some seemingly random number.mp3

```
/mnt/sdcard/Android/data/com.google.android.music/cache/music
```

---

### Post by aysiu on 2011-06-26
> **tgm4883 said:**
> It most definitly is there, just tested it. It's renamed to some seemingly random number.mp3

```
/mnt/sdcard/Android/data/com.google.android.music/cache/music
```
I just went there, and the folder is empty.

---

### Post by tgm4883 on 2011-06-26
> **aysiu said:**
> I just went there, and the folder is empty.

Strange, cause I didn't have that music on there before I marked it for offline use. 

Did you mount the sd drive on your computer or did you use a file manager android app?

Is your phone rooted or stock?

---

### Post by aysiu on 2011-06-26
I used the file manager on the phone, and my phone is rooted.

Also, since this does work for you, how big a cache does it hold and for how long?

---

### Post by tgm4883 on 2011-06-26
> **aysiu said:**
> I used the file manager on the phone, and my phone is rooted.

Also, since this does work for you, how big a cache does it hold and for how long?

Well I just enabled it today for the test, so I don't have any length of time references for you. I do know that there are 60+ songs that are in that directory right now.

---

### Post by haqking on 2011-06-28
[http://www.androidcentral.com/using-google-music-manager-ubuntu-made-easy](http://www.androidcentral.com/using-google-music-manager-ubuntu-made-easy)

---

### Post by mastermindg on 2011-06-28
Downloads have been capped so far....need alternate dl sites.

---

### Post by bluescreenkid on 2011-06-28
> **mastermindg said:**
> Downloads have been capped so far....need alternate dl sites.

use [http://ge.tt/97A26s4](http://ge.tt/97A26s4)

this is the 2nd version of the script, it doesn't contain any binaries but instead downloads the executable from google and installs it for you.

README can also be read at [http://pastebin.com/CYpEY300](http://pastebin.com/CYpEY300)


BSK :D

---

### Post by mastermindg on 2011-06-28
I just installed wine 1.3 from the repository on Lucid. Initially the app wouldn't open but I ran it from cl and realized that odbc needs to be native. I setup odbc with winetricks and set odbc to native under winecfg. It's working fine now.

---

### Post by mczenfold on 2011-06-30
has anybody elses upload just gotten stuck?  Mine has gotten stuck for days and doesn't seem to be uploading anything anymore, even if I restart and play around with the options.

---

### Post by tgm4883 on 2011-06-30
> **mczenfold said:**
> has anybody elses upload just gotten stuck?  Mine has gotten stuck for days and doesn't seem to be uploading anything anymore, even if I restart and play around with the options.

I had that happen as well. I ended up firing it up on my XP VM and it finished.

---

### Post by mczenfold on 2011-06-30
> **tgm4883 said:**
> I had that happen as well. I ended up firing it up on my XP VM and it finished.

Whenever I use a VM (using latest VMware), I keep getting this error message saying:

"login failed, could not identify your computer", and it sends me to this troubleshooting link that says VMs aren't supported.

[http://www.google.com/support/music/bin/answer.py?answer=1308383&hl=en](http://www.google.com/support/music/bin/answer.py?answer=1308383&hl=en)

did you have to do something special to get it to work on your VM?

---

### Post by tgm4883 on 2011-07-01
> **mczenfold said:**
> Whenever I use a VM (using latest VMware), I keep getting this error message saying:

"login failed, could not identify your computer", and it sends me to this troubleshooting link that says VMs aren't supported.

[http://www.google.com/support/music/bin/answer.py?answer=1308383&hl=en](http://www.google.com/support/music/bin/answer.py?answer=1308383&hl=en)

did you have to do something special to get it to work on your VM?

Nope, XP in a VirtualBox VM

---

### Post by mattv111 on 2011-07-08
Every time I get to the screen to enter my email and password it crashes. Any help would be appreciated

---

### Post by andrewthestudent on 2011-07-10
> **mattv111 said:**
> Every time I get to the screen to enter my email and password it crashes. Any help would be appreciated
Make sure you are using wine1.3.  See [this page]("http://www.winehq.org/download/ubuntu") for instructions.  I had to install the Wine beta packages.  Now it seems to be working. (I had the exact same issue you did.)

---

### Post by Foxcow on 2011-07-22
We now have a native client!

[http://www.omgubuntu.co.uk/2011/07/google-music-beta-finally-launches-linux/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2011/07/google-music-beta-finally-launches-linux/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by Madspyman on 2011-07-22
Better late then never.

---

### Post by zachthejones on 2011-07-22
Guessing this thread could be marked as "solved"?

---

### Post by bupahs on 2011-07-23
Its not actually solved since the Music Manager does not work on Ubuntu 11.04

---

### Post by zachthejones on 2011-07-23
Interesting. It's working relatively fine for me on 11.04, though it doesn't seem to want to remember my password after I shutdown/restart. That's the only real bug I've run into (I am running the 64 bit version, if that makes a difference).

Was it posted somewhere that it didn't work in 11.04? I never saw anything along that line, just installing it straight from their website.

---

### Post by dog-soldier on 2011-07-23
anyone have a invite to spare?

---

### Post by rimez on 2011-07-23
> **bupahs said:**
> Its not actually solved since the Music Manager does not work on Ubuntu 11.04

Hmm... It's working for me in 11.04 (though there are some performance issues).

---

### Post by tgm4883 on 2011-07-23
> **bupahs said:**
> Its not actually solved since the Music Manager does not work on Ubuntu 11.04

My 11.04 machine seems to disagree with this statement. Maybe you should post what issues you are seeing?

---

### Post by vraicovi on 2011-07-23
> **tgm4883 said:**
> My 11.04 machine seems to disagree with this statement. Maybe you should post what issues you are seeing?

Agreed, it's working on my 64-bit 11.04 machine as well.  My only issue seems to be a lack of a menu bar/indicator icon.

---

### Post by Foxcow on 2011-07-23
> **vraicovi said:**
> Agreed, it's working on my 64-bit 11.04 machine as well.  My only issue seems to be a lack of a menu bar/indicator icon.




Same here.

---

### Post by Anno8 on 2011-07-24
Anyone know how to uninstall [this]("http://www.androidcentral.com/using-google-music-manager-ubuntu-made-easy") now that we have a native one?


And how do we get the menu bar icon with this native client?
...wait for update?

---

### Post by tgm4883 on 2011-07-24
> **Anno8 said:**
> Anyone know how to uninstall [this]("http://www.androidcentral.com/using-google-music-manager-ubuntu-made-easy") now that we have a native one?


And how do we get the menu bar icon with this native client?
...wait for update?

Wow that's a terrible application. Looking at the install script, you should just need to 

I'm not 100% sure if this is copying stuff into a directory that already contains stuff. 
```
cp -R Programs/ ~/.wine/drive_c/users/$user/Local\ Settings/Application\ Data/
```


You will need to do these too
```
rm ~/.local/share/applications/musicmanager.desktop
cp ~/.config/menus/applications.menu.bak ~/.config/menus/applications.menu

```

---

### Post by Anno8 on 2011-07-26
> **tgm4883 said:**
> Wow that's a terrible application. Looking at the install script, you should just need to 


Thanks, it worked

---

### Post by Anno8 on 2011-07-26
How do I get the native Google Music Manager for Linux to start at login and remember my password/not ask for it every time I boot up my PC...?

---

### Post by hfdragon on 2011-07-26
> **Anno8 said:**
> How do I get the native Google Music Manager for Linux to start at login and remember my password/not ask for it every time I boot up my PC...?


I have this same problem :(

And also I don't have the icon in the notification aera when Google Music Manager is running :(

Anyone know how to solve both problems ?

---

### Post by Anno8 on 2011-07-26
> **hfdragon said:**
> 
Anyone know how to solve both problems ?

Wait for an update, I guess...

---

### Post by natrixgli on 2011-08-14
Thanks to [this thread]("http://www.google.com/support/forum/p/Google%20Apps/thread?tid=1fa46ba11fa09a6d&hl=en") over on Google's support group, I figured out how to fix the "Could not identify your computer" error.

Music Manager creates a settings database (sqlite3) at ~/.config/google-musicmanager/Peer.db. I used 'sqlitebrowser' to edit the database but you could easily do it with sqlite3 from the terminal as well.

You have to update the value for "MachineIdentifier" in the table "CONFIG" with your network adapter's MAC Address. You can find this by right-clicking your network icon in the notification area and going to "Connection Information". 

Since this doesn't appear to affect everyone using Ubuntu 11.04 I am inclined to believe it only happens if you're using a wireless device where your interface is not 'eth0'.


-n8

---

### Post by Lindsay.Mathieson on 2011-08-27
> **Anno8 said:**
> How do I get the native Google Music Manager for Linux to start at login and remember my password/not ask for it every time I boot up my PC...?

From: [http://www.google.com/support/music/bin/static.py?page=known_issues.cs](http://www.google.com/support/music/bin/static.py?page=known_issues.cs)

[I]We're aware that it isn't currently possible to stay signed in from session to session with the Linux version of the Music Manager, and are working on a fix.
n the meantime, other users have reported that they've been able to work around the issue by starting the program, and with the "-p" option followed by their password, it logs them in successfully without a windowed prompt asking for the password. /opt/google/musicmanager/google-musicmanager -p mypassword[/I]

---

### Post by h.aling on 2011-09-07
> **natrixgli said:**
> Thanks to [this thread]("http://www.google.com/support/forum/p/Google%20Apps/thread?tid=1fa46ba11fa09a6d&hl=en") over on Google's support group, I figured out how to fix the "Could not identify your computer" error.

I've set the MachineIdentifier to my MAC-address, but the Google Music Manager keeps nagging me every time that my machine couldn't be identified.

Did anyone manage to solve it permanently?

---

### Post by matteosister on 2011-11-22
> **Lindsay.Mathieson said:**
> From: [http://www.google.com/support/music/bin/static.py?page=known_issues.cs](http://www.google.com/support/music/bin/static.py?page=known_issues.cs)

[I]We're aware that it isn't currently possible to stay signed in from session to session with the Linux version of the Music Manager, and are working on a fix.
n the meantime, other users have reported that they've been able to work around the issue by starting the program, and with the "-p" option followed by their password, it logs them in successfully without a windowed prompt asking for the password. /opt/google/musicmanager/google-musicmanager -p mypassword[/I]


this solution works great for me! Many thanks.

---

### Post by Mikeb85 on 2011-11-23
> **smellyman said:**
> google taking over the world is not a good thing.

Why not?  Would you rather Apple or Microsoft?  Google is without a doubt the most innovative large tech company out there, and give away most of their services/products.  They've also been more supportive of Linux than most other tech companies...  Apple, Microsoft, Amazon, etc..., most of these companies do not have a very good record when it comes to controlling what their customers can do, locking customers in, etc...  

(when I say Google is innovative though, not talking about the music thing, they're just doing that to make the Android experience more 'seamless' in the way that Apple's iOS experience is...)

---

### Post by Lorenzo233 on 2012-01-20
What do they mean with > by starting the program, and with the "-p" option followed by their password? (I can't open the webpage you linked, and i'm a newbie). It would be great if you could explain me the steps needed for the workaround :) 
I'm using Lubuntu.

---

### Post by barrack on 2012-01-25
I'm not sure if anyone already answered the two-step verification problem , but I just found a link that was easy and helpful:

[http://www.rogerethomas.com/b/110/how-to-get-google-music-manager-beta-remember-your-password-in-ubuntu](http://www.rogerethomas.com/b/110/how-to-get-google-music-manager-beta-remember-your-password-in-ubuntu)

---

### Post by jackgu1988 on 2012-01-30
> **barrack said:**
> I'm not sure if anyone already answered the two-step verification problem , but I just found a link that was easy and helpful:

[http://www.rogerethomas.com/b/110/how-to-get-google-music-manager-beta-remember-your-password-in-ubuntu](http://www.rogerethomas.com/b/110/how-to-get-google-music-manager-beta-remember-your-password-in-ubuntu)

I am using arch linux and this was almost the solution. google-musicmanager is installed via AUR, thus on the /opt dorectory. The file mentioned was there, but did not solve my problem. What I had to edit accordingly to the tutorial you mentioned was /opt/google/musicmanager/google-musicmanager.desktop

Any archers looking for a solution will find this helpful :)

---

### Post by GrindcoreVlad on 2012-04-10
Does anybody know where can I find the logs for Google Music manager? I try to upload some folders but I can't.

---

### Post by derklempner on 2012-05-14
Oddly enough, I figured out the whole ***-p*** flag on my own.  My email correspondence with Google Music Beta's support team wasn't yielding any answers, and they actually thanked me when I told them I found the answer on my own and conveyed it to them.

Since Google's updated their Music manager software, the new executable is now named **MusicManager**, although it's located in the same directory (**/opt/google/musicmanager**).

However, the ***-p*** flag no longer works with the new executable.  Has anybody been able to figure out how to launch it without being prompted for your password?  I've tried ***-P*** as well as ***-p***, but I can't think of anything else to try.  Using the ***-h***, ***-H***, ***-?***, ***--h***, ***--H***, and ***--?*** just launches the program, so I can't even find out if there's a help command!

---

### Post by Mars11 on 2012-06-05
> **derklempner said:**
> Oddly enough, I figured out the whole ***-p*** flag on my own.  My email correspondence with Google Music Beta's support team wasn't yielding any answers, and they actually thanked me when I told them I found the answer on my own and conveyed it to them.

Since Google's updated their Music manager software, the new executable is now named **MusicManager**, although it's located in the same directory (**/opt/google/musicmanager**).

However, the ***-p*** flag no longer works with the new executable.  Has anybody been able to figure out how to launch it without being prompted for your password?  I've tried ***-P*** as well as ***-p***, but I can't think of anything else to try.  Using the ***-h***, ***-H***, ***-?***, ***--h***, ***--H***, and ***--?*** just launches the program, so I can't even find out if there's a help command!

I'm having the same problem, I hate that after every reboot I have to retype a strange application-specific password. Does anyone know how to fix this?

---

### Post by xak on 2012-06-05
> **Mars11 said:**
> I'm having the same problem, I hate that after every reboot I have to retype a strange application-specific password. Does anyone know how to fix this?

Same here, I wonder why they took out the -p functionality. All the usual help flags do nothing but launch the app. Anyone? :confused:

---

### Post by yock on 2012-06-13
Confirmed that the reported workaround doesn't work and the problem persists. What's worse is that the Google Help Center has no references to the bug and the workaround page has been removed. Time like these I can't help but wonder if the problem is considered not worth fixing.

---

### Post by Green_Star on 2012-08-15
Its crazy to enter app specific password every time I start google music manager. The only way to login is either save the app specific password some where in my system or delete the old one from google account and create a new one. Both are not good solutions.

---

