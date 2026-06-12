---
title: "Adobe flash cache worries, is bleachbit the answer?"
date: 2012-07-29
forum: Security
---

### Post by kansasnoob on 2012-07-29
Probably about one year ago I set up a very basic Media Center for streaming movies and TV shows, originally just from Hulu but now from multiple sources.

I've just been manually managing the .adobe/Flash_Player cache(s) by literally sending .adobe to the trash via "rm -r" occasionally but I wonder about setting up bleachbit?

Just thought I'd pick some brains and get some opinions :)

Many thanks in advance.

---

### Post by kansasnoob on 2012-07-31
Bump ;)

---

### Post by vasa1 on 2012-07-31
What exactly do you want to do?
Do you want to get rid of .sol files?

---

### Post by kansasnoob on 2012-07-31
> **vasa1 said:**
> What exactly do you want to do?
Do you want to get rid of .sol files?

I'm clueless regarding ,sol files :redface:

I don't even know where to look for them :confused:

In fact I'm a bit clueless about the whole nine yards, thus the question. What I was most worried about was the cruft in .adobe.

I'll show you an example soon, right now I'm working on something else while streaming Grace Potter and the Nocturnals. If I break that right now I'll lose what little mind I have left :D

---

### Post by vasa1 on 2012-07-31
I feel that for normal users, .sol files should be in their home folder.
**locate *.sol** will send a listing to your screen.
I'm not comfortable deleting them *en masse*.

The actual video files (or their byproducts) maybe in your browser's cache and would go away on clearing cache.

---

### Post by kansasnoob on 2012-07-31
From the streaming machine:

```
lance@lance-AMD-desktop:~$ ls -a
.                 .fontconfig                 .mozilla_OLDER
..                .gconf                      Music
.AbiSuite         .gksu.lock                  .onboard
.adobe            .gnome2                     .opera
AMD symlink       .gnome2_private             Pictures
.bash_history     .gphoto                     .profile
.bash_logout      .gstreamer-0.10             Public
.bashrc           .gtk-bookmarks              .pulse
.cache            .gvfs                       .pulse-cookie
.compiz           Hardware_profiles           .shotwell
.compiz-1         .hplip                      .sudo_as_admin_successful
.config           .ICEauthority               Templates
.dbus             .icedtea                    .thumbnails
Desktop           .indicator-sysmonitor.json  .thunderbird
.dmrc             .libreoffice                Videos
Documents         .local                      .Xauthority
Downloads         .macromedia                 .xsession-errors
.esd_auth         .mission-control
examples.desktop  .mozilla

```

What troubles me:

```
lance@lance-AMD-desktop:~$ ls .adobe
Flash_Player
lance@lance-AMD-desktop:~$ ls .adobe/Flash_Player
AssetCache  NativeCache
lance@lance-AMD-desktop:~$ ls .adobe/Flash_Player/AssetCache
CV46NPRP
lance@lance-AMD-desktop:~$ ls .adobe/Flash_Player/NativeCache
018F9C4F5B8996AC6E06AB3826E7F205            671FF58E5FBB02EAE5F29F07C0832F7D
19161DB1A6F7DA235681214946791CA0            A5482CAF2C9D2FEFAD9E9DEAF0010A49
226C2D9FB437BC2212C312D39081FE06            F9A67BE648B1AA6F5DCE1CEE1FC01622
28DD3C6228998A91C43098C2CB668BB6            NativeCache.directory
50A1CF0242F7480909CAF6B361521A85.directory  Updater.directory

```

Visually:

[ATTACH]222049[/ATTACH]

[ATTACH]222050[/ATTACH]

[ATTACH]222051[/ATTACH]

Lots of cruft!!!!!!!!!!!

---

### Post by kansasnoob on 2012-08-01
Well I did some playing with bleachbit. It works OK to clear the .adobe/Flash_Player/AssetCache but doesn't touch .adobe/Flash_Player/NativeCache.

I'm sort of thinking about creating a startup script that'll:

```
cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache
```

Any thoughts :confused:

---

### Post by houseworkshy on 2012-08-01
Bleachbit will remove most of the rubbish when run with sudo, including the flash cache,  but not the sqlite from firefox.  Be careful when setting it up or you could take out stuff you want to keep,  I like to keep all the language supports for example and don't feel the need to securely wipe disc space as I never buy or bank online.
Another thing for flash video is a plugin for firefox called "better privacy" which deleles what they call super cookies ( lso's).  These are usually associated with flash video.  If using firefox  click on Tools, then addonns, then find the add on and click more to read up on it.  Getting them off your drive will save a little space as they usually last for ever.

---

### Post by kansasnoob on 2012-08-01
> don't feel the need to securely wipe disc space as I never buy or bank online.

Likewise on this one puter, it's dedicated to media streaming alone. OTOH it is connected to a wired network with computers that are used for banking and on-line purchases.

---

### Post by houseworkshy on 2012-08-01
Oooh me too, of course ....  the web!  Ooops.  Ah well I never do selling transactions online either so my non-existant clients should be safe anyway.  Well I hope so,  don't much fancy; "Dear Sir,   Just because I don't exist it doesn't mean that I don't have rights.   With referance to the court summons for not taking adequate steps to protect my private details  ....."  I bet non existant people are really keen on privacy too, I never hear anything about them.

---

### Post by kansasnoob on 2012-08-01
> **houseworkshy said:**
> Oooh me too, of course ....  the web!  Ooops.  Ah well I never do selling transactions online either so my non-existant clients should be safe anyway.  Well I hope so,  don't much fancy; "Dear Sir,   Just because I don't exist it doesn't mean that I don't have rights.   With referance to the court summons for not taking adequate steps to protect my private details  ....."  I bet non existant people are really keen on privacy too, I never hear anything about them.

I was actually talking about my own super cheap wired router:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156001](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156001)

I'm a skeptic when it comes to so called router security :)

---

### Post by tubbygweilo on 2012-08-01
The Mozilla add-on [betterprivacy]("https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/")offers some form of control over flash cache and other assorted bits and bobs. 

May be worth a look as in conjunction with other ideas, add-ons & code may well do the job.

---

### Post by houseworkshy on 2012-08-01
"I was actually talking about my own super cheap wired router:"

Ah, sorry about that.  I just felt like being silly it wasn't actually a real comment.  

I think that your right about security.  Given a strong motivation, skills and equipment anyone could probably get anything. But if one is insignificant and poor perhaps one can make it too tedious to be worth the effort when so many other soft targets, who haven't even tried, are up for grabs.  Avoid facebook if you ever do enable wireless is one tip
[http://archive.org/details/FiresheepVs.Facebook](http://archive.org/details/FiresheepVs.Facebook) 
Never bank online, why do Paypal et al  need to keep making public statements about how safe they are anyway?
Other wise head down,  nose clean,  do the security basics and stay updated is good enough at the moment.  Not sure how long the linux honeymoon will last so make the most of it, as it becomes more popular it will attract malware and it'll be back to a high percentage of time going on mending things instead of just using them.

---

