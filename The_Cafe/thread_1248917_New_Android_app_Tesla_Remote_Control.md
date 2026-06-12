---
title: "New Android app: Tesla Remote Control"
date: 2009-08-24
forum: The Cafe
---

### Post by SeanHodges on 2009-08-24
[COLOR="Red"]NOTE: Unfortunately I don't regularly check UF these days and it looks like this thread has been locked for inactivity. If you need help using the app, or have and questions/suggestions - please visit the [project support page]("http://sourceforge.net/projects/android-tesla/support") and email either the mailing list or myself directly. I also monitor the bug tracker regularly.

This project is very much alive![/COLOR]


Hey everyone,

I've been quietly working on a new project for the Android platform called Tesla...

It's a remote control for Ubuntu/Linux designed to work with a variety of media players. Currently it supports VLC, Amarok (1 and 2), Rhythmbox, Totem, Dragon Player, and Banshee. I hope to expand this as requests come in. You can use it to control playback, change the volume, and shutdown the PC using an easy to use remote control-like UI. Connection to your computer requires a Wifi network.

Anyone with an Android mobile phone, please give it a try and give me feedback. I'm more than happy to help out with any issues people have.

The project site is: [http://tesla.seanhodges.co.uk]("http://tesla.seanhodges.co.uk"). You can download the app by following [these instructions]("https://sourceforge.net/apps/trac/android-tesla/wiki/Instructions"), or using [AndAppStore]("http://andappstore.com/AndroidApplications/apps/186356").

**A note to VLC fans:** You need to follow [these steps]("http://ubuntuforums.org/showpost.php?p=7824159&postcount=13") for Tesla to work with the version of VLC available in Ubuntu 9.04.

[IMG]http://seanhodges.co.uk/~sean/tesla-res/Playback.png[/IMG] [IMG]http://seanhodges.co.uk/~sean/tesla-res/Volume.png[/IMG]

Thanks,

Sean

---

### Post by meeples on 2009-08-24
dont have an android soz.

but i love these sort of things, i sometimes use my Sony Erricson mobile's Bluetooth Desktop remote as a mouse when i get lazy XD

your app is pretty :P

---

### Post by Muppeteer on 2009-08-24
Looks awesome, i'll check it out tomorrow :)

---

### Post by SeanHodges on 2009-08-25
Great, I was hoping there would be some interest :)

I'll post up any new builds as I go along, hopefully I'll be able to provide a stable release on the Android market before long.

If you have any problems/questions/suggestions, please let me know - the project is open-source as well (see the project site), for those of you who are curious.

---

### Post by LookTJ on 2009-08-25
You had me thinking a bluetooth program to control a telsa ev car.

:lolflag:

EDIT: And I don't have android phone.  Your project looks cool though

---

### Post by SeanHodges on 2009-08-25
> **LookTJ said:**
> You had me thinking a bluetooth program to control a telsa ev car.

Hahaha a little false advertising never hurt anyone :)

I'll look into adding a configuration for the Tesla EV Roadster in a future release. Perhaps use the volume control to accelerate, Prev/Next to steer, and the Play button as a turbo-charge feature that "fuel dumps" a large capacitor...

---

### Post by ELD on 2009-08-25
This does sound rather amazing can't wait to try it on my G1!

How exactly does it work though? You say wifi, so it will connect to my pc via the local wireless network basically?

---

### Post by fishy6969 on 2009-08-25
Given it a go on a Vodafone Magic. Good going so far. It won't replace Gmote quite yet, but I'll carrying on testing.

---

### Post by SeanHodges on 2009-08-25
> **ELD said:**
> This does sound rather amazing can't wait to try it on my G1!

How exactly does it work though? You say wifi, so it will connect to my pc via the local wireless network basically?

Yes, it connects to your PC over SSH (using your local Wireless network), and sends/receives commands to whatever remote API the target player has to offer.

The idea is to keep the number of dependencies down, and support a large number of media players using the same secure connection interface. You just need to install [openssh-server]("apt://openssh-server"), launch the media player that you want to remote control, and enter your IP address, and PC login details into your phone.

---

### Post by SeanHodges on 2009-08-25
> **fishy6969 said:**
> Given it a go on a Vodafone Magic. Good going so far. It won't replace Gmote quite yet, but I'll carrying on testing.

Hey fishy6969, thanks for giving it a go. 

I'm not trying to directly compete with Gmote, but I would be interested to hear what specific areas you feel Tesla is lacking in comparison. Some features might be well worth copying, obviously the tight integration between VLC and Gmote will make some features difficult to work across the other media players.

Great to hear it works on the Magic, your the first to report that for me!

---

### Post by SeanHodges on 2009-08-25
I've packaged a new 0.6 release, with various fixes to VLC and Amarok support:

- Fixed force-close when Amarok 1.4 is stopped
- VLC now shows its video title in the media info panel
- You can now increase VLC's volume to the full 200%

Get it fresh from [Sourceforge]("https://sourceforge.net/projects/android-tesla/files/") or [AndAppStore]("http://andappstore.com/AndroidApplications/prerelease/186356!show")!

---

### Post by SeanHodges on 2009-08-26
I was having some problems pushing the latest source code for the 0.6 release to Sourceforge. Turns out they changed their service so I needed to change my Git config as described [here]("https://sourceforge.net/apps/trac/sourceforge/ticket/2886#comment:4").

Anyway, the source code is now up-to-date, so anyone interested can download it and maybe even help out!

---

### Post by fishy6969 on 2009-08-26
I'll have a look tonight. I'm not great with Java, but I'll be happy to test.

---

### Post by r-mo on 2009-08-27
I would love to see an android remote that would let me control kaffeine particularly the dvb tv.  Would it also be possible to use the phone trackball and keyboard as devices on the PC?

---

### Post by SeanHodges on 2009-08-27
Hey r-mo,

I will definitely add support for Kaffeine, and in particular the DVB support. Tesla does not have a playlist function yet, so channel changing will be a little cumbersome until that has been added (which is also planned). Banshee support is already available, so you should be able to control that straight away.

At the moment, I don't plan to add raw mouse/keyboard control support, as it is slightly out of scope of Tesla's objectives. I recommend taking a look at the [RemoteDroid]("http://www.remotedroid.net/") app or Gmote's ["Touch" mode]("http://www.gmote.org/faq#What_s_Gmote_Touch_What_is_the_22575769294053316") for this kind of functionality.

Congratulations on getting your HTC Hero :)

---

### Post by aktiwers on 2009-08-27
Cool! I will try this out on my G1 when I have time :)

---

### Post by Colonel Kilkenny on 2009-08-27
Any chance of developing this app for Maemo as well? Would be handy.
[http://maemo.nokia.com](http://maemo.nokia.com) / [http://maemo.org](http://maemo.org)

---

### Post by r-mo on 2009-08-27
Oh wow, the GMote Touch mode works great, I just hadn't noticed it before.  Thanks!!

---

### Post by SeanHodges on 2009-08-27
> **Colonel Kilkenny said:**
> Any chance of developing this app for Maemo as well? Would be handy.
[http://maemo.nokia.com](http://maemo.nokia.com) / [http://maemo.org](http://maemo.org)

It's not an impossibility, although in honesty right now the application is completely native to Android, so straight porting would be tricky.

The best chance would be to re-write the back-end service for Maemo, and build a cross-platform Web front-end to support a UI on both systems at the same time. Both platforms could share the media player command database and general architectural design. Once this was done for a second platform like Maemo, it would be much easier to port the application to iPhoneOS, Blackberry OS, Symbian, etc. The biggest problem will be doing the first port.

My time is going to be pretty much consumed with the milestones for the existing Android implementation, so I don't see myself finding much time in the near future to tackle this. However, if others wanted to take on the task, I will be happy to help out as much as I can. I would definitely like to see Tesla on non-Android phones.

Having said all that, if a compatibility layer for running Android apps on Maemo is released, then I may look into doing a port myself sooner rather than later.

---

### Post by SeanHodges on 2009-08-27
> **aktiwers said:**
> Cool! I will try this out on my G1 when I have time :)

Please do! I'm planning another release in the next couple of days. There will be some cool new stuff and a lot of improvements on stability. But definitely try out the 0.6 release in the meantime.

Support for Kaffeine is on its way, amongst other things.

---

### Post by lordyosch on 2009-08-29
I've just downloaded it after you mentioned it in the thread I started about the Hero.

Its pretty cool! I get a long-winded error from Banshee (on the phone) when I start it up but it seems to play/pause/skip and change volume too -so no worries.

I like the way it picks up album art too!


As a proof of concept its great, looking forward to any enhancements you make.

Jay

---

### Post by SeanHodges on 2009-08-29
Version 0.7 of Tesla is now available! This version includes:

- Volume control can change system or player volume (see Menu -> Preferences)
- Play-back pauses on incoming call (configurable, see Menu -> Preferences)
- Players are auto-launched if they are not already running on connection
- Improved media info retrieval (reduced data resetting)
- Support for Exaile music player (Hendrik Kaju)
- VLC set-up instructions now provided on first launch
- Support for Kaffeine video player
- More "user-friendly" error messages, hopefully you'll never see this feature ;)
- Various small bug fixes

Available, as usual, on [Sourceforge]("http://tesla.seanhodges.co.uk") and [AndAppStore]("http://andappstore.com/AndroidApplications/prerelease/186356!show").

---

### Post by SeanHodges on 2009-08-29
> **lordyosch said:**
> I've just downloaded it after you mentioned it in the thread I started about the Hero.

Its pretty cool! I get a long-winded error from Banshee (on the phone) when I start it up but it seems to play/pause/skip and change volume too -so no worries.

I like the way it picks up album art too!


As a proof of concept its great, looking forward to any enhancements you make.

Jay

Jay,

Thanks for giving Tesla a try, I've added some improvements to the new release that may fix the error you get with Banshee.

Be sure to let me know if there are any specific enhancements that you have in mind :) I'm always open to ideas.

Sean

---

### Post by SeanHodges on 2009-08-30
Someone emailed me saying they couldn't find Tesla in the AndAppStore market. It was there, just hidden in a "pre-release" subsection. 

I've changed the release flag to "Public Release", and it now appears in the new releases section.

---

### Post by SeanHodges on 2009-09-10
Just thought I'd let you all know that Tesla 0.8.1 is now available from [Sourceforge]("http://tesla.seanhodges.co.uk") and [AndAppStore]("http://andappstore.com/AndroidApplications/prerelease/186356!show").

Features in this release:

- Seek bar feature (excludes Kaffeine, eXaile, and Totem players)
- Lots of stability fixes, performance should be improved as well
- System volume control more flexible for different sound cards

Please let me know if you have any issues or comments!

---

### Post by brendanpiater on 2009-09-20
Hi,

Looks great and keen to try it! 

I've installed the latest version but I'm unable to connect. Just shows, "connecting to computer" message.

Any suggestions?

Cheers
Brendan

---

### Post by jackhynes on 2009-09-20
Excited to try it out as well. I get the error code 83340.

---

### Post by pantz on 2009-09-21
Hi :) any plans to support Boxee media center?

---

### Post by abhiroopb on 2009-09-21
> **brendanpiater said:**
> Hi,

Looks great and keen to try it! 

I've installed the latest version but I'm unable to connect. Just shows, "connecting to computer" message.

Any suggestions?

Cheers
Brendan

Could be a number of things...I'll just run down the list of things I can think of right now:

1. Have you got openssh-server installed? If not type this in a terminal:
```

sudo apt-get install openssh-server
```

2. Are both your Android phone AND your computer connected to the same wireless network?

3. Ensure you are inputting the correct IP address for your PC (to check right click on the network icon and select "Connection Information").

4. Make sure you put in your correct username and password into Tesla.

Are you doing all these things?

---

### Post by brendanpiater on 2009-09-21
Thanks for the reply.

I can confirm all is 100% on the point's above. I lso tested SSH access via a SSH client on the phone and was able to connect to the machine ok.

I reset all the options and tried again, this time I got quite a long error message ending in "Could not find dbus session ID in user enviroment; fi :- bash:no job control in this shell"

From my auth.log file;

Sep 21 16:50:00 XXXX sshd[15547]: pam_sm_authenticate: Called 
Sep 21 16:50:00 XXXX sshd[15547]: pam_sm_authenticate: username = [XXXX] 
Sep 21 16:50:00 XXXX sshd[15547]: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Sep 21 16:50:00 XXXX sshd[15549]: Error attempting to open [/home/XXXX/.ecryptfs/wrapped-passphrase] for reading 
Sep 21 16:50:00 XXXX sshd[15549]: Error attempting to unwrap passphrase from file [/home/mrb/.ecryptfs/wrapped-passphrase]; rc = [-5] 
Sep 21 16:50:00 XXXX sshd[15549]: Error adding passphrase key token to user session keyring; rc = [-5] 
Sep 21 16:50:00 XXXX sshd[15547]: Accepted password for mrb from 192.168.1.64 port 60974 ssh2
Sep 21 16:50:00 XXXX sshd[15547]: pam_unix(sshd:session): session opened for user mrb by (uid=0)
Sep 21 16:50:00 XXXX sshd[15558]: Received disconnect from 192.168.1.64: 11: Closed due to user request.
Sep 21 16:50:00 XXXX sshd[15547]: pam_unix(sshd:session): session closed for user XXXX
Sep 21 16:50:01 XXXX CRON[15586]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 21 16:50:01 XXXX CRON[15586]: pam_unix(cron:session): session closed for user root

Cheers
B

---

### Post by magicfab on 2009-09-21
I am also getting an infite "Working... Connecting with your computer" message.

I disabled PKA-only logins to test this, but I can't see how I would regularly use it, knowing it essentially asks for my PCs main credentials. :(

Screenshots look like the interface is nice, isn't there another way to access these apps APIs ?

---

### Post by SeanHodges on 2009-09-22
> **brendanpiater said:**
> I can confirm all is 100% on the point's above. I lso tested SSH access via a SSH client on the phone and was able to connect to the machine ok.

I reset all the options and tried again, this time I got quite a long error message ending in "Could not find dbus session ID in user enviroment; fi :- bash:no job control in this shell"

Hey Brendan,

It sounds like the app is connecting to your machine OK, but then failing to retrieve your desktop session ID for some reason. I'll take a look tonight and see if I can reproduce the problem.

Are you running Ubuntu 9.04, and using Gnome or KDE as your desktop? If not, I may need to test against your specific set-up...

---

### Post by SeanHodges on 2009-09-22
> **jackhynes said:**
> Excited to try it out as well. I get the error code 83340.

I've seen this before. If you connect to Rhythmbox whilst it is "stopped", Tesla crashes because there is no song information to retrieve. This only happens when you first launch Rhythmbox, before you play a song for the first time. After that everything works as expected.

There will be a fix in the next release, but for now you need to ensure you play (and optionally pause) a song before connecting.

---

### Post by brendanpiater on 2009-09-22
Thanks for the time and effort.

Running Jaunty 9.04, AMD64 with Gnome enviroment.

---

### Post by SeanHodges on 2009-09-22
> **magicfab said:**
> I am also getting an infite "Working... Connecting with your computer" message.

I disabled PKA-only logins to test this, but I can't see how I would regularly use it, knowing it essentially asks for my PCs main credentials. :(

Screenshots look like the interface is nice, isn't there another way to access these apps APIs ?

Hi magicfab,

If you are confident that the phone should be able to connect to your PC successfully, then your infinite "connecting" message may be the same issue as Brendan's. I'll be looking into this tonight, but any clues you think might be helpful would be great. Connectivity problems have usually been related to some system configuration I haven't considered yet.


Public key authentication is definitely possible, the only reason it is not currently available is because I haven't had time to consider how it might work. 

Obviously there will need to be some way of getting the public key onto the phone, and managing the keys that have been set-up. I was thinking of looking at how ConnectBot and others have done it, but it be great to maybe interface with a public key server so that key management could be done almost entirely within Seahorse on the PC.

I definitely intend to take a look at PKA support soon, but in case you are interested and would like to beat me to it, the source code is available on Sourceforge:

[https://sourceforge.net/projects/android-tesla/](https://sourceforge.net/projects/android-tesla/)

I will happily help out in any way I can, should you, or someone else, like to take on the task.

---

### Post by SeanHodges on 2009-09-22
> **pantz said:**
> Hi :) any plans to support Boxee media center?

I should think so :)

I hope to expand the supported players some more once I've fixed the connection issues some people are having, and completed the playlist feature. Keep checking back, and I'll post an update when Boxee support is available.

---

### Post by Islington on 2009-09-22
Reddited: [http://www.reddit.com/r/linux/comments/9n1kx/tesla_android_app_a_remote_control_for_your_linux/](http://www.reddit.com/r/linux/comments/9n1kx/tesla_android_app_a_remote_control_for_your_linux/)

---

### Post by Arquis on 2009-09-22
I want my HTC Hero PRONTO! :(

---

### Post by SeanHodges on 2009-09-25
brendanpiater, magicfab,

I've done a fair bit of testing to try and reproduce the connecting issue you are both having. So far, I've had no luck. The only time I was able to get a "permission denied" error was when I tried to connect with a username/password that didn't match the user currently logged into the PC.

Could you both run the following command on your machines (changing "[username]" as appropriate), and let me know what you get back?

```
ssh [username]@localhost "grep DBUS_SESSION_BUS_ADDRESS= ~/.dbus/session-bus/*-0 | cut -d '=' -f 2,3,4"
```

This command is similar to the command that is failing when Tesla is connecting to your machine, hopefully we'll get something a bit more descriptive than what Tesla is reporting.

---

### Post by brendanpiater on 2009-09-26
Hiya,

Ran that command and had a " REMOTE HOST IDENTIFICATION HAS CHANGED!" message.

Removed offending key then tried again. Output attached.

Also tried the following;
# Logging in with incorrect user, gives a different message stating user/pass error as one would expect.
# Connecting after removing the host key mentioned above, same error as before.

Thanks again for the time and effort.

Cheers
B

---

### Post by jackhynes on 2009-09-26
> **SeanHodges said:**
> I've seen this before. If you connect to Rhythmbox whilst it is "stopped", Tesla crashes because there is no song information to retrieve. This only happens when you first launch Rhythmbox, before you play a song for the first time. After that everything works as expected.

There will be a fix in the next release, but for now you need to ensure you play (and optionally pause) a song before connecting.

I tried again using your advice, but it still gives the same error code. After trying with VLC I got the error code 83360 and with totem the app seemed to have no effect on the state while playing a video.

---

### Post by SeanHodges on 2009-09-28
> **brendanpiater said:**
> Hiya,

Ran that command and had a " REMOTE HOST IDENTIFICATION HAS CHANGED!" message.

Removed offending key then tried again. Output attached.

Also tried the following;
# Logging in with incorrect user, gives a different message stating user/pass error as one would expect.
# Connecting after removing the host key mentioned above, same error as before.

Thanks again for the time and effort.

Cheers
B

Brilliant, the output you sent me proved that you have multiple DBUS sessions running, and that I was only expecting one.

Thanks a lot for that, I've produced a fix and plan to roll a release tonight. Let me know if you still have problems after updating.

---

### Post by SeanHodges on 2009-09-28
> **jackhynes said:**
> I tried again using your advice, but it still gives the same error code. After trying with VLC I got the error code 83360 and with totem the app seemed to have no effect on the state while playing a video.

Hello Jack,

It sounds like the app is having some real trouble working correctly on your machine.

Could you tell me which version of Ubuntu you are using? and whether you are using Gnome, KDE, or something else?

I'll be rolling a new release soon which may provide slightly different error codes (providing a bit more info for debugging) - if you could test that release and report any of the errors you get, that would be great.


Thanks for your patience on this,

Sean

---

### Post by brendanpiater on 2009-09-28
Awesome, thanks again. Will probably get to try it tomorrow or so and will let you.

All the best
B

---

### Post by SeanHodges on 2009-09-28
Version 0.8.2 of Tesla has been released. It's not particularly exciting (unless you are affected by the bugs that it fixes):

* Tesla does not crash if Rhythmbox is not playing when connecting 
* "Permission denied" and "No job control" errors when connecting hopefully fixed

Hopefully my next release will follow soon, with lots of exciting new features :)

---

### Post by Fl3s on 2009-09-30
Unfortunately I've got the same problem connecting with the server, the message "Working... Connecting with computer" shows endlessly.

My output of ssh and the parameters you gave is as follows:

unix:abstract=/tmp/dbus-hRaWcVyeQ7,guid=799184d0c4a360230201386d4ac38f62

Running Gnome on 9.04

BTW, I think I really like your app ;)

---

### Post by SeanHodges on 2009-10-01
> **Fl3s said:**
> Unfortunately I've got the same problem connecting with the server, the message "Working... Connecting with computer" shows endlessly.

My output of ssh and the parameters you gave is as follows:

unix:abstract=/tmp/dbus-hRaWcVyeQ7,guid=799184d0c4a360230201386d4ac38f62

Running Gnome on 9.04

BTW, I think I really like your app ;)

OK thanks for letting me know.

Is the Wifi enabled on your phone, and successfully connected to your network? If not, the "Connecting with computer" message will wait indefinitely whilst it waits for the network to become available.

A good test is to install the ConnectBot app and try logging into your PC over SSH, using the same username/password you are trying to use for Tesla. If you encounter problems when connecting, then the same thing will be happening in Tesla.

It would also be useful to know what phone you are using. So far I haven't heard of any compatibility issues between Tesla and a particular phone, but you might be using a device that hasn't had much testing yet, like the Archos Android devices.

---

### Post by jackhynes on 2009-10-11
> **SeanHodges said:**
> Could you tell me which version of Ubuntu you are using? and whether you are using Gnome, KDE, or something else?

I'll be rolling a new release soon which may provide slightly different error codes (providing a bit more info for debugging) - if you could test that release and report any of the errors you get, that would be great.


Working great now after the newest update, thanks for the help. I'm running the latest beta of Karmic. What I'd like to see next is the ability to access to ~/.local/share/rhythmdb.xml so we could choose what song to put on next.

---

### Post by SeanHodges on 2009-10-13
New release of Tesla - the long delayed 0.9

[LIST]
[*]New Playlist Support (currently VLC and Amarok 1/2 only)
[*]Seek buttons for more accurate skipping in media
[*]Crash when changing tracks too quickly in Rhythmbox ( #27 )
[*]Tesla crashes when attempting to launch Amarok 1.4 ( #28 )
[*]Add song info support for Dragon Player ( #48 )
[*]Exaile play/pause button does not toggle when pressed ( #50 )
[/LIST]

Sorry Rhythmbox fans, I'm close to adding playlist support for you; but I was beginning to sit on this release, and want to start getting some feedback on the players I can support already.

I hope to follow this with another release soon, there are some features I've nearly finished, but didn't get the time to test enough.

---

### Post by SeanHodges on 2009-10-13
> **jackhynes said:**
> Working great now after the newest update, thanks for the help. I'm running the latest beta of Karmic. What I'd like to see next is the ability to access to ~/.local/share/rhythmdb.xml so we could choose what song to put on next.

Hey Jack, thanks for the feedback. Good to know the last release worked for you.

I'm in the process of adding playlist support for Rhythmbox at the moment. Hopefully I will be able to include it in the next release.

Right now, I'm focusing on allowing you to only select the tracks for the currently playing album. Obviously this is fairly limited, but should be a good start. I will soon start to consider how a collection browser feature might work (across all the players supporting playlist editing), but I don't have an ETA for this yet.

If you happen to be a developer with a little free time and an interest in learning Android, I'd be happy to help you make a start on extending the playlist functionality for Rhythmbox, so we can get it sooner rather than later :)

---

### Post by dizzystreak on 2009-10-14
Hi Sean!

I am a dedicated mplayer user and I was wondering if you could implement remote control for that too.
Maybe this could be of some help:
[http://bit-rot.blogspot.com/2009/07/mplayer-remote-control-using-cellphone.html](http://bit-rot.blogspot.com/2009/07/mplayer-remote-control-using-cellphone.html)

---

### Post by SeanHodges on 2009-10-14
> **dizzystreak said:**
> Hi Sean!

I am a dedicated mplayer user and I was wondering if you could implement remote control for that too.
Maybe this could be of some help:
[http://bit-rot.blogspot.com/2009/07/mplayer-remote-control-using-cellphone.html](http://bit-rot.blogspot.com/2009/07/mplayer-remote-control-using-cellphone.html)

Hi dizzystreak,

MPlayer support would definitely be a great addition, I was also a dedicated mplayer user for a while.

I've added a task to my bug tracker ([https://sourceforge.net/apps/trac/android-tesla/ticket/51](https://sourceforge.net/apps/trac/android-tesla/ticket/51)) and will investigate it as soon as I get chance. In the meantime, if you are aware of someone who might like to take the development task on, I'll be more than happy to work with them to get the support added.

Thanks for the suggestion.

---

### Post by brendanpiater on 2009-10-22
Sorry for the late reply/update. Just wanted to say that with the latest Karmic builds the app is working 100% for me! Fantastic, thanks very much.

Cheers
B

---

### Post by atlas2003 on 2009-10-24
Hello
I would love to try this cool app on my android but I have the same connection problem.
I've just installed karmic today (a fresh install)
I've got my android phone since 2 days only, and I have installed the last version (0-9) of tesla today.
I have the message "connecting with computer" endlessly
My wifi is working. I have tring to log on my computer with connectBot and it's working very well


So i don't know what to do know :( Have you some advice for me please?

---

### Post by SeanHodges on 2009-10-25
> **atlas2003 said:**
> Hello
I would love to try this cool app on my android but I have the same connection problem.
I've just installed karmic today (a fresh install)
I've got my android phone since 2 days only, and I have installed the last version (0-9) of tesla today.
I have the message "connecting with computer" endlessly
My wifi is working. I have tring to log on my computer with connectBot and it's working very well


So i don't know what to do know :( Have you some advice for me please?

Hi atlas2003, thanks for giving Tesla a try :)

I must confess I haven't done much testing on Karmic myself, but I know of others who have reported it works for them. A couple of things to try straight away:

1. Have you set up a Firewall, using a tool like Firestarter or UFW? If so, you will probably need to add a rule to allow Tesla to connect. I suspect that your test with ConnectBot has probably ruled this out, but worth considering.

2. Sometimes Android phones can have trouble resolving host names on a local network. Have you tried typing the IP address of your computer into the Hostname field instead?

If neither of these solve your problem, I'll get the Karmic RC installed and we'll see if I can reproduce it here.

---

### Post by atlas2003 on 2009-10-25
Thank you for your reply.
No, I don't have any firewall
Yes, I use the IP directly

I'm sure it's a very stupid note but when I try to connect to my computer via another computer via SSH, the first time, the program ask me if I want to connect (or something like that) and I must type "YES". Could it be the same thing on tesla and tesla don't reply YES ?

Thank you!

---

### Post by SeanHodges on 2009-10-25
> **atlas2003 said:**
> Thank you for your reply.
No, I don't have any firewall
Yes, I use the IP directly

I'm sure it's a very stupid note but when I try to connect to my computer via another computer via SSH, the first time, the program ask me if I want to connect (or something like that) and I must type "YES". Could it be the same thing on tesla and tesla don't reply YES ?

Thank you!

That is a perfectly reasonable suggestion. The code in Tesla is expected to accept the session automatically, but that's not to say there isn't something unexpected happening. I'm looking to get a new release out this weekend, but after that I'll fire up a copy of Karmic and see if I can reproduce your issue. I suspect there is some change in Karmic that is only present on fresh installations... 

One last thing you could try is ensure that [libpam-ck-connector]("apt://libpam-ck-connector") is installed on your system? This was a problem for Hardy Heron users in the past.

---

### Post by atlas2003 on 2009-10-25
Yes, the package is already installed.
Thank you for your help :) I will wait the next release

---

### Post by Holmen on 2009-10-26
Hi and thank you for an awesome app!

Banshee works flawlessly but Totem is unfortunately not. It seems like it just aint getting contact with the PC.

I'm running Ubuntu Karmic on my PC and CyanogenMod 4.2.1 on my Magic device. I have also checked the D-Bus plugin for Totem, doesnt do the trick.

Any ideas?

---

### Post by Excedio on 2009-10-26
Any plans for Songbird support?

---

### Post by SeanHodges on 2009-10-27
> **Holmen said:**
> Hi and thank you for an awesome app!

Banshee works flawlessly but Totem is unfortunately not. It seems like it just aint getting contact with the PC.

I'm running Ubuntu Karmic on my PC and CyanogenMod 4.2.1 on my Magic device. I have also checked the D-Bus plugin for Totem, doesnt do the trick.

Any ideas?

Hey Holmen,

Thanks for reporting this. I haven't encountered the issue myself, but will give it a try.

At the moment the Totem support is based on the version shipped with Jaunty, which had no D-Bus plugin. I'm interested in having a play with the D-Bus interface for a future release though, as it may add a number of missing features into Tesla for that player.

Currently, Tesla sends commands to Totem using the CLI interface, for example:

"DISPLAY=:0 totem --play-pause"

Should pause/unpause the playing movie in Totem.

Would you mind running that command directly on your PC, and let me know if it works? I suspect there may be some changes in the version in Karmic.

---

### Post by SeanHodges on 2009-10-27
> **Excedio said:**
> Any plans for Songbird support?

I've added a ticket to look into Songbird support: [https://sourceforge.net/apps/trac/android-tesla/ticket/56](https://sourceforge.net/apps/trac/android-tesla/ticket/56)

Taking cursory look now, it seems that support could be added fairly easily using the "MPRIS" plug-in that is available in the Extensions directory. It will mean, however, that this plug-in will be required for Tesla to work with Songbird.

---

### Post by Holmen on 2009-10-27
> **SeanHodges said:**
> Hey Holmen,

Thanks for reporting this. I haven't encountered the issue myself, but will give it a try.

At the moment the Totem support is based on the version shipped with Jaunty, which had no D-Bus plugin. I'm interested in having a play with the D-Bus interface for a future release though, as it may add a number of missing features into Tesla for that player.

Currently, Tesla sends commands to Totem using the CLI interface, for example:

"DISPLAY=:0 totem --play-pause"

Should pause/unpause the playing movie in Totem.

Would you mind running that command directly on your PC, and let me know if it works? I suspect there may be some changes in the version in Karmic.

Thank you,

It did work with the commands above.

---

### Post by SeanHodges on 2009-10-27
Version 0.10 of Tesla has been released.

* Rhythmbox playlist support (wohoo!)
* Support for MPD music server (#35)
* Hostname field now accepts a port number as well: 1.2.3.4:22
* SSH compression, improves performance
* Fixed Amarok 2 playlist support
* Fix for shutdown button in mixed Gnome/KDE sessions (#30)
* Larger previous/next buttons (#43)

---

### Post by SeanHodges on 2009-10-27
> **Holmen said:**
> Thank you,

It did work with the commands above.

OK thanks, I'll keep searching. I have been testing the Totem support through 3 episodes of Futurama now, I think I will need to install Karmic to test further.

---

### Post by Holmen on 2009-10-28
It seems that I cant even use the command above from a SSH connection via ConnectBot on my mobile.

---

### Post by SeanHodges on 2009-10-28
> **Holmen said:**
> It seems that I cant even use the command above from a SSH connection via ConnectBot on my mobile.

That is definitely an interesting development. I'm downloading Karmic at the moment, I will have a try over the next couple of days and let you know my findings.

---

### Post by jorgealfaro on 2009-10-31
Hi, I have an Android and have been looking for a remote control application. I'm a Rhythmbox user. Any chance you can enable shuffle on/off for Rhythmbox (I don't know if you are using D-bus to control Rhythmbox, since I think shuffle can't be control that way). The other thing that would make this app perfect is if one could filter via the search bar.
Thank you for your effort. BTW why isn't this app on the android market? That way one could keep it updated, and you can also add another app for donation$ ;)

---

### Post by SeanHodges on 2009-11-01
> **jorgealfaro said:**
> Hi, I have an Android and have been looking for a remote control application. I'm a Rhythmbox user. Any chance you can enable shuffle on/off for Rhythmbox (I don't know if you are using D-bus to control Rhythmbox, since I think shuffle can't be control that way).

Hi jorgealfaro,

Shuffle mode sounds like a good idea, I've added it to the bug tracker:

[http://sourceforge.net/apps/trac/android-tesla/ticket/57](http://sourceforge.net/apps/trac/android-tesla/ticket/57)

By the looks of it, a lot of players have the ability to set their shuffle mode, but not to find out what it's currently set to. This will mean that the shuffle mode button will need to be just a simple button.

Unfortunately, as you said, Rhythmbox does not have the ability to change the shuffle mode remotely at all. If the functionality is added for the other media players, we could then contact the Rhythmbox developers and discuss what we need to add support for Rhythmbox.

> The other thing that would make this app perfect is if one could filter via the search bar.

Sounds interesting, which search bar are you referring to? The widget on the home screen?

> Thank you for your effort. BTW why isn't this app on the android market? That way one could keep it updated, and you can also add another app for donation$ ;)

I've purposefully left Tesla off Android Market right now. It is  currently not stable enough to withstand the user-rating system that AM uses, and publishing it exclusively on AndAppStore means more promotion for my preferred alternative market for Android apps :)

AndAppStore has a client app just like Android Market does, by the way, so you can get updates automatically and give donations (although I haven't turned donations on for Tesla.. yet). You can download it from [here]("http://andappstore.com/AndroidApplications/apps/AndAppStore_Client").

However, I do intend to publish on Google's Android Market (and Archos' AppLib market) once the project reaches it's stable 1.0 release. I also hope that 1.0 will happen soon. Feel free to subscribe to the project mailing lists for updates on this.

Thanks for your feedback!

---

### Post by nekr0z on 2009-11-01
I'm sorry to say that, but I have installed Tesla onto my HTC Hero (from AndAppStore), and all I get is "Connecting with computer" forever. The computer is running Karmic and is perfectly connectable via ConnectBot.

---

### Post by SeanHodges on 2009-11-01
Hi nekr0z,

Have you tried using your IP address instead of the hostname? and do you make sure the Wifi is connected before attempting a connection?

Those are the 2 most common solutions I've come across for people reporting the same problem as you. Also, are you running a firewall like ufw? I had one report where the person had simply forgotten to add a firewall rule to allow Tesla to connect...

If none of the above are the cause, can you let me know which version of Android are you running, so I can try and diagnose the problem?

---

### Post by nekr0z on 2009-11-01
Hi Sean,

I have actually only tried using my IP address, but hostname doesn't work either. :) And I'm pretty sure WiFi is connected, both laptop and Android are in the same network, the IP address I'm trying to connect is actually laptop's IP, laptop is not running any firewall (and can be connected with ConnectBot from the same Android device), and all the credentials (IP, login, password) are the same that work properly in ConnectBot.

Android is Android 1.5 running on HTC Hero (European version), and says it has "2.6.27-4cda1252 htc-kernel@and18-2 #789" for a kernel and "1.0.0.A6288" for firmware version.

---

### Post by SeanHodges on 2009-11-09
> **nekr0z said:**
> Hi Sean,

I have actually only tried using my IP address, but hostname doesn't work either. :) And I'm pretty sure WiFi is connected, both laptop and Android are in the same network, the IP address I'm trying to connect is actually laptop's IP, laptop is not running any firewall (and can be connected with ConnectBot from the same Android device), and all the credentials (IP, login, password) are the same that work properly in ConnectBot.

Android is Android 1.5 running on HTC Hero (European version), and says it has "2.6.27-4cda1252 htc-kernel@and18-2 #789" for a kernel and "1.0.0.A6288" for firmware version.

Hi nekr0z,

I have a possible fix for your issue, and currently working on a new release (should be available in a day or so).

It's very difficult to determine exactly what the problem is, as a "cannot connect to my Wifi network" report is not easy to reproduce. I have, however, managed to get Tesla into an infinite loop by attempting to connect to a network that was not not broadcasting it's SSID in the expected way.

I've removed the check for a valid SSID in the next release, so if you could test that for me it would really help.

If it doesn't fix the issue, I could use any information about your Wifi configuration that you feel happy to provide for me, for example - is it MAC address filtered? is it static/dynamic IP addressing? and are there other connection complications such as hiding the SSID, or using WPA security? ? I don't know how much of this you will be able to give me, but it will allow me to more closely configure my Wifi network to match what you have.

Thanks for your patience

---

### Post by nekr0z on 2009-11-09
Thank you, Sean, I'm looking forward to testing a new release.

Concerning your questions about WiFi configuration, I must say that SSID is not hidden, no MAC-filtering is set up, WiFi is DHCP-configured by the router and WPA2-Personal protected.

---

### Post by nekr0z on 2009-11-11
I see the same behaviour in 0.11. Maybe it's me doing something wrong.

---

### Post by SeanHodges on 2009-11-11
> **nekr0z said:**
> I see the same behaviour in 0.11. Maybe it's me doing something wrong.

Thats disappointing. I'll have a think about it tonight. I might be able to apply a few custom mods to Tesla that interrupts the connection process and displays a report on what it was trying to do when it got stuck.

---

### Post by sarion on 2009-11-13
Hi Sean,

Thank you for creating this app! :-)

I have just got it running on my HTC Hero. Now I can control Songbird playing on my Ubuntu Jaunty machine. I love it!

Before I got my Hero, I used Songbird Remote on my iPod Touch, which had some connection issues, which I don`t experience with Tesla. Also, I like that Tesla pauses my songs when I make calls on the phone.

When I press Playlist, and select another song, the music just keeps playing. After that, Tesla won't work again until I kill and restart it. So I`m not using the playlist feature at the moment.

Are you planning to add functions that let you choose songs & albums from the entire collection that Songbird has? That would be high on my wish list.

Again, thank you and please keep up the good work!

---

### Post by SeanHodges on 2009-11-19
Hey sarion, glad to hear you've got Tesla working with Songbird. You're the first to give me feedback for that player :)

> **sarion said:**
> When I press Playlist, and select another song, the music just keeps playing. After that, Tesla won't work again until I kill and restart it. So I`m not using the playlist feature at the moment.

It appears that you've found a bug. The MPRIS plug-in for Songbird does not support adding/changing tracks, so for the next release I've disabled that functionality until I can find a workable solution.

This means you'll be able to view the playlist, and Tesla won't crash/hang when you attempt to change the track, but it won't change the track either.

> Are you planning to add functions that let you choose songs & albums from the entire collection that Songbird has? That would be high on my wish list.

I definitely intend to add this functionality to Tesla soon, but the Songbird support will not be possible until I find some way of changing the playing track in Songbird remotely. I'll let you know when I have any progress on this...

---

### Post by purifiedmadness on 2009-11-19
installed it on my G1 my computer is running 9.10 and it works great for Rythmbox, but when i try and use it with vlc it trys to connect and then tells me the host is no longer available. my vlc is 1.0.2 and i do have D-Bus turned on. i havnt not tryed using it with any other players yet. thanks for all the work you have done on the program.

---

### Post by sarion on 2009-11-20
Hi Sean,
 
Thanks for the response. When I used Songbird Remote, that allowed me to browse and select songs from my collection to play. That requires a separate plug-in for Songbird. Perhaps you can find out how that works?
 
All the best,
 
Sarion

---

### Post by SeanHodges on 2009-11-20
> **sarion said:**
> When I used Songbird Remote, that allowed me to browse and select songs from my collection to play. That requires a separate plug-in for Songbird. Perhaps you can find out how that works?

Sarion,

Thanks, I'll be sure to look into it.

The only complication is that the collection browsing has to work for the other supported media players too. Still, it might provide some standard interface that Tesla can re-use.

---

### Post by rich-brun on 2009-11-23
Found this app through the ADC2, loved it, best remote. Works perfectly on my G1, Android 1.7, controlling Banshee. I'm looking forward to seeing this app in the market place and giving it a suitably good rating.

For what its worth, I believe the that having some form of control over playlists will be the killer feature (currently lacking in Banshee). Though a nice touch would be to loose the volume and playlist buttons and replace them with swipes e.g. left swipe to switch application, right swipe for playlist (so a sort of back / forwards thing) and vertical swipes to control the volume (either directly, or bring up a volume controller). Just some ideas, do what you will with them :p

Many thanks for your efforts!

Rich.

---

### Post by SeanHodges on 2009-11-24
Hi Rich,

Great to know it's working for you. The plan is to get Tesla on the Android market pretty soon, once some of the final major tasks are complete. This is just to avoid getting too much negative feedback whilst the app is incomplete.

> For what its worth, I believe the that having some form of control over playlists will be the killer feature (currently lacking in Banshee).

The playlist control had to be disabled for Banshee for the moment, because Banshee does not provide playlist support using the remote control interface that Tesla is using. I'll take another look to see if this might be possible some other way, if not I plan to contact the developers and see if the support can be added in a future release.

> Though a nice touch would be to loose the volume and playlist buttons and replace them with swipes e.g. left swipe to switch application, right swipe for playlist (so a sort of back / forwards thing) and vertical swipes to control the volume (either directly, or bring up a volume controller).

Gesture support is definitely something I'd like to add, as long as it doesn't negatively impact the simplicity of the UI.

I think the big easy-to-press buttons are preferable for some people, but I've always thought an alternative "gesture mode" would be neat for people like yourself who would find gestures a better method of controlling the player. 

I'll add your suggestions to the bug tracker so that they can be considered when I (or someone else) gets around to adding gesture support. You can keep an eye on the feature request here: [http://sourceforge.net/apps/trac/android-tesla/ticket/47](http://sourceforge.net/apps/trac/android-tesla/ticket/47)

Thanks a lot for your feedback, suggestions and comments are always welcome :)

---

### Post by SeanHodges on 2009-11-24
purifiedmadness, nekr0z,

I've Spent a fair bit of time debugging the connection process in Tesla, and just made another release.

Would you both mind testing the new release, and letting me know if your connection problems have been resolved?

Thanks for your patience.

---

### Post by zaphod777 on 2009-11-24
Using the HTC Magic on 1.6 I can connect to my ubuntu 9.10 machine and view songs playing in songbird but as far as changing songs adjusting volume etc none of that works. It's as if I have read only access.

I have the MPRIS addon in songbird installed.

Overall great app I can't wait until it is polished.

---

### Post by zaphod777 on 2009-11-24
> **zaphod777 said:**
> Using the HTC Magic on 1.6 I can connect to my ubuntu 9.10 machine and view songs playing in songbird but as far as changing songs adjusting volume etc none of that works. It's as if I have read only access.

I have the MPRIS addon in songbird installed.

Overall great app I can't wait until it is polished.

Actually I just updated to the latest version you just posted and I can start, stop, skip songs, and adjust volume. However I can't pick a song from the playlist and have it play.

Also it would be sweet to be able to add songs to the playlist from the remote. 

Also multiple profiles would be good.

This uses the standard ssh port right? That way I can forward the port from my router and access from anywhere. But my router doesn't support local loopback so it would be nice to have an away profile and a home profile.

Thanks for the awesome app!

If you need a next project I know people would love to use the blue tooth to control their PS3 so we don't have to buy the $30 PS3 BlueRay remote.

---

### Post by nekr0z on 2009-11-24
> **SeanHodges said:**
> Would you both mind testing the new release, and letting me know if your connection problems have been resolved?
Thanks a lot for not giving up, Sean, and yes, 0.11.1 finally works for my configuration. Man, you've done a grrrrreat job, my English is not just good enough to say how much I appreciate that!

And I completely share zaphod777's eagerness to see Tesla polished, as well as rich-brun's thoughts about gestures interface (as an option, perhaps), my personal concern being too large steps in volume adjusting, but I totally understand it's a lot of work, and you've already done a tremendous amount of it. Just don't give up yet, please!

I only hope Remuco doesn't get a functional Android client before Tesla is mature enough to hit the Market, as your app definitely deserves "king of the hill" status. I must confess that as soon as Remuco does that and Android opens bluetooth to work properly, I'll be very tempted to switch, since bluetooth is a killer feature for me, at least sometimes (imagine me at my seaside house during vacation: a laptop playing music and no internet connection but slow and expensive GPRS on the phone), but as it stands now I'm a great Tesla fan. Thanks again!

---

### Post by zaphod777 on 2009-11-24
Also one suggestion. I have noticed that people will lose a star on their rating if the user doesn't like the icon.

This one isn't bad but I think with a name like Tesla you could have a pretty cool looking icon.

Somehow I imagine a cool looking remote with blue lightning arcing off of it.

---

### Post by nekr0z on 2009-11-24
Sean, it looks like I've found a bug in Tesla. I have enabled an option to pause the playback when a call is being received, and it works great. But then I have the music stopped, Tesla still connected, and I decide to call my girlfriend. I dial her number, she picks up the phone, and guess what? All of a sudden my computer's speakers give all their 2x80W "Die My Darling" by Metallica! I admit it was funny.

Looks like Tesla triggers play/pause regardless of whether anything is being played or not, which can be a little inconvenient.

By the way, this feed is obviously not the best place to report bugs. What's the right place? Somewhere on Launchpad would be nice...

---

### Post by SeanHodges on 2009-11-26
> **zaphod777 said:**
> Actually I just updated to the latest version you just posted and I can start, stop, skip songs, and adjust volume. However I can't pick a song from the playlist and have it play.

Glad to hear it's working for you now, I think the extra time spent on stability in 0.11.1 has really paid off.

I had to disable changing tracks in Songbird, the MPRIS plugin currently does not support that feature. When I get time, I hope to contact the developer and discuss the issues with adding the "DelTrack()" and "AddTrack()" functions to the plugin - he does actually state they are not supported in the plugin description.

There may be some other way to get the playlist functionality to work, but I wanted to ship what was working so people could start using it. Hopefully a fix will be possible in a future release.

> Also it would be sweet to be able to add songs to the playlist from the remote. 

The explanation above applies to this as well. A collection browser is in the works for Tesla, but Songbird will not be supported until the plugin supports the ability to add tracks (or a better plugin is written).

> Also multiple profiles would be good.

This uses the standard ssh port right? That way I can forward the port from my router and access from anywhere. But my router doesn't support local loopback so it would be nice to have an away profile and a home profile.

Connection profile support has also been suggested in the bug tracker: [http://sourceforge.net/apps/trac/android-tesla/ticket/25](http://sourceforge.net/apps/trac/android-tesla/ticket/25). I admit it's something I would really like too. I'll look into adding it soon.

> If you need a next project I know people would love to use the blue tooth to control their PS3 so we don't have to buy the $30 PS3 BlueRay remote.

Bluetooth support is definitely planned ([http://sourceforge.net/apps/trac/android-tesla/ticket/8](http://sourceforge.net/apps/trac/android-tesla/ticket/8)), right now it is waiting for Android 2.0 to gain market share, as 1.5 and 1.6 can't support this.

As far as controlling a PS3, it's not an impossibility, I'd very much like to add support for it. Unfortunately I don't own one, so either someone else will need to contribute that to Tesla - or they will need to buy me a PS3 :)

> Also one suggestion. I have noticed that people will lose a star on their rating if the user doesn't like the icon.

This one isn't bad but I think with a name like Tesla you could have a pretty cool looking icon.

Somehow I imagine a cool looking remote with blue lightning arcing off of it. 

I'll come clean, I'm really not much of a graphic designer. I dabble with it, but really I'm a software developer. As you say, the Tesla icon is OK, but not great. 

I hope to start a donation scheme soon, which might be able to fund some hours for a graphic designer to beef up the Tesla artwork. In the meantime though, we can only hope someone might contribute some better artwork to the project for free.


Thanks for your points, it's always great to get feedback on the project!

---

### Post by SeanHodges on 2009-11-26
Hey nekr0z,

> **nekr0z said:**
> Thanks a lot for not giving up, Sean, and yes, 0.11.1 finally works for my configuration. Man, you've done a grrrrreat job, my English is not just good enough to say how much I appreciate that!

Thanks for the encouragement nekr0z. Hopefully Tesla will continue to improve. The idea pool is definitely expanding, and I'm enthusiastic it will implement a lot of them, the only bottleneck is my free time :) Hopefully others might start to jump onto the project and help to expand it even further.

> I only hope Remuco doesn't get a functional Android client before Tesla is mature enough to hit the Market, as your app definitely deserves "king of the hill" status.

I've seen a number of competitors to Tesla, but I must say Remuco is not one I've come across before. It looks cool.. thanks for pointing it out to me.

To be honest, I'm not too concerned about competition right now. Projects like G-Mote, android-vlc-remote, and Remuco are already very popular, and the concept of a mobile phone remote control is definitely not new.

My aim with Tesla is to support a large number of media players with very little configuration from the user. I like the idea that you could take your Android phone to someone's house, armed with little more than maybe a Linux live-CD, and control your friend's music using your phone at a house party. In fact, I recently heard that someone did just that - so in a way my objective was met ;)

I also want to utilise the capabilities of the Android platform. Projects like Remuco aim to support multiple phone platforms, which obviously restrict how much of Android's capabilities they can support. At the moment I've only scratched the surface of this with the "pause on call" feature, my hope is that this is just the start.

I also want this project to be a community effort, rather than a closed-off design process. This bit I'm still struggling with, but these things do take time and effort for a new project.

> it looks like I've found a bug in Tesla. I have enabled an option to pause the playback when a call is being received, and it works great. But then I have the music stopped, Tesla still connected, and I decide to call my girlfriend. I dial her number, she picks up the phone, and guess what? All of a sudden my computer's speakers give all their 2x80W "Die My Darling" by Metallica! I admit it was funny.

Looks like Tesla triggers play/pause regardless of whether anything is being played or not, which can be a little inconvenient.

Whoops, ha ha! I see what you mean, this problem must have slipped the net when I was testing.

I can see a fix for most players, but the problem gets a little more tricky for the ones that don't report whether they are playing (e.g. Songbird and Totem). I'll have a think, there must be some way to detect if sound is coming out of the speakers or something.

> By the way, this feed is obviously not the best place to report bugs. What's the right place? Somewhere on Launchpad would be nice...

The bug tracker for Tesla is powered by Trac/Sourceforge. You can get to it on the project website: [http://tesla.seanhodges.co.uk/]("http://tesla.seanhodges.co.uk/") (scroll down to the Contributing section)

Whilst I'm happy for people to report bugs however they like, the best place to report them is there, because that is the list I ultimately use to track the progress of the project. It also makes it easier for others to pick up the bugs and contribute fixes.

---

### Post by zaphod777 on 2009-11-26
> **SeanHodges said:**
> 
I'll come clean, I'm really not much of a graphic designer. I dabble with it, but really I'm a software developer. As you say, the Tesla icon is OK, but not great. 

I hope to start a donation scheme soon, which might be able to fund some hours for a graphic designer to beef up the Tesla artwork. In the meantime though, we can only hope someone might contribute some better artwork to the project for free.


Thanks for your points, it's always great to get feedback on the project!

Thanks for the great explanation I really like this app. 

My brother just happens to be a graphic designer so I might be able to get him to make an icon if you let me know what specs you need for it and a general idea of what you want it to look like. 

But he did just have a baby so I can't promise anything right away but it sounds like something he could do without too much trouble.  

As far as the PS3 goes I have one but I haven't programed since college so I'm not sure I can be much help there.

I am actually interested in writing some simple apps for my phone can you point me in the right direction to get the software I need to try my hand at writing some android code?

It looks like there is quite a bit I need to do to get the SDK running. I am using Ubuntu 9.10 x64. 

Thanks again.

---

### Post by Dave M G on 2009-12-08
I am experiencing the same problem that many have reported, which is that I get the "Connecting with computer" message and nothing else.

I am running Ubuntu Karmic 9.10, and I am trying to connect to Amarok 1.4.

Question 1: You say the Firewall needs to be opened up for Tesla to connect, however, I have seen no mention of what port that should be. I am using Firestarter for a firewall, and I have attempted turning the firewall off completely, but that made no difference. In any case, what port or confirguration should I use to ensure the firewall is not blocking Tesla?

Question 2: What else do I need to do to diagnose and or fix the problem?

Thanks for making this potentially great app.

By the way, I'm running Android 1.6 on an ht-03a.

---

### Post by zaphod777 on 2009-12-08
> **Dave M G said:**
> I am experiencing the same problem that many have reported, which is that I get the "Connecting with computer" message and nothing else.

I am running Ubuntu Karmic 9.10, and I am trying to connect to Amarok 1.4.

Question 1: You say the Firewall needs to be opened up for Tesla to connect, however, I have seen no mention of what port that should be. I am using Firestarter for a firewall, and I have attempted turning the firewall off completely, but that made no difference. In any case, what port or confirguration should I use to ensure the firewall is not blocking Tesla?

Question 2: What else do I need to do to diagnose and or fix the problem?

Thanks for making this potentially great app.

By the way, I'm running Android 1.6 on an ht-03a.

Greetings! I am typing from Chigasaki make sure you have the latest version installed and ssh server installed on your machine also you need to have the MPRIS plugin installed on songbird.

it uses the standard ssh port to connect so make sure that that is opened up on your machine.

How are you connecting by internal network or 3G? if 3G you need to make shure the port is forwarded and you are using the puplic ip.

---

### Post by zaphod777 on 2009-12-08
BTW I have the same phone on DOCOMO.

---

### Post by Dave M G on 2009-12-08
Zahod777,

Thank you for your reply.

Can you be a little more specific?

> MPRIS plugin installed on songbird

Songbird? I am trying to connect to Amarok. Isn't Songbird an entirely different music player application?

I have the latest openssh-server installed, and I assume it is working because I can connect from both of my other two Ubuntu computers.

And I am connecting by internal network. At least, as far as I can tell I am.

---

### Post by zaphod777 on 2009-12-08
OK then disregard the songbird part. I have it working in songbird. Let me check tomorrow and get back to on Amorok. Its pretty late and I have Japanese language school in the morning. 

I will test with mine since I basically has the same config but not using Amorok.

---

### Post by Dr Rude on 2009-12-08
So, what if one were to set up an ad-hoc network? I've been considering learning how to do this any way, so if your app works with it, I really have no choice...

Or, is this something I should do and post the details?

---

### Post by zaphod777 on 2009-12-08
> **Dr Rude said:**
> So, what if one were to set up an ad-hoc network? I've been considering learning how to do this any way, so if your app works with it, I really have no choice...

Or, is this something I should do and post the details?

You should give it a try as long as your machine is pingable and you know the IP I don't see why it wouldn't work.

---

### Post by zaphod777 on 2009-12-09
> **zaphod777 said:**
> OK then disregard the songbird part. I have it working in songbird. Let me check tomorrow and get back to on Amorok. Its pretty late and I have Japanese language school in the morning. 

I will test with mine since I basically has the same config but not using Amorok.

I got it to connect just fine using Amorok did you install
apt://libpam-ck-connector 
?

[http://sourceforge.net/apps/trac/android-tesla/wiki/Instructions](http://sourceforge.net/apps/trac/android-tesla/wiki/Instructions)

That step is requred as you can see on the bottom of the page.

---

### Post by SeanHodges on 2009-12-09
Hey Zaphod777, sorry for the slow reply:

> **zaphod777 said:**
> My brother just happens to be a graphic designer so I might be able to get him to make an icon if you let me know what specs you need for it and a general idea of what you want it to look like. 

But he did just have a baby so I can't promise anything right away but it sounds like something he could do without too much trouble. 

If he is interested that would be a great :D 

There are some comprehensive guidelines for Android icons in the [developer documentation]("http://developer.android.com/guide/practices/ui_guidelines/icon_design.html"). The basics are that the icon must be 48x48 pixels in size, use the "launcher icon" colour palette for the background, and drawn in the traditional Android 3D icon perspective.

Beyond that, I'm happy for something new and different. I like your blue lightning idea, though I think I'll reserve further comment. I often find brain dumping suggestions can stifle the creativity of designers :)

As you say, he's probably very busy right now, but if he has some spare time a new icon design would be very welcome.

> I am actually interested in writing some simple apps for my phone can you point me in the right direction to get the software I need to try my hand at writing some android code?

It looks like there is quite a bit I need to do to get the SDK running. I am using Ubuntu 9.10 x64.

I know what you mean about setting up the SDK for the first time being hard work. The process is actually quite easy, once you know where to start.

I haven't read it carefully, but [this guide]("http://unixlab.blogspot.com/2009/09/how-to-install-android-sdk-16-on-ubuntu.html") seems to be fairly up-to-date, with screenshots and simple steps. At a glance it does seem a little long-winded, but I think it just describes the steps in a lot of detail.

One other option is to do what I did when I started developing for Android, and download a VM with the SDK pre-installed. The one I used is now seriously out of date, but a quick search turned up [this one]("http://forum.openhandsetdevelopers.com/android-open-handset-developers-community-vmware-appliance-t16.html"). Obviously this is best as a stepping stone for getting familiar with the Android development environment - eventually you will want the SDK on your native machine.

One thing to bear in mind is that the SDK is not officially supported on 64bit platforms yet. I use it on 64bit myself and it works fine, but just be warned you may find some bugs along the way.

If you still have trouble, let me know and I'll try writing up some instructions myself. I will probably make use a tutorial like this again some time anyway.

---

### Post by SeanHodges on 2009-12-09
Hey Dr Rude,

The "Connecting to computer" message that you describe sounds like your version of Tesla is out of date. Can you check that you have downloaded the latest version (0.11.1)? I would expect you to get a more descriptive message appear on the progress dialog.

> **Dr Rude said:**
> So, what if one were to set up an ad-hoc network? I've been considering learning how to do this any way, so if your app works with it, I really have no choice...

Or, is this something I should do and post the details?

Hmm, well Tesla should work on any network, but in some cases people have had to use their IP address instead of their hostname to connect properly. So the only requirement you might have is to use a static IP address on your computer to avoid typing in a new address each time, you should still be able to get Tesla working with a dynamic IP address though.

If you hare having trouble connecting, a good test is to install the "ConnectBot" app (an SSH client) from the market and try to connect with that. Both Tesla and ConnectBot use a very similar connection method.

The port that you want to unblock in Firestarter is port 22 (TCP).

If you continue to have problems, please post them up. A lot of work has been done to get Tesla connecting reliably, but occasionally people report new complications that we haven't yet thought of.

---

### Post by Dave M G on 2009-12-09
Solved!

I thought I had the latest version, which I had acquired through the Android Developer Challenge.

But I uninstalled it, went to the site, and downloaded the latest.

Worked like a charm. I'm using it now to play songs with Amarok, and it's great.

Well made app. This is definitely going to get a lot of use.

Keep up the good work, and thanks to all those who offered helpful suggestions.

---

### Post by SeanHodges on 2009-12-09
> **Dave M G said:**
> Solved!

I thought I had the latest version, which I had acquired through the Android Developer Challenge.

But I uninstalled it, went to the site, and downloaded the latest.

Worked like a charm. I'm using it now to play songs with Amarok, and it's great.

Well made app. This is definitely going to get a lot of use.

Keep up the good work, and thanks to all those who offered helpful suggestions.

Great! There is another update on it's way soon, with some fixes that will be relevant to you. I'll let you know when it's available.

---

### Post by Dave M G on 2009-12-09
SeanHodges,

Now that I've had time to play with it a bit, as expected, I have a few questions.

1. If Amarok is already open, then Tesla will not connect, saying something like "media player is no longer available". Is it not possible for Tesla to join an already running Amarok? It would be ideal if it could, because I like to leave the Amarok interface up and running, and then I go to it and mix playlists whenever I feel like it. So really, Tesla would just be for me to start and stop songs, and volume control.

2. The "turn of computer" option seems a bit drastic to me. The computer I have Amarok on is a Mythbuntu machine that I never turn off. Shut down, lock screen and suspend are all not options for me. Wouldn't it be best to simply have it exit the application? Currently, once I start Amarok with Tesla, I can not make Amarok stop and I have to exit the application directly with my computer.

3. Now that I have installed Tesla directly from the web site, will it automatically update and upgrade like other applications? I've never installed anything outside of the Android market before.

Thanks for your time and effort with this great app!

---

### Post by kyle99 on 2009-12-09
Works great with my droid, I use exaile for my media player, and it changes songs flawlessly. One thing I think you should add is a library that will show all songs in the library, but it works great otherwise :)

---

### Post by JungleBeast on 2009-12-10
Hi there, brilliant app!
- i'm desperately trying to install it, but it seems to be falling over.

I'm running ubuntu 9.10 32 bit with OpenSSH installed and running.
Tesla app is installed on HTC Hero, and I'm using my IP address as host name.

It goes through the following steps:
Establishing SSH connection
Starting a remote session
Connection Complete

Then I get 'failed to connect to remote machine' with a very long error msg basically saying that it failed to send the command to the device.

Any ideas?

---

### Post by SeanHodges on 2009-12-11
> **Dave M G said:**
> SeanHodges,

Now that I've had time to play with it a bit, as expected, I have a few questions.

Excellent, feedback and suggestions are always welcome.

> 1. If Amarok is already open, then Tesla will not connect, saying something like "media player is no longer available". Is it not possible for Tesla to join an already running Amarok? It would be ideal if it could, because I like to leave the Amarok interface up and running, and then I go to it and mix playlists whenever I feel like it. So really, Tesla would just be for me to start and stop songs, and volume control.

This sounds like a bug. It doesn't seem to be behaving like that for me, both with Amarok 2.2.1 and Amarok 1.4. Can you let me know which exact version of Amarok you are using? Also, try connecting whilst Amarok is "playing" and again whilst it is "stopped" - It would be useful to know if there is a difference.


> 2. The "turn of computer" option seems a bit drastic to me. The computer I have Amarok on is a Mythbuntu machine that I never turn off. Shut down, lock screen and suspend are all not options for me. Wouldn't it be best to simply have it exit the application? Currently, once I start Amarok with Tesla, I can not make Amarok stop and I have to exit the application directly with my computer.

Good idea. I'll look into adding a "close player" option soon.


> 3. Now that I have installed Tesla directly from the web site, will it automatically update and upgrade like other applications? I've never installed anything outside of the Android market before.

If you downloaded it directly from the Sourceforge website, then no. 

I intend to publish Tesla on the Android Market soon, but in the meantime if you want to get automatic updates, you can install Tesla from the AndAppStore market, which is similar to Google's Android Market. You can get a client for you phone [here]("http://andappstore.com/AndroidApplications/apps/AndAppStore_Client"), download that on your phone, then run it and search for "Tesla". You'll probably need to uninstall your existing version of Tesla first.

---

### Post by SeanHodges on 2009-12-11
> **kyle99 said:**
> Works great with my droid, I use exaile for my media player, and it changes songs flawlessly. One thing I think you should add is a library that will show all songs in the library, but it works great otherwise :)

Great! I'm currently working on that exact feature at the moment. Hopefully an update will be available soon.

---

### Post by SeanHodges on 2009-12-11
> **JungleBeast said:**
> Hi there, brilliant app!
- i'm desperately trying to install it, but it seems to be falling over.

I'm running ubuntu 9.10 32 bit with OpenSSH installed and running.
Tesla app is installed on HTC Hero, and I'm using my IP address as host name.

It goes through the following steps:
Establishing SSH connection
Starting a remote session
Connection Complete

Then I get 'failed to connect to remote machine' with a very long error msg basically saying that it failed to send the command to the device.

Any ideas?

Hmm, I'll take a proper look this weekend and see if I can figure out whats going on.

It sounds like it is connecting properly, but then failing to launch the player you have selected. Which media player are you trying to remote control? Do you get the same behaviour if you select a different player?

---

### Post by SeanHodges on 2009-12-16
Hey all,

As of last night 0.12 of Tesla has been released... The big news this
time is the ability to search your PC's music and video collection!

You can get the latest release in the usual ways, see [the project website]("http://tesla.seanhodges.co.uk/") for details.

Full feature list:

* Collection browser (Currently only MPRIS supporting players)
* More accurate volume control
* Asynchronous artwork retrieval (improves UI refreshing)
* More SSH connection handling improvements
* The obligatory bug fixes

The collection browser requires the Tracker service to be enabled and
up-to-date on your PC (check the System -> Preferences -> Startup
Applications utility in Gnome, details on KDE4 support to come soon).
It is currently not available for Songbird, Rhythmbox, Banshee, and
Kaffeine; support for these players is intended to be added soon.

Focus for next release will be to expand the current functionality for
all media players. Currently some players do not support certain
features because they lack a complete API. Hopefully some
collaborative development will help to bridge this gap.

---

### Post by nekr0z on 2009-12-20
Thanks for volume precision, Sean, it's much better this way. I'm still having that controversial behaviour on outgoing calls with music stopped, though.

And I must confess I have never seen album art in Tesla using Banshee (and I don't see it still). Not that I missed it too much.

---

### Post by zaphod777 on 2009-12-20
in the new version I can't view current playlist in Songbird I could before.

---

### Post by SeanHodges on 2009-12-20
> **nekr0z said:**
> Thanks for volume precision, Sean, it's much better this way. I'm still having that controversial behaviour on outgoing calls with music stopped, though.

And I must confess I have never seen album art in Tesla using Banshee (and I don't see it still). Not that I missed it too much.

I'll take a look at both of those issues in the next release. I have some ideas for the outgoing calls issue. 

The Banshee issue is interesting, so you see album art for other media players? I'll do some testing.

---

### Post by SeanHodges on 2009-12-20
> **zaphod777 said:**
> in the new version I can't view current playlist in Songbird I could before.

Ah, that is my fault. I was getting quite a few reports that the playlist was broken in Songbird, so I disabled it whilst the track changing functionality is not available.

If viewing the playlist is still useful, I'll re-enable the support in the next release. I'm also in discussion with the Songbird plugin developer about adding the necessary support for changing tracks, hopefully it won't be long before that can be added as well.

---

### Post by zaphod777 on 2009-12-20
> **SeanHodges said:**
> Ah, that is my fault. I was getting quite a few reports that the playlist was broken in Songbird, so I disabled it whilst the track changing functionality is not available.

If viewing the playlist is still useful, I'll re-enable the support in the next release. I'm also in discussion with the Songbird plugin developer about adding the necessary support for changing tracks, hopefully it won't be long before that can be added as well.

It is pretty handy to view the play list even if you can't select a song that way you know how many times to skip ahead if you want to find a song. Also a cool feature to add would be to start the media player selected if not already started since you have an ssh connection already I don't think it would be too hard.

For songbird since users can really put it in any location maybe add the option to specify the path. 

Thanks for all of the hard work!

More features in Songbird are much welcomed so please thank the devs for the help the seem to be a good group of guys from what I can tell on the SongBird site. Hopefully maybe they can even feature your app on their web page I think if more people were aware of it you could get a few bucks in the Android market when it is done.

---

### Post by nekr0z on 2009-12-20
> **SeanHodges said:**
> The Banshee issue is interesting, so you see album art for other media players?

Haven't checked till today, actually, I only use Banshee with Tesla. Just tried Rhythmbox, no art either.

---

### Post by nekr0z on 2009-12-21
Cover arts suddenly appeared for Banshee today. Banshee is the same, Tesla is the same… Must be X-mas.

---

### Post by darchstar on 2009-12-22
Hi, I'm having some problems getting this app to work, i'm getting errors saying that it cannot find dbus session id in user environment when connecting to my computer. 
I can connect to my computer via connectbot ssh

---

### Post by SeanHodges on 2009-12-23
> **nekr0z said:**
> Cover arts suddenly appeared for Banshee today. Banshee is the same, Tesla is the same… Must be X-mas.

That's good news, sort of :) Please keep an eye on this for me, If I get any more reports of missing cover artwork I'll run some more tests.

---

### Post by SeanHodges on 2009-12-23
> **darchstar said:**
> Hi, I'm having some problems getting this app to work, i'm getting errors saying that it cannot find dbus session id in user environment when connecting to my computer. 
I can connect to my computer via connectbot ssh

Hey darchstar,

Are you using the latest version of Tesla? This was a known problem in earlier versions. You can get the latest version from either AndAppStore or Sourceforge. Download links and installation instructions are available on the project website: [http://tesla.seanhodges.co.uk](http://tesla.seanhodges.co.uk)

If you are seeing this problem on the latest version, the most likely issue is that you are using a Linux distribution that hasn't been tested yet. Can you let me know the following:

1. Which distribution you are using (Ubuntu, Fedora, Slackware, etc)
2. Which desktop environment you are using (KDE, Gnome, XFCE, etc)
3. The output of the following command:

```
echo "DBUS session ID = $DBUS_SESSION_BUS_ADDRESS"
```

---

### Post by zaphod777 on 2009-12-23
> **SeanHodges said:**
> That's good news, sort of :) Please keep an eye on this for me, If I get any more reports of missing cover artwork I'll run some more tests.

I had noticed before at first album work doesn't show then it did later. Not sure if that helps much.

Maybe it needs to initialize some connections then next time it works? 

But it in the new verion basicly none of the functions work in songbird can't skip pause or change volume. No error just doesn't effect the media player.

Recently I updated the latest songbird mpris plugin.

---

### Post by SeanHodges on 2009-12-23
> **zaphod777 said:**
> I had noticed before at first album work doesn't show then it did later. Not sure if that helps much.

Maybe it needs to initialize some connections then next time it works?

Possibly. Thanks, I'll take a look at the fetching code to see what might be causing the intermittent problems. 

> But it in the new verion basicly none of the functions work in songbird can't skip pause or change volume. No error just doesn't effect the media player.

Recently I updated the latest songbird mpris plugin.

The latest plugin should be fine, it just bumps the version number so the add-on supports the next release of Songbird.

I've seen this problem a couple of times actually, I suspect the song polling might be a bit too frequent, as it very occasionally seems too take over the connection completely and not allow any commands to be sent to the server. In each case I found that closing Tesla and reconnecting seemed to fix the problem. I'll run a few tests against this; the fact it seems to be a timing issue makes debugging quite difficult, but hopefully I can produce a fix after the new year.

---

### Post by cgb on 2009-12-23
This looks pretty nice, will have to give it a shot when I get home.  Thanks for your work on this!

---

### Post by darchstar on 2009-12-23
> **SeanHodges said:**
> Hey darchstar,

Are you using the latest version of Tesla? This was a known problem in earlier versions. You can get the latest version from either AndAppStore or Sourceforge. Download links and installation instructions are available on the project website: [http://tesla.seanhodges.co.uk](http://tesla.seanhodges.co.uk)

If you are seeing this problem on the latest version, the most likely issue is that you are using a Linux distribution that hasn't been tested yet. Can you let me know the following:

1. Which distribution you are using (Ubuntu, Fedora, Slackware, etc)
2. Which desktop environment you are using (KDE, Gnome, XFCE, etc)
3. The output of the following command:

```
echo "DBUS session ID = $DBUS_SESSION_BUS_ADDRESS"
```

Yea, I'm using Arch linux on Fluxbox window manager.
The output of the command you gave me was:

```
$ echo "DBUS session ID = $DBUS_SESSION_BUS_ADDRESS"
DBUS session ID =

```

---

### Post by SeanHodges on 2009-12-23
> **cgb said:**
> This looks pretty nice, will have to give it a shot when I get home.  Thanks for your work on this!

Great, if you have any problems, please post them up :)

---

### Post by SeanHodges on 2009-12-23
> **darchstar said:**
> Yea, I'm using Arch linux on Fluxbox window manager.
The output of the command you gave me was:

```
$ echo "DBUS session ID = $DBUS_SESSION_BUS_ADDRESS"
DBUS session ID =

```

Ah, it seems that your session does not have a running D-Bus daemon, which is needed for Tesla to interact with most of the media players.

I've added a fix for the next release, but you should be able to get it running straight away if you add the following code to your ~/.fluxbox/startup script (just before the "# exec /usr/bin/fluxbox" line):

```
if test -z "$DBUS_SESSION_BUS_ADDRESS" ; then
    eval $(dbus-launch --sh-syntax --exit-with-session)
fi
```

This will start the D-Bus daemon and add the session bus ID into the environment variables. You'll need to restart your session for the change to take effect.

---

### Post by darchstar on 2009-12-23
> **SeanHodges said:**
> Ah, it seems that your session does not have a running D-Bus daemon, which is needed for Tesla to interact with most of the media players.

I've added a fix for the next release, but you should be able to get it running straight away if you add the following code to your ~/.fluxbox/startup script (just before the "# exec /usr/bin/fluxbox" line):

```
if test -z "$DBUS_SESSION_BUS_ADDRESS" ; then
    eval $(dbus-launch --sh-syntax --exit-with-session)
fi
```

This will start the D-Bus daemon and add the session bus ID into the environment variables. You'll need to restart your session for the change to take effect.

Ok, Thanks. The command now shows that I have a dbus session id, but I am still having problems connecting with the error "Init script failed with output: Could not find dbus session id in user environment"

heres the output of the command you gave me before

```
$ echo "DBUS session ID = $DBUS_SESSION_BUS_ADDRESS"
DBUS session ID = unix:abstract=/tmp/dbus-XOafx5b9P9,guid=f26ebb4a36ea9128367a6d494b326e3c

```

---

### Post by wsonar on 2009-12-23
Will check it out on my G1

---

### Post by SeanHodges on 2009-12-23
> **darchstar said:**
> Ok, Thanks. The command now shows that I have a dbus session id, but I am still having problems connecting with the error "Init script failed with output: Could not find dbus session id in user environment"

heres the output of the command you gave me before

```
$ echo "DBUS session ID = $DBUS_SESSION_BUS_ADDRESS"
DBUS session ID = unix:abstract=/tmp/dbus-XOafx5b9P9,guid=f26ebb4a36ea9128367a6d494b326e3c

```

Can you provide me with the output of this command?

echo "Desktop session cookie = $XDG_SESSION_COOKIE"

If it returns an empty variable (like last time), you may need to run add this command to your startup script as well:

```
ck-launch-session
```

It will start ConsoleKit, which D-Bus depends on to identify each running desktop session on the machine.

Test the command in your terminal first, as ConsoleKit might need to be installed through pacman before it becomes available...

Also, it turns out that there are security measures preventing me from automating this, so I'll be using this discussion to write-up some set-up instructions for FluxBox. Please let me know if it works, and whether you had to install any additional packages...

---

### Post by darchstar on 2009-12-23
> **SeanHodges said:**
> Can you provide me with the output of this command?

echo "Desktop session cookie = $XDG_SESSION_COOKIE"

If it returns an empty variable (like last time), you may need to run add this command to your startup script as well:

```
ck-launch-session
```

It will start ConsoleKit, which D-Bus depends on to identify each running desktop session on the machine.

Test the command in your terminal first, as ConsoleKit might need to be installed through pacman before it becomes available...

Also, it turns out that there are security measures preventing me from automating this, so I'll be using this discussion to write-up some set-up instructions for FluxBox. Please let me know if it works, and whether you had to install any additional packages...

The output of the command you gave me was
```
$ echo "Desktop session cookie = $XDG_SESSION_COOKIE"
Desktop session cookie = c89125a950e4f664311ecd9e4b3006ff-1261598230.226956-852686305

```

It still is not letting me connect, saying that it failed to send command to device. At the end of the error it says there is no such file "/home/user/.dbus/session-bus/-0

---

### Post by SeanHodges on 2009-12-23
> **darchstar said:**
> The output of the command you gave me was
```
$ echo "Desktop session cookie = $XDG_SESSION_COOKIE"
Desktop session cookie = c89125a950e4f664311ecd9e4b3006ff-1261598230.226956-852686305

```

Was this after you issued the ck-launch-session command, or was the variable already available?

> It still is not letting me connect, saying that it failed to send command to device. At the end of the error it says there is no such file "/home/user/.dbus/session-bus/-0

OK, so this is the entire script being sent to the PC over SSH:

```
#!/bin/bash

XDG_ID="$(echo $XDG_SESSION_COOKIE | cut -d '-' -f 1)"
QUERY_ENVIRON="$(grep DBUS_SESSION_BUS_ADDRESS= ~/.dbus/session-bus/${XDG_ID}-0 | cut -d '=' -f 2,3,4)"
	
if [ "${QUERY_ENVIRON}" != "" ]; then
	export DBUS_SESSION_BUS_ADDRESS="${QUERY_ENVIRON}"
	echo "success"
else
	echo "Could not find dbus session ID in user environment"
fi
```

By the looks of it, your XDG_SESSION_COOKIE is not available over SSH, so this is getting a little more complicated.

You may need to add the ck-launch-session somewhere else, so it is started for each SSH login. I'll take a look at where it is started on my machine.

---

### Post by SeanHodges on 2009-12-23
It looks like ConsoleKit is started in my /etc/X11/Xsession script. If you edit that file and add:

```
/usr/bin/ck-launch-session
```

near the end, it should initialise the session at the correct time (as root, before D-Bus is started) and you should find the XDG_SESSION_COOKIE is set as expected (try that command I gave you earlier as a test).

You will need to restart your X server this time, so the Xsession script is called.

EDIT: Oh, and it's probably a good idea to remove it from your ~/.fluxbox/startup script again, if you added it earlier...

---

### Post by darchstar on 2009-12-23
> **SeanHodges said:**
> It looks like ConsoleKit is started in my /etc/X11/Xsession script. If you edit that file and add:

```
/usr/bin/ck-launch-session
```

near the end, it should initialise the session at the correct time (as root, before D-Bus is started) and you should find the XDG_SESSION_COOKIE is set as expected (try that command I gave you earlier as a test).

You will need to restart your X server this time, so the Xsession script is called.

EDIT: Oh, and it's probably a good idea to remove it from your ~/.fluxbox/startup script again, if you added it earlier...

Ok, so I didn't have an /etc/X11/Xsession file to begin with, so i created it and added the line you gave me, then removed it from my .fluxbox/startup script, now when i echo "echo "Desktop session cookie = $XDG_SESSION_COOKIE"" it comes up with nothing and the app is still giving me the same error. hmm

---

### Post by SeanHodges on 2009-12-23
> **darchstar said:**
> Ok, so I didn't have an /etc/X11/Xsession file to begin with, so i created it and added the line you gave me, then removed it from my .fluxbox/startup script, now when i echo "echo "Desktop session cookie = $XDG_SESSION_COOKIE"" it comes up with nothing and the app is still giving me the same error. hmm

OK, it sounds like I need to fire up my Arch VM and take a proper look at this issue. I suspect we need to follow some instructions for ConsoleKit in Arch before we can get any further.

I'll try and take a look as soon as I can, and will post up my findings here. It may take a few days if I don't manage to get some computer time over christmas eve/day.

Thanks for trying out my suggestions so far :)

---

### Post by Post Monkeh on 2009-12-23
my 5800 is an s60v5 so i can't use this, but it looks great. good work !

---

### Post by darchstar on 2009-12-24
> **SeanHodges said:**
> OK, it sounds like I need to fire up my Arch VM and take a proper look at this issue. I suspect we need to follow some instructions for ConsoleKit in Arch before we can get any further.

I'll try and take a look as soon as I can, and will post up my findings here. It may take a few days if I don't manage to get some computer time over christmas eve/day.

Thanks for trying out my suggestions so far :)

Alright, and thanks for your help. This app looks real sweet from the screenshots i saw. can't wait to finally get it to work on my box

---

### Post by zaphod777 on 2010-01-09
One suggestion give the option to prevent the phone from hibernating. My wireless turns off when the phone hibernates and I have to reconnect. 

Also my previous issues skipping tracks works fine now.  

I do notice in song bird that when I adjust the volume the little dot for the volume moves but not the solid bar. I have attached a screen shot. 

Also when decreasing the volume it doesn't change the bar in the volume solid bar but does lower the volume.

I am using the latest song bird that was released a little bit ago.

---

### Post by SeanHodges on 2010-01-09
> **zaphod777 said:**
> One suggestion give the option to prevent the phone from hibernating. My wireless turns off when the phone hibernates and I have to reconnect. 

This is the bug I'm currently working on. Some earlier fixes mean the Wifi should not be dropping, but I think now the connection times out because the song polling stops when the display is no longer being drawn. Hopefully I will have a fix soon, it's pretty much the last big obstacle before a stable release is possible.

There is actually a work-around for now:- Enable "Display always on" in the Tesla preferences and the phone should stay connected to the Wifi indefinitely. This is not the default setting, because of the obvious problem of battery consumption when preventing the phone from hibernating.

> Also my previous issues skipping tracks works fine now.  

I do notice in song bird that when I adjust the volume the little dot for the volume moves but not the solid bar. I have attached a screen shot. 

Also when decreasing the volume it doesn't change the bar in the volume solid bar but does lower the volume.

I am using the latest song bird that was released a little bit ago.

This looks like a cosmetic bug in Songbird. If the volume is changing correctly then Tesla is sending the correct commands. If I get chance I'll try and flag it up with the Songbird developers. If you decide to report it to them directly, the problem appears to be that this D-Bus command:

```
org.freedesktop.MediaPlayer.VolumeSet
```

Does not force the volume bar widget to re-draw correctly in Songbird. That, along with your screenshot, should be enough for them to work with. I'm happy to help where I can.

---

### Post by qualudeburrito on 2010-01-23
Edit:  I got it working.  It seems magic was involved.  Awesome app!  Thanks for your work!


I am having problems connecting to my computer.  After it says "Establishing SSH connection," it spits out the error 

"Error whilst authenticating with connected device: Incorrect password for user qualudeburrito"

I am positive that I am entering my password correctly and have successfully connected using ConnectBot.  

Does anyone have any ideas on how to resolve this?

---

### Post by mustang on 2010-01-23
This looks *really* cool. Big kudos to you for contributing to the community. 

Once I format, I'm going to give this a go. I'll let you know how it turns out.

---

### Post by SeanHodges on 2010-02-03
Version 0.13 of Tesla was released just last night...

[LIST]
[*]Collection browser support for Banshee and Rhythmbox
[*]Better adheres to the Android lifecycle
[*]Fix for connection dropping after ~5 mins of inactivity
[*]Check playback status before pausing/resuming on incoming call
[*]Various small fixes to connection process
[/LIST]

As usual, please let me know if you encounter any problems with this release...

---

### Post by SeanHodges on 2010-02-03
> **mustang said:**
> This looks *really* cool. Big kudos to you for contributing to the community. 

Once I format, I'm going to give this a go. I'll let you know how it turns out.

Great! Be sure to let me know how you get on...

---

### Post by hendrikwout on 2010-02-19
This is an AMAZING app and it working very nice with rhythmbox.

Thank you very much!

---

### Post by nekr0z on 2010-02-19
Great job, Sean. Got two questions though.

1. This Banshee playlist feature in the new release, that works, but… Say, I have half of my collection in playlist in Banshee, and press "Playlist" button in Tesla. What I have on screen is not the playlish that's playing, it's only the album from which the currently playing song is. More funny, the tracks from the album will appear here on the screen even if they are not in the playlist, I basically just get the full album. Is this a bug or a feature?

2. Banshee has a well- and long-known bug (that nobody seems to try to fix): it ignores the cover images for the albums that have no latin alphanumeric characters in artist's or album's name (say, the names are in Russian and thus in cyrillic letters, or, say, they are Greek or Hebrew or whatever), even if such images rest in album's folder and/or have been pointed to manually. Banshee ignores those covers, but Tesla shows them! I'm not saying it's a bug, I'm just wondering how that's possible… ;-)

---

### Post by SeanHodges on 2010-02-22
> **nekr0z said:**
> 1. This Banshee playlist feature in the new release, that works, but… Say, I have half of my collection in playlist in Banshee, and press "Playlist" button in Tesla. What I have on screen is not the playlish that's playing, it's only the album from which the currently playing song is. More funny, the tracks from the album will appear here on the screen even if they are not in the playlist, I basically just get the full album. Is this a bug or a feature?

It's not so much a feature as a work-around. Banshee doesn't support much in the way of remote controlling playlists, so I just query the music collection database for the rest of the album that matches the playing song. It also re-uses some code I wrote for Rhythmbox, which has similar restrictions with regards to playlists.

I'll take another look soon and see if there might be some way I can get the playlist information. Hopefully a Banshee developer might be able to point me in the right direction.

> 2. Banshee has a well- and long-known bug (that nobody seems to try to fix): it ignores the cover images for the albums that have no latin alphanumeric characters in artist's or album's name (say, the names are in Russian and thus in cyrillic letters, or, say, they are Greek or Hebrew or whatever), even if such images rest in album's folder and/or have been pointed to manually. Banshee ignores those covers, but Tesla shows them! I'm not saying it's a bug, I'm just wondering how that's possible… ;-)

Well Tesla doesn't actually get the album covers from Banshee. It neatly avoids needing that kind of support by requesting the album covers directly from the Last.fm API using the album and artist information. This way, Tesla does not actually need every media player to provide album covers in order to show them, it only needs them to provide the artist and album names of the song that is currently playing.

That Banshee language problem seems interesting, I imagine the song information must get corrupted somehow when it is passed to the artwork server. Post a link to the bug and I'll see if I can write a fix... You never know, it might be something simple :)

---

### Post by nekr0z on 2010-02-22
> **SeanHodges said:**
> That Banshee language problem seems interesting, I imagine the song information must get corrupted somehow when it is passed to the artwork server. Post a link to the bug and I'll see if I can write a fix... You never know, it might be something simple :)

The problem is actually some poor design decisions initially made by people who think all the world speaks nothing but English, and, as far as I understand, what stops developers from fixing this bug now that everybody is aware of other languages is the transition problem. Actually, it looks like there's been some movement finally during the last couple of months, but the bug is not fixed yet.
[https://bugzilla.gnome.org/show_bug.cgi?id=520516](https://bugzilla.gnome.org/show_bug.cgi?id=520516)

---

### Post by Holmen on 2010-03-01
Couldn't you add a option to add a special key or more. So that you could send custom commands. Like I want to be able to turn my monitor off.

You can to that by running the command:
```
set dpms force off
```

Maybe add this to the shutdown-button?

---

### Post by SeanHodges on 2010-03-01
> **Holmen said:**
> Couldn't you add a option to add a special key or more. So that you could send custom commands. Like I want to be able to turn my monitor off.

You can to that by running the command:
```
set dpms force off
```

Maybe add this to the shutdown-button?

Love it. I'll look into adding the monitor-off command this weekend.

I think the option to assign arbitrary commands might be a tad too liberal (e.g. someone could take your phone and re-bind a key to contain some nasty "rm -rf" bomb), but I like the concept that people can bind their own commands...

Perhaps there is a work-around: Maybe the special keys could attempt to call a fixed script name on the computer, and if the user wants it to do something they only have to create a script with that name, and insert the custom operation into it. That way the configuration is done at the PC end, which is likely to be less accessible to others.

What are your thoughts?

---

### Post by Holmen on 2010-03-04
> **SeanHodges said:**
> Love it. I'll look into adding the monitor-off command this weekend.

I think the option to assign arbitrary commands might be a tad too liberal (e.g. someone could take your phone and re-bind a key to contain some nasty "rm -rf" bomb), but I like the concept that people can bind their own commands...

Perhaps there is a work-around: Maybe the special keys could attempt to call a fixed script name on the computer, and if the user wants it to do something they only have to create a script with that name, and insert the custom operation into it. That way the configuration is done at the PC end, which is likely to be less accessible to others.

What are your thoughts?

Yeah, I did think about that users became able to run such "bombs", but I just wanted to get the discussion going - and was in quite a hurry.

Anyways, a computer-based script would be awesome! Great idea! Creating a ~/.tesla.sh file that could do all such of stuff. Ie. turning off and on monitor.

---

### Post by zaphod777 on 2010-03-04
Also it would be cool if it could check if the music app you want to remote control is running or not and if it isn't to run the command to start it. 

It would be sweet if I could just start songbird from my phone. The only complication I think would be is for media players not in the repositories you would need a custom path location for the program. Maybe a separate computer based script called ~.teslastart or something like that that we can add a command to start our media player of choice. Then if tesla tries to connect but can't connect to the media player it will run that script and try and connect in 5 seconds.

---

### Post by SeanHodges on 2010-03-04
> **zaphod777 said:**
> Also it would be cool if it could check if the music app you want to remote control is running or not and if it isn't to run the command to start it.

This should already be the case. Tesla does a check to see if the program is running and sends a launch command if it is not (you should see a "Launching player" message in the connection progress dialog when this happens)

I assume this isn't happening for Songbird. I'll take a look this weekend whilst I'm doing work on it.

---

### Post by DeanoCYM on 2010-04-14
Brilliant app thanks a lot!
Works perfectly with lucid and a htc tattoo.
Keep up the good work and thanks again!

Rhys

---

### Post by steigerjb on 2010-05-30
> **SeanHodges said:**
> Hey everyone,

I've been quietly working on a new project for the Android platform called Tesla...

It's a remote control for Ubuntu/Linux designed to work with a variety of media players. Currently it supports VLC, Amarok (1 and 2), Rhythmbox, Totem, Dragon Player, and Banshee. I hope to expand this as requests come in. You can use it to control playback, change the volume, and shutdown the PC using an easy to use remote control-like UI. Connection to your computer requires a Wifi network.

Anyone with an Android mobile phone, please give it a try and give me feedback. I'm more than happy to help out with any issues people have.

The project site is: [http://tesla.seanhodges.co.uk]("http://tesla.seanhodges.co.uk"). You can download the app by following [these instructions]("https://sourceforge.net/apps/trac/android-tesla/wiki/Instructions"), or using [AndAppStore]("http://andappstore.com/AndroidApplications/apps/186356").

**A note to VLC fans:** You need to follow [these steps]("http://ubuntuforums.org/showpost.php?p=7824159&postcount=13") for Tesla to work with the version of VLC available in Ubuntu 9.04.

Thanks,

Sean

thats is pretty cool. know what would be cool?, an app to control Ubuntu's mouse. and then use your phone keyboard to type.

---

### Post by jackhynes on 2010-06-26
> **steigerjb said:**
> thats is pretty cool. know what would be cool?, an app to control Ubuntu's mouse. and then use your phone keyboard to type.

We've been able to do it for a while now: [http://www.remotedroid.net/](http://www.remotedroid.net/)

---

### Post by sideaway on 2010-10-03
Works perfectly with my CM6 HTC Desire. Cheers! I was actually looking into writing an app nearly exactly like this, using ssh to control a range of linux servers. One request, a landscape mode, I'd love to use it on my tablet in landscape mode :)

Cheers!

[[IMG]http://img40.imageshack.us/img40/4528/screenshotjfd.png[/IMG]](http://img40.imageshack.us/i/screenshotjfd.png/)

---

### Post by sideaway on 2010-10-03
Couple of things, the shutdown feature doesn't work (have to log on as root in connectbot), a more comprehensive (accurate) volume control would be awesome, and the search feature doesn't work - just returns error, please specify a media format. I pretty sure that shouldn't be too hard to fix. Is it open source?

---

### Post by Shakz on 2010-10-03
That is so friggen awesome dude. Thanks for putting the time into making something like this. The fact that it works with VLC is a seller for me!

---

### Post by Holmen on 2010-10-04
Why can't I connect when UFW is enabled? Port 22 is open and other SSH connections work.

---

### Post by cfps on 2010-10-09
Hi 
Nice app!!!

I am having some problems using the remote commands.
I am using ubuntu 10.10 with rhythmbox, my phone is the samsung Galaxy s I9000 running android 2.1.
when I connect  i get this error message:
"init script failed with output: Linux mambo 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux Ubuntu 10.10"
An then offers me a "close"button
if I then start the app again it will show me what is playing on rhythmbox but I cant change anything. everything seems to work except the remote-commands.

I hope you can help me:)

---

### Post by constellanation on 2010-10-12
I received the same error as listed above and also am running 10.10.
Restarting the app seems to lose the connection, however.

Seeing as the original developer hasn't posted in many months nor has his sourceforge page been updated.  I don't have high hopes for a fix, which is really disappointing because everything I read in this thread, got me pretty excited about it.

I'm contemplating starting a thread at xda-developers about it, maybe they can pick up work on it there...

edit: started a thread there [http://forum.xda-developers.com/showthread.php?t=806958](http://forum.xda-developers.com/showthread.php?t=806958)

---

### Post by sideaway on 2010-10-19
oh-ou, it appears 10.10 breaks it :P

---

### Post by nekr0z on 2010-10-19
> **sideaway said:**
> oh-ou, it appears 10.10 breaks it :P
It does.

By the output it seems like the connection to another machine is initiated after connecting to the machine I'm trying to control, which is strange and scary.

Well, I double-checked and it doesn't try to connect to another machine. I was confused by the output, it first gave the usual ssh-login "Ubuntu 10.10" thing, and then followed with "Ubuntu 10.04.1 LTS" which looked like another login. I happen to have a 10.04.1 server in my network, into which the machine I'm on is authorized to log in via ssh using a key, without asking for password, thus the confusion. I checked the logs on server, there was no login at the time, sorry for misleading.

---

### Post by sideaway on 2010-10-20
Need a dev! It is open source...

I've had a look, but I really have no idea what I'm doing :(

---

### Post by ahorriblemess on 2010-10-20
I tried this application. It looks cool. I set it up, after disabling the firewall, I got it to connect. The application shows the music playing, but I can't control it. It doesn't connect with the firewall on, whether I have ports open or allow from my phone's static IP.

Ubuntu 10.10
Droid Eris on 2.1
Static IP addresses on both

---

### Post by jinliew on 2010-10-21
I'm having exactly the same problem as cfps whereby:

1) When I first log in I get the same message as cfps.  If I click ok and reopen, then Tesla connects to my computer and displays which song is currently playing.

2) I can't control the music player in any way - can't skip songs, change volume etc.

This only started happening after upgrading to Ubuntu 10.10.  I had other problems with sound previously, but I've fixed them now.

OS: Ubuntu 10.10
Music Player: Rhythmbox

I used to have Tesla working perfectly with Ubuntu 9.10

Any help would be greatly appreciated!  Such a useful app!

> **cfps said:**
> Hi 
Nice app!!!

I am having some problems using the remote commands.
I am using ubuntu 10.10 with rhythmbox, my phone is the samsung Galaxy s I9000 running android 2.1.
when I connect  i get this error message:
"init script failed with output: Linux mambo 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux Ubuntu 10.10"
An then offers me a "close"button
if I then start the app again it will show me what is playing on rhythmbox but I cant change anything. everything seems to work except the remote-commands.

I hope you can help me:)

---

### Post by fraig on 2010-10-26
There seems to be a problem with the "message of the day" (MOTD) which is displayed when logging in via ssh.

You can disable this message by editing (as superuser) the configuration files "/etc/pam.d/login" and "/etc/pam.d/sshd" and commenting out the lines containing "session optional pam_motd.so".

After doing so, my Tesla remote app works again.

---

### Post by me_cee on 2010-10-26
> **fraig said:**
> There seems to be a problem with the "message of the day" (MOTD) which is displayed when logging in via ssh.

You can disable this message by editing (as superuser) the configuration files "/etc/pam.d/login" and "/etc/pam.d/sshd" and commenting out the lines containing "session optional pam_motd.so".

After doing so, my Tesla remote app works again.

:KS:KS:KS

Ur a Star!!! now my Tesla works as well! Cheers!

---

### Post by Jose Catre-Vandis on 2010-10-29
Audacious support please ?
XBMC support please?

---

### Post by sideaway on 2010-10-31
I have no pam.d folder :(

EDIT: I realise you're talking about on the actual PC, lol whoops. Now my Tesla crashes wheneverthe player is running, I've tried both amaroK and Rhythmbox, I can connect if I select amaroK and rhythmbox is playing, but as soon as I launch amarok, my phone goes nuts... then if I play music, the app will crash... looks really weird XD

Same thing happens with rhythmbox, any ideas?

HTC Desire, Cyanogen Mod 6.1 RC.

---

### Post by sideaway on 2010-11-01
bu-u-u-mpity ump!

---

### Post by skarard on 2010-11-04
I'm having the same issue as sideaway. I disabled to MOTD and it connected but when I connect to either VLC or Rhythmbox the app on the phone keeps repeating "lost connection to media player" then eventually force closes. Great Idea with the SSH and DBUS. Should be simple. It's a shame i don't know enough about it :(

---

### Post by sideaway on 2010-11-05
lemme know if you find a solution skarard?

---

### Post by ubunterooster on 2010-11-05
I assume it to be working on the LTS still?

---

### Post by spartan7 on 2010-12-06
Just wanted to report it working properly. Desktop running ubuntu 10.04 i7, and Android Cog ROM Perception Build 7. 

Thank you for this.

PS: is there thought of adding a keyboard function? Is there an app already for that?

---

### Post by pepejackson on 2010-12-09
I will get my first Android in the next coupple of weeks! Tesla is a nice name and is quite apropriate in a way. it would bea nice touch if it could work through bluetooth. generally if you are uising the phone as a remote you'll be in range of bluetooth. I had an ancient symbian (nokia) that had an app that would do this it was basic but it worked like a treat. 
In any case kudos for the great work!!!

---

### Post by mathyou on 2010-12-10
This is a really nice program, such a shame that development has stopped. If I had the skills I'd definitely pick it up. 

It works for me with 10.04 and HTC Legend, Froyo. (after doing the motd fix).

---

### Post by plopp37 on 2011-01-12
Does not work for me; installed the SSH server on my PC, disabled the motd in 2 system files as mentioned, but after connecting to the PC, Tesla gives me this message:

Post-connection tasks failed on remote machine
Init scipt failed with output:
You have new mail.
success

And the application crashes...

Seems there is still some message output from my machine not acceptable by Tesla, how to disable it?

I have tried to include "unset MAILCHECK" in my .bashrc and .bash_profile files but that has no effect...

EDIT:

OK, I have commented out lines containing pam_mail.so in login and sshd configuration files in /etc/pam.d/ and that made the trick with checking for new mail after logging in...

anyway, Tesla crashes soon after starting, staying in the notification area

EDIT:

The crash could be caused by playing a radio with Rhythmbox Radio Browser plugin, stopping the radio made Tesla run, finally ;)

---

### Post by ste.sancri on 2011-01-14
Keep on force-closing on Galaxy S running Froyo.

Let me know if/when this bug will be fixed! It sounds an amazing app!

---

### Post by Ektor-5 on 2011-01-15
I have a problem on my ArchLinux64 with Exaile:

 Post-connection tasks failed on remote machine
 Init script filed with output: ConsoleKit session manager is not running

But I'm quite sure that it's running (from ps aux and the logs).

I tried almost everything, even logging with root! What can I do?

Thanks in advance! ;)


EDIT: Maybe I have found something... It seems that the ssh shell doesn't keep the same environment of a normal shell!

I tried to execute attach_dbus_session.sh but it didn't recognise the $XDG_SESSION_COOKIE variable in ssh shell on localhost...
But if I try to execute it in a normal shell it give me a beautiful "Success!" output. 

So, the problem now is: how to tell ssh to keep the same environment of a normal shell?

------
Ek5

---

### Post by xenotrax on 2011-04-30
Hi,

My Archos 32 is unable to connecct with Tesla to my Linux PC over SSH.
Has someone Tesla running on a Archos device?

My Error message: **Error whilst connecting to device: Host is not reachable**.

I tried with a wireless **Labtop** to connect over SSH port 22 and there was **no problem to connect**.
Is there a Firewall inside the Archos android device?

---

### Post by xenotrax on 2011-05-01
The connection is OK now
If you have the same error enable your hosts in the file /etc/hosts.allow 

for example:
sshd: 192.168.1.0/255.255.255.0

and now do a restart of ssh --> # /sbin/service sshd restart

Now I have still an error coming up..

Post-connection tasks failed on remote machine

Init script failed with output:
ConsoleKit session manager is not running

---

### Post by deonis on 2011-08-07
Hi! I was wondering, were you able to make it to work ? I have the same problem on my Nexus S.  I am absolutely sure that everything is fine with my server since I can connect to it using conectbot or any other ssh client.

---

### Post by cabez0n on 2011-08-28
Excellent app. 
Worked very well (despite some small errors) on my HP laptop with Ubuntu Natty and a Motorola Milestone android 2.2

---

### Post by Norwegiandude on 2012-01-24
I was redirected to this site after clicking the bit.ly/tesla-app:

[http://andappstore.com/AndroidApplications/apps/Tesla](http://andappstore.com/AndroidApplications/apps/Tesla)

Am i supposed to download the socio Mall-client?

---

### Post by kealan on 2012-04-21
Hello, I've been searching forums and whatnot about this problem.

When I attempt to connect to either of my computers, I get this error: **Failed to connect to remote machine | [192.168.1.150] Error whilst connecting to device: Failed to connect to SSH server, is it running?**

Background info:

[INDENT]I installed Tesla-0.14.apk on my motorola Droid a855 (This seemed to be the latest version on sourceforge)

I'm running Ubuntu 11.04

I have openssh-server installed

when I type sudo start ssh, it says it's already running.

I can connect using ConnectBot[/INDENT]

Thanks for any help you can give me,

---

